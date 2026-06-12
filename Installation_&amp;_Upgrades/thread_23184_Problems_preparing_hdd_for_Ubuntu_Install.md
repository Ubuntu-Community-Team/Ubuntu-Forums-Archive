---
title: "Problems preparing hdd for Ubuntu Install"
date: 2005-03-31
forum: Installation &amp; Upgrades
---

### Post by abyss on 2005-03-31
Hi everyone.

I'm hoping someone can help a novice with a problem.

I've been doing extensive reading since I decided to explore the possibility of using Linux OS instead of windows. The good news is I haven't been put off by the amount of learning and work involved.

The Problem:

I have Windows installed already on a 20Gb (more like 17.5Gb) hard drive - about 9Gb is in use, 8.5Gb free. It has a single partition which I want to resize so that I can create a couple new smaller partions to install Ubuntu. I have downloaded the SystemRescueCD image and burned it to CD and it works just fine, but when I run qtparted the programme limits me to resizing the 17.5Gb partition to only 16Gb, which would not leave me with enough to install Ubuntu.

I tried defragging the drive several times incase it was because there was still data at the end portion of the disk causing the programme to restrict the resizing (if you understand?) but no matter how many defrags I do (or which programme I use) I still can't get qtpartedto allow me to reduce the size of the partion further. Is it a programme limitation?

I also have a second hdd (as in rdisk1) with loads of space (30Gb free) on which I could create several partitions if I wanted to. But I don't know if the Ubuntu installer would just install to the first/main drive (the 17.5Gb one) and erase everything that's on there. 

Any help would be much appreciated, or a nudge in the direction of a link/post that already answers my questions.

Thanks.

---

### Post by malegria on 2005-03-31
I'm not sure about qtparted, but if you keep coming into that problem then just go for installing Ubuntu on the 2nd hard drive. But when you install the 2nd hard drive go for the *MANUAL* partitioning. I've heard that the automatic partitioning *WILL* erase everything on a harddrive and install Ubuntu. I believe a screen will show up showing you the partitions on both harddrives: Harddrive #1 labeled as /dev/hda and harddrive #2 labeled as /dev/hdb (notice the difference in the letters). 

And so make sure to install Ubuntu on the 2nd hard drive by creating the proper partitions. Hope this helps.

---

### Post by arctic on 2005-03-31
in order to prepare hdd1 for linux, qt parted is only the second step. the best tool is partition magic. it will move all hidden files, so you will have enough space for a linux-partition, which can be created with pmagic itself in ext2 or ext3 mode.

but me, too, i recommend using the second harddisk (hdb) and do a manual partitioning, simply because you can add some extra speed out of your box then. ;)

the best layout you could create is imho:
at the beginning of your harddisk, create a swap partition that is ~double your ram size. so, if you have 512 mb ram, create 1 gb of swap. 
after that one, create one ext3 partition , labeled / (=root filesystem). make it approximately 4-5gb and you have lots of room for your apps.
make the rest your /home partition (make it ext3 or reiserfs, whatever you want). this is where your personal data will be stored. music, documents, pictures,...

let the bootloader install itself on your primary harddisk (hda1 / master). it will set up a dualboot system, so you can boot into windows whenever you want.
if you have more questions, just ask. :)

---

### Post by abyss on 2005-03-31
Thanks guys for your help.

Arctic: I wish I had seen your post sooner. Because I let the installer automatically partition the free space on my hdd I ended up with:

swap file 328.6Mb
and 
 \ 6.8Gb

... thats it. Installation was EXTREMELY slow (try 3-4 hours lol, or is that normal?) but I didn't wanna interrupt the installation in the middle - a bit paranoid. Plus the file format (I've just learned) was ext2fs, which I didn't want. I'm sure I would have got better performance following the scheme you posted.

Oh well. I might have to do it over again to get it how I want, as smooth and efficient as possible! Unless anyone has any better ideas?

Thanks for the help. Any additional tips are welcome :mrgreen:

---

### Post by Born2love on 2005-04-01
[QUOTE=arctic]in order to prepare hdd1 for linux, qt parted is only the second step. the best tool is partition magic. it will move all hidden files, so you will have enough space for a linux-partition, which can be created with pmagic itself in ext2 or ext3 mode.

but me, too, i recommend using the second harddisk (hdb) and do a manual partitioning, simply because you can add some extra speed out of your box then. ;)

