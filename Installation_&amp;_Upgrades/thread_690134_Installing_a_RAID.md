---
title: "Installing a RAID"
date: 2008-02-07
forum: Installation &amp; Upgrades
---

### Post by SteveHillier on 2008-02-07
Right at the outset I record my thanks to kragen for kick starting the process, Keldek for adding another twist to the tale and to the seemingly unknown author of the Quick HOWTO: Ch26: Linus Software RAID.

What was I trying to do.
I am creating a webserver and thought I really ought to offer some security as we will be hosting client sites on this machine.  The obvious choice is to use mirrored disks - hence RAID 1.

I first tried with Dapper but no matter what I did I could never see more than the first of three SATA disks.  As Plesk supports both Dapper & Gutsy I moved to Gusty.  I had several attempts to install on to my AMD64 machine using the Live CD but I could not get the install disk to run.  In a different post I have recorded my efforts with this.

I then used the alternate CD which gives more control over the install process.  Despite the good advice offered by kragen I could not set the RAID up this way.  kragen's comments are good but I did feel that for an absolute beginner (and even me) there was not enough detailed comments in the advice.  To a user who has never done a manual partitioning (which as it happens is NOT me - I remember early DOS days of partitioning with FDISK) I did feel that kragen's description that goes "On my two identical 250GB drives, I created two 1 GB swap partitions, two +150 GB partitions ......" could have benefitted from a description of how to set a partition up, the type of use, the format, and mount point etc.  It is not straight forward as you have to partition the disk then create the RAID and then partition the RAID etc.

I completed my install to find no RAID and no data at the mount point I specified.

I then came across keldek's useful post.  I got dmraid which told me I had no RAID.  I was beyond asking why at this time as I thought I had partitioned OK.  This forced back to consider how to set up a RAID on a working system and I did have a panic when he spoke about writing details to the GRUB loader.  Writing to boot loaders is for cleverer people than me.

I then came across the HOWTO.  This uses FDISK but I chose to use gParted to do the actual partitioning.  I found this tool very useful because it was a clue that the RAID Disks were present on the machine but not being seen by the user.  The 'devices' menu option showed this.  

Having partitioned the disks OK the HOWTO now came into it own.  A good description of how create the raid using mdadm - worked like a dream.  Then an equally descriptive on how to format that RAID - beautiful.  Then a desciption of how to set up mdadm.conf.  The only problem here that was not in the HOWTO was that, unlike everything else, I could not get it to run with sudo in a terminal.  I had to log on as root through the text window.  Creating the mount point and setting it up to mount automatically were equally well described.

This has been a very long process and at times a frustrating one.  What really gets me is that you spend hours struggling and then when it does work it takes only a few seconds and it is a bit anticlimactic.  After hours of struggling you really expect the machine to get up and do a dance or something.

It is probably a good thing that for the most part users do not have to do these complicated things and that is what makes Ubuntu such a better offer than the other distros I have used.  For the most part you can get a machine up and running and usable with the same (or maybe greater) ease than Windows.  With any luck there will be thousands of Ubuntu users out there who have installed and are running the system without having to resort to the forum or the thing we discuss here.  If there are it is a sign that Ubuntu is working as it should.

I do want to leave this post with one thought to provoke the mind.  For the most part we are all using the same tools to do the same job so why is it that parted works for some people and fdisk for others?  Why is it that kragen's method worked for him and others but I could not get it to work?  Why is it that keldek's process got me results when I ignored most of the early parts of his advice?  Why is it we can all get it to work for us when we pick and mix advice from different players?  Why is it that for some people the Live CD works when for others the alternate CD is needed?

Lolgic would tell you that given the same set of tools and the required outcome then there should be one method that would work for ALL people ALL the time.  Maybe it's like the advice I got way back in the mists of time when I started programming in C.  I was told that it was not a case of "How do you do this or that" but rather "How am I going to do this or that TODAY!"

Must go now.  I have a customer who is having problems getting client machines to access a database on the server.  I suspect firewall issues due to a recent upgrade because it was and has been working for 2 or 3 years now.  If only I could get the customer to use proper client / server systems rather than peer to peer Win XP.

---

### Post by bwtranch on 2008-02-07
Very interesting post. I have often wondered the same thing as I try to help people with their problems (not always computer-related). Why does one thing work and another doesn't? Sometimes it's like analizing the flea to see what was wrong with the dog. A little intuition goes a long way, but it does not always get you all the way home. I suppose it comes down to the human condition. Humans make machines and they will always be an image of ourselves. Flawed in some way, although we like to think of them as perfect (unlike us), but they are flawed just as we are.

