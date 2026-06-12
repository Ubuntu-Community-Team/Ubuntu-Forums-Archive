---
title: "Problem after upgrading Ubuntu 13.04 to 14.04"
date: 2015-11-19
forum: Installation &amp; Upgrades
---

### Post by durward2 on 2015-11-19
I have a self-modified computer: Asus M3A78-EMH with a AMD Phenom 9600 quadcore, 2GB RAM, 2 LCD monitors, boot harddriive in Linux format, 3 other hdd's in NTFS format, DVD-RW (sometimes works, sometimes does not), connected to my home network with 2 routers and 1 24-port switch, hooked to Windstream as my ISP.

I had Ubuntu 13.04 running fine for a couple of years. I decided to click on the upgrade to Ubuntu 14.04 and started down that path. When the upgrade finished setting up, it was ready to restart and finish installing 14.04.

When the computer came up at the log-in screen, all my users from 13.04 were there. I typed in my password and the computer proceeded to start. Blink, and it was back to the log-in screen.

I turned around and connected to this computer from another computer running Ubuntu 15.04, using SSH. I can run programs that are not graphical. 

What can I do to get my log-in to work?

---

### Post by Bashing-om on 2015-11-19
durward2; Hummm ...

Proprietary graphic's driver that got broke in the upgrade process ??
At the login screen, key combo ctl+alt+F1,
Can you log into the system here ?

If so, consider purging/(re-)install the driver.

[INDENT][INDENT]just my thought
[/INDENT][/INDENT]

---

### Post by durward2 on 2015-11-19
I was able to open terminal window 1 (Ctrl-Alt-F1) and log in. Then I had to determine the video card model (this machine is 6 years old). It has an ATI Radeon HD 3200. I then searched how to remove video drivers and followed directions (rebuilt the X11 etc.). Now I have to look up how to get the drivers for the ATI Radeon HD 3200 so that I can split the display between my two monitors at their desired resolution.

Thanks.

---

### Post by durward2 on 2015-11-19
How do I mark this question as Solved?

---

### Post by Bashing-om on 2015-11-19
durward2; Ouch !

AMD dropped support for all cards less than 5X a few years back . Open source driver ( or 12.04.1 ) is your best option.

to mark as solved :
1st post -> thread tools -> drop down menu :
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]sad but that it the way it is .
[/INDENT][/INDENT]

---

### Post by durward2 on 2015-11-20
I have tried to follow, one at a time, several ways to install AMD/ATI Radeon HD 3200 graphics drivers in Ubuntu 14.04.03, but to no avail.

I have not been able to get a simple VGA graphics driver installed to get a graphical display. I can only get a terminal (6 of them on the computer) and several through SSH from other computers (I have 7 computers with Ubuntu of various versions and two MS Windows computers at working distance in my office corner).

Where is a site to step me through re-installing a basic VGA driver? and maybe a work-around for the Radeon HD 3200 on-board graphics of my Asus M3A78-EMH board?

---

### Post by Bashing-om on 2015-11-21
durward2; Morning .

Yes, there are some guides around... be aware however, that with HWE in 14.04.3 one has to be sure to install the modules for the HWE stack Not for a "normal" kernel.
[https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection#Problem:_Need_to_purge_-fglrx](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection#Problem:_Need_to_purge_-fglrx)
[http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide#Removing_Catalyst.2Ffglrx)

But the method for removing the driver depends on how you installed it.
Did you install it from the repo; by downloading from ATI and creating a .deb; or by running the .run file from ATI directly?

[https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

If you are HWE enabled. one must understand the packages/modules installed and to be (RE-)installed for the open source driver.
see:
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

-------------------

I have been though this a couple of times, and I will be more than glad to offer continued assistance to clean your system up and get the open source driver installed .

together we will
[INDENT][INDENT]figure out what is not going on
[/INDENT][/INDENT]

---

