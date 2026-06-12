---
title: "Preparing to install Ubuntu"
date: 2013-10-20
forum: Installation &amp; Upgrades
---

### Post by jmarkrobinson on 2013-10-20
**BACKGROUND:**

I'm new to these forums.  I have minimal experience with Linux but come from a background of 34 years of IT experience.  MY PC experience began pre-Microsoft and when they launched DOS for PC's, I became quite proficient with the command line, therefore, I'm not the least scared off by Linux command line.

I'm going to migrate two PC's w/ WIN-XP to Ubuntu only.  The priority is to change the HP Pavillion desktop w/ AMD64 Athlon.

**QUESTIONS:**

1. Where do I begin with prepping the hard drive?  I am familiar with GParted and used it to repartition the drive on this PC a few years ago.  I am going to delete all of the additional partitions and use one only.

2. I read a comment somewhere that suggested that GParted was integrated with the Ubuntu install package?

3. What file system should the drive be formatted to and what options, if any, for maximum performance?  It's currently NTFS and I am aware that it is not compatible with Linux.

Thanks, in advance, for your help.

---

### Post by xiccarph on 2013-10-20
Hi there.

I would begin by creating a Live Distro USB stick and boot the machines in question using the live version.  That will be helpful in determining if there are any hardware issues that pop up.
Here is a link to creating a bootable USB stick on Windows: [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

[LIST=1]
[*]In regards to the disk prep, you really don't have to do much.  The Ubuntu install program will guide you through that when you install (which you can do from the Live Distro USB).
[LIST]
[*]It is useful to have any idea of what you want to do (encryption, multiple partitions, etc).  You can find alot of commentary and advice here in the forums.
[/LIST]

[*]The Ubuntu Install program will guide you through setting up your harddrives and partitions.
[LIST]
[*]If you want to you can use the Disks program to partition the hard disks while you are trying out Ubuntu from the Live USB stick.  When you boot to the Live Distro it is running off of the flash drive so you can reformat any harddrives you want.
[/LIST]

[*]You can use NTFS fine under Linux, but you may want to read about the many filesystem options, mostly superior to NTFS, available in Ubuntu.  You would probably not want to run Ubuntu installed to an NTFS filesystem.
[LIST]
[*]Here is a useful forum thread about Linux filesystems: [http://ubuntuforums.org/showthread.php?t=2109175](http://ubuntuforums.org/showthread.php?t=2109175).
[/LIST]
[/LIST]
Hope this helps get you started.

---

### Post by Bashing-om on 2013-10-20
john_robinson2; Hi ! My Welcome to the forum !

If I may, in addition to xiccarph's advise, add;

Your fears are groundless in respect to installation of 'buntu. It is simple, quick and painless for the default install.
However, as you are presently running XP, this may be older hardware. The flagship editions of ubuntu are resource hungry and require some hosses for a favorable experience. For older hardware I really endorse lubuntu. That is not to say you can not try ubuntu and see.
See some options for 'buntu editions in the link "ubuntu Community" located above the thread post, choose your flavor and download the .iso image file;
check the file integrity, and burn as a "image" to disk;
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
As advised run 'buntu in "try ubuntu" mode to insure there are no hardware issues;
When ready to install 'buntu - do so with a WIRED internet connection !

I suggest for the 1st time install that you do it as a simple default install, the install wizard will take care of everything, you just need to answer a few simple questions but take care to note and remember your username and PASSWORD. Your password is crucial to administering your system.
In the install -as you want only 'buntu installed as the single operating system- choose "erase entire disk and install ubuntu" , and like I said the wizard will take care of everything. At a later time when you have some familiarity with the ubuntu operating system you can consider making alterations to the standard install !

GParted is included in the desktop liveMedium, but you will not need it for this standard install.

" What file system should the drive be formatted  ->" as said above, not to fret, the install wizard will take care of it.

Command Line Interface, the means to unleash the true power of this operating system. In my 50 years exposure to computer in general the most powerful interface I have ever encountered ! It can be very complex and have a steep learning curve. Not to take away from the GUI, a wonder in it's own right.

What can I say but welcome to open source, a place where you will never hear:
[LIST]
[*]that is proprietary information
[*]you have no need to know
[*]we can not tell you
[*]and other degrading statements
[*]
[/LIST]
Linux is a great operating system and the support for ubuntu, in many many arenas, make it a suburb operating system. Millions of programmers have and do make it so for many generations.
[INDENT][INDENT]that's my story and I am 
[INDENT][INDENT][INDENT]stick'n to it
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jmarkrobinson on 2013-10-20
[COLOR=#008000][B]Hi Basnhing-om

Thanks so much for the advice.[/B][/COLOR]

> **Bashing-om said:**
> jmarkrobinson; Hi ! My Welcome to the forum !

[COLOR=#008000]**Thanks.**[/COLOR]

If I may, in addition to xiccarph's advise, add;

Your fears are groundless in respect to installation of 'buntu. It is simple, quick and painless for the default install.
[COLOR=#008000]
**I have no fears.  Read again, I said, "I'm not the LEAST scared off by Linux command line."  I lived and breathed command lines in DOS and large scale legacy systems. (IBM/360,3083, AS/400, Univac 1100, DEC PDP-11)**[/COLOR]

However, as you are presently running XP, this may be older hardware. The flagship editions of ubuntu are resource hungry and require some hosses for a favorable experience. For older hardware I really endorse lubuntu. That is not to say you can not try ubuntu and see.
[COLOR=#008000]
[/COLOR][B][COLOR=#008000]The hardware is about 4y old with a 64bit AMD processor.  I'll max out the RAM now that it's dirt cheap.[/COLOR]
[/B]
See some options for 'buntu editions in the link "ubuntu Community" located above the thread post, choose your flavor and download the .iso image file;
check the file integrity, and burn as a "image" to disk;
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
As advised run 'buntu in "try ubuntu" mode to insure there are no hardware issues;
When ready to install 'buntu - do so with a WIRED internet connection !

[COLOR=#008000]**I'm wired all the time...but that's another story ;-)  All devices are wired all the time with the exception of a small tablet and my netbook but only when it's not on the desk, which is almost never.**
[/COLOR]
I suggest for the 1st time install that you do it as a simple default install, the install wizard will take care of everything, you just need to answer a few simple questions but take care to note and remember your username and PASSWORD. Your password is crucial to administering your system.
In the install -as you want only 'buntu installed as the single operating system- choose "erase entire disk and install ubuntu" , and like I said the wizard will take care of everything.

**[COLOR=#008000]Including eliminating existing partitions?  There are currently 4, I'm taking it back to 1.  That's why I asked about GParted and thought I may have to do this before starting.  I want this done before the O/S installs.[/COLOR]**[COLOR=#000080]
[/COLOR]
 At a later time when you have some familiarity with the ubuntu operating system you can consider making alterations to the standard install !

GParted is included in the desktop liveMedium, but you will not need it for this standard install.

" What file system should the drive be formatted  ->" as said above, not to fret, the install wizard will take care of it.

Command Line Interface, the means to unleash the true power of this operating system. In my 50 years exposure to computer in general the most powerful interface I have ever encountered ! It can be very complex and have a steep learning curve. Not to take away from the GUI, a wonder in it's own right.

**[COLOR=#008000]I'm not totally unfamiliar with Linux, I had a little Unix training a few years ago and have played with Linux live a few times.  I understand it's power which is why I'm migrating away from Windows.[/COLOR]**
[COLOR=#008000]-----------------
||Sidebar||  What really convinced me Linux was no longer the geek's O/S was when I had a job interview for a help desk position with a large NPO last summer.  The head office has over 200 employees, 10% were using Macs, 70% on Windows XP and the balance were Ubuntu.  I asked if Linux accounted for the back office/server farm plus IT staff and the Director replied, *"No, that represents operational workstations across the enterprise.  We are moving entirely away from Windows.  By 2014, all staff, but the department using Mac, will be Ubuntu on the desktop.  And, yes, we have dumped all of our WIN servers and replaced them with outsourced Unix boxes, the exception being one Exchange server that is still in-house and it will be gone by the end of 2013 as we outsource email."*||
-----------------[/COLOR]

What can I say but welcome to open source, a place where you will never hear:
[LIST]
[*]that is proprietary information 
[*]you have no need to know 
[*]we can not tell you 
[*]and other degrading statements 
[/LIST]
[COLOR=#008000][B]I'm already an open source fan and have been for years.  Most of the apps I use are open, now it's time to go to open source O/S.  The main reason is that I have two great workstations that are not old and I don't feel like trashing them just because XP is going away next year.

Unfortunately, I might still be buying a new WIN laptop shortly because of one mission critical software package that I rely on that has not been, and probably never will be, ported to Linux.  I'm debating whether to try to run it in a virtual environment with Linux. The issue is that it includes full support and I've been told that they provide zero support if it is not installed and running natively on Windows or MacO/S.  It's quite an expensive database/CRM package and I just upgraded to the newest version that came out a few weeks ago.  It's been heavily rebuilt by the developer and I don't want to throw away the support component.[/B][/COLOR]


Linux is a great operating system and the support for ubuntu, in many many arenas, make it a suburb operating system. Millions of programmers have and do make it so for many generations.[INDENT][INDENT]that's my story and I am[INDENT][INDENT][INDENT]stick'n to it
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]

[COLOR=#008000][B]
Thanks again![/B][/COLOR]

---

### Post by jmarkrobinson on 2013-10-20
[COLOR=#008000][B]Hi Basnhing-om

Thanks so much for the advice.[/B][/COLOR]

> **Bashing-om said:**
> jmarkrobinson; Hi ! My Welcome to the forum !

[COLOR=#008000]**Thanks.**[/COLOR]

If I may, in addition to xiccarph's advise, add;

Your fears are groundless in respect to installation of 'buntu. It is simple, quick and painless for the default install.
[COLOR=#008000]
**I have no fears.  Read again, I said, "I'm not the LEAST scared off by Linux command line."  I lived and breathed command lines in DOS and large scale legacy systems. (IBM/360,3083, AS/400, Univac 1100, DEC PDP-11)**[/COLOR]

However, as you are presently running XP, this may be older hardware. The flagship editions of ubuntu are resource hungry and require some hosses for a favorable experience. For older hardware I really endorse lubuntu. That is not to say you can not try ubuntu and see.
[COLOR=#008000]
[/COLOR][B][COLOR=#008000]The hardware is about 4y old with a 64bit AMD processor.  I'll max out the RAM now that it's dirt cheap.[/COLOR]
[/B]
See some options for 'buntu editions in the link "ubuntu Community" located above the thread post, choose your flavor and download the .iso image file;
check the file integrity, and burn as a "image" to disk;
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
As advised run 'buntu in "try ubuntu" mode to insure there are no hardware issues;
When ready to install 'buntu - do so with a WIRED internet connection !

[COLOR=#008000]**I'm wired all the time...but that's another story ;-)  All devices are wired all the time with the exception of a small tablet and my netbook but only when it's not on the desk, which is almost never.**
[/COLOR]
I suggest for the 1st time install that you do it as a simple default install, the install wizard will take care of everything, you just need to answer a few simple questions but take care to note and remember your username and PASSWORD. Your password is crucial to administering your system.
In the install -as you want only 'buntu installed as the single operating system- choose "erase entire disk and install ubuntu" , and like I said the wizard will take care of everything.

**[COLOR=#008000]Including eliminating existing partitions?  There are currently 4, I'm taking it back to 1.  That's why I asked about GParted and thought I may have to do this before starting.  I want this done before the O/S installs.[/COLOR]**[COLOR=#000080]
[/COLOR]
 At a later time when you have some familiarity with the ubuntu operating system you can consider making alterations to the standard install !

GParted is included in the desktop liveMedium, but you will not need it for this standard install.

" What file system should the drive be formatted  ->" as said above, not to fret, the install wizard will take care of it.

Command Line Interface, the means to unleash the true power of this operating system. In my 50 years exposure to computer in general the most powerful interface I have ever encountered ! It can be very complex and have a steep learning curve. Not to take away from the GUI, a wonder in it's own right.

**[COLOR=#008000]I'm not totally unfamiliar with Linux, I had a little Unix training a few years ago and have played with Linux live a few times.  I understand it's power which is why I'm migrating away from Windows.[/COLOR]**
[COLOR=#008000]-----------------
||Sidebar||  What really convinced me Linux was no longer the geek's O/S was when I had a job interview for a help desk position with a large NPO last summer.  The head office has over 200 employees, 10% were using Macs, 70% on Windows XP and the balance were Ubuntu.  I asked if Linux accounted for the back office/server farm plus IT staff and the Director replied, *"No, that represents operational workstations across the enterprise.  We are moving entirely away from Windows.  By 2014, all staff, but the department using Mac, will be Ubuntu on the desktop.  And, yes, we have dumped all of our WIN servers and replaced them with outsourced Unix boxes, the exception being one Exchange server that is still in-house and it will be gone by the end of 2013 as we outsource email."*||
-----------------[/COLOR]

What can I say but welcome to open source, a place where you will never hear:
[LIST]
[*]that is proprietary information 
[*]you have no need to know 
[*]we can not tell you 
[*]and other degrading statements 
[/LIST]
[COLOR=#008000][B]I'm already an open source fan and have been for years.  Most of the apps I use are open, now it's time to go to open source O/S.  The main reason is that I have two great workstations that are not old and I don't feel like trashing them just because XP is going away next year.

Unfortunately, I might still be buying a new WIN laptop shortly because of one mission critical software package that I rely on that has not been, and probably never will be, ported to Linux.  I'm debating whether to try to run it in a virtual environment with Linux. The issue is that it includes full support and I've been told that they provide zero support if it is not installed and running natively on Windows or MacO/S.  It's quite an expensive database/CRM package and I just upgraded to the newest version that came out a few weeks ago.  It's been heavily rebuilt by the developer and I don't want to throw away the support component.[/B][/COLOR]


Linux is a great operating system and the support for ubuntu, in many many arenas, make it a suburb operating system. Millions of programmers have and do make it so for many generations.[INDENT][INDENT]that's my story and I am[INDENT][INDENT][INDENT]stick'n to it
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]

[COLOR=#008000][B]
Thanks again![/B][/COLOR]

---

### Post by Bashing-om on 2013-10-21
jmarkrobinson; Hey;

You will make a great addition to our family.
Getting started I still suggest you do a standard simple install letting the install wizard take care of all the details. The process will wipe the 1st hard drive of anything presently on it, reformat the disk to ext4 , and partition it into one partition for "/" containing all the file system in that single partition and a small partition for swap (page file in Windows speak). Once you are familiar with the file system, on subsequent installs on this and other machines you will know how you use the system and have some ideas as to how to better partition for a particular purpose. We will get into that later.

For now I want you to dive in, doing more than just getting your feet wet. The better way I know is with a standard install and learn from there. No one knows how you use your system or what is in your best interest better than you.

Keep in mind, this advise is for a stand alone ubuntu operating system. If you are not prepared in all respects to leave Windows behind, then there is the option in the install wizard to "dual boot" sharing the hard disk between Windows and ubuntu . If you do take this route, then I do advocate rather letting the installer handle things, to take matters into your own hands and prepare a partition for sharing between the two operating systems. As you are manually setting up one partition, may as well go whole hog and set up at least a separate "/home" partition too .. there are distinct advantages in having that "/home" in it's own partition. Might consider this on your 2nd machine ?

Departing from Windows is not to be taken lightly; as many say " ubuntu is not a replacement for Windows"

I left Window's behind at XP service pack 2 - and I have never looked back. However, I have no deep grained commitments to anything Windows' related and ubuntu fulfills all my needs. Your mileage will vary. Time and experience will tell.

[INDENT][INDENT]jump right in,
[INDENT][INDENT][INDENT]but keep a live preserver
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bucky Ball on 2013-10-21
Welcome. I will add that,

* No, Ubuntu will NOT install on NTFS. You need to use EXT* filesystem;
* You will need more than one large partition as you will need a /swap partition as well as / (unless you don't intend using a /swap);
* You can let Ubuntu install 'automagically' but, as you are comfy with Gparted, that is boring as you might not like what you end up with: I suggest choosing 'Something Else' at the partitioning section of the install and making your one large / partition with a 2Gb /swap at the end: use *exactly* the setup and sizes you want;
* You can format the entire disk to 'free space' and fire away before or during the install process, you don't need to 'pre-format' any partitions or set anything up, though: just leave free space.

Considering your previous experience, I'd say you're good to go. 'Trying' Ubuntu from the install media will give you an idea of how it will run, then fire away. Terminal not required. Good luck. ;)

PS: There are many exotic variations but, as Bashing-Om suggests, keep it simple for starters. I will suggest though that you make the entire disk an extended partition then create logical partitions in there for / and /swap. If you want to shrink and add partitions later this might save a headache and, yes, Ubuntu will run from a partition inside an extended partition (unlike Win).

---