But it's not so grim as all that. Look at what we have accomplished. I am communicating with you and everyone in the world who wants to read what we have to say. This has never been done before and is a proud moment in human history, and we are part of it.

That's not what I started this post about, but it's OK. What I really wanted to say is that you are ready for Gentoo [www.gentoo.org](www.gentoo.org)

Have a nice day, my friend. I wish someday we might meet and have a really interesting conversation.

---

### Post by SteveHillier on 2008-02-07
Message to bwtranch - thank you for your reply.
Jut picking up on your comment about our being able to communicate.  When I started in this business getting on for 30 years ago there was a lot in the press about how can we get IBM machines to talk to DEC, or Burroughs, or Wang or all those others (the PC hadn't arrived at that point).  Boy haven't we come a long way since then!!
That's all for now.

---

### Post by SteveHillier on 2008-02-12
> **bwtranch said:**
> 
That's not what I started this post about, but it's OK. What I really wanted to say is that you are ready for Gentoo [www.gentoo.org](www.gentoo.org)

OK.  Never one to be faint hearted I thought I would take a look at this Gentoo stuff.
I tried the universal install disk, but it is not that universal as my AMD machine did not think the CD was bootable - even on the second burn.
Not to be beaten I got a Live CD version.  It booted OK and I like the front end.  Having a few icons on the desktop looked neat.  I was brave and thought I would use the command line install process and it all went well up to the partitioning moment I thought I had got it right but it failed to go beyond the partitioning stage.
OK so let's try the GLI installer (graphics mode).  Again it went through OK.  I set up the partitions and mount points but then the install failed.  Back again to the partitioner.  Chose the 'let the installer choose' mode but again the install failed.  at one stage there are text messages that break out of the graphics field and then the install fails.  Some message about not being able to create a location on the disk.
I can't even be fagged to write it down and inform the Gentoo crew.  That is for them to sort out.
I have a distribution thats works out of the box - it is called Ubuntu.
Why should I bother with others.  
I haven't tried Redhat or fedora for a couple of years but I have not forgotten my failed attempts at getting a working system with those distros.
I tried OpenSUSE 10.3 the other week.  It gave me a GRUB error and would not install.  I have notified the team but no one has told me there is a fix.
I have now tried Gentoo but I have not got beyond the Live CD stage.
Now let's think here.  Speaking to a friend last night work works for a UK based High Street Bank, they have concerns.  They currently use Windows XP, like most business does.  Similar to other businesses they have not migrated to Vista.  I do not recommend Vista to businesses and while I can still get XP I will use it.  Vista SP1 is due but delayed and in fact is long overdue.  Microsoft are talking about withdrawing support for XP and so supplies may dry up (maybe I should stock pile some)
So lets think, XP become unavailable.  People do not want Vista.  Where are they going to turn to?  Apple?  Linux?
Unless distributions are able to make installation faultless then Linux is never going to get the corporate market, it will remain in the hands of a few die hard computer techies as a curiosity or the bespoke markets such as TV decoders and recorders where no one knows they are running a computer underneath the sexy packaging.
For this operating system to catch on we have to have faultless reliable installations, an easy way of installing commercial packages, and a plethora of business software supported on the system.
Are we up for it?
Me, I am going to complete the installation of my web server.  Guess what I am using?  It is six letters and starts and ends with a 'U'.

---

### Post by bwtranch on 2008-02-12
> **SteveHillier said:**
> OK.  Never one to be faint hearted I thought I would take a look at this Gentoo stuff.
I tried the universal install disk, but it is not that universal as my AMD machine did not think the CD was bootable - even on the second burn.
Not to be beaten I got a Live CD version.  It booted OK and I like the front end.  Having a few icons on the desktop looked neat.  I was brave and thought I would use the command line install process and it all went well up to the partitioning moment I thought I had got it right but it failed to go beyond the partitioning stage.
OK so let's try the GLI installer (graphics mode).  Again it went through OK.  I set up the partitions and mount points but then the install failed.  Back again to the partitioner.  Chose the 'let the installer choose' mode but again the install failed.  at one stage there are text messages that break out of the graphics field and then the install fails.  Some message about not being able to create a location on the disk.
I can't even be fagged to write it down and inform the Gentoo crew.  That is for them to sort out.
I have a distribution thats works out of the box - it is called Ubuntu.
Why should I bother with others.  
I haven't tried Redhat or fedora for a couple of years but I have not forgotten my failed attempts at getting a working system with those distros.
I tried OpenSUSE 10.3 the other week.  It gave me a GRUB error and would not install.  I have notified the team but no one has told me there is a fix.
I have now tried Gentoo but I have not got beyond the Live CD stage.
Now let's think here.  Speaking to a friend last night work works for a UK based High Street Bank, they have concerns.  They currently use Windows XP, like most business does.  Similar to other businesses they have not migrated to Vista.  I do not recommend Vista to businesses and while I can still get XP I will use it.  Vista SP1 is due but delayed and in fact is long overdue.  Microsoft are talking about withdrawing support for XP and so supplies may dry up (maybe I should stock pile some)
So lets think, XP become unavailable.  People do not want Vista.  Where are they going to turn to?  Apple?  Linux?
Unless distributions are able to make installation faultless then Linux is never going to get the corporate market, it will remain in the hands of a few die hard computer techies as a curiosity or the bespoke markets such as TV decoders and recorders where no one knows they are running a computer underneath the sexy packaging.
For this operating system to catch on we have to have faultless reliable installations, an easy way of installing commercial packages, and a plethora of business software supported on the system.
Are we up for it?
Me, I am going to complete the installation of my web server.  Guess what I am using?  It is six letters and starts and ends with a 'U'.

I can't disagree with a lot that you have said. Gentoo is for those persons who are ready to go past the one size fits all type of thinking which is what windows is. Ubuntu is moving closer to that type of standard every day. However, Gentoo is more of a learning experience for those that know about Linux. This is not for a casual user and customization is the key, not necessarily immediate usability. Windows works out of the box:confused:supposedly. And some others, too. I think "works out of the box" has come to mean that you get a fancy splash screen when you boot it. What happens later on is to figure out what went wrong yourself or open a ticket. $$$ (even in Ubuntu)
Here's something else to try that I have gotten up and running in less than three days, with very little problems. It's called Archlinux and there is now a sub-forum on Ubuntu to check out how it works. If you look at this closely, you will find persons more loyal to this OS than Apple and for good reason. You still install from the CLI, but this is way easier than Gentoo and really does "work, right out of the box". You can see my posts and other things there. Just go to Community Forums -> Other OS -> Arch. You may be pleasantly surprised how well this works.

---

### Post by SteveHillier on 2008-02-13
> **bwtranch said:**
> Gentoo is for those persons who are ready to go past the one size fits all type of thinking which is what windows is. Ubuntu is moving closer to that type of standard every day. However, Gentoo is more of a learning experience for those that know about Linux. This is not for a casual user and customization is the key, not necessarily immediate usability. Windows works out of the box:confused:supposedly. And some others, too. I think "works out of the box" has come to mean that you get a fancy splash screen when you boot it. What happens later on is to figure out what went wrong yourself or open a ticket. $$$ (even in Ubuntu)


Thank you for your response.  I do not think I fit into the one size fits all person.  My interest in Linux started when I was in education when I thought children should be exposed to something other than the MS offerings.
My interest in Redhat et al was not to get workstations for myself.  All my installations have been with a non standard function in mind, even the workstation I am using at this moment is here because I want to use it to attach to a Windows domain running server 2003.
I want Linux as a domain server, as a web server, as a file server, as a network workstation (but not a video recorder!!).  My interest now is not to have lots of machines for my on use but can I find a distribution that I can ship to my customers in place of Windows. 
What does peeve me is when an installation does not work.  I am not able to look at Gentoo and assess it's configurability because I cannot get it installed on a hard disk machine.  I cannot even get started with it.  I cannot assess its potential.  This is the problem I had with openSUSE.
Now Windows when you are installing onto a virgin machine - which I do a lot of - works.  The install goes through and you get a working system.  I have had some re-installs go wrong, when you are running the repair function, when you are trying to install and not destroy user data and settings, those things are not for the faint hearted and are prone to hiccups.
But my Gentoo machine was for all intents and purposes a virgin install (it was a clean disk out of stock) and yet even running the automatic install failed.
If we now extrapolate to the world of users out there.  Most windows machines are shipped with a recovery disk or the original install disk.  A number of users out there are prepared to do a re-install themselves (and some of them shouldn't!!).  Could I in all honesty ship a product that I, who spends my like these days building, upgrading, repairing and shipping computers, cannot get to install without problem.
I'll try this ARCH and see how it goes.

---

