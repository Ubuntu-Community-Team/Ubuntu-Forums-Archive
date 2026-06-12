---
title: "Ubuntu wont boot after install"
date: 2006-04-07
forum: Installation &amp; Upgrades
---

### Post by greenstar on 2006-04-07
I've installed Ubuntu many times since Hoary was released and this is the 1st time I've seen this.

GRUB is working fine - I can boot into WinXP or start to boot Ubuntu Breezy. WinXP works fine, but Ubuntu doesn't. Just after the brown screen comes on and says 'Loading Modules' Ubuntu returns to text mode without reporting any modules as successfully loaded, and this is what I see:

Uncompressing Linux... OK, booting the kernel.
Loading, please wait...
ALERT! /dev/hde1 does not exist. Dropping to a shell!

/dev/hde1 is my root partition. I know it's there because I can mount it with Live CD and browse it's contents. I'm beginning to wonder if I have a damaged partition or something.

Any suggestions?

Thanks,
Greenstar

---

### Post by greenstar on 2006-04-07
Ok, it's not the partitions. I DBAN'ed the hard disk I'm installing on, then created brand new partitions with Ubuntu's partitioner. 

Any ideas or suggestions?:confused:

Greenstar

---

### Post by greenstar on 2006-04-08
After zeroing the disk & partitioning with Ubuntu, I reinstalled fresh with the same result. 

Next, I rearranged my drive cables & jumpers so that my Ubuntu disk is hda & the / partition is hda1, reinstalled (yeah, I know I could've just edited grub's menu.list...) This time I get a similar error.

The kernel starts to boot, then I get the brown Ubuntu screen that says loading modules near the bottom, 5-10 seconds go by while nothing appears to happen, then I'm dropped back to text mode and see this:

Uncompressing Linux... OK, booting the kernel.
Loading, please wait...
ALERT! /dev/hda1 does not exist. Dropping to a shell!

I get this from Ubuntu & Kubuntu. Can anyone shed some light on this?

---

### Post by AmboyGuy on 2006-04-08
Never mind, you already were aware of what I posted.
Sorry.

---

### Post by greenstar on 2006-04-08
AmboyGuy,

Thanks for stopping in and looking anyway. I appreciate your willingness to help.:-D

Greenstar

---

### Post by greenstar on 2006-04-08
:-k
I just tried to boot Ubuntu again and this time it gave additional errors:

```
Uncompressing Linux... OK, booting the kernel.
Loading, please wait...
[B]FATAL: Module unknown not found.
mount: Mounting /dev/hda1 on /root failed: No such device
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /dev on /root/dev failed: No such file or directory
Target filesystem doesn't have /sbin/init
[/B]
BusyBox v1.00-pre10 (Debian 20040623-1ubuntu22) Built-in shell (ash)
Enter 'help' for a list of built-in commands.
[B]
/bin/sh: can't access tty; job control turned off[/B]
#
``` 
I would appreciate any assistance. Thanks,

Greenstar

---

### Post by greenstar on 2006-04-08
I just booted up the Beatrix LiveCD to browse my disks & hda1 is there, as well as the files and directories one would expect to see on Ubuntu's / directory. I looked for & found /sbin/init, so it is in fact there. So far as I can see, Ubuntu installed correctly & grub is attempting to boot from the correct partition.

I've been running Ubuntu on this box since Hoary was released, and have been using breezy for some time. Now I try to reinstall, and I can't get Ubuntu to boot. I'm at a loss for what to do next.

Greenstar

---

### Post by greenstar on 2006-04-09
Just successfully installed Hoary. So why won't breezy install? Maybe I'll try Dapper Testing tomorrow. I think I'm going to try apt-get dist-upgrade and see if breezy will boot then. Should be interesting... I'm curious now.

Greenstar

---

### Post by greenstar on 2006-04-09
Apt-get successfully upgraded hoary to breezy and everything was fine until I rebooted, then I find myself right back in the place I started.](*,) Same error message as the last time. Guess I'll try Dapper Testing today. I think they just released flight 6...

Anybody out there? Suggestions? Hints? Ideas?

Greenstar

---

### Post by HwyXingFrog on 2006-04-10
> **greenstar]:-k
I just tried to boot Ubuntu again and this time it gave additional errors:

