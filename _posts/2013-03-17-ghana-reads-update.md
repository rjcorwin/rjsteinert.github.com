---
layout: post
category : lessons
tagline: "Supporting tagline 2"
tags : [intro, beginner, jekyll, tutorial]
---
# The BeLL LMS, now in 10 Schools 
In January, OLE Ghana with the help of OLE International deployed to 8 schools each a Raspberry Pi Server and 35 tablets.
2 additional installs were deployed in the Central East region after I left.  
OLE Ghana has a team of 5 coaches that are now using the BeLL LMS on the Raspberry Pi Servers to help coach teachers in the ten schools. 
(Could use a blurb on exactly what the Coaches are Teaching teachers)

![Raspberry Pi Servers in ten schools in Ghana](school-collage.jpg)

When one thinks of "Learning Management System" (LMS), one often thinks of tools to help teachers manage a student's learning experience.  
The OLE Ghana team took this a step further and built a tool to help a Coach manage a Teacher's learning experience.  
In the BeLL LMS, a teacher uses the Lesson Plan tool to select Resources in the Library and answer questions about how they will approach using those Resources.

![Lesson Plan Tool](lesson-plan-tool.png)

Coaches can then review the Lesson Plans that Teachers have submitted and provide feedback on the Teacher's development.  

![Coach Dashboard](coach-dashboard.png)



# Next steps
As part of OLE International's BeLL Project, we've been building a Library system that works offline and distributes data from school to school via traveling SD Cards. 
This allows us to build Collection Creation tools for teachers that behave as if they are all connected to the Internet and using the same One World Library App. 
In order to accomplish this, it was important for us to realize that there are two types of data in schools. 
Data that needs to be shared across the network and data that that only needs to end up in a central office. 

 __Shared Data between Schools__
- Resources
- Feedback on Resources
- Resource usage
- Locally generated Collections


__Site Specific Data shared with a Central Office__
- groups
- users
- assignments
- student progress

Using CouchDB's "Eventual Consistency" feature for data, we are able to spread the data in the shared category via SD Cards to all schools giving them an experience that they are all using the same website.  
When Teachers create Collections in the One World Library App and then assign those Collections to their Groups in the BeLL LMS they'll be able to review the feedback that teachers in other schools have given to resources. 
To keep things simple for teachers in the Ghana Reads program, we've created a default Collection for each Group which the Teacher then manages as an ongoing Collection that gets synced to their Class's devices as opposed to creating a new Collection every week. 
Teachers can then give feedback on those Resources they used, feedback that becomes "Eventually Consistent" around the network  as if everyone is using the same website.  
We'll soon be connecting this offline website to the Internet and other Sneakernets, at that point it will truly be a One World Library App.    

Here's an annotated walk through of the system as it stands now.

<a href="https://raw.github.com/open-learning-exchange/OLE-Development-Blog/master/20130317-Ghana-Reads-Progress/one-world-library-app-in-bell-lms.jpg?login=rjsteinert&token=09899817295d8b502f367cfabb04dd55">
![One World Library App in BeLL OMS](https://raw.github.com/open-learning-exchange/OLE-Development-Blog/master/20130317-Ghana-Reads-Progress/one-world-library-app-in-bell-lms.jpg?login=rjsteinert&token=09899817295d8b502f367cfabb04dd55)
</a>


## Getting Collections to Devices
The next immediate step is to make sure that these collections get synced properly to the Ghana Reads App for Android.  
The One World Library App is currently generating Collections in the Khan Academy Topics format (KAT) which means the generated Collections can be viewed on the following Apps.

- Khan Academy Lite
- Khan Academy Extra Lite for Android
- Flying Owl serverless content browser that can be played in most web browsers straight from a USB Drive.  

The Ghana Reads App uses a custom XML format for Collections, we'll need to either start generating Collections in that custom XML format or modify the Ghana Reads App to understand KAT files.

## Gamify the Collection Creation Process
OLE Ghana and OLE International will be collaborating in the coming weeks to work on making the process of creating Collections more user friendly and provide incentive structures for participation.  
In other words, we're going to gamify the process of creating Collections.  
Some ideas so far include...

- A point system that rewards teachers for being the first to comment on a resource in the library
- A one screen/no page reload experience of creating a Collection
- The ability to configure a Resource when adding it to a collection (ie. Set the amount of time a game/book/video should be played, set the focus of a game, etc.) 

## Teacher tools for tracking student progress
While the focus of the Ghana Reads program is first on training the teacher, we also want to provide the teacher tools to help aid them in their students learning process.  
We were saddened that between the time we started planning the Ghana Reads program and its inception, Innovations for learning discontinued their Teacher Mate product for offline use in the classroom.
We were however extremely excited to find out about the KA Lite project this past December which specifically focuses on giving teachers in offline classrooms the tools to help them understand a student's progress in their course work.  
We're currently looking at ways to integrate that with our current system. 
The OWL App can already generate collections that can be used in KA Lite but we may also want to integrate accounts between the BeLL LMS and KA Lite.

![KA Lite Dashboard for Teachers](ka-lite.png)


## Interactive Exercises for Early Grade Reading
Last year one of our first experiments with the Raspberry Pi, in collaboration with Innovations for Learning, was to try to get the Teacher Mate OMS to work on a Raspberry Pi.  
Unfortunately we found ourselves in a similar situation as [Khan Academy's "Khanberry Pi" experiment](http://jamiealexandre.com/blog/2012/12/12/what-i-did-at-khan-academy-khanberry-pi-ka-lite/) and found we were unable to achieve something we thought was stable enough to deploy.  
Since we've taken a lighter weight approach, we still have yet to achieve the quality of interactive content found on the Teacher Mate system.  
We'll continue to experiment with "carving" the Teacher Mate content out so it can be distributed using the One World Library App as well as pursue making our own interactive content that is similar to the Teacher Mate's content.  
[The BeLL Video Book Player](https://github.com/open-learning-exchange/BeLL-Video-Book-Player) is an example of one of our first experiments. Next month, I'll actually be teaching a workshop in Ghana on how to make Khan Academy inspired "no frill" Video Books. 
I'm looking forward to it!  
A big thanks goes out to OLE International volunteer Christine Manzo for helping to pioneer this concept.  
Her Video Book examples were crucial in demonstrating the value of the Video Books.

## Connecting the Sneakernet with the Internet using the OWL Bridge
One of the great things about having an app that adheres to Eventual Consistency in a Sneakernet is that it's possible to build a bridge between the Internet and the Sneakernet.  
The OWL Bridge project is just that.  
We've been working closely with the Jake Johnson of Archive.org to build on top of their API a bridge that makes this Sneakernet to Internet connection a reality.  
We've currently built the bridge so that it can move resources from Archive.org on the Internet to an OWL App instance in the Sneakernet.  

![A screenshot of our OWL Bridge prototype](owl-bridge.png)

Meanwhile, Librarian Christina Manzo has been [curating a excellent collection of content in our BeLL collection on Archive.org](http://archive.org/details/bell).  
In the coming months we hope to build a bridge that pushes data from an OWL App in the Sneakernet to Archive.org on the Internet.

# A parting note
**Phew** We have some lofty goals and a shoestring budget to do this on.  
We're currently only three developers (Stefan in Boston, Leonard and RJ in Ghana) so if you would like to join forces let us know! 
Also, on a sad note, our beloved OLE Ghana Mobile, the personal car of the Director of OLE Ghana and also the car that we depend on for servicing schools, recently bit the dust. 
If anyone knows of a good used car in Ghana let us know!















