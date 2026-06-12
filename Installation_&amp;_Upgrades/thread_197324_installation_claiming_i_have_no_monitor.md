---
title: "installation claiming i have no monitor"
date: 2006-06-15
forum: Installation &amp; Upgrades
---

### Post by bob_the_d on 2006-06-15
I'm trying to install Ubuntu 6.06 for the first time, and I'm hitting a roadblock that I have no idea to fix.

To get it out of the way, here are my system specs:

Monitor: Dell 2005 FPW (DVI)
Video Card: Sapphire ATI Radeon x800 GTO PCI-E
Memory: 1GB
CPU: Athlon XP 3200+ 64 Bit
Motherboard: MSI K8N Neo4

I downloaded Ubuntu Desktop 6.06 Desktop edition.  I verified the disc and checked the memory and everything seems to check out.

When I try to start and install Ubuntu, it tries to load everything and spits out an error.

"Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly."

The server output says:

(==) Log File: "/var/log/Xorg.0.log", Time: Thu Jun 15 15:45:19 2006
(==) Using config file: "/etc/X11/xorg.conf"
(EE) No devices detected.

Fatal server error:
no screens found

I'm pretty new to Linux in general and this is my first time trying to install Ubuntu, and I was hoping someone could tip me in on what's going on here.

Thanks in advance!

---

### Post by bob_the_d on 2006-06-15
Trolled the forum archives some more, ran across some related issues but they either worked, or dealt with resolution problems after the installation occured.  However, I can't even get the installation to run.  Anyone have any solutions?

---

### Post by bob_the_d on 2006-06-15
So when the regular (first option) of the install menu gives me the error and takes me back to the console, I tried the configuration utility using the command:

```
sudo dpkg-reconfigure xserver-xorg
```

After choosing the color depth in bits, it takes me back to the console with the following message:

```
xserver-xorg postinst warning: overwriting possibly-customized configuration file; backup in /etc/X11/xorg.conf.20060615213515
ubuntu@ubuntu:~$
```

Has anyone with the same problem I had or anyone who knows a lot about this particular issue know if I'm on the right track at all, and if so, what I should do from here?

---

### Post by bob_the_d on 2006-06-15
Oh yeah, and another thread which I'm on which another person had the same problem (but neither of us could figure out) is located here:

[http://ubuntuforums.org/showthread.php?t=186781](http://ubuntuforums.org/showthread.php?t=186781)

But I still haven't been able to figure it out, but there's some parallel information about my problem there (I pretty much covered it all here though) which may help explain what's wrong with my system, I don't know.

But nobody else helped him out either, and on a forum this big I find it hard to believe that neither of us could get anyone to help us.  If you have any tips on this, I'd highly appreciate it.

---

### Post by bob_the_d on 2006-06-16
Nobody?

---

### Post by teaker1s on 2006-06-16
hi have you tried the alternative  iso and selected text mode? if you do you can set up monitor during the install proccess

oh and from personal experience leave network cable unplugged on fresh install and the forum users are a friendly bunch,just a bit shy unless they know the answers:-)

---

### Post by bob_the_d on 2006-06-16
Ah, I never thought of the alternate ISO.  I thought that was just for OEM's and stuff so they can jam their logos in.  In any case, I'll burn it and give that a shot.

---

### Post by teaker1s on 2006-06-17
great, could you please tell me how you get on, I'm only a average user and occassionally I edit a couple of wilki pages-if this cures your problem then it would be worth including. I believe you will find 90% of it is the monitor not recognised make sure you know horisontal and vsync details and resolutions it is capable of when you install for xserver.xorg.

good luck

Daniel

---

### Post by bob_the_d on 2006-06-17
Nope.  It gives me the same problem with the text install.  Except that instead of giving me the error when it's installing, it gives me the error when booting.

---

### Post by bob_the_d on 2006-06-17
bump

---

### Post by raptros-v76 on 2006-06-17
```
 sudo aptitude update&&sudo aptitude install xserver-xorg
```

---

### Post by bob_the_d on 2006-06-17
Tried that, installed a bunch of things, but when I launched X again, it just spat out the same (EE) no devices detected message again, and the terminal said "Fatal server error: no screens found".

---

### Post by bob_the_d on 2006-06-18
Nobody?

---

### Post by teaker1s on 2006-06-18
i'm guess i that it's an xserver-xorg issue, now I'll be the first to say I 'm not sure how to set yours up.
 but i'm guessing if xserver-xorg is either configured with a basic driver and possibly there is a way to edit config file so it doesn't try and detect monitor at boot then that will solve your problem, did you allow xserver to detect settings or manually set them-try manually setting them.
If I remember rightly there is a basic versa driver which MAY WORK second issue is the ATI card which although they work are troublesome google your model card linux,
 have a look at 'common problems' in wilki and also search 'graphics' in wilki

---

### Post by bob_the_d on 2006-06-18
Yeah, someone suggested that.  I tried doing the xserver congif thing and set it to use the VESA drivers, but that was a no go as well.

---

### Post by teaker1s on 2006-06-18
[ati linux drivers]("http://www2.ati.com/drivers/linux/linux_8.23.7.html") I now know your issue is the fact that ubnutu possibly has no driver have a look at the links in this post
and [here to download]("https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=300")

Surprised the versa driver didn't work-would have thought you'd get something. still the issue will be requiring the specific driver I think.

**also found this in first link above**

