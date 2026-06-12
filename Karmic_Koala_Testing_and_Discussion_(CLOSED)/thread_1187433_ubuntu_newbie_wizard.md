---
title: "ubuntu newbie wizard"
date: 2009-06-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sandyd on 2009-06-14
After seeing all the newbies in the absolute beginner section crying out for help just becuase of a very common package thats not installed, i think we should do the following.

1. After the installation, add a "first time startup screen". There, you will see two options. Skip the Setup (naturally for non-newbs) and guided setup (for newbs).

2. Find a whole bunch of common wireless cards (just to begin with!) and find out how their setup. Test the procedure than make a script for each card. Now newbs can select their card (or the installer can do it manually) to install the drivers painlessly. Add a dialog onto the "Newbie Setup" for that.

3. Restricted formats. I see too many newbs complaining aoub how they can't play music, videos .etc .etc. A dialog should be added for the installation of this. (while reminding the user about [https://help.ubuntu.com/community/RestrictedFormats/](https://help.ubuntu.com/community/RestrictedFormats/))

4. Video card drivers. Newbies should have an option to either use the OSS version, or to install the newest version from Nvidia/ATI.

5. Give users the choice of selecting alternate desktop environments (KDE, Gnome, XFCE, Fluxbox ,etc) in the Newbie setup.

6. Get a whole slew of common programs that newbs will eventually use with descriptions that the newbies can understand. (unlike the ones in synaptic).

What do you think?
(and yes, i know, some of that stuff above me will violate the ubuntu philosophy and i Know this will make newbs who like to learn mad at me, but some people just like it simple)

---

### Post by kc3 on 2009-06-14
I actualy think this is a great idea and would help make the system more popular for people who aren't as good at computers

---

### Post by Amilo1718 on 2009-06-14
popularity makes dumb & doesn't help the user (imho)
if someone wants to use linux, he/she has to learn linux
a guidance may be helpful but cannot be torough (imho)

---

### Post by Screwdriver0815 on 2009-06-14
I would not support it. Because this makes Ubuntu bloated like Windows or worse.

When I remember right, the first start-site in Firefox directs new users to the Ubuntu wiki and helps also to find Ubuntuforums. 
Ubuntu has a comprehensive help section too.
As far as I know, Windows has no Wiki and no first startsite in IE which directs the user to help and support sites ;)
So if a new user is not able to read this and to find the stuff he needs, like he did it in Windows too, years ago, then he should stay with windows. 

So if this feature...sorry... bug would be implemented in Ubuntu, I would switch to another Distro. But this should not mean anything to all the folks who want it ;)

---

### Post by MaxIBoy on 2009-06-14
> **carlee said:**
> After seeing all the newbies in the absolute beginner section crying out for help just becuase of a very common package thats not installed, i think we should do the following.

<snip>

3. Restricted formats. I see too many newbs complaining aoub how they can't play music, videos .etc .etc. A dialog should be added for the installation of this. (while reminding the user about [https://help.ubuntu.com/community/RestrictedFormats/](https://help.ubuntu.com/community/RestrictedFormats/))The main issues I see with number 3 are the potential legal problems-- if Canonical was seen to encourage people to install restricted codecs in the USA, for example, that's an easy target to sue. I know that you understand the issues, but Canonical is already on shaky ground for making it available in the first place, it's a good legal strategy to try to "hide" the restricted formats a bit.

However, if every single user installed the codecs of their own choice, it's hard to pick any one person to sue, which is what keeps us safe. A disclaimer about how "this might not be legal in your country, you're responsible for making sure you obey the laws" would solve the problem legally, but it might also be a bit off-putting, especially if it's the first thing you see as soon as you've installed.

Right now, *assuming they play the media with the default media player*, they get a little pop-up the first time they try to play in a restricted format, offering to automatically fetch and install the codec for it. (Has this changed since 8.04?)

>  <snip>

5. Give users the choice of selecting alternate desktop environments (KDE, Gnome, XFCE, Fluxbox ,etc) in the Newbie setup.Nice idea in theory. Here's the problem-- the liveCD installer is intended to give users a *complete working environment* on the first boot. This involves bundling a desktop environment or window manager on the CD itself. And for user-friendliness reasons, something of negligible size (for example Fluxbox) isn't really considered an option, over at Canonical HQ. So that means including a significantly-sized DE on the CD. So someone downloads the ISO image, including a full copy of GNOME, just so that they could install KDE instead? Very few people are going to be willing to actually do that.

Right now, you can get an alternate installer CD, and build up your own desktop from there. I could see the idea of an alternate CD with a very minimal window manager and a step-by-step guided process to install various different desktops, but in my opinion this kind of thing will mainly appeal to advanced users, not newbies.

