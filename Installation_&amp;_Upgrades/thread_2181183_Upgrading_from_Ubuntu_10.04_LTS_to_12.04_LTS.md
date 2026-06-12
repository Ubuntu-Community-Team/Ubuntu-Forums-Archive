---
title: "Upgrading from Ubuntu 10.04 LTS to 12.04 LTS"
date: 2013-10-16
forum: Installation &amp; Upgrades
---

### Post by Bill Dubinski on 2013-10-16
Good Day Folks,
   First, I would like to thank you in advance for reading my post and replying and for your time in doing so. I greatly appreciate it. 

First off, I am a "newer" user of Ubuntu, about three years now, coming from Winblows, I have learned what I needed to to operate Ubuntu, not not much outside of that. I tried various copies of Ubuntu distros in the beginning until I found what I liked. I started with 12.12 (Maverick), went to 11.10 (Natty), then I went back and tried 10.04 (Lucid) LTS and LOVED it, still using it to this day. But noticing Flash might now be working correctly as it is out of it's service update window and not updating. The update manager has notified me for some time now that 12.04 LTS is available for "upgrade". I have been tempted to hit the button, but using 11.10 Natty, I hated Unity and liked Gnome. Personally, I hate getting used to "new" things, it slows me down for what I need my computer for. I like knowing where things are, going for it, and walla, its there. I don't like how Unity is laid out on the desktop, I like the two (upper & lower) task bars, etc. 

My issue with doing "upgrades" from one Ubuntu distro to another within the distro is I have never done it and don't know what to expect. 
I will mark specific questions I have with an * to indicate a specific question that anybody has the answer too. 

*Is hitting the "upgrade" button in the "update manager" just as easy and simple as "kernel updates" in the update manager?
Meaning I will not have to back up, I will not lose files, I will not lose apps and small little tweaks that I have done to my system over the last couple years and I don't remember how to get again or what the official names of them were. 

*When I hot that button, will the system basically "upgrade my kernel in the "correct partition" or partitions without having to re-set up the partitions like in a new install where I always done "custom install partitions". 

Basically, what I am trying to say is, I would love to have to do little to nothing after "upgrade". Will my small apps and programs be here after the upgrade in the same place it was prior?
I would assume that after upgrade, my system will begin to upgrade web browsers, adobe flash and other apps & plug-ins as it was prior to 10.04 going out of service. 
I may be thinking of things in the "perfect world" but my experiences with Ubuntu and Linux have been more in a perfect world like since converting from Winblows. So it would not surprise me if it can be like this. I use my computer solely for internet web "graphic arts" work, so any down time is time out my work day. The GIMP is my most used program on here. I am running GIMP 2.6, which I understand 2.8 had been out for some time. Will this automatically upgrade also? Or will I have to do that in the Synaptic afterword? This is fine, that won't be too much to have to do, or other "upgrading" after the fact.?

Please correct me if I am wrong in any of my assumptions. Please give me any and all details as per updating my Ubuntu distro as far as "keeping my system as it was with Files in "Home directory", apps like "system monitor" which lets me view my system at a glance as far as CPU usage, Memory, Network, Swap space, system load and disk usage. Weather app, my customizations, and programs currently installed like GIMP, Krita, Libre Office, and various other programs installed. 
And if I have to back up, please explain to me how I do this, since I have never done it before. I have a 1TB hard drive with lots of things on it and my slave drive is not big enough to hold it all if I were to transfer files/images over. I can do some, but not all will fit as it is only 80 GB with it being about half full now. 

My system is configured like this now as far as **** usage if relevant. 
1 TB hard drive
1 GB for boot section
20 GB for swap (little much considering I only use 4% of it at the most when programs have been running for a while, but usually none with 16 GB or Ram) So swap space could stand to be reduced by about 40% or more and given to Home, but don't know how to after OS is installed. So have not since space is not close to being maxed out. 
40 GB for Root section
939 GB for Home

Again, I thank you all for your time, advise and input

Bill

Please note, I am using 10.04 LTS (Lucid) as stated above also. I know my account says 12.12 (Maverick) But it would not let me update it. Sounds stupid, I know, but it said I had not made 10 posts yet. But I am using 10.04 LTS (Lucid) and NOT 12.12 (Maverick).

---

### Post by TheFu on 2013-10-16
TL;DR
Never attempt any update/upgrade without a backup first. Most of the time, things go well, but sometimes bad things happen. I cannot answer for your specific question - it has been years since I did a 10.04 to 12.04 update.  For me, some things changed related to networking.

I dislike Unity too. The GUI is **not** the OS. That is MS-Windows, NOT Linux.  Don't like unity, install something else - xfce, lcxde, mate, cinnamon, gnome3 ... your choice. Must be 30 different choices.

