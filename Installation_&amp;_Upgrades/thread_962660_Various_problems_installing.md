---
title: "Various problems installing"
date: 2008-10-29
forum: Installation &amp; Upgrades
---

### Post by Matpen on 2008-10-29
Hi everybody, 

I'm a GNU/Linux newbie and I'm having some problems intalling a distro on my machine. 

I'll try ti briefly explain what happens: 
1) I downloaded and burned many different distros and checked the md5: 
- Fedora 9 
- Ubuntu 8.4.1 
- Zenwalk 5.2 
- Puppy Linux 4.1 
- Deli Linux 0.8.0 
- Slax 6.0.7 

2) Where available, I tested the LiveCD on a AsusTek Laptop with Pentium 4 2.66GHz 480MB RAM, which works fine 

3) The goal would be to install on at least one of following older machines (further hardware infos available if needed): 
a) Pentium II 300 Mhz 128MB RAM 10GB HDD Award BIOS 1997 
b) Celeron 1100 Mhz 128MB RAM 8,4GB HDD Award BIOS 2001 

4) I'm experiencing all the possible problems: 
- Fedora, Ubuntu: Install freezes at different stages, sometimes sooner sometimes later, sometimes after "checking hlt instruction..." (doesnt display OK yet), sometimes whith a "kernel panic" and a stack trace 
- Zenwalk, Deli: almost always during install a "kernel panic" and a stack trace 
- Puppy and Slax: Could manage to use the LiveCD and get to the DE, with Puppy even to use some Apps, but after a short while everything freezes, or I get a "panic" 

