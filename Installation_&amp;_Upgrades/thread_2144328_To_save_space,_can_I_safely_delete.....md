---
title: "To save space, can I safely delete...."
date: 2013-05-11
forum: Installation &amp; Upgrades
---

### Post by dgermann on 2013-05-11
Friends--

To save space, can I safely delete these files from my boot directory?

Current OS on this server is "3.2.0-41-generic-pae #66-Ubuntu SMP Thu Apr 25 03:50:20 UTC 2013 i686 i686 i386 GNU/Linux".
```

doug@earth:/boot$ ls -alh
total 214M
drwxr-xr-x  4 root root 5.0K May 11 18:31 .
drwxr-xr-x 26 root root 4.0K May 11 18:31 ..
-rw-r--r--  1 root root 642K Nov 14 06:48 abi-2.6.32-45-generic-pae
-rw-r--r--  1 root root 783K Nov 15 07:22 abi-3.2.0-34-generic-pae
-rw-r--r--  1 root root 784K Dec  5 14:06 abi-3.2.0-35-generic-pae
-rw-r--r--  1 root root 784K Jan  8 18:03 abi-3.2.0-36-generic-pae
-rw-r--r--  1 root root 784K Jan 24 12:01 abi-3.2.0-37-generic-pae
-rw-r--r--  1 root root 784K Feb 19 08:44 abi-3.2.0-38-generic-pae
-rw-r--r--  1 root root 784K Feb 27 18:27 abi-3.2.0-39-generic-pae
-rw-r--r--  1 root root 786K Mar 25 18:55 abi-3.2.0-40-generic-pae
-rw-r--r--  1 root root 786K Apr 25 01:01 abi-3.2.0-41-generic-pae
-rw-r--r--  1 root root 114K Nov 14 06:48 config-2.6.32-45-generic-pae
-rw-r--r--  1 root root 144K Nov 15 07:22 config-3.2.0-34-generic-pae
-rw-r--r--  1 root root 144K Dec  5 14:06 config-3.2.0-35-generic-pae
-rw-r--r--  1 root root 144K Jan  8 18:03 config-3.2.0-36-generic-pae
-rw-r--r--  1 root root 144K Jan 24 12:01 config-3.2.0-37-generic-pae
-rw-r--r--  1 root root 144K Feb 19 08:44 config-3.2.0-38-generic-pae
-rw-r--r--  1 root root 144K Feb 27 18:27 config-3.2.0-39-generic-pae
-rw-r--r--  1 root root 145K Mar 25 18:55 config-3.2.0-40-generic-pae
-rw-r--r--  1 root root 145K Apr 25 01:01 config-3.2.0-41-generic-pae
drwxr-xr-x  3 root root 5.0K May 11 18:31 grub
-rw-r--r--  1 root root  13M Dec  8 15:28 initrd.img-2.6.32-45-generic-pae
-rw-r--r--  1 root root  17M Dec  8 15:52 initrd.img-3.2.0-34-generic-pae
-rw-r--r--  1 root root  17M Dec 18 23:14 initrd.img-3.2.0-35-generic-pae
-rw-r--r--  1 root root  17M Jan 29 20:55 initrd.img-3.2.0-36-generic-pae
-rw-r--r--  1 root root  17M Feb  2 19:26 initrd.img-3.2.0-37-generic-pae
-rw-r--r--  1 root root  17M Mar 14 19:56 initrd.img-3.2.0-38-generic-pae
-rw-r--r--  1 root root  17M Mar 20 18:20 initrd.img-3.2.0-39-generic-pae
-rw-r--r--  1 root root  17M Apr 10 10:53 initrd.img-3.2.0-40-generic-pae
-rw-r--r--  1 root root  17M May 11 18:31 initrd.img-3.2.0-41-generic-pae
drwxr-xr-x  2 root root  12K Oct 24  2010 lost+found
-rw-r--r--  1 root root 173K Nov 27  2011 memtest86+.bin
-rw-r--r--  1 root root 175K Nov 27  2011 memtest86+_multiboot.bin
-rw-r--r--  1 root root 1.7M Nov 14 06:48 System.map-2.6.32-45-generic-pae
-rw-------  1 root root 2.3M Nov 15 07:22 System.map-3.2.0-34-generic-pae
-rw-------  1 root root 2.3M Dec  5 14:06 System.map-3.2.0-35-generic-pae
-rw-------  1 root root 2.3M Jan  8 18:03 System.map-3.2.0-36-generic-pae
-rw-------  1 root root 2.3M Jan 24 12:01 System.map-3.2.0-37-generic-pae
-rw-------  1 root root 2.3M Feb 19 08:44 System.map-3.2.0-38-generic-pae
-rw-------  1 root root 2.3M Feb 27 18:27 System.map-3.2.0-39-generic-pae
-rw-------  1 root root 2.3M Mar 25 18:55 System.map-3.2.0-40-generic-pae
-rw-------  1 root root 2.3M Apr 25 01:01 System.map-3.2.0-41-generic-pae
-rw-r--r--  1 root root 1.2K Nov 14 06:48 vmcoreinfo-2.6.32-45-generic-pae
-rw-r--r--  1 root root 4.0M Nov 14 06:48 vmlinuz-2.6.32-45-generic-pae
-rw-------  1 root root 4.8M Nov 15 07:22 vmlinuz-3.2.0-34-generic-pae
-rw-------  1 root root 4.8M Dec  5 14:06 vmlinuz-3.2.0-35-generic-pae
-rw-------  1 root root 4.8M Jan  8 18:03 vmlinuz-3.2.0-36-generic-pae
-rw-------  1 root root 4.8M Jan 24 12:01 vmlinuz-3.2.0-37-generic-pae
-rw-------  1 root root 4.8M Feb 19 08:44 vmlinuz-3.2.0-38-generic-pae
-rw-------  1 root root 4.8M Feb 27 18:27 vmlinuz-3.2.0-39-generic-pae
-rw-------  1 root root 4.8M Mar 25 18:55 vmlinuz-3.2.0-40-generic-pae
-rw-------  1 root root 4.8M Apr 25 01:01 vmlinuz-3.2.0-41-generic-pae
```