Support for 10.04 desktop ended last April/May. Your install has been at risk since then.

Adobe stopped developing Flash for Linux some time ago. The only way that I know to get a newer flash is to run Google Chrome - which I find completely unacceptable.  We are tracked enough online, I don't need to be tracked on my desktop too.

12.04.3 will be supported until April 2017 for both desktops AND servers.

Swap should be 2G or equal to the amount of RAM for most people on laptops, which ever is more.  For servers and desktops that don't go into standby or hibernate - 2G is fine.

To backup, see the links in my signature.  Lots of choices.  If you don't want to learn anything, but want a solution that will work, buy another HDD that is a little larger than your current HDD and use clonezilla/partimage to backup everything.  You'll backup lots of stuff you don't need necessarily, but without more detailed understanding, this is the only safe way.  If you do learn more, then you can be much more selective about what you backup - settings, data, and /home are usually it. That doesn't mean it is always the same for everyone, just "usually."  Every system is a little different, so what you backup is a little different for every system - unless backing up everything is done.

---

### Post by grahammechanical on 2013-10-16
I have not read all your post. No time and little inclination to read long posts.

The first thing that you need to understand is that Ubuntu development has not gone backwards. The Unity interface that you did not want to learn is still there. It is now at version 7 in Ubuntu 13.10 to be released on 17th October and work is already being done on Unity 8 for use in Ubuntu 14.10.

So, if you want to move to a Ubuntu based distribution that still has service support and looks like 10.04 then you will either need to install version 12.04 Xubuntu or 12.04 Lubuntu or understand how to get a 10.04 type User Interface on Ubuntu 12.04.