```
Uncompressing Linux... OK, booting the kernel.
Loading, please wait...
[B]FATAL: Module unknown not found.
mount: Mounting /dev/hda1 on /root failed: No such device
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /dev on /root/dev failed: No such file or directory
Target filesystem doesn't have /sbin/init
[/B]
BusyBox v1.00-pre10 (Debian 20040623-1ubuntu22) Built-in shell (ash)
Enter 'help' for a list of built-in commands.
[B]
/bin/sh: can't access tty said:**
> 
#
``` 
I would appreciate any assistance. Thanks,

Greenstar

I also have the exact same problem.

I have been running ubuntu on an old athlon computer (pre 64bit) since mid Feb as a web server and it was working awesome. I had Ftp, SSH, Apache, Gallery 2.0, C & C++ compiler, and java compiler working awesome as well.

I was uploading some pics at night to Gallery 2.0, everything was fine, I then went to bed with a working web server.  About midway through the next day I decided to try to upload some more pics and nothing happened.  I switched my monitor over to analog to see what was up and it was a black screen but the computer was still on, tried some stuff and nothing happened so I turned it off.

When it booted I got the exact same messages about booting the filesystem.
I have no clue what happened, I thought maybe the hard drive died, but I also had a very small windows partition on it that I hadn't used since I set up the computer (it was kinda a backup plan incase it didn't work, this was my first attempt at Ubuntu).  The windows partition booted fine!!!

I also have no clue what is wrong now, I am in the middle of final exams in engineering so I will not be able to play with it for a couple weeks.

---

### Post by HwyXingFrog on 2006-04-10
.....and to continue....

The only thing I did recently was add a USB 2.0 PCI card, but it has worked for a couple weeks with no problems.  I just don't know how long it was up for between reboots, and if it may have been an update that caused it.

---

### Post by greenstar on 2006-04-10
HwyXingFrog,

I'm gonna go out on a limb and say I'd be surprised if your USB card was the problem... real surprised.

Ok, the verdict is in: Hoary & Dapper boot fine. Breezy refuses to play. Strange, I've been running Breezy fine for several months (since shortly after it's release) and never had any problems. Now I can't get Breezy to boot after re-installation.:-k 

Now that I think about it, there have been a few computers that have forced me to install Hoary, then dist-upgrade to Breezy since Breezy wouldn't install from CD. But my box wasn't one of them... until now.

Anyone have any ideas? Otherwise it looks like I won't be bothering with Breezy anymore, I'll stick with Dapper Testing until official release.

Greenstar

---

### Post by chopper77 on 2006-04-12
I'm having the same issue and no one knows how to solve it.  I see other threads where it's been posted have pretty much been ignored.

My situation is a little different, but all the material facts are the same.  It's disappointing because I really thought distros like Ubuntu were making great strides in Linux usability (for the "average" user), but when stuff like this can still happen and the only answer is "reinstall" I think that it's pretty clear I was incorrect.

I don't know what to say except that it's too bad.

---

### Post by HwyXingFrog on 2006-04-13
Will a reinstall work?

I don't have time to try yet.  If I reinstall, i might try kubuntu.

---

### Post by chopper77 on 2006-04-13
Yes, I think a reinstall would probably work, but then you still may get the error again sometime.  You just don't know.  I read about one guy who reinstalled 2 or 3 times and kept getting this.  Not gonna take that risk.

As of right now I'm installing MEPIS.  Had good luck with it before, I just need something to do a little programming and indulge my nerd side here and there.  They recently decided to merge in a bunch of Ubuntu stuff, I'm not sure how much exactly, but I'll cross my fingers and hope it doesn't suck as horribly.

---

### Post by skendale on 2006-04-20
has anyone figured this out yet? noob here trying to install ubuntu to external hard drive...but am getting this same error...tried a couple of reinstalls and messing around w grub menu.lst to no avail...

---

### Post by louca on 2006-04-21
[QUOTE=greenstar]I've installed Ubuntu many times since Hoary was released and this is the 1st time I've seen this.