I think I can remove all but the directories and the 3.2.41 files. Maybe for safety I'd keep the 3.2.40 files.

What's safe?

Also, what is the way to resize the partition using cli? This box does not have x installed.

Thanks!

---

### Post by lisati on 2013-05-11
A good place to start with freeing up space is with these:
```

sudo apt-get update
sudo apt-get clean
sudo apt-get autoremove

```

What the "update" does is to resynchronize the package list on your system, "clean" cleans out your system's cache of retrieved installation pacakages, and "autoremove" looks for packages that might not be needed any more.

---

### Post by ajgreeny on 2013-05-11
It is also much better to install **synaptic-package-manager** and use that to remove all kernels except the two most recent.

If you do a "name" search in synaptic for the kernel numbers that you dont want any more (eg **3.2.0-34**) you can remove the kernel and any headers still installed safely.

---

### Post by ibjsb4 on 2013-05-11
[Synaptic]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9") makes it easy to see whats up :)

[ATTACH=CONFIG]242485[/ATTACH]

```
sudo apt-get install synaptic
```

---

### Post by dgermann on 2013-05-11
lisati--

Thanks. Think I had forgotten to do the clean step, but had done autoremove. Still all those files are there, taking up a fair amount of space. Would it be safe to remove them? Not sure why clean would leave them behind....

ajgreeny and  ibjsb4 --

Thanks! This box does not have x. Would love to use synaptic, but will it run without x?

---

### Post by ibjsb4 on 2013-05-11
> Thanks! This box does not have x. Would love to use synaptic, but will it run without x? 						

Good question as I never ran a box without xorg.

Here's a link to kernel removal in terminal.

 [http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+old+kernels+in+terminal&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+old+kernels+in+terminal&sa=Search&cof=FORID:9)

---

### Post by matt_symes on 2013-05-11
Hi

To remove your old kernels

```
sudo apt-get purge vmlinuz-2.6.32-45-generic-pae vmlinuz-3.2.0-{34,35,36,37,38,39}-generic-pae
```

When you say resize partition, do you want to format this partition ? 

I.E Does this have to be non destructive to the data on the partition ? 

What partition is it ?

This is a bare metal install or in a VM ?

BTW: Before doing anything on your drives partitions, clone the drive.

EDIT:

Very nearly forgot to ask: What filing system type ?

Kind regards

---

### Post by dgermann on 2013-05-12
ibjsb4--

Thanks! Did not know googlubuntu existed. See below for what I have done, so far.


matt_symes--

Thanks!

Curious. I ran the command you suggest and got this:
```


doug@earth:~$ sudo apt-get purge vmlinuz-2.6.32-45-generic-pae vmlinuz-3.2.0-{34,35,36,37,38,39}-generic-pae
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package vmlinuz-2.6.32-45-generic-pae
E: Couldn't find any package by regex 'vmlinuz-2.6.32-45-generic-pae'
E: Unable to locate package vmlinuz-3.2.0-34-generic-pae
E: Couldn't find any package by regex 'vmlinuz-3.2.0-34-generic-pae'
E: Unable to locate package vmlinuz-3.2.0-35-generic-pae
E: Couldn't find any package by regex 'vmlinuz-3.2.0-35-generic-pae'
E: Unable to locate package vmlinuz-3.2.0-36-generic-pae
E: Couldn't find any package by regex 'vmlinuz-3.2.0-36-generic-pae'
E: Unable to locate package vmlinuz-3.2.0-37-generic-pae
E: Couldn't find any package by regex 'vmlinuz-3.2.0-37-generic-pae'
E: Unable to locate package vmlinuz-3.2.0-38-generic-pae
E: Couldn't find any package by regex 'vmlinuz-3.2.0-38-generic-pae'
E: Unable to locate package vmlinuz-3.2.0-39-generic-pae
E: Couldn't find any package by regex 'vmlinuz-3.2.0-39-generic-pae'
```

