---
title: "Linux in general not appreciated from company techs"
date: 2007-12-21
forum: Installation &amp; Upgrades
---

### Post by Browser_ice on 2007-12-21
Even if the subject mentions Linux in general, I think the Ubuntu team should have a look at it to perhaps see if they have the same problem and if they can improve it to make the client happier.

I work at IBM as a contractor for a Consulting Agency and this week I had a surprising comment from a technician that came to work on a client's server. I do not recall if he was an IBM technician or from another company.

I had seen him a couple of times so I started small talking with him and we happened to mention Linux. He said it is a great software and his client had chosen to use Linux on most of his servers because it is free and because it is open source. But he did mention the one thing him and all other technician hate about Linux. It is something that are giving them more and more painfull work to do at an increasing rate.

He said it is not rare to see a 200Mb update to do an a Linux server every day. He said because they have to insure that all the client's applications are not impacted and still running ok, that they have to do compatibility tests on the client's server, almost every day. He said that this is very time consuming and that it leaves him less and less time to work on the other tasks he has to do. 

That made me think about Ubuntu and all its deratives: 

Everytimes there are updates to be released, how deeply are they tested and what is included in their tests. 

Are the updates tested only against all the O/S componants ?

Are the updates tested against all major company softwares running on Ubuntu client servers ?

Do the support team receive company comments telling them their update is not compatible with an in-house software they have ?

I am just curious about this. If there is a potential problem in this area, then it is in the best interests of the Ubuntu team to adress this to make the client happier and therefore, make Ubuntu even safer then all other Linux O/S out there.

If the team doesn't think there are issues there, can they make a small survey on the client side to ask their technician if themselves are having issues ?  Just because the client says they do not have issues, doesn't mean their technician/support team don't. Maybe one day it will become an issue because their technician/support staff simply cannot keep up with the changes or that major compatibility issues are poping up.

Call it a safe precaution to ensure there are no problems on that aspect. Make sure Ubuntu is a step ahead of all other Linux O/S to make client's switch to Ubuntu even more. Include a simple comment with each client's install or update, to tell them Ubuntu has been fully tested and if known issues have been detected (with a resultion ETA). All this, just to make the client feel even more confident into Ubuntu.

What do you think Ubuntu team ?


added notes, hummm, wanted to change the title but looks like I cannot.

---

### Post by RIchard James13 on 2007-12-21
> He said it is not rare to see a 200Mb update to do an a Linux server every day.

Sound like a load Chinese whispers to me. Someone said they had to do 20MBytes a Month and you get the end version where it is 200MB/day. You have to ask yourself when someone tells you a ridiculous number like that, what is that 200MB/day of code actually doing? Who is writing it? What value does it add to the server? to the business? Obviously the number is made up because no business could survive any such process for very long.

> He said because they have to insure that all the client's applications are not impacted and still running ok, that they have to do compatibility tests on the client's server, almost every day.

In most large enterprises this is true for every software change you make to a system, it has to be tested. It does not matter what vendor your Operating System comes from because the Operating System is a single piece of the puzzle. You have the Hardware the Software, Networks, Security systems etc to check. Also most companies run some of their own proprietary software and that can never be tested by an outside vendor. Also each business is unique it what software they have on their computers because each business has different business needs and their automation customized for that. 

In most of the companies I work for they follow a model similar to the following. They dedicate a group or department to testing each version of the software for each of the pieces of hardware (a development/deployment group). This group then sends updates out to the technicians who update the systems, normally over the network. Then there is the service and maintenance groups (I work in that area) when a server falls over or a users machine needs to be rebuilt we get the software and install instructions from the development/deployment group.

Because of the cost of maintaining a lot of different software and hardware most companies choose to select just a few computer types and a specific OS and specific applications. This is called SOE or Standard Operating Environment. This eliminates the need for a lot of upgrades and testing. However SOE normally only applies to workstations, servers are different. There are very few servers and lots of workstations. But servers are still tested before being rolled out and most of the time they are hardly touched because they don't need updates. These are not Internet connected systems. These are the databases that the business applications run off of. A business that had a lot of Internet usage would use different deployment and maintenance models.

Most of the work I do is for companies that do retail so their servicing and deployment policies are different from say manufacturing or logistics. In retail shops close or go into periods where there is not as much usage as others, so we try to fit in repairs at those times to avoid disrupting business.

I can't really answer the rest of your questions about Ubuntu since I don't work with Ubuntu servers, I am not in any business relationship with Canonical, I am not a Ubuntu developer.

I have maintained in the past a Slackware Server that I built. But that was for a very small organization 10 people.

The only thing I can really say is that when you talk about business and computing is there are thousands of different business types, there are small, medium, large and huge businesses, there are businesses that are in niches and others that cover a broad range of industries, so saying X piece of software or hardware doesn't work for my business does not apply to all other businesses. Each business has unique needs and the job of making a server OS is a small part of fulfilling that need, there are other companies out there that will take a Linux Server and deploy custom apps for a specific range of businesses and then supply all the support for those products and then there are corporations that do all that work themselves. Some OS developers also offer that sort of service, I think Redhat uses that business model.

---

### Post by jespdj on 2007-12-22
So one person, who is likely biased (he works for IBM and wants to sell IBM hardware and software, such as AIX instead of Linux), tells you his opinion, and then you immediately believe that everything he says is true?

Linux is very popular for enterprise use. Probably Red Hat Enterprise Linux is the most popular distribution for this purpose.

On the project I am working on, our client was first using OpenVMS, because of its reputation of stability and reliability. But OpenVMS is slowly fading into history, and for example Java doesn't work that well on OpenVMS. So they replaced OpenVMS by Red Hat Enterprise Linux and now the systems are a lot more stable, no problems with Java, and the software also runs twice as fast.

I don't know about Ubuntu Server; I think Ubuntu is in the first place geared towards desktop users, and I've never seen Ubuntu Server being used by a company, but probably they are out there. In my opinion, there are other Linux distributions which are better than Ubuntu for enterprise server applications.

---

### Post by gilgongo on 2007-12-22
Agreed - ithis is what Red Hat is all about. They test and maintain all updates to their distros against a set list of supported hardware and software to minimise the chances of stuff breaking between updates. 

It is true that free distributions (like Debian and Ubuntu) *may* display problems between updates more frequently than Red Hat (or Windows), but we are still talking about a very low instance of problems. The guy you talked to said that updates needed to be checked daily, but did he say how often problems were *detected*?

---