[http://ubuntuforums.org/showthread.php?t=1859961](http://ubuntuforums.org/showthread.php?t=1859961)

An important point to consider when making a decision to upgrade or do a new installation is, there will be problems with an upgrade if you have heavily modified the desktop. Upgrades to newer releases work fine if the OS is basically the default OS that was originally installed.

Revert back to default themes and stuff, switch to the open source video driver if that works on your 10.04 machine, remove any PPAs.

You have a separate /home partition. That is a good thing to have. Normally an upgrade will also upgrade the main applications to newer versions simply because the newer versions are default in the newer Ubuntu. Your settings should also be used in the newer versions. Having those settings/configuration files in a separate /home partition will stop those files from being messed with. It should not normally happen but it is safer with a separate /home partition.

If you decide to do a new install (because you want Xubuntu or Lubuntu) then you choose the Something Else option and mount the 3 partitions as they are now.
 
1GB = /boot
40GB = /
939GB = /home

You will need to research using the Something Else option. Basically what you do is when you get to the partitioner dialog you select each of those partitions in turn and then you click Change. A new dialog will appear. You go to the Use As menu and select EXt4 and you can tick Format for the /boot and the / partitions but you MUST NOT format the /home partition. Then you give those partitions a mount point. 1GB = /boot; 40GB = /; 939GB = /home but they will be listed as sda-number something or other. Ok, your selection and when back at the partitioner screen, if you are satisfied, click Install Now. The installer will do the work and you should have a newer OS with newer applications but everything in /home as it should be. The important thing is not to format the /home partition.

Regards.

---

### Post by Bill Dubinski on 2013-10-16
> **TheFu said:**
> TL;DR
Never attempt any update/upgrade without a backup first. Most of the time, things go well, but sometimes bad things happen. I cannot answer for your specific question - it has been years since I did a 10.04 to 12.04 update.  For me, some things changed related to networking.

I dislike Unity too. The GUI is **not** the OS. That is MS-Windows, NOT Linux.  Don't like unity, install something else - xfce, lcxde, mate, cinnamon, gnome3 ... your choice. Must be 30 different choices.

Support for 10.04 desktop ended last April/May. Your install has been at risk since then.

Adobe stopped developing Flash for Linux some time ago. The only way that I know to get a newer flash is to run Google Chrome - which I find completely unacceptable.  We are tracked enough online, I don't need to be tracked on my desktop too.

12.04.3 will be supported until April 2017 for both desktops AND servers.

Swap should be 2G or equal to the amount of RAM for most people on laptops, which ever is more.  For servers and desktops that don't go into standby or hibernate - 2G is fine.

To backup, see the links in my signature.  Lots of choices.  If you don't want to learn anything, but want a solution that will work, buy another HDD that is a little larger than your current HDD and use clonezilla/partimage to backup everything.  You'll backup lots of stuff you don't need necessarily, but without more detailed understanding, this is the only safe way.  If you do learn more, then you can be much more selective about what you backup - settings, data, and /home are usually it. That doesn't mean it is always the same for everyone, just "usually."  Every system is a little different, so what you backup is a little different for every system - unless backing up everything is done.


Thank you Sir for replying. Yes sir, I am aware that Unity is not the OS, that it's a desktop environment. On Ubuntu 11.04 and 11.11 (that my wife had on her laptop), it had the capability of choosing in the log in screen, "Ubuntu Classic" OR Aka, GNOME fall back I would presume to make it look like GNOME 2 that was used in 10.04. This is what I am referring to. Making 12.04 look and feel like 10.04 in the form of a desktop environment. 

Correct me if I am wrong, but I think GNOME 3 is very different from GNOME 2. Again, correct me if wrong, considering I never used GNOME 3, but GNOME 3 is "closer" to Unity? Correct?. 

MATE is a little closer to GNOME 2, but I have "heard" is has issues with GNOME 3, since from what I understand, you need GNOME 3 to run MATE. 

Yes, I am aware I am atleast 3 times larger than my ram. I have 16 GB of ram. But It is not causing any sort of issue, I rarely use swap at all. And no issues were caused and I don't need the extra room, so it has not driven me to re-partition the HDD to lessen the swap space. 

It is really not that I don't want to learn anything, I just want the least amount of down time. I use my computer as my source of income, so really, any down time will be a hit to the already burdened pocket book. Plus, there will always be days of finding something I forgot to re-download and install, stopping work to install and get it, set up and so fourth. This is also why Id like to use GNOME classic or the like because I am used to where to go with using this for over two years and will have to break my rhythm when I try and go to something out of habit and it is moved because of the new desktop environment and I have to look in a different place. Like for instance with GNOME 2, I have "Applications, Places & System and tabs under that, but with Unity, I do not have that. 
I will look in your signature for backup suggestions, thank you for that. I needed some suggestions as to what is good.

---

### Post by Bill Dubinski on 2013-10-17
Good day Sir, thank you for replying. 
I really don't understand how Unity is an "upgrade" or by going back to GNOME 2 is a "downgrade" or going backwards. As far as I look at it, GNOME Classic, or GNOME 2 worked just fine. There was nothing wrong with it. Atleast for me. I can not really speak for anyone else, but for me it works/ed awesome. Now, I don't game or do any fancy stuff. I don't need graphics or fancy. From what I understand about why Ubuntu went to Unity is to attract more Windows users since the computer did everything for the user, so in order for Ubuntu to attract more users, they had to make it more "Windows Like". Now, when I came over. The buddy that got me to switch from Winblows to Linux worked hard, I was stubborn. It took him a year. But now after three years, I have learned what I need to to operate it atleast, get what I need to to work and browse the internet. That is to extent all what I do. So I don't see using what I am used to as a bad thing or "downgrade" when nothing was broke. Ubuntu attracted me with what they had with 10.04, and I am one of the most illiterate computer users there is. I don't need big clocks on my desktop telling me what time it is, I have the time in my task bar. I don't need little folders that blow up at me when I cruise my mouse over it. I want simple. I want routine. 

I think what I need is to [COLOR=#000000]understand how to get a 10.04 type User Interface on Ubuntu 12.04. I have your link, thank you so much for that. After reading it, my wifes lap top running 11.04 gives the option of "Ubuntu classic" upon log in. I think this is what I need for a 10.04 look and feel. It also could be a 12.12 look also as Maverick had the same look as Lucid. 

Other than installing programs from the software center and synaptic, it is really not modified from the original version. I think it is sort of basic and 10.04. Other than using CompizConfig, almost everything is original.  

Yes Sir, I have a separate /home partition. The buddy that got me onto Ubuntu advised me before or as I installed to do a manual install versus the default install to make them separate. Thank you for that info. 

Tank you sir, yes, I am looking for /home to be untouched. I also did not know that "settings" and stuff were stored in the /home section. I would have thought another. 
[/COLOR]

---

### Post by QIII on 2013-10-17
Hello!

GNOME 2 maintenance/development was dropped by the GNOME developers some time ago.  That's why you don't see it any longer. 

It was forked and is now reincarnated as MATE, which you may be interested in installing.  But even it has moved forward from where it began, so things may have changed a bit.

---

### Post by oldfred on 2013-10-17
I have been using gnome-panel with 12.04. While some changes where things are it to me is very similar to the old gnome2.
I just installed gnome flashback in 13.10. Have not used it much but still similar.

       sudo apt-get install gnome-panel
On login screen click on logo/cog-wheel/star and choose 
[http://www.psychocats.net/ubuntu/classicgnome](http://www.psychocats.net/ubuntu/classicgnome)
12.04 LTS / Precise Classic (No effects) Tweaks and tricks kansasnoob & cortman
[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370) 
[http://ubuntuforums.org/showthread.php?t=2090021](http://ubuntuforums.org/showthread.php?t=2090021)
[http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed](http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed)

If you have a large hard drive, you can just shrink your /home by 25GB and install a test version of 12.04 or 13.10. I actually use 12.04, but still have every install since 10.10 thru 13.10 in partitions. Time to houseclean some old ones. :)

---

### Post by mastablasta on 2013-10-17
upgrade overwrites settings and previous OS files with new ones (settings go to default on new os mostly), but it leaves data intact.

---

### Post by Bill Dubinski on 2013-10-17
Thank you so much for replying, I greatly appreciate the info. Okay, interesting. Now, say if I were to upgrade of do a fresh install of 12.04 LTS and in the log in screen, choose "Ubuntu Classic", atleast on 11.04 and 11.10 it gave me the choice, and I choose to run "Ubuntu Classic" instead of Unity. What does that do for me in 12.04? And what am I actually running?

---

### Post by Bill Dubinski on 2013-10-17
Thank you so much for replying and thank you so much for your hands on speak with the same preferences to GNOME 2. This goes a long way. Thank you for taking the time to share the links. 
Yes, I am the type that likes the LTS releases so I don't have to worry about this for a long time and I have a good OS for a long time to come. I was very happy with 10.04 LTS and are sad to let it go honestly. Even since I started using Ubuntu with 12.12, went to 11.04, I went back and tried 10.04 and loved it. But my first distro was Mint 8 before moving to Ubuntu. 

What is the best way to "shrink partitions"? Gparted I presume? I really should lessen my swap space since I don't need that much with my system.

---

### Post by mastablasta on 2013-10-17
ubuntu 12.04 has gnome fall back mode. I think it's the last version that still has it.then ther eis always Mate and also xubuntu (which is kind of like old gnome and uses old gnome libraries anyway..).

to shink parittion use  gpardted running in liveOS boot. /swap can be the size of your ram.

---

### Post by Bill Dubinski on 2013-10-18
Good Day Sir, 
Thank you for you time and your input. I am getting alot of great info here. I ran 12.04 off of Live CD for the most part all day yesterday and was able to run sudo apt-get install gnome-fallback to run it even off Live CD and test drove that also. It looked pretty decent, it was not 100% Gnome 2 (alike). I would have to figure out what happened to all my stuff under the "system tab", but with having a barebones OS at that point, it seemed and felt pretty good. 

Any more suggestions or 12.04 cool stuff suggestions would be appreciated further. This is also why I was not fond of upgrading also, was because for days I would consume myself in the fun stuff, and not focus on work. Lol. But after test driving 12.04, I am anxious to get backed up and upgraded.

---

### Post by Keith_Beef on 2013-10-20
I'm having trouble upgrading from 10.04 to 12.04. I keep getting the message below.

> Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug using the command 'ubuntu-bug update-manager' in a terminal.

I know that I have a fair amount of third-party software installed, but I can't find which of it is causing the problem. Looking in /var/log/dpkg.log.2 shows up the efforts I made to fix a small annoyance caused by gstreamer-tools, but nothing to do with the attempted distribution upgrade.

Any ideas where else I should be looking?

---

### Post by oldfred on 2013-10-20
Do you have any ppa's installed, that almost always causes issues and they have to be commented out.

look in 
       etc/apt/sources.list
You may want to backup before editing:

 cp /etc/apt/sources.list ~/sources.list.backup

 gksu gedit /etc/apt/sources.list

---

### Post by Keith_Beef on 2013-10-21
> **oldfred said:**
> Do you have any ppa's installed, that almost always causes issues and they have to be commented out.

look in 
       etc/apt/sources.list
You may want to backup before editing:

 cp /etc/apt/sources.list ~/sources.list.backup

 gksu gedit /etc/apt/sources.list

Ah, yes… thanks for that. I did have a ppa declared.

In the end, though, I took the same route as for my main computer: installed 11.04 from a downloaded disc, and after that the upgrade over the internet worked.

Now I have another little problem: I have a nasty clicking noise coming out of the Vaio speakers. When I look in the sound config I see that the output is constantly switching between the built-in speakers and the headphone socket and back again. I've not seen this problem before, not on this hardware or on any other (Linux since 1997, in my household, and on this Vaio since 2008 or 2009).

---

### Post by oldfred on 2013-10-21
Best start a new thread as that is a different issue.

---

### Post by Keith_Beef on 2013-10-21
> **oldfred said:**
> Best start a new thread as that is a different issue.

You're right, it's [here]("http://ubuntuforums.org/showthread.php?t=2182556").

---