> 6. Get a whole slew of common programs that newbs will eventually use with descriptions that the newbies can understand. (unlike the ones in synaptic).+1

---

### Post by Amilo1718 on 2009-06-14
> **MaxIBoy said:**
> Right now, *assuming they play the media with the default media player*, they get a little pop-up the first time they try to play in a restricted format, offering to automatically fetch and install the codec for it. (Has this changed since 8.04?)
solved (if you know what you're doing :p )

---

### Post by sandyd on 2009-06-14
> **MaxIBoy said:**
> <snip>

Nice idea in theory. Here's the problem-- the liveCD installer is intended to give users a *complete working environment* on the first boot. This involves bundling a desktop environment or window manager on the CD itself. And for user-friendliness reasons, something of negligible size (for example Fluxbox) isn't really considered an option, over at Canonical HQ. So that means including a significantly-sized DE on the CD. So someone downloads the ISO image, including a full copy of GNOME, just so that they could install KDE instead? Very few people are going to be willing to actually do that.

<snip>
i meant that they could download it from the internet. (installing additional window managers OTHER than the one they already have. for example, kubuntu users could have a choice of isntalling gnome, fluxbox...).

---

### Post by sandyd on 2009-06-14
> **Amilo1718 said:**
> popularity makes dumb & doesn't help the user (imho)
if someone wants to use linux, he/she has to learn linux
Its kinda hard to learn when you don't have internet just because your missing wifi drivers.
> **Amilo1718 said:**
> a guidance may be helpful but cannot be torough (imho)
A explanation **can** be given at each step and/or a terminal opened to show what in the world is going on.

---

### Post by Amilo1718 on 2009-06-14
> **carlee said:**
> Its kinda hard to learn when you don't have internet just because your missing wifi drivers.
cuz you miss something like a manual for commands?
> **carlee said:**
> An explanation **can** be given at each step and/or a terminal opened to show what in the world is going on.
like a demonstration video?

---

### Post by cariboo on 2009-06-14
You"ll be happy to know that something like you suggest is being worked [thread=1185535]on[/thread]. Unfortunately codecs can't be installed by default because of legal reason, mostly in the US. Graphics drivers are moving targets, they change fairly often. during the alpha cycle of a release, they can change 3-4 times, and by using a seperate installer, the user is assured of getting the latest one. The open source drivers for ATI are proceeding nicely, while the os drivers for Nvidia are a little behind.

The main problem is that there is only so much that can be put on a 700Mb cdrom.

---

### Post by lisati on 2009-06-14
I'm wondering if a compulsory course of the "computers 101" variety might be of some value in conjunction with such a Wizard. I've encountered people with better education than myself who sometimes expect me to perform miracles by fitting several DVDs worth of data on a single CD or memory stick. Even basic literacy sometimes seems to cause problems......

---

### Post by aysiu on 2009-06-14
A tutorial during installation is already in the works (finally!):
[http://brainstorm.ubuntu.com/idea/136/](http://brainstorm.ubuntu.com/idea/136/)

Prompting for codecs and restricted drivers are already in place. If you think it's not working properly file a bug report:
[https://bugs.launchpad.net](https://bugs.launchpad.net)

And it's a really bad idea to make people choose desktop environments during installation. Ubuntu is a new-user-friendly distro and shouldn't confuse people with a bunch of blahblahblah options. What new user is going to know whether to use Gnome, KDE, Xfce, Fluxbox, or IceWM?
[http://brainstorm.ubuntu.com/idea/15294/](http://brainstorm.ubuntu.com/idea/15294/)

---

### Post by freeman2000 on 2009-06-14
Great idea!  There's a reason MS left DOS behind years ago.  Probably 99+% of the general public does not want to see a command line.  They want to hit the power button, see graphics, and have the computer run.  So long DOS!  Get the hint Linux ???

---

### Post by aysiu on 2009-06-14
> **freeman2000 said:**
> Great idea!  There's a reason MS left DOS behind years ago.  Probably 99+% of the general public does not want to see a command line.  They want to hit the power button, see graphics, and have the computer run.  So long DOS!  Get the hint Linux ???
Ubuntu has had a graphical user interface since its first release.

Ubuntu is nothing like DOS.

---

### Post by H2SO_four on 2009-06-14
I like idea #136, also what might work is having a textbook or two on ubuntu included in the install.  Have them placed directly on the desktop, first thing the new user sees (and hopefully reads).

---

### Post by sandyd on 2009-06-15
just had a spark in my brain this morning..


what about installing a macro that would show them around while using zenity, or some other dialog to outline everything. THat would be much better than a video, or -worded- guide

---

### Post by Slug71 on 2009-06-15
I think its a good idea too. 
Many Linux users want their friends and family to switch over to Linux but like ive said before, older people who are already struggling to come to terms with technology and computing arent going to want to learn something all over again. So saying something like "well they just have to learn it" is bogus. 

Most everyday people simply dont have the time, patience or interest to sit in front of a computor for hours and signing up to forums to learn how to use a new OS. They dont know what bloatware or all the other bad habits of MS is except Virus and Spyware. Therefore all the want is a system to turn on and just work and thats easy to install programs on. 

Unfortunately things cant be boths ways and there has to be some compromise. I think a small program to help 'newbs' and potentially benefit Linux in the long run is a great idea and if you dont need it then simply uninstall it.

---

### Post by aysiu on 2009-06-15
No one is saying a tutorial is a bad idea.

Yet another desktop icon isn't going to help, though. Non-tech-savvy users won't click on it. Power users will just be annoyed by it. It's better to have a slideshow during installation (which is already in the works, by the way), as power users can easily ignore it (install and go away) and new users won't have much else they could be doing besides watching it.

---

### Post by psyke83 on 2009-06-15
> **aysiu said:**
> No one is saying a tutorial is a bad idea.

Yet another desktop icon isn't going to help, though. Non-tech-savvy users won't click on it. Power users will just be annoyed by it. It's better to have a slideshow during installation (which is already in the works, by the way), as power users can easily ignore it (install and go away) and new users won't have much else they could be doing besides watching it.

I just hope that usability is taken into consideration when implementing this idea. Installing from CD can be quite slow due to the slow seek time of optical media (especially while multitasking in the live environment).

Displaying a slideshow during the installation process will slow things down even more, unless some sensible caching is implemented (but this will increase memory requirements). Detecting low memory situations and disabling or degrading the slideshow in such cases could be a possible answer to this problem, though.

---

### Post by ranch hand on 2009-06-15
Just what is going to left off the LiveCD to make room for some hand holding feature?

Everything that you put on there takes room.

I would hope that people that want to use a different OS than they are using currently would havethe brains to do a little research FIRST.  I do not think this is an unreasonable hope.  I am not the brightest bulb in the pack but I did that.

I would rather have features rather than some generic "presentation" that will, naturally, not cover the things that are really giving people trouble.  You have to make these things ahead and by the time you use them the problems have changed.

---

### Post by psyke83 on 2009-06-15
> **ranch hand said:**
> Just what is going to left off the LiveCD to make room for some hand holding feature?

Everything that you put on there takes room.

I would hope that people that want to use a different OS than they are using currently would havethe brains to do a little research FIRST.  I do not think this is an unreasonable hope.  I am not the brightest bulb in the pack but I did that.

I would rather have features rather than some generic "presentation" that will, naturally, not cover the things that are really giving people trouble.  You have to make these things ahead and by the time you use them the problems have changed.

Keep your mouth shut and let them add anything if it means the adoption of [SquashFS LZMA]("http://www.squashfs-lzma.org/")! :)

Maybe we'll get [LZMA-compressed debs]("https://wiki.ubuntu.com/dpkg-lzma") as well, and everybody's bandwidth requirements will go way down...

---

### Post by aysiu on 2009-06-15
If you want more details of what the implementation will look like, check out this thread:
[url=http://ubuntuforums.org/showthread.php?t=1185535] 	
Slideshow during Install[/url]

---

### Post by meeples on 2009-06-15
i completely agree with this. apart from number 6.

i think if we gave them an option to select a desktop environment, thats too advanced an option, there installing the o.s advertised, not kubuntu, xubuntu, fluxbuntu. whatever, 

:)

---

### Post by meborc on 2009-06-15
i think a slideshow is good idea and a wizard as suggested by OP is a bad idea

but i would rather have non of those on the cd... but that is just me :)

---

### Post by zekopeko on 2009-06-15
> **psyke83 said:**
> Keep your mouth shut and let them add anything if it means the adoption of [SquashFS LZMA]("http://www.squashfs-lzma.org/")! :)

Maybe we'll get [LZMA-compressed debs]("https://wiki.ubuntu.com/dpkg-lzma") as well, and everybody's bandwidth requirements will go way down...

this sound great in theory. but you are forgeting that LZMA uses more CPU and RAM. so that means stepper minimum requirements.

**On The Wizard Thingy **

what the OP outlined is a wrong solution. it's attacking the problem from the wrong angle. this things should work out of the box or be inteligentlly opened once the user tries to do something that doesn't have necessary packages installed.

And help should be discreetly positioned so that the user can find simple solutions to the problem. example would include: the start.ubuntu.com page that is set as the homepage. it should have the simple google search text field and underneath it should have links to wiki, help, ubuntu guide and firefox extensions (the last one should be presented if the user doesn't have any extensions installed except ubufox). 
the guide should be a tour of all the latest features in the current ubuntu version plus a simple guide through ubuntu ie. how things work and what apps are provided for what. this guide should be similar to the ubiquity-slideshow integration but with more detail.
as Mr. Picklesworth said best: encourage the user to explore the system and it's possibilities.

---

### Post by psyke83 on 2009-06-15
> **zekopeko said:**
> this sound great in theory. but you are forgeting that LZMA uses more CPU and RAM. so that means stepper minimum requirements.

Yes, that's true. However, some considerations:
[LIST]
[*]CPU and memory usage is significantly higher for **compression** - not an issue for the end-user when downloading debs or using the live cd.
[*]Decompression requires more CPU and memory compared to gzip (the current default), but the requirements are only slightly higher than bzip2. Overall performance may improve on the Live CD if it uses SquashFS LZMA; the transfer speed of the optical media will be the bottleneck, so it's feasible that the improved compression ratio may improve performance overall (but testing is required to prove this, of course).
[/LIST]

Perhaps SquashFS LZMA won't work out for the LiveCD (due to memory issues), but I see **no** credible arguments against implementing the dpkg-lzma specification. Memory usage during decompression is raised by perhaps 30MB, but even on an extremely limited system (with say, 196MB ram), decompression will work properly even if it has to resort to swapping. 

I'll go out on a limb and say that most users with low memory systems probably have low-bandwidth connections, so it's a valuable trade-off.

---

### Post by 23meg on 2009-06-16
> **aysiu said:**
> 
Prompting for codecs and restricted drivers are already in place. If you think it's not working properly file a bug report:
[https://bugs.launchpad.net](https://bugs.launchpad.net)

Directing people to that URL for reporting bugs is suboptimal, because:

[list][*]That is not the URL for [the Ubuntu bug tracker at Launchpad]("bugs.launchpad.net/ubuntu"), nor is it the URL for [the "+filebug" page]("https://bugs.launchpad.net/ubuntu/+filebug"), which takes you to the bug reporting process directly; it's the home URL for Launchpad's bug tracking component, which hundreds of projects use.

[*] In most cases [it's  better idea]("http://mdzlog.alcor.net/2009/03/31/please-dont-report-ubuntu-bugs-directly-to-launchpad/") to lead people to use the "Help -> Report a Problem" menu item in default applications, or the "ubuntu-bug" CLI bug reporting tool instead of going to Launchpad directly, since these methods trigger [Apport]("https://wiki.ubuntu.com/Apport"), which saves everyone time and effort by automatically attaching information such as package versions, Ubuntu version, dependencies etc. that bug triagers will otherwise have to ask for, and reporters will have to look for and provide.[/list]

The best practice will be to link to [http://help.ubuntu.com/community/ReportingBugs](http://help.ubuntu.com/community/ReportingBugs) when you want to inform people about filing bug reports.

---

### Post by ashmew2 on 2009-06-16
> **carlee said:**
> After seeing all the newbies in the absolute beginner section crying out for help just becuase of a very common package thats not installed, i think we should do the following.

1. After the installation, add a "first time startup screen". There, you will see two options. Skip the Setup (naturally for non-newbs) and guided setup (for newbs).

2. Find a whole bunch of common wireless cards (just to begin with!) and find out how their setup. Test the procedure than make a script for each card. Now newbs can select their card (or the installer can do it manually) to install the drivers painlessly. Add a dialog onto the "Newbie Setup" for that.
 This could be actually great to see imo..
> 
3. Restricted formats. I see too many newbs complaining aoub how they can't play music, videos .etc .etc. A dialog should be added for the installation of this. (while reminding the user about [https://help.ubuntu.com/community/RestrictedFormats/](https://help.ubuntu.com/community/RestrictedFormats/))
 Its no point putting it on a CD. Downloading from the internet and then installing is pretty good i must say. Maybe you meant downloading and installing , anyway , i thought you meant to put it on the Live disc.
> 
4. Video card drivers. Newbies should have an option to either use the OSS version, or to install the newest version from Nvidia/ATI.

There's no point in adding something like that , would just bloat the setup , Its pretty plain and simple with the Restricted Drivers Manager (which NEEDS improvements OF COURSe)

> 
5. Give users the choice of selecting alternate desktop environments (KDE, Gnome, XFCE, Fluxbox ,etc) in the Newbie setup.

No point in that , The standalone Kubuntu/Xubuntu discs are there for a reason. And i think that most "newbies" are quite scared when it comes to selecting which Desktop you want etc. They're mostly coming from Windows and its "JUST A DESKTOP , Whats the Difference?!!? FFS!" ;)

> 
6. Get a whole slew of common programs that newbs will eventually use with descriptions that the newbies can understand. (unlike the ones in synaptic).
 I think thats pretty bloated on the Menus lol..And they can always get the things they want from the internet.

> 
What do you think?

Well I just told you ;) But nice ideas none the less.

---

