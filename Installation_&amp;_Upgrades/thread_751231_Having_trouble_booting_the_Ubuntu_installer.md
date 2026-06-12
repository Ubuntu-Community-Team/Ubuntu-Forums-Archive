---
title: "Having trouble booting the Ubuntu installer"
date: 2008-04-10
forum: Installation &amp; Upgrades
---

### Post by jmcorro on 2008-04-10
I'm a relative Linux newbie and have been trying to install Ubuntu server 7.1.  Contrary to all the great things about how easy Ubuntu is, I've been having nothing but frustrations and I don't even have the d@mn thing installed yet!  I'm looking for this box to be a file server and perhaps web server if I have time.  I have chosen the server edition instead of the desktop edition as this is an older box and I've read that (as far as less-capable hardware is concerned) its easier to "build up" the server edition to my file/web server needs than to "dumb down" the desktop edition.  Additionally, I've read that the server edition is intended to be headless which is the case here.  

My box has an AMD Athlon 900mhz, a gig of memory (I *think*), (2) 40gb Western Digital (not SATA) hard drives in master/slave configuration, and a single Iomega CD-RW drive.   The primary HD had Windows 2000 server on it and *might* have been formatted using NTFS (don't remember anymore).

When I go through the installer I boot from CD w/o any problems.  After selecting "Install to Disk" from the main menu, I get a number of exceptions printed out...I don't know if that's normal or what, but it continued through so I just ignored it.  The first problem is when it gets to the point where it tries to detect the CD-ROM.  It says it doesn't recognize it.  I read in various forums different ways of handling the problem and eventually found that going to a terminal and typing "hdc=nodma" got me past the problem.  The next frustration occured when it couldn't find the primary hard drive.  At this point, I was already ~2 hours in and losing my patience.  I tried searching the forums for useful tips, but yielded nothing.  

My questions are:

- Can someone tell me if my solution to getting past the "CD-ROM not recognized" problem is appropriate?  I have no idea what "hdc=nodma" means so I don't know if I'm setting myself for future headaches or am actually causing the "no hard drive found" problem later on.  I'd LOVE a listing of what potential solutions can be tried as well as what the implications/side-effects/etc of said solutions are.
- Can anyone suggest possible solutions w/ the "no hard drive found" problem?

At this point, I'm ready to chuck ubuntu out the window and go back to MS.  Please don't let me fall back to the dark side!!!  Thanks in advance for any help!

john

---

### Post by dstew on 2008-04-10
> Can someone tell me if my solution to getting past the "CD-ROM not recognized" problem is appropriate?If it works, that is fine. The kernel parameter hdc=nodma tells the kernel not to attempt to use direct memory access with the hdc drive, which is probably your CD-ROM drive. It only affects the kernel used by the installer, and will not be carried over into your installed system.

What .iso did you download? Have you tested the CD for integrity (menu item at the first screen)?

---

### Post by warp99 on 2008-04-10
If this is just going to be a server don't use the GUI install. Download the 'alternative CD' from the Ubuntu.com download page, just tick the box marked 'Check here if you need the alternate desktop CD.'

Also use this guide for kernel boot options for install:

[https://help.ubuntu.com/community/BootOptions?highlight=%28bootoptions%29](https://help.ubuntu.com/community/BootOptions?highlight=%28bootoptions%29)

The various options I would try are 'noacpi' 'irqpoll' and the 'hdc=nodma' if that is working.

Edit:
You understand that a Ubuntu Server install does not include a desktop for security purposes.

---

### Post by jmcorro on 2008-04-10
> **warp99 said:**
> 
You understand that a Ubuntu Server install does not include a desktop for security purposes.

Hmmm...I didn't know that.  When I read another poster on another forum state that the server edition was "intended to be headless" I didn't know that meant the omission of a desktop all together.  That little note right there probably saved me hours of screaming "this f'ing thing FINALLY installed and the UI isn't even able to start!?".  

My goal was to not use a monitor on the computer so that it can sit off on a shelf nice and neat and instead remote connect in, but still connecting to a desktop.  Since I'm a newbie, I'm not comfortable doing all my work from the command line.  I'm planning on relying on the desktop to be my crutch until I learn more.  I think I'll now opt to go Kubuntu and vnc (or nomachine as someone recently informed me of) in.  

Thanks for the very helpful responses!

---

### Post by jimbo99 on 2008-04-10
I'd recommend you run an analysis of your hardware before attempting.  I'd be embarrassed if you got all hot and bothered about Ubuntu not working when it turns out to be a hardware issue.

Off the manufacturer's web site there's generally a link to a set of diagnostic tools to run against your hard drives.

Off the live CD is generally a memory test option.  You should run those before attempting to get this to work.

Examine your motherboard and look for bulging and burst capacitors.  If you have any give up the ghost on that board.

That is also a socket 462, so that means that you can most likely upgrade the processor to a 1.3 or 1.4 ghz cpu, being either another Duron or an Athlon.  Would be worth the attempt to get better performance.

Also, I have had similar errors on installing, so my suggestion would be to temporarily use a different CD/DVD drive for the install.

Another suggestion would be to burn that CD/DVD at a low rate (4x or 1x).

And, finally, others have suggested passing parameter to the kernel at boot to overcome some of this.  They are worth a try also.

---

### Post by warp99 on 2008-04-10
> **jmcorro said:**
> I think I'll now opt to go Kubuntu and vnc (or nomachine as someone recently informed me of) in.  

Thanks for the very helpful responses!

Kubuntu is the same thing as Ubuntu with the only difference being that it uses KDE instead of Gnome as the Desktop. You may have the same problems unless you use some of the kernel boot options that I suggested in a prior post. So try the boot options and possibly you will need to use the alternate CD for Kubuntu.

---

### Post by jmcorro on 2008-04-11
> **jimbo99 said:**
> 
Off the manufacturer's web site there's generally a link to a set of diagnostic tools to run against your hard drives.

Off the live CD is generally a memory test option.  You should run those before attempting to get this to work.

That is also a socket 462, so that means that you can most likely upgrade the processor to a 1.3 or 1.4 ghz cpu, being either another Duron or an Athlon.  Would be worth the attempt to get better performance.

Also, I have had similar errors on installing, so my suggestion would be to temporarily use a different CD/DVD drive for the install.

Another suggestion would be to burn that CD/DVD at a low rate (4x or 1x).

And, finally, others have suggested passing parameter to the kernel at boot to overcome some of this.  They are worth a try also.

In the case of the potential hardware failures, I did run the memory test and didn't see any reported errors.  I didn't try the diagnostic tools you referenced to verify my harddrives, but I had to run W2K server to move various files to an external USB harddrive in preparation for Ubuntu.  Everything worked as expected in that case so I wouldn't think I'd have any HD problems.  

As for processor, I'm considering that option.  Since I'm also building a MythTV box much of my computer fund is already spoken for.  I'm hopeful that the current hardware will be sufficient (and several, more Linux-experienced co-workers than myself think I should be fine)...based on that I don't want to spend for a more powerful CPU when it may not be necessary.

I'm taking your suggestion of burning at a slower speed though - I'll be trying to install from a new kubuntu CD (burnt at a slower speed) tonight.  We'll see how that goes.

---

### Post by jmcorro on 2008-04-12
<sigh> About 6 -7 hours worth of trying to get this f'ing thing working an still no farther than I was last night.  My brain is pretty fried at this point, but I'll try to enumerate the things I've tried (in order as much as I remember).  Btw...I said earlier that the "ide=nodma" option got me past this...I must've been wrong.  Being up till 3am last night got me punchy...I got past the CD-ROM problem and to the point where it asked for the computer's name then failed on not being able to find the hard drive.  Well when I tried tonight, what I thought were the same steps did not get me past the CD-ROM problem.  I must've done something w/o knowing/remembering it to get me past the problem last night and am not doing it tonight.


[LIST]
[*] Installing from Kubuntu 7.1
[*] Installing from Kubuntu 7.1 w/ the boot option (I used the F6 key to get a command line and appended) "ide=nodma"
[*] Installing from Kubuntu 7.1 alternate CD
[*] Installing from Kubuntu 7.1 alternate CD w/ the "ide=nodma" option
[*] Installing from Kubuntu 7.1 alternate CD w/ "pci=noacpi", "acpi=oldboot", and "ide=nodma"
[*] Installing from Kubuntu 7.1 alternate CD w/ the "hdc=cdrom" option
[/LIST]

In all cases I always got the "No common CD-ROM was found" and ultimately ended up being prompted for a driver from the floppy which I declined leading me to the dialog asking me for which device file that should be used.  It stated I can check the /dev directory (I'm presuming to see if there's an hda, hdb, hdc, etc).  I looked in the /dev dir as suggested, but didn't see anything w/ hda, hdb, etc.  I also didn't see anything listed under "/cdrom".  Is this to be expected?  

When I look at the /dev directory I see the following contents: bus, console, disk, fb0, fd0, full, hpet, input, kmem, kmsg, log, mem, net, null, oldmem, port, psaux, ptmx, pts, a whole bunch of ones starting w/ "pty", several ones starting w/ "ram", random, rd, rtc, shm, snapshot, tts, a whole bunch starting w/ "tty", urandom, usb1, usb2, usbdev1.1_ep00, usbdev1.1_ep81, usbdev2.1_ep00, usbdev2.1_ep81, vc, several starting w/ "vcs", and zero.  I've been noticing that I will *sometimes* get an "scd0" displaying in /dev too, but not all the time.  Is there anything to that?  I thought that I read SCSI drives can display as "scd", but my CD-RW is connected via IDE.

I was reading tons of posts on how to debug this and one suggestion was to do a "cat /etc/fstab".  In my case the results were:
none   /dev         devfs      defaults   0   0
none   /dev/pts   devpts   defaults    0   0
none   /proc        proc       defaults    0   0
none   /sys          sysfs      noauto      0   0
Shouldn't there be one listing my cdrom drive in there?

The hardware coniguration is 2 EIDE 40gb hard drives in master/slave on the primary IDE and the CD-RW as a master on the secondary IDE.  Should I be looking to change this to have the CD-RW as the slave on the primary IDE?

I'm REALLY getting my tail kicked here.  Can anyone lend a hand?

---

### Post by dstew on 2008-04-12
I think the kernel parameter you used before was hdc=nodma. You can also try acpi=off.

The Live CD file system is different from the file system on a hard disk install. The fstab file in the Live CD system is just a stub, and editing it doesn't help. The Live CD file system is mounted using different techniques than those used in a hard disk install. You only need to edit fstab if you have trouble with an installed system. You are having trouble with the Live CD.

> The hardware coniguration is 2 EIDE 40gb hard drives in master/slave on the primary IDE and the CD-RW as a master on the secondary IDE. Should I be looking to change this to have the CD-RW as the slave on the primary IDE?
I am not sure it would help. If you change where the CD-ROM is, then the kernel parameter might have to change also. You could try it, though.

Since it seems like your problems are mainly with the CD-ROM, you might consider other installation methods. Sometimes you can take out a hard drive, put it in another computer, install Ubuntu on it, put it back in the first computer, and it works. You can do a Debian minimal install using floppies, and then use [Unetbootin]("http://lubi.sourceforge.net/unetbootin.html") to install directly over the internet.

---

### Post by jmcorro on 2008-04-13
Ok...last update for this thread.  After thrashing about trying to install 7.10 I was getting ready to go to Fedora as I read other posts from people w/ similar problems on Ubuntu that didn't have it w/ Fedora.  I finally read one post that said to try 7.04 or 6.10 so I opted to try 7.04 first and magically everything worked.  Not even so much as a blink from the installer about not being able to find any hardware.  As a Linux newbie, it diminishes my perception of Ubuntu that something that works in 7.04 would *not* work a couple minor revisions later....isn't 7.10 supposed to be the final release Gutsy Gibbon?

---