Then I tried this:
```
doug@earth:~$ sudo dpkg -P vmlinuz-2.6.32-45-generic-pae
dpkg: warning: there's no installed package matching vmlinuz-2.6.32-45-generic-pae
doug@earth:~$ 
```

But you see from my post #1 that this is still on the disk. How about purging the abi, config, initrd.img, and System.map files, or just deleting them? In the past I have done sudo apt-get purge on the linux-image and linux-headers files up through 2.6.32-42-generic, now that I go back and look at old notes.

OK, so I tried this:

```
doug@earth:~$ sudo apt-get purge linux-image-2.6.32-45-generic-pae
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-2.6.32-45-generic-pae*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 98.3 MB disk space will be freed.
Do you want to continue [Y/n]? 
```

And that seemed to go. A "dpkg-query -l | awk '/linux-image-*/ {print $2}'" showed a whole lot of old ones, so I ran ```
sudo apt-get purge linux-image-2.6.32-{24,25,26,27,28,29,30,31,32}-generic-pae
```
as well as {43,44} and sudo apt-get purge linux-image-3.2.0-{34,35,36,37,38,39}-generic-pae

And that seemed to clean things up nicely. This now shows the /boot partition at 25% use--some breathing room! Thanks for pointing me in the right direction. 

(Hopefully these notes will help someone, maybe even me, in the future!)


About resizing--it still seems to make some sense, but I do not have the sense of urgency after the above cleared some space.

This is the /boot partition (/dev/sda1), ext2, 227 Megs, 218 Megs used.

Yes, I want it to be non-destructive, just want to get it some breathing room.

This is a server which I upgraded to 12.04.2 from 10.04 a few months ago, and that was probably upgraded from 8.04. No it is not a virtual machine.

Do you have any favorite way to clone the drive? Have never done that before.

I presume cloning means the whole HDD, not just this partition. Only have one HDD on this box.

---

### Post by matt_symes on 2013-05-12
Hi

> **dgermann said:**
> OK, so I tried this:

```
doug@earth:~$ sudo apt-get purge linux-image-2.6.32-45-generic-pae
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-2.6.32-45-generic-pae*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 98.3 MB disk space will be freed.
Do you want to continue [Y/n]? 
```

And that seemed to go. A "dpkg-query -l | awk '/linux-image-*/ {print $2}'" showed a whole lot of old ones, so I ran ```
sudo apt-get purge linux-image-2.6.32-{24,25,26,27,28,29,30,31,32}-generic-pae
```
as well as {43,44} and sudo apt-get purge linux-image-3.2.0-{34,35,36,37,38,39}-generic-pae

And that seemed to clean things up nicely. This now shows the /boot partition at 25% use--some breathing room! Thanks for pointing me in the right direction. 

Yep. That's what i meant to type. I copied and pasted your kernel list from /boot to create the list to delete and forgot to change the name of the kernels to the packages themselves.

:redface: It was very late/early here. 

I'm glad you understood what i was trying to type. That's my standard way of removing kernels. It should have also removed the abi and map files for those kernels as well.

It will not have removed the kernel headers and you may want to remove them. That'll free up a whole load of inodes as well as some space.

> About resizing--it still seems to make some sense, but I do not have the sense of urgency after the above cleared some space.

This is the /boot partition (/dev/sda1), ext2, 227 Megs, 218 Megs used.

Yes, I want it to be non-destructive, just want to get it some breathing room.

This is a server which I upgraded to 12.04.2 from 10.04 a few months ago, and that was probably upgraded from 8.04. No it is not a virtual machine.

Do you have any favorite way to clone the drive? Have never done that before.

I presume cloning means the whole HDD, not just this partition. Only have one HDD on this box.

Yep. Clone the whole hard drive. Don't do anything until you have done that. I tend to clone using gddrescue but you can use clonezilla or other tools. Do this from a livecd/usb.

As this is your boot partition, i would use

```
gparted
```

from a livecd/usb. It's quick and easy that way.

If you were ever going to use the cli into an install you were booted into

```
sudo parted resize ...
```

and then...

```
sudo resize2fs ..
```

would be one way to go.

However, your boot partition will be mounted, unless run from a livecd/usb, and i'm not sure if Ubuntu's kernel will allow online resizing of partitions.

So use gparted from a live cd/usb.

Kind regard

---

### Post by dgermann on 2013-05-14
matt_symes--

Thanks. Will check it out. Have been busy and it may be a week or more till I can report back. Thanks, Matt!

---

