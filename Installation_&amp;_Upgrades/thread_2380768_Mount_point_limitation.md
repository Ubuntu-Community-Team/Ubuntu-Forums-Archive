---
title: "Mount point limitation"
date: 2017-12-21
forum: Installation &amp; Upgrades
---

### Post by Neville Hillyer on 2017-12-21
I am returning to Ubuntu after a considerable lapse. Initially I have set up a test facility on an old PC using Ubuntu 9.1 to start with. All went as expected with 4 primary partitions: Existing Windows, Ubuntu 9.1, Ubuntu 9.1, small Fat 32 volume. I have no swap partitions but will probably introduce swap files if necessary.

Eventually I will install the latest Ubuntu on partition 2 and experiment with various versions of Linux on partition 3. I wish to have all partitions/installations as independent as possible. Why will the installer not allow me to set both Ubuntu mount points to '/' ?

---

### Post by yancek on 2017-12-21
> Why will the installer not allow me to set both Ubuntu mount points to '/' ? 		

What are you doing?  You mention using Ubuntu 9.10 which has been out of support for over 7 years, why?  Are you asking this question in regard to installing 16.04?  Is your hardware new enough to be able to do that?  Each install of a Linux system will mount the system at /, the symbol for the root of the filesystem as long as they are on separate partitions.  It's difficult to understand from your post what you are actually trying to do.

---

### Post by Neville Hillyer on 2017-12-22
> What are you doing?
I am trying to set up a test computer for various types of Linux including old, new and very small versions such as used on old routers.

> You mention using Ubuntu 9.10 which has been out of support for over 7 years, why?
Most of this playing will be done at a location with limited hardware and very slow broadband but I had a Ubuntu 9.1 iso with me. For the time being I am not too concerned about the level of support or security.

> Are you asking this question in regard to installing 16.04?
No.

> Is your hardware new enough to be able to do that?
Not sure - it is an Optiplex GX620, 2.8 GHx, 2 GB ram, 80 GB hard disk

> Each install of a Linux system will mount the system at /, the symbol  for the root of the filesystem as long as they are on separate  partitions.
Why does the Ubuntu 9.1 installer refuse to accept a / mount point because it is being used on another partition?

> It's difficult to understand from your post what you are actually trying to do.
I hope I have indicated that this is an exercise to get me back into playing with Linux. I am a retired Electrical Engineer and I 'play' with a lot of old hardware. This is being written on one of the first Intel Macs but my normal computer is a Mac PPC G5.

---

### Post by Morbius1 on 2017-12-22
Mount points are not absolutes across both Linux installations. What is the "/" partition of one is just another partition to the other.