X Fails to Load on Systems with Linux Kernel Version 2.6.x

This information applies to the following system configurations:

    * Linux kernel version 2.6.x
    * Any ATI Linux driver 

A blank screen may appear momentarily when X starts to load. The following error message (or similar) may appear on the text console or in /var/log/XFree86.0.log:
(EE) fglrx(0): [agp] unable to acquire AGP, error ""xf86_ENODEV""xf86_ENODEV""

This is not a problem with the display driver.

Version 2.6 kernels require a second kernel module in addition to agpgart, which should be named similar to the manufacturer of your motherboard AGP chipset. This error message should occur if the other agp module is not loaded.

This issue can be worked around as follows:

   1. First make sure that agpgart is loading properly.
   2. To find out which AGP controller your motherboard uses, issue the following command: lspci | grep AGP
   3. To find a list of AGP related kernel modules installed on your machine, issue the following command and look for a module (*.ko file) that suits your AGP Controller: ls /lib/modules/`uname -r`/kernel/drivers/char/agp
   4. Use the modprobe command (as root) to load the module. For example: On a motherboard using a VIA® AGP Controller, you would load the via-agp.ko using modprobe as follows (notice that the trailing.ko is omitted): modprobe via-agp

Check the modprobe manpage for more information on loading kernel modules.

   5. To verify that the AGP module is already loaded, run lsmod as root. With the X server running and the connection established, the usage count of this module must be greater than zero. 

If you cannot find a suitable agp module for your motherboard, then you may want to upgrade to the latest version of the Linux kernel, or check your motherboard manufacturer's website for more information.

---

### Post by bob_the_d on 2006-06-18
What about PCI-E cards?  My x800 GTO isn't on the AGP bus and I don't know if the procedure is the same.

---

### Post by bob_the_d on 2006-06-18
It's also why my error message doesn't raise any issues with the buses, but rather that it just can't seem to find the display at all.

---

### Post by teaker1s on 2006-06-18
what I'm trying to say is we have tried xserver-xorg without success and it's quite possible as your card is listed in first link and you have no display that you require ati driver. As I said I'm only a basic user, but I would say it's a good route to try.
As for PCI express etc don't worry about it, your looking for a driver with same chipset.

---

### Post by Poetjevel on 2006-06-19
I have the exact same problem as you, i have a ATI RADEON X700 pci-E card. I am totally new to both linux and ubuntu so i can't really figure it out either. :\

---

### Post by confused57 on 2006-06-19
These 2 links may help:

[http://www.ubuntuforums.org/showthread.php?t=192677&highlight=graphics+5500](http://www.ubuntuforums.org/showthread.php?t=192677&highlight=graphics+5500)
I know you have ATI, but may help with PCIe detection.

[http://www.ubuntuforums.org/showthread.php?t=190133](http://www.ubuntuforums.org/showthread.php?t=190133)
This link may help with ATI driver.

---

### Post by teaker1s on 2006-06-19
hi, guys this install business can be fun- 5 installs and 3 gave problems.
So I fully understand your fustration in these matters](*,) 

Now I've only ever done an install with an old ati card and that ran perfectly, I would suggest that you have a look at [this]("https://wiki.ubuntu.com/BinaryDriverHowto/ATI")

The other thing that occured to me I have a recollection of some problems with a large screen and ATI graphics card, it may be worth reconfiguring xserver  with an old screen and seeing if it will load gnome, if it will it will make ati driver install easier.

---

### Post by jondejong on 2006-06-20
I'm also getting this problem.  This is my first attempt at Linux... I've heard that the install was so easy, I thought it would be a great place to start my switch to Linux.  I have an old Dell, and am still using the integrated Intes 828461 GL/GE/PE/GV video card on PCI 0 Dev 2.  I'll probably spend the evening on this, so if I make progress, I'll let ya know.

Sorry I can't be more help right now!

---

### Post by jondejong on 2006-06-20
Ok.... if I set my driver to VESA, I still get the no screens found error.  However, inspection of the log file says:

(EE) VESA(0): No matching modes
(EE) Screens(s) found, but none have a usuable configuration

Why this is, I have no idea.

---

### Post by teaker1s on 2006-06-21
[QUOTE= I have an old Dell, and am still using the integrated Intes 828461 GL/GE/PE/GV video card on PCI 0 Dev 2.  I'll probably spend the evening on this, so if I make progress, I'll let ya know.[/QUOTE]

that would be an intel chip there is a 915resolution package in repositories that may work look at this page for more info on intel 915resolution

[URL="http://www.geocities.com/stomljen/"]http://www.geocities.com/stomljen/
[/URL]

---

### Post by bob_the_d on 2006-06-22
```

In a terminal type

sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```

That seemed to do the trick.

---

### Post by teaker1s on 2006-06-23
[QUOTE=bob_the_d]```

In a terminal type

sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```

That seemed to do the trick.[/QUOTE]


glad that's sorted, I'm surprised that with dapper we didn't have a basic ATI driver that worked!!

---

### Post by bob_the_d on 2006-07-02
Yeah, go figure.

Although unfortunately I reinstalled Windows shortly after figuring out why Ubuntu didn't work.

Why?

...the Prey demo was released.

As much as I hate Windows and really wanted my Linux setup working... I've been waiting for this game for over a decade.  Couldn't miss it.

But if anything, I hope this helps out some other person in the same situation.

---

