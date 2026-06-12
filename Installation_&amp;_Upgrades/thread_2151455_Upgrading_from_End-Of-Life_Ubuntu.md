---
title: "Upgrading from End-Of-Life Ubuntu"
date: 2013-06-04
forum: Installation &amp; Upgrades
---

### Post by ajr893 on 2013-06-04
Hey, All,

I've been using Ubuntu for some time now. I am currently working with an older server that I have put ubuntu 9.04 on, in hopes of upgrading from there to 12.04. The reason for this was because the drivers were not installing when I was trying to run the 12.04 installer, and I had to go all the way back to 9.04 before I actually made headway. 

Unfortunately, I was not up to date on "end of life". 9.04 was my first Ubuntu just a few years back, I figured it would still have limited support, I didn't think to actually go look for the end of life date. Which apparently was three years ago, already!

Does anyone know of a way to do an in place upgrade from 9.04?

---

### Post by Cheesemill on 2013-06-04
It's probably going to be much quicker and easier to install 12.04 from scratch rather than upgrading as you would have to do 3 consecutive upgrades, each of these will take a long time as well as the possibility of the upgrade failing.

What errors were you getting when you tried to install 12.04?

Also can you post your hardware specs so that we can make sure your machine can actually run 12.04.

---

### Post by ajr893 on 2013-06-04
My best guess is that there aren't any drivers for my hardware in the 12.04 base install. After I install, the machine gets past post and then I lose signal to the monitor, but it is still running.

Hardware:
HP DL360 G4

8GB DDR2
two Intel Xeons (3GHz)
Integrated graphics

That's all I know off the top of my head.

---

### Post by Sef on 2013-06-04
[COLOR=#000000] > The reason for this was because the drivers were not installing when I was trying to run the 12.04 installer,[/COLOR]

What drivers were not installing, and what was happening because of the lack of them?

---

### Post by beatgr on 2013-06-13
[QUOTE=ajr893]I've been using Ubuntu for some time now. I am currently working with an older server that I have put ubuntu 9.04 on, in hopes of upgrading from there to 12.04. The reason for this was because the drivers were not installing when I was trying to run the 12.04 installer, and I had to go all the way back to 9.04 before I actually made headway.

Does anyone know of a way to do an in place upgrade from 9.04?[/QUOTE]
IF you are using UBUNTU SERVER editions -- stick to the LTS releases.
* Leave the intermediate and development releases for Desktops and Experimental PCs.*

At a minimum, I would do a fresh install of Ubuntu 10.04.4 LTS (Lucid Lynx) Server edition.
*This likely still supports your hardware, IF that is truly your issue.*
[http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

The last *Lucid Lynx* image refresh was performed in Febuary 2012, and Server edition support is good till April 2015

10.04.4 Release Notes
[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes/ChangeSummary/10.04.4](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes/ChangeSummary/10.04.4)

[QUOTE=ajr893]My best guess is that there aren't any drivers for my hardware in the 12.04 base install. 
After I install, the machine gets past post and then I lose signal to the monitor, but it is still running.[/QUOTE]
That is a monitor resolution issue, very common when you swap different video monitors on a Ubuntu install / upgrade.
*You can edit the /etc/default/grub file to resolve that issue.*
[https://help.ubuntu.com/community/Grub2#Boot_Display_Behavior](https://help.ubuntu.com/community/Grub2#Boot_Display_Behavior)

IF you still desire to install Ubuntu 12.04.2 LTS (Precise Pangolin), download the latest Server CD image.
Support is good to April 2017.
[http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

DO a Clean install, on your boot drive.  USE a full-featured (resolution support) monitor.

Consult the Ubuntu BOOT OPTIONS Tutorial
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

GRUB2 Documentation
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by beatgr on 2013-06-13
[QUOTE=ajr893]After I install (12.04.2 LTS), the server gets past POST and then I lose signal to the monitor, but it is still running.[/QUOTE]
Identical issue (blank video) when I upgraded from 10.04.4 LTS to 12.04.2 LTS Server versions this evening.

I ALWAYS install OpenSSH Server on my Ubuntu servers.  
THEN I can work with the server via network to address (correct) these issues !

I use puTTY on my Windows computer for accessing the server remotely (via network) using SSH.

The problem, for me, was resolved by editing the file:  /etc/default/grub

12.04.2 LTS Server goes into Graphical modes (I am not fond of that default situation with simple server hardware)
You will need to uncomment (remove) the console and 640x400 entries.

I did that and came back to expected operations.

gb

---

### Post by 1clue on 2013-06-13
Unless I missed it somewhere you seem to be trying to run a desktop version.

You can go through the supported hardware for each version and compare that with what you have in your box, to find out what version is the best fit.  Then download the iso of that version, burn it to CD and then boot off it.  When it comes up, don't install directly, just go to the 'try it' option or whatever it is.

If the version on the CD works, then chances are you can get the installed product to work even if it takes a little tweaking.

This will help you keep you from ruining your setup.

I don't know what your budget is, but a new box can be had for a really small amount of money.  An Atom processor would easily keep up with most desktop hardware that old.  Have you considered replacing your existing hardware?  Another thing to consider is there are a lot of "minimal" systems out there, meaning just a board and minimal hardware, not much room for cards but plenty of room for RAM and one or two disks.

Another option is to convert your box into a VM and run it on KVM or similar on a newer system.

---