the best layout you could create is imho:
at the beginning of your harddisk, create a swap partition that is ~double your ram size. so, if you have 512 mb ram, create 1 gb of swap. 
after that one, create one ext3 partition , labeled / (=root filesystem). make it approximately 4-5gb and you have lots of room for your apps.
make the rest your /home partition (make it ext3 or reiserfs, whatever you want). this is where your personal data will be stored. music, documents, pictures,...

let the bootloader install itself on your primary harddisk (hda1 / master). it will set up a dualboot system, so you can boot into windows whenever you want.
if you have more questions, just ask. :)[/QUOTE]


I got same problem. :)
 :D  Thank  you for your help!!
That will be very useful for me.

---

### Post by abyss on 2005-04-01
Hello again,

I've got another problem, but no doubt I'm gonna run into many while trying to get accustomed to linux.

Ubuntu installed successfully, albeit very, very slowly (and it takes 10 minutes to boot to a useable desktop from power on - could I get some feedback as to whether a reinstallation could improve this?)

The main problem right now is that when I shutdown, it exits the desktop, and starts terminating all the services and whatnot that are running, but then starts to displays this error message repeatedly:

APIC error on CPU0: 02(02)

It gets stuck on this and just keeps filling up the screen with the error.

Could someone tell me how to fix this?

Thanks.

---

### Post by arctic on 2005-04-01
>  ... thats it. Installation was EXTREMELY slow (try 3-4 hours lol, or is that normal?)
well, ubuntu is basically debian, thus it is not the fastest to install but you will get a distro that is a lot more stable than rpm based distros imho. that fact is worth the extra time taken. and it is still a lot faster than slackware or gentoo installs. ;)

---

### Post by arctic on 2005-04-01
[QUOTE=abyss]Hello again,

I've got another problem, but no doubt I'm gonna run into many while trying to get accustomed to linux.

Ubuntu installed successfully, albeit very, very slowly (and it takes 10 minutes to boot to a useable desktop from power on - could I get some feedback as to whether a reinstallation could improve this?)

The main problem right now is that when I shutdown, it exits the desktop, and starts terminating all the services and whatnot that are running, but then starts to displays this error message repeatedly:

APIC error on CPU0: 02(02)

It gets stuck on this and just keeps filling up the screen with the error.

Could someone tell me how to fix this?

Thanks.[/QUOTE]
 please post some information on your hardware / type of computer you are using. is it a laptop?

---

### Post by arrizaba on 2005-04-01
Hi,

You should have a look at the thread:
[COLOR=DarkOrange]
[http://ubuntuforums.org/archive/index.php/t-16766.html](http://ubuntuforums.org/archive/index.php/t-16766.html)[/COLOR]

It's a bit weird that your computer takes so much time to get the desktop. Does it get stuck on specific places (such as "Configuring Network Interfaces...")? 
Some is these issues are addressed in the Ubuntuguide ([COLOR=Blue]http://www.ubuntuguide.org/[/COLOR]).

---

### Post by arctic on 2005-04-01
okay, here is some basic stuff i found about your problem on a kernel-mailing list:
> 02 = Receive checksum error. Your APIC bus is corrupting messages 
 sent to the CPU. This is a serious hardware problem, indicating 
that the board hasn't been properly designed for APIC usage. 


 First try to avoid using the APIC bus: disable SMP and UP_IOAPIC. 
If your BIOS allows it, set interrupt mode to PIC not APIC. 
If you still get these errors (but you shouldn't unless the HW 
is _really_ broken), also disable UP_APIC. 


 Or replace the board with something better.
but before you head to this stuff, if you get to the boot/grub/lilo menu, hit <ESC>, select the kernel you want, press "e" for editing the kernel paramenters and try to load the kernel with the following parameters:

linux noapic nolapic

and hit <Enter>
good luck. :)

---

### Post by abyss on 2005-04-01
All the help is much appreciated.

System Specs (Desktop PC):

ASRock K7VT2 Motherboard
AMD Athlon 2400 Processor
384Mb RAM


Is that enough info?

Arctic: 

I'm not sure exactly what the line should look like once I've edited the kernel parameters in the GRUB menu. There are some parameters there already and I don't know if I just add the new parameters (with no colons, semi-colons or commas - to separate from other parameters) or what?

You're talking to a complete Linux virgin here :)
Shoot, I don't even know how to find the equivalent the Windows command console once I'm in Ubuntu...You're talking to a clean slate.

(Scratch that. I just realised its the Terminal in system tools. You learn something new everyday.)

AND...

Any suggestions on the performance of Ubuntu? It takes like 10 minutes to reach a usable desktop, and often programmes take like a minute (or even 2) to open, but not always.

Anxiously awaiting some (more) advice. Thanks  :)

---

