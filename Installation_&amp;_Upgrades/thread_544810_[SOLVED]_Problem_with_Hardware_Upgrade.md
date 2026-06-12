---
title: "[SOLVED] Problem with Hardware Upgrade"
date: 2007-09-06
forum: Installation &amp; Upgrades
---

### Post by MacDuff on 2007-09-06
Have been running Ubuntu 7.04 on an older computer but other than slow operation it ran fine.

I decided to install a new motherboard and processor to improve performance and I have grief!  My techie told me that components should work perfectly with Ubuntu but  I cannot boot up.

The new board is a Foxconn 945G7MC-KS2HV and the CPU is an Intel CORE 2 Duo E6420
There is no external video card, video is provided by the on-board video connector.

When I boot from the original hard drive I get the following message:

================================
X Windows System Version 7.2.0
Release date 22 January 2007
XProtocol Version11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu 
Current Operating System: Linux ubu-comm 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686
Build Date: 04 April 2007

Before Reporting problem check [http://wiki.x.org](http://wiki.x.org) to make sure you have the latest version

Module Loader Present

Markers: (- -) probed, (**) from config file, ( = =) default setting, (++) from command line, (!!) notice (II informational, (ww) warning, (EE) error, (NT) not implimented, (??) unknown.
(==) Log files:"/var/log/xorg.0.log", Time Thu Sept 6 15:57.07 2007
(==) using config file:"/etc/X11/xorg.conf
No devices detected.     f" 
			<OK>
=======================


If I try to boot from the Live CD, there do not appear to be any error messages 
and I get the tan coloured Ubuntu screen with the chokolate coloured inset in the centre but then the mouse stops working and the system freezes.

Anyone have any suggestions?

Mac

---

### Post by merlinus on 2007-09-06
IIRC, making major hardware changes almost always requires a fresh install.

-merlin

---

### Post by MacDuff on 2007-09-07
Hi Merlinus:

I figured that but when I try to do a new install, I get to the point where the tan coloured Ubuntu screen opens and then the mouse stops working and the system freezes.  It does not get to the point where the install icon appears on the desktop.  On one try I did get a couple of icons appear at the top bar but nothing in the main desktop.

Assuming it might be a video problem, I tried several installations with difference video settings but no jou

I also tried downloading and burning another image but it did not change anything.

Any more suggestions?

---

### Post by merlinus on 2007-09-07
Alternate text-based install cd will not have video problems.

-merlin

---

### Post by MacDuff on 2007-09-07
Will give that a try.  Should have thought of it myself!

Thanks

Mac

---

### Post by merlinus on 2007-09-07
You are most welcome.  Glad to help.  Let us know how it goes.

-merlin

---

### Post by MacDuff on 2007-09-07
Hi Merlin:

I thought I knew where to find the Alternate CD but I just had a look and can't find it.  Where is it located?

---

### Post by merlinus on 2007-09-07
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Tick the box below the green Start Download text, then click the text to begin.

-merlin

---

### Post by MacDuff on 2007-09-07
Duhh OK

I am REALLY not as vacant as I sometimes appear to be.  But those of us who get in a rush OFTEN don't read what is right in front of us.

I knew I had seen it somewhere.  In fact I probably have a copy of the Alternate CD somewhere but with all the changes taking place I could not find it.

By the way, the monitor on what is to become my dedicated Linux box, (if I ever get it running) just burned out so I guess somebody does not want me to run Linux.   I am off to the monitor store for a new one.

Thanks Merlinus

Mac

---

### Post by MacDuff on 2007-09-08
Hello again Merlinus:

You asked to be kept informed.  I think I will write a book!
The alternate install disk installed perfectly BUT the system would not run more than about 5 minutes before freezing.  It did not seem to matter what it was doing: downloading updates, installing updates, changing preferences.

This is the first experience that the people at the shop that has done my servicing for the past few years, have had with Ubuntu and they were surprised at the problems we are having. 

They made telephone calls to their supplier and gamely started swapping out parts of the new system,  without any success so far.  They were frustrated by the fact that every time a component is changed, Ubuntu has to be re-installed.   That wastes much time and since they know even less than I do about Ubu, I stated with them to do the testing.

Since we here are all "babes in the woods" that brings me to a a series of serious questions:
1.  Is there any way to avoid a complete re-install of all the applications that come with Ubuntu?
Can just the OS be installed?  I noticed that on the alternate CD there is mention of a "Manufacturer's Installation".  Is that, perchance, a stripped down version of Ubuntu?   I tried to use the "Repair system" option but it did not appear to work or I did not know how to use it.

2.  Can Ubuntu be re-iinstalled over top of the previous installation? If so, how can that be done?  It seems that each time Ubuntu is re-installed it insists on re-partitioning the drive.   Any advice you can offer would be appreciated.

My tech shop had to order some more components to try.  When the order comes in we will continue to swap parts to see what fixes the problem.

All of the parts are brand new and supposedly have worked successfully in other Ubuntu installations according to the wholesaler who supplies my local shop, so everyone here is a tad frustrated.  I keep telling myself that one of the pieces HAS to be defective since Ubuntu worked on my old  computer but drove my wife crazy using Firefox.  FF was so terribly s l o w w w when multiple pages were loaded that she freaked out and refused to touch the Ubuntu box. 

My reputation is hanging by a thread on my decision to impose a Linux computer on our office.  Were it not for the fact that we have three other (Windows) machines to fall back on, we would be out of business at the moment.

Answers to the questions posed and other suggestions would be much appreciated.

Mac

---

### Post by merlinus on 2007-09-08
Sounds like a tale out of the Twilight Zone.....  :)

You can reinstall ubuntu by selecting the partition it is already installed on, and choosing to reformat only that one for / (root).

If you have created a separate partition for /home, then all of your settings, preferences, bookmarks, email, etc. will remain untouched.  Just do not format that partition upon reinstall, or upgrade.

Unfortunately, you will have to reinstall apps that are not included on the install cd (e.g. thunderbird, thunar).

Good luck!  And tell the techs that they are getting a free learn-as-you-go education, which will serve them well as more and more folks switch to linux!!!

:guitar:

-merlin

---

### Post by MacDuff on 2007-09-08
Thanks Merlinus but I am not clear on your response.

Question 1 was:

Is there any way to avoid a complete re-install of all the applications that come with Ubuntu?
Can just the OS be installed? I noticed that on the alternate CD there is mention of a "Manufacturer's Installation". Is that, perchance, a stripped down version of Ubuntu? I tried to use the "Repair system" option but it did not appear to work or I did not know how to use it.

You mentioned an install CD.  Is that the Alternate CD?  Is there just a System install on it somewhere whereby I can just re-install the OS without always re-installing the applications?  If so, how do I go about that?  Am I missing something or is there a hidden command somewhere?

I have not received word that the parts are in so it may be next week before the next chapter unfolds.

Mac

---

### Post by merlinus on 2007-09-08
Unless you do a barebones install ([http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)), everything on the installation cd will be installed.  In doing a reinstall, the partition into which you are doing this needs to be re-formatted, so everything is gone.

If you do a barebones, you will still need to install applications, etc., as outlined on the link above.

Also, as I said, a separate /home partition is not for the apps themselves but for configurations, preferences, settings, and such.  Even if you do not, be sure to back up that folder, and make sure Show Hidden Files is activated before doing so.

I know nothing about a Manufacturer's Installation.

-merlin

---

### Post by MacDuff on 2007-09-08
This has been quite an experience Merlinus.  I still do not have a functioning Ubunut 7.04.

We spent the afternoon swapping out everything on my new box and every time we started the system, it would freeze, sometimes before the nautilus screen appeared, sometimes when down loading updates, sometimes when installing them but always withing 5 minutes of starting the system. 

Everyone was quite frustrated. One of the least experience staff spent most of her time poring over information on the Internet and suggested that most people seem to be having trouble with 7.04 freezing when using it on the latest hardware.  She suggested that we try version 6.06 and just before the store closed this afternoon, we burned a live CD of it to try.  It seemed to work perfectly but I did not have time to actually install it.  Tomorrow I will remove all the various versions of Ubuntu that we tried (32 and 64 bit) with different video cards and configurations.  I will also remove the windows installs (which were very smooth, thank you very much).    After re-formatting the drive I will install 6.06- 64 bit Ubuntu and try it out.    My only concern is that I don't think it can read and write NTFS and I wanted to use this computer as my communications server as well as a desktop machine.  

However if it does work with the FoxConn motherboard, Intel DuoCore chipset and Asus graphics card then perhaps in another month or three, the next version of Ubuntu will be out and it may support the hardware I have.  Certainly a hell of a lot of people seem to be having problems similar to mine and someone must be sweating bullets over it.  

I have spent almost a grand and over 100 hours of my time trying to make the transition to the "free" OS known as Ubuntu Linux.  I have said it before, and it bears repeating "If money is a concern, stay with Windows.   If money and time are no object, you can build a great deal of character playing with Ubuntu."  

As stubborn as I am, I will not give up...... although the temptation has been great lately.  I started playing with the Live CD in April and still do not have a Ubuntu system that does what my old Windows XP system did.

Mac

---

### Post by Pumalite on 2007-09-08
I installed Ubuntu 7.04 at the first try on an Intel D975XBX, Core 2 Duo, 2 GB Ram, Nvidia 7800GT, and 3 SATAII drives

---

### Post by MacDuff on 2007-09-10
Well I finally have Ubuntu working on the hardware but it is not 7.04 which is what I wanted.
We installed Version 6.06, 64 bit and that has worked perfectly for the past day. 

Now my concern is:  Will I be able to install Ubuntu 7.04 and future versions or am I stuck with version 6.06 for ever and ever amen.  My techie and I both wonder why the newest version of Ubuntu will not work with the new hardware but an older version will.

Can anyone explain?

Thanks

---

### Post by Pumalite on 2007-09-10
It's just not 'the right new hardware'. Try one of my systems and you are all set.

---

### Post by merlinus on 2007-09-10
> 
Try one of my systems and you are all set.


Great!  I will await the UPS or Fed-Ex Delivery truck!!!

:guitar:

---

### Post by Pumalite on 2007-09-10
ha, ha, ha. How are you doing Merlin?

---

### Post by MacDuff on 2007-09-11
Pumalite:

Tell me more about "one of my systems".  What motherboard are you using with that chipset (Intel D975XBX)?

Bear in mind that I am a newbie and my mind is overflowing with information provided by many people, (much of it well meaning but just added to my problems).  

Try to explain everything to me in non-technical words if that is possible and please tell me everything I need to pass on to my local service shop.  They have been searching for solutions and their supplier appears to also be stumped.

Thanks
Mac

---

### Post by MacDuff on 2007-09-18
You were right Pumalite.

It just wasn't the right hardware.  On the weekend we replaced the new Foxconn board and Intel Core 2 with a Gigabyte S series board and an AMD 64 processor.

FINALLY 7.04 works and everything works at the speed I would expect.  I have the 32 bit version of Ubuntu 7.04 on it and am satisfied with its performance.  Having spend so much time in computer perdition, I am not anxious to install the 65 bit version right now.

This has been a real trial, not only for me but for my service shop.  However the head guy there who is a certified Microsoft engineer, has become so intrigued by my mission to get Ubuntu running that he started playing with Ubuntu on one of his home computers.  Hopefully he will not have a fraction of the grief I had but if he does, I am around to give him suggestions based on my experience.  

A HUGE part of the solution to problems of Windows trained computer users installing Linux is that we do not know what to look for or even where to begin.  Answers provided on forums usually assume that the person seeking help has some knowledge or experience with Linux.  It takes months, perhaps  the better part of a year to get enough experience to get meaningful help from the forums.

I don't mean to put the forums down because if it was not for the encouragement provided by them, I would have trashed Ubuntu months ago.  It is just that those of us who are new to Linux are really clueless when it comes to applying the suggestions provided in the forums.   You people who know it all forget what it was like when you first began to use Linux.

A local Ubuntu user to whom I could have called upon for advice would have been a great benefit.  Hopefully as more and more people experiment with Linux the day will come when such people are more plentiful.   I know that I will certainly do my best to encourage those with whom I come in contact, to persevere because, in the end, I believe that Ubuntu will be the OS of choice for the thinking computer user.    

Actually during the process I endured, I often thought that, given the right hardware, Ubuntu would be a better choice than Windows for a new computer user or someone who had only limited experience with Windows.   A client of mine who has better than average knowledge  of the various Windows Op Systems  purchased a new laptop loaded with Windows Vista and he has spent days trying to get Vista set up.  His son (the manager of IT services in a government department) and spent three hours trying to change Vista settings but with only limited success.  In the end he suggested that his dad blow out Vista and install XP on the machine.  

Anyway, we are making headway and within the next couple of months, I hope to be in a position to assist others around me when they become interested in a better alternative to Windows.

Mac

---

### Post by Pumalite on 2007-09-18
I am very glad you got it working. I like your attitude; it's the right one for Linux.

---