5) I tryed following solutions 
- Formatting and partitioning the HDD in different ways with different fs (xfs, ext2, ext3, even FAT) and trying to install WIN95 (which works) or set up a dedicated HDD 
- Using text mode, which works (just with LiveCDs 'cause installs never get to end), but often I dont even get through kernel loading 
- Passing all possible boot parameters: nohlt, noapic, apci=off among them 
- Suggested by some forums, I opened both machines and switched RAM between them and between slots, even tryed to use them together to 256MB (WIN95 works - and the Celeron used to work even with WIN XP and 128MB before). Also tryed to use different CD drives, or one HDD in the other machine, or used both machines with just CD, or just CD and HDD 
- Noticed one lucky time where I got through with Puppy, that the free mem indicator displayed "836MB free", so thought to try with boot option mem=128M, but this stops the loading even sooner 
- Tryed BIOS with different options (example HDD with "LDA" or "Normal") 
- Tryed to boot from USB, but this seems not to be possible on both machines 

Being a Linux newbie, I like the idea of a free OS, but I have no idea anymore on how this could happen with 2 different machines and so many different distros, and how to solve the problem. 

Any help would be appreciated. Thanks in advance! 
Matteo

---

### Post by Matpen on 2008-10-29
there are news: somehow (dont really know how, i didnt change anything especial) i got through the install with zenwalk. however, it stopped again during booting, showing that the problem was not a bad cd.

what I could read on screen is:

md: autorun done
RAMDISK: couldnt find valid RAM disk image starting at 0
UDF-FS: No VRS found
XFS mounting filesystem sda1
VFS: Mounted root (xfs filesystem) readonly
Freeing unused kernel memory: 252k freed
INIT: version 2.86 Booting

then it freezed. of course, being a newbie, this doesnt mean anything to me. So I just tryed to add RAM from the other machine, coming to 256MB. This time I could login, and starting using Zenwalk. But...everything I start stops shortly later and the app's window suddently closes. I tryed many times, my guess is that there are problems in the kernel's memory management system.

I wrote down some errors I get during installation with other distros, maybe it can help finding out what it is about. Mainly 'cause it could serve as a bug fix. I believe it could happen to other newbies, and anybody else would have given up long time ago saying that "Linux is just for experts, pity".

Zenwalk
--------
RAMDISK: Compressed image found at block 0
RAMDISK: Incomplete write (-28 != 32768) 4194394
invalid compressed format (err=2)
VFS: Cannot open root device "null" or unknown-block(0,0)
Please append a correct "root=" boot option; here are the available partitions
0100       4096 ram0 (driver=?)
0800 10005408 sda driver: sd
 0801  8787523 sda1
 0802  1212907 sda2
0b00 1048575 sr0 driver: sr
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

Puppy
------
boot:
Loading vmlinuz..................
Loading initrd.gz......................ready

Unlzmaing Linux..........done
Booting the kernel
Kernel panic - not syncing: junk in compressed archive

(note that I get this with 2 different install-CDs)

Fedora
--------
Modules linked in: nls_ISO8859_1 fan thermal button processori2c_i801 uhci_hcd
Pid: 0, comm: swapper Not tainted (2, 6, 25, 4 #1)
---here a stack trace with many numbers---
kernel panic - not syncing: Fatal exception in interrupt

Slax
-----
---here a stack trace with many numbers---
kernel panic - not syncing: Attempted to kill init!

Zenwalk (other try)
-------------------
---here a stack trace with a list of drivers---
kernel panic - not syncing: Unable to mount root fs on unknown-block(253,0)

Zenwalk (again - and others too)
--------------------------------
Checking "hlt" instruction...

Sorry for the long post. I hope it can be useful for the community somehow. I even took pix if somebody requests them...

thanx for any help!!

---

### Post by RJARRRPCGP on 2008-10-30
Are you overclocking your processor or RAM? 

I dunno about the symptoms, but I wonder if this could be an unstable system?

---

### Post by Matpen on 2008-10-31
unfortunately no...i loaded bios safe presets, and manually went through all of them...

thanx anyway for the idea!

---

### Post by Dumdideldum on 2008-10-31
try a memtest86 run - should be available through different distributions - not sure, if Ubuntu offers it through livecd or alternate either - but this one does it for instance:
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

Sounds like a damaged RAM to me.

---

### Post by xphlo on 2008-10-31
Move your 10Gb hard drive and the extra 128Mb ram to the Celeron, your chances may be better (rather than on the pentium).

Most of the problems you are having are related to RAM. You just dont have much to work with. Avoid Live-CDs. Your text-mode installs should be (more) successful. Try the Ubuntu 8.04 Alternate CD (Ill get back to this) 

Also, once installed, you can eat up 256Mb Ram (let alone 128 ) very quickly in a graphical environment. If you want graphical, you shouldnt be using KDE or Gnome. Look into using Fluxbox,Openbox, XFCE or similar.

I know you are new to linux, and this may seem daunting, but your choice of hardware is not making this all that easy. To get things working on such limited hardware, you almost need the command line at some point. Your average desktop distro needs more RAM to run smoothly. You are looking at limited desktop distro&#347; or command line systems.

I think you need an installer that doesnt make you do a full install. You need to be picking what you want installed (which is not much), and build from the ground up. Your installers are doing to much, and that is why they freeze.

If you have access to the internet other than your would-be linux boxes, there are people who can help you (myself included) walk through some command line help, and that might be just enough to get you to a light-weight desktop environment.

My suggestion would be Ubuntu 8.04 Alternate CD, and select ¨Command Line Install¨ as the mode. This will only give you a terminal once it has finished installing. But from the terminal, you can then add fundamental packages to get you up and running.
Assuming your internet works out of the box, you can enter this into a fresh install,
```

sudo apt-get install xorg openbox obconf dillo

##When finished successfully, then type...

startx

```
This is only meant to be an example of keeping it simple.

Gotta go now, if no-else posts within the next few hours, Ill get back to ya.

Good Luck

---

### Post by Matpen on 2008-11-05
It works! it does really!!

First of all, a big thank you to everybody who posted to me and tryed to help. I must honestly say, I thought many time to give up, but the all the ideas provided pushed me every time to try again. Its a sign that the "community" really exists and works.

And now, back to the problem. Or actually the problems.

Following the your suggestions, I tryed a more "scientific" approach: Meaning that I quit to randomly try combinations of distros and hardware, and start focusing on one thing and try to see what exactly is wrong with it.

1)First I tested ram. Ubuntu comes with memtest, so I tryed every DIMM singularly, in combination with others, and also every possible combination of slots. All fine.
2) Then, I worked without HDD. The livecd works perfectly on the Pentium. However, I found out the problem #1 on the celeron. Continuos errors, no matters what cd drive, ide cable or ide slot I use. I even tryed to use a different power supplyer. I guess something is wrong in the motherboard itself. I recall having crashes with win xp also.
3) So, adding HDD to the pentium. As soon as I do, I start sweating. Even without trying to install. I guess the livecd still uses it, if found, for example for swapping, and finds bad sectors there (see vootie's post)
4) Indeed, by changing the partition layout to WIN95 FAT32, formatting with a WIN diskette, then back to ext3+swap, formatting again, and setting the access mode to "normal" as opposite to "LDA" in the bios, I could perform a smooth full install.

I then started enjoying the beauty of linux. it really works great, fast and stable. I even installed python, a couple of pets and now I'm currently fighting with the blender install, but this is another story (or another thread)!

So then! It was hard to find out, because there were more issues crossing each other, but maybe this thread will help somebody else. Again, thanx everyone for posting!!

---