GRUB is working fine - I can boot into WinXP or start to boot Ubuntu Breezy. WinXP works fine, but Ubuntu doesn't. Just after the brown screen comes on and says 'Loading Modules' Ubuntu returns to text mode without reporting any modules as successfully loaded, and this is what I see:

Uncompressing Linux... OK, booting the kernel.
Loading, please wait...
ALERT! /dev/hde1 does not exist. Dropping to a shell!

/dev/hde1 is my root partition. I know it's there because I can mount it with Live CD and browse it's contents. I'm beginning to wonder if I have a damaged partition or something.

Any suggestions?

Thanks,
Greenstar[/QUOTE]

i am new to linux and this is the first distro i am trying, and i am getting almost the same problem.

my problem is alittle different only that everything was going fine until it got to the part where it synchronizes the clock with ubuntu.org or which ever site it is :confused: 
then like you said, it switches to text mode.. sort of :? 
I can still see an installation bar behind some of the words and then they just scroll up and engulf the screen, in some cases the computer seems to get to the sign in screen judging from the results i get when i press buttons.

what is going on? :?

edit:
each line that comes up looks like this
[xxxxxxx.xxxxxxx] hub 1-0:1.0 over-current change on port 1
[xxxxxxx.xxxxxxx] hub 1-0:1.0 over-current change on port 2

where each of the x's is part of a larger number which keeps incrementing.

thanks for ne help rendered

---

### Post by louca on 2006-04-22
i am up and running.

try unplugging all usb devices and disabling usb in the bios, then booting.

if it works, install all the updates then reboot and turn on usb again and plug them in, and you should be able to use them.

---

### Post by greenstar on 2006-04-27
skendale is installing to an external hard disk. Is anyone else having this problem using a non-standard disk layout. For example, I have 3 internal hard disks, 2 internal optical drives, 1 hard disk & 1 optical drive are on a PCI to IDE RAID card, the other 2 hard disks & 1 optical drive are on the motherboard's IDE channels.

I am now using Dapper Testing because it installed without hassle. This is really weird since I've been using Ubuntu on this box since Hoary was released. Never had trouble until this. My motherboard died recently, so I bought a new one and attempted to reinstall Ubuntu. I also rearranged the layout of my disks. Before my mobo died I had 2 hard disks on the RAID card, each as master on it's own IDE channel, and I had the 3rd hard disk & 2 optical drives on the motherboard's IDE channels.


louca,

Congratulations, I'm glad you got up and running and I hope you enjoy Ubuntu as much as I do.:D

---

### Post by barryred on 2006-05-30
I too am pretty new to this whole Linux thing, but have installed a couple of distros on my maching before trying Ubuntu(including linspire, Red Hat Enterprise Linux(by accident) and Fedora Core 5). All of these worked fine and I could boot into the GUI.

I tried disableing the "OnChip USB Controller" in the BIOS, but it made no difference. 

Ubuntu is installed onto a hard-disc which it partitioned itself(albiet that I chose the partitions). And had 50Gb to it's self as a primary partition, as well as 50 for a logical partition, and 10 for as SWAP space.

A previous poster commented on the fact that he is using a pre 64bit Athlon processor, and I too am using the same (AMD Athlon 2000+), althought I doubt that that would make any differene.

After the error comes up, i get the following prompt:
```
BusyBox v1.00-pre10 (Debian 20040623-1ubuntu22) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
#
```

Obviously most of that's unimportant, but I presume that error starting with "/bin/sh: ..." in relevant.

I also tried, from "#"  to 
```
#cd /dev/hde1
```
and it says: 
```
cd: 15: can't cd to hde1
```

Any help would be usefull, I decided to try ubuntu because I got the impression there was a fairly good community backing, but I'll go back to Fedora Core5 if there are a lot of niggly things like this in ubuntu, community support or no support.

Cheers.
Barry

---

### Post by mully on 2006-06-09
barryred,

Did you unplug all of your USB devices and reboot?

I was having the exact same issue with Dapper after successfully using for a week.  After reading louca's post above, I unplugged all of my USB devices, powered off, powered back on again, and Gnome booted up like a champ!  I did not even have to disable USB in the bios.  

After boot up, I plugged all of my USB devices back in and I am good to go again.  I am just hoping that this does not have to become a routine with every reboot!

---