Here is how the "/" partition is defined for my Xubuntu 16.04 installation in it's fstab:
> [COLOR=#0000cd]**UUID=29abeef1-fc9f-4dec-8c20-94bf996823a5**[/COLOR] /               ext4    errors=remount-ro 0       1
And here is how that same partition is defined in my Xubuntu 14.04 installation in it's fstab:
> [COLOR=#0000cd]**UUID=29abeef1-fc9f-4dec-8c20-94bf996823a5**[/COLOR] /Xub1604        ext4    defaults        0       2
Same partition. Two different mount points depending on which operating system is running.

The "/" partition in my Xubuntu 14.04 install has it's own declaration in it's fstab.

---

### Post by Neville Hillyer on 2017-12-22
Given that I expect to have 2 totally independent OSs why should the second one refuse to install unless I select a mount point other than / ?

---

### Post by Morbius1 on 2017-12-22
> ... why should the second one refuse to install unless I select a mount point other than / ?

I do not understand your post. The second OS can only be installed to it's "/" mount point.

---

### Post by coffeecat on 2017-12-22
@Neville Hillyer, you appear to be entirely missing the point that both yancek and Morbius1 have made about the ‘/’ mountpoint. Let me try.

‘/’ refers to the root of your filesystem. It is entirely specific to the particular operating system and is defined in /etc/fstab – each separate operating system installation has its own /etc/fstab. You answer your own question in this:

[quote=”Neville Hillyer”]Why does the Ubuntu 9.1 installer refuse to accept a / mount point because it is being used on another partition?[/quote]

The answer is: because it is being used on another partition.

Let’s use a hypothetical case to illustrate this. I create partitions on a hard drive that include sda2 and sda3 – I intend to install Ubuntu on sda2 and Fedora on sda3. Ubuntu will mount sda2 on / , and Fedora will mount sda3 on its own /. To Ubuntu, sda3 is just another partition to Ubuntu - it is not / - so it cannot be mounted on /. Likewise Fedora with sda2.


By the way – it’s Ubuntu 9.10 not 9.1. This is not a nitpicking point - 9.10 is not a decimal number. The Ubuntu numbering scheme is year-of-release.month-of-release. Hence Ubuntu 9.10 was released in October 2009. That is, after the appearance of the dinosaurs, but somewhat before the appearance on the scene of Tyrannosaurus Rex.

---

### Post by Morbius1 on 2017-12-22
> **coffeecat said:**
> Let’s use a hypothetical case to illustrate this. I create partitions on a hard drive that include sda2 and sda3 – I intend to install Ubuntu on sda2 and Fedora on sda3. Ubuntu will mount sda2 on / , and Fedora will mount sda3 on its own /. To Ubuntu, sda3 is just another partition to Ubuntu - it is not / - so it cannot be mounted on /. Likewise Fedora with sda2.
Consider the following scenario:

I have a partition sda2 and when I installed Ubuntu1 I installed and mounted it to the / mount point. 

Now I go to install Ubuntu2 into sda3. In defining my partitions I set sda2 to "/" because that's where I put it when I installed Ubuntu1. 

I have to install Ubuntu2 to "/" but I can't do it to sda3 since I already told the installer to assign "/" to sda2.

It's the only scenario that fits the description of the problem.

The answer: When you install Ubuntu2 tell the installer that sda2 has the mount point: /Ubuntu1. Now you can tell it to use / for sda3.

---

### Post by Neville Hillyer on 2017-12-22
> **Morbius1 said:**
> Consider the following scenario:

I have a partition sda2 and when I installed Ubuntu1 I installed and mounted it to the / mount point. 

Now I go to install Ubuntu2 into sda3. In defining my partitions I set sda2 to "/" because that's where I put it when I installed Ubuntu1. 

I have to install Ubuntu2 to "/" but I can't do it to sda3 since I already told the installer to assign "/" to sda2.

It's the only scenario that fits the description of the problem.

The answer: When you install Ubuntu2 tell the installer that sda2 has the mount point: /Ubuntu1. Now you can tell it to use / for sda3.

For both installs I was booted into an iso image on a usb flash stick. From memory it did not offer me the option of changing the earlier mount point.

In OS X default mount points are always / but each OS has a /Volumes directory which has a list of aliases to other volumes, some of which may contain OSs. Hence I can install OSs on different volumes without bothering with mount points. Each OS has a / mount point relative to itself, ie the root of its volume. In what way does Linux differ from this?

---

### Post by Morbius1 on 2017-12-22
> For both installs I was booted into an iso image on a usb flash stick.  From memory it did not offer me the option of changing the earlier mount  point.
You are not changing an earlier mount point. 
> In OS X default mount points are always / but each OS has a /Volumes  directory which has a list of aliases to other volumes, some of which  may contain OSs. Hence I can install OSs on different volumes without  bothering with mount points. Each OS has a / mount point relative to  itself, ie the root of its volume. In what way does Linux differ from  this?
It works the same way in Linux. 

In my example the file that defines the mount point for Ubuntu1:

[1] Is in /etc/fstab when I am in Ubuntu1

[2] And in /Ubuntu1/etc/fstab when I am in Ubuntu2

In both fstab files the Ubuntu1 OS is mounted to / - it's own /

I'm running out of examples. There is a real probability that as yet I still don't understand the nature of the problem

---

### Post by Neville Hillyer on 2017-12-22
This reminds me of one of Apple's most serious security mistakes. In the days when they sold quite expensive OS X server harware and software one of their software updates confused FTP root with OS root such that if FTP was active it published the whole disk to the world. It took me a while to convince them what they had done.

Is the communication issue here confusion between relative and some form of absolute / ?

When I tell the installer that I want the new mount point to be / I assume this is relative to the partition it is being installed on. I can see no conflict in both OSs having the same mount point relative to its own partition.

---

### Post by Morbius1 on 2017-12-22
For a given Linux OS the starting point is what partition that OS is installed into. 
It is given a mount point of /.
All the other partitions are mounted off /.
If I have multiple Linux installs each one has it's own / pointing to it's own partition and all the other partitions are mounted off their respective /..


You can't have two partitions - in the same operating system install - with the same mount point. In this case it would result in a path of //.

Here's an idea. When you install Ubuntu2 don't specify anything for Ubuntu1. Then the issue won't come up. You can still mount it after the install.

---

### Post by Neville Hillyer on 2017-12-22
Let me try and put it another way.

Assume I have two computers and I install linux on each.

What would happen if I put both disks into one computer?

---

### Post by Neville Hillyer on 2017-12-22
From the definitions I had read I thought the mount point was the location of the OS but perhaps it should be the directory in which locations of OSs (or volumes) are stored.

If this is so perhaps I could set all mount points (including the first) to eg /Volumes - If my assumption is correct this should give the same structure which OS X installs automatically every time.

---

### Post by QIII on 2017-12-22
What will happen?

The boot process will pass from the motherboard to whichever disk you have set as the first in the boot order.  The bootloader will look for / and pass control to it.

If you want to boot the other disk, you can change the boot order in your BIOS if you want.

But the typical way is to update GRUB on the primary boot disk.  It will search for other devices with a bootable flag and add them to a menu.  When you boot, you will get the GRUB menu.  If you choose the OS on the primary device, control will be passed to / there.  If you choose the OS on the other disk, control will be passed to / on the other disk.

They are not the same / partition.  Each OS, on its separate physical device, has its own.

Similarly, if you dual boot on the same disk, you effectively create two different "devices", one for each OS.  Each will have its own /.  Not the same one.  There will be two separate ones.

Let me try to put this in a different way:  You can't park two cars in the same parking space.

---

### Post by Neville Hillyer on 2017-12-22
> **QIII said:**
> What will happen?

The boot process will pass from the motherboard to whichever disk you have set as the first in the boot order.  The bootloader will look for / and pass control to it.

If you want to boot the other disk, you can change the boot order in your BIOS if you want.

But the typical way is to update GRUB on the primary boot disk.  It will search for other devices with a bootable flag and add them to a menu.  When you boot, you will get the GRUB menu.  If you choose the OS on the primary device, control will be passed to / there.  If you choose the OS on the other disk, control will be passed to / on the other disk.

They are not the same / partition.  Each OS has its own.

Similarly, if you dual boot on the same disk, you create two different "devices", one for each OS.  Each will have its own /.  Not the same one.  There will be two separate ones.

If I understand you correctly your last sentence is what my installer stops me doing - it will not let me set both mount points to /.

---

### Post by coffeecat on 2017-12-22
@Neville Hillyer, what everyone is trying to tell you is really quite straightforward. A Linux operating system's root partition is mounted to / . That's it. 

There can only be one / mountpoint for a particular operating system. If there are other operating systems installed to the same machine, whether on other partitions on the same physical drive, or other partitions on other physical drives, they will simply be other partitions to that operating system. You can define a mountpoint if you wish to mount one of those other partitions, but the mountpoint cannot be / . Of course it can't.

---

### Post by QIII on 2017-12-22
Not quite.  It will not let you set the mount point to the same /.  

Go back to your example, where you installed Linux on two different devices (assuming a typical installation):  

Physical device A has three partitions:  /, /home and swap.
Physical device B has three partitions:  /, /home and swap.

If you put them in the same computer, attached to the same motherboard and set Physical device A as the first in the boot order, after the BIOS is done with POST, it will pass control to A if it is bootable.  GRUB will pass control to / on A.

If you set Physical device B as the first in the boot order, after the BIOS is done with POST, it will pass control to B if it is bootable.  GRUB will pass control to / on B.

If you update GRUB on your primary boot device, it will look for bootable mount points on the other device and add them to the list.  GRUB will facilitate passing control to one or the other OS's /.  But those will NOT be the same /.

You are getting wrapped around the axle about the name "/".  They are not the same location.

Bill Smith who lives in Chicago is not the same Bill Smith who lives in Toledo.

---

### Post by Neville Hillyer on 2017-12-22
> **coffeecat said:**
> @Neville Hillyer, what everyone is trying to tell you is really quite straightforward. A Linux operating system's root partition is mounted to / . That's it. 

There can only be one / mountpoint for a particular operating system. If there are other operating systems installed to the same machine, whether on other partitions on the same physical drive, or other partitions on other physical drives, they will simply be other partitions to that operating system. You can define a mountpoint if you wish to mount one of those other partitions, but the mountpoint cannot be / . Of course it can't.

What is a "root partition" is one OS and its partition different to the others?

With OS X I can clone one partition to another and instantly have a dual boot system with one OS a precise mirror of the other. From what I have been told this will not work with Linux but I still don't understand why.

---

### Post by QIII on 2017-12-22
If you install linux without a separate /home (the default partition scheme in most Linux installations) so that /home is contained within /, then you clone / to a different place, you will also have two separate OSes instantly.  They will each have their own / -- in two different places.  (Or, as in Morbius1's case, /foo)

I've had quite enough of this obtuse resistance to a simple concept, so others will have to continue.

---

### Post by Neville Hillyer on 2017-12-22
> **QIII said:**
> If you install linux without a separate /home (the default partition scheme in most Linux installations) so that /home is contained within /, then you clone / to a different place, you will also have two separate OSes instantly.  They will each have their own / -- in two different places.  (Or, as in Morbius1's case, /foo).

With OS X I can use an installer to install indentical OSs in 2 separate volumes. Why is this not possible with Linux?

---

### Post by coffeecat on 2017-12-22
You can indeed install identical Linux OSs to two different partitions with most distros, but I can't see the point. Different desktops, yes. Different distros, yes. But, identical? 

Anyway, this is all very well, but your original question has been answered repeatedly to the point of tedium, so I'm closing this thread now. Please do not stretch the patience of those trying to help you again.

---

