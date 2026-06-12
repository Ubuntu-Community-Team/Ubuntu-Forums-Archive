---
title: "Installing Linux on a Windows 10 PC"
date: 2023-02-15
forum: Installation &amp; Upgrades
---

### Post by wollyvio on 2023-02-15
[COLOR=#141414][FONT=&quot]Hi,I want to change from Windows 10 to Ubuntu or Red Hat Enterprise (RHEL)Linux because there is an app that I would like to use,[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]What are the advantages for using Ubuntu or Red Hat Enterprise (RHEL)Linux over Windows 10?[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]Should I stay with Windows 10 or should I move to Ubuntu or Red Hat Enterprise (RHEL)Linux?[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]I'm a noob at opperating system and I don't know which one to install on my PC![/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]What are your opinions?[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]Are both Red Hat Enterprise (RHEL)Linux and Ubuntu opperating systems? How do they differ from Windows?
How can you install Linux Ubuntu on your PC? Is there a tutorial with video?
I don't want to keep Windows 10 on my PC anymore because my GPU only supports Linux or Ubuntu or RHEL![/FONT][/COLOR]

---

### Post by TheFu on 2023-02-15
RHEL is for servers, not desktops.  There's no GUI.  You aren't ready to run a server based on the other questions.

All the other questions have been answered 100,000 times over the last 30 yrs.  Use any web search engine to find in-depth articles, since rehashing all the differences here makes little sense.
Youtube has thousands of videos about these questions too, if you don't like reading thoughtful articles.

Here's some light reading:
[https://www.computerworld.com/article/2534926/which-platform--cathedral-or-bazaar-.html](https://www.computerworld.com/article/2534926/which-platform--cathedral-or-bazaar-.html) - different philosophies 
[https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html) - Linux for Windows users
[https://en.wikipedia.org/wiki/Unix_Philosophy](https://en.wikipedia.org/wiki/Unix_Philosophy) - Unix Philosophy
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)  - Linux isn't Windows

Any my personal thoughts on these things: [https://blog.jdpfu.com/2013/08/23/common-answers-for-ubuntu-and-linux-issues](https://blog.jdpfu.com/2013/08/23/common-answers-for-ubuntu-and-linux-issues)

One other suggestion it to find a LUG, Linux Users Group, that you can attend for free and ask these questions of the people there so you get lots of different answers. Most meet monthly, but some meet weekly and there are virtual LUGs that meet using online video conferencing.

95% of Linux is the same underneath.  Ignore the GUI.  That's just an interface and for Unix-like OSes, it is just another program that can be swapped as desired.  Linux has a million choices, unlike MS-Windows or MacOS where you get what they provide and YOU WILL like it, or else.  The specific distribution doesn't matter in large ways ... er ... until it does.
90% of Linux is just like UNIX. They share the same philosophies.

And don't forget that proprietary software has restrictive licenses that go against what we were all taught in kindergarten.  In general, there are always exceptions, Linux and linux distros work like we teach our 6-7 yr old children.

> How can you install Linux Ubuntu on your PC? 
Use any web search tool to find instructions. There are text versions, wizards, videos.  They are all found easily.

> Is there a tutorial with video?
Yes.

> I don't want to keep Windows 10 on my PC anymore because my GPU only supports Linux or Ubuntu or RHEL!
I doubt GPU support would be better on Linux than on Windows.  If a GPU is that old, you'll likely have issues on Linux too.
GPU support on RHEL doesn't matter, since that distro is completely inappropriate for you.

The version of Linux you should install depends on who you know already running Linux and what they'd be willing to help you run.  If your neighbor runs MX Linux and is willing to help, perhaps you should run that release?

BTW, you don't actually need to install most Desktop Linux distros to use them.  They almost always come with a "Live Boot" environment, which means you can boot from the ISO file and use it to get a feel for the specific distro.  All it costs is the bandwidth, time, and storage to get the ISO file.  Ubuntu does this with a "Try Ubuntu" option.

Step 1: Read those links above
Step 2: Google for some answers, read, watch, and learn.
Step 3: Find a LUG you can attend, engage with them, ask questions and show up.
Step 4: Determine which release of a Linux distro is a good choice for your hardware, desired tasks, and temperament.  There are many distros created for specific purposes.

I know nothing about your hardware and if the GPU isn't supported by Windows, I'm a little worried it is old, underpowered, and can be challenging to run the flagship Ubuntu Desktop.  Post the exact CPU model, RAM, GPU model and storage information, if you'd like guidance.

[https://ubuntuhandbook.org/index.php/2022/04/install-ubuntu-2204-step-by-step/](https://ubuntuhandbook.org/index.php/2022/04/install-ubuntu-2204-step-by-step/) - 22.04 install
[https://www.youtube.com/watch?v=W-RFY4LQ6oE](https://www.youtube.com/watch?v=W-RFY4LQ6oE) - Complete Beginner's Install Guide - it is from 2019, but still accurate.  New users should choose the LTS version.
If you are new, like you claim, I'd push you to consider Linux Mint rather than Ubuntu.  It is based on Debian too, so many things are similar, including the debian package management, but it doesn't add some confusing things that Canonical (the company that packages Ubuntu) has decided to mandate in their recent releases. The default desktop environment (aka DE) for Linux Mint is also lighter than Gnome is, so older computers should be faster running it.
[https://linuxmint.com/](https://linuxmint.com/) has a download link and other things you'll likely want to know.  BTW, the way we install almost every Linux is extremely similar for desktops/laptops.  Looks like 21.1 is the current release and they have 3 different DEs - Cinnamon, Mate, Xfce. I've ordered them by which has the most "cheese" - the highest graphics requirements so newer hardware would be good.  I haven't used Mint in about a decade, BTW, so I don't have recent first-hand knowledge.  Some of the guys in my LUG use it. These are some of the less technical people who just want an OS that stays out of their way.  Installation of Mint is about the same as for Ubuntu or Fedora.

Ooops.  I didn't mean to post so much. Sorry.

---

### Post by tea for one on 2023-02-15
> **wollyvio said:**
> I'm a noob at opperating system and I don't know which one to install on my PC!
Are you familiar with running a live Ubuntu session on your PC?
[https://ubuntu.com/tutorials/try-ubuntu-before-you-install#1-getting-started](https://ubuntu.com/tutorials/try-ubuntu-before-you-install#1-getting-started)

---

### Post by SeijiSensei on 2023-02-15
I'd start by installing VirtualBox on Windows so you can create virtual machines. 

Click here to download and run the installer: [https://download.virtualbox.org/virtualbox/7.0.6/VirtualBox-7.0.6-155176-Win.exe](https://download.virtualbox.org/virtualbox/7.0.6/VirtualBox-7.0.6-155176-Win.exe)

Then you can create a virtual machine by running the VirtualBox manager. Install a Linux ISO image and see what it looks like. You could try different flavors of Ubuntu like Kubuntu or Lubuntu that present different desktops by default. (I use Kubuntu with the KDE desktop.)

Here are some options for 22.04, the current stable release.

Standard Ubuntu: [https://cdimage.ubuntu.com/jammy/daily-live/current/](https://cdimage.ubuntu.com/jammy/daily-live/current/)
Kubuntu: [https://cdimage.ubuntu.com/kubuntu/jammy/daily-live/current/](https://cdimage.ubuntu.com/kubuntu/jammy/daily-live/current/)
Lubuntu: [https://cdimage.ubuntu.com/lubuntu/jammy/daily-live/current/](https://cdimage.ubuntu.com/lubuntu/jammy/daily-live/current/)

You can build and destroy virtual machines at will, so you can try out different versions before making a decision and still have Windows available at all times.

---

### Post by grahammechanical on 2023-02-15
Not only is RHEL a server OS it is for sale.

[https://www.redhat.com/en/store/linux-platforms](https://www.redhat.com/en/store/linux-platforms)

I have yet to see an edition of Ubuntu that is not free to download, install, and distribute. Canonical is the sponsor of Ubuntu. It makes its profit from selling services not from selling a Linux distribution.

If you are interested in an alternative to RHEL that has a desktop environment then look at Fedora. I understand that Fedora is maintained by a community and is built on Redhat code.

[https://getfedora.org/](https://getfedora.org/)

Regards

---

### Post by wollyvio on 2023-09-11
[COLOR=#141414][FONT=&quot]Is the GPU ATI RADEON HD 8490 compatible with Linux Ubuntu?[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]Can you install the drivers from the AMD website?
[/FONT][/COLOR]https://help.ubuntu.com/community/BinaryDriverHowto/AMD
Is the article true? You can't install Ubuntu anymore on Windows?

---

### Post by wollyvio on 2023-09-11
Anyone? I have searched google and I haven't found an answer!

---

### Post by SeijiSensei on 2023-09-11
Did you not see this disclaimer at the top of the page?

> Neither the fglrx driver nor any version of Ubuntu that would use it are supported by their respective purveyors. This entire article is obsolete.

Have you even tried yet? All the Ubuntu installers let you run it from the installation media so you can see right away how well it will work on your machine without making any changes.

Did you try VirtualBox? What happened? Sounds like you didn't really pay much attention to the advice you were given before.

---

### Post by guiverc on 2023-09-12
This question was already asked at [https://askubuntu.com/questions/1485415/can-i-install-the-amd-graphics-card-driver-in-linux](https://askubuntu.com/questions/1485415/can-i-install-the-amd-graphics-card-driver-in-linux)

Support is often dropped on older video cards because of *security flaws* being discovered, that cannot be easily fixed. A number of old cards have *disappeared* from being supported by Microsoft (Windows) and Linux because of this. For others its only that the cards have *flaws* that again aren't easily resolved, thus its easier to *drop* support.

AMD for a number of products used to provide their own *kernel modules *(*commonly called drivers*) as they provided greater support, but those can get dropped if they decide the open source drivers are almost as good (*esp. easy as creating kernel modules cost developer time to maintain*).  With the *fglrx* kernel module; AMD help improve the open source radeon driver & stated the *fglrx* was no longer necessary.  I've seen reports from many end-users who agree it wasn't needed, but also a *smaller number* of *noisy* users who complain they got better performance from the *dropped fglrx*.

In the end, it's best to just try a *live* system & see for yourself, as was suggested in the 3rd post in this thread (ie. 2nd reply) !

For Ubuntu 20.04 LTS for example; there are ISOs available which have the 5.4, 5.8, 5.11, 5.13 & 5.15 kernels available; giving you 5 different kernels for the same release to try.. though if using it online, there are only two kernel stacks that get fixes (GA or 5.4 & HWE which is 5.15 for 20.04). You can then try another release... What's important is you're testing it on your actual hardware!

FYI:  I perform QA of Ubuntu (*and especially flavors*) using hardware as old as from 2005. In the last couple of years I've replaced (*as in swapped out*) a few video cards on some boxes, as those boxes were mostly used for install testing, and some GPUs are just less hassle. For some of the old cards I've recently replaced (*up to 20 years old*) I could still use them with Ubuntu if without issue, I'd just be using an older kernel stack by choice.. but most QA involves the *next* release; which currently is *mantic* or what will be released in 2023-October (23.10)... ie. most QA is newer stack only; where older cards usually perform better on older stacks in my experience; on installing a system you decide what stack at install time.

---

### Post by slickymaster on 2023-09-13
*Thread moved to **Installation & Upgrades**.*

---

### Post by MAFoElffen on 2023-09-13
I am an IT Consultant, and have been doing support for over 34 years now... I have some questions back to you, before attempting to assist you.

Much of this would be answered if you ran the [UbuntuForum 'system-info' script]("https://github.com/UbuntuForums/system-info") and posted a URL to the report it generates.

I am a bit confused. Maybe you could clear some of this up. What you are posting seems to conflict back and forth (by omission of details). You said you have a "Windows 10 computer." That usually implies that someone has a computer that came from the vendor with Windows 10 installed as OEM, and is of recent issue. But that is a bit misleading. Windows 10 was released in 2015, so it is less than 8 years old. The GPU you asked about (ATI RADEON HD 8490) was released in 2013 (Before Windows 10)... So about 10 years old.

Implied by this:
> **wollyvio said:**
> I don't want to keep Windows 10 on my PC anymore because my GPU only supports Linux or Ubuntu or RHEL!
Does Windows 10 still has legacy drivers for that GPU? I believe it does. Though, I'm thinking the hardware (CPU Generation) does not meet the minimum requirements for Windows 11, right?

Let's get down to it... Ubuntu is free of charge. Ubuntu is one of the most popular Linux Distributions, because it is well supported, and is easy for a User to learn to use. When I say well supported, I mean both by the hardware it can run on, and by the community of volunteer users here, and at AskUbuntu.com.

There is a learning curve. Do not expect it to be just like Windows. It is not, and it is not meant to be.

It sounds like it will run fine on your hardware, but as suggested by members here, if you ran a LiveUSB, you could confirm that for yourself. If you post the URL of the system-info Report, we would have the hardware details to make an educated guess at that. Right now we are in a vacuum with that. (No hardware details.)

Being from the Windows World, you might be more comfortable looking at one of Ubuntu's flavors: Kubuntu. It is a bit heavier in using resources, but would probably be the least learning curve for you to get productive. You are free to choose whatever Desktop Environment you want.

One big change from Windows. Linux gives you the freedom to make unlimited customization's to make whatever you use, to your own personal liking. Interchange the pieces to tweak it to "be your own". The settings are not locked down to protect itself from "you". With that freedom, comes some risks. It can't protect itself from you if you do something wrong, or does not make logical sense. It cannot protect "yourself" from "you."

---

