---
title: "Installed on new partition...won't boot"
date: 2008-06-22
forum: Installation &amp; Upgrades
---

### Post by patrickrclark on 2008-06-22
Hi. I am new to Ubuntu and Linux as a whole so bear with me. So a little while ago I decided I'd like to switch over from Windows XP to either Ubuntu of Fedora. Today I finally backed up all of my important files onto my friend's large external hard drive and began the install process. I popped my Ubuntu CD into the drive and booted to it. I didn't bother booting live. Not knowing exactly what I was doing or really what I wanted to do, when I got to the partition screen went into manual mode, I deleted my old xp partitions and created a 4gb swap and 316gb ext3 partition mounted to "/". So things installed without error and I excitedly rebooted in hopes to boot my new OS. Just to be safe I went into my boot priority and made sure the hard drive was first (even though my cd was out of the drive). Then to boot and voila...the drive is practically ignored. The system tries to boot from my intel network card (lowest boot priority). So I do a live boot and try to install again. When it gets to the partition manager I select the option for guided while using the entire capacity of the drive. Again no errors during the install and upon trying to boot the same thing happens again. Grasping for straws I live boot yet again and install GRUB (according to [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")) and tried booting again, but to no avail. I feel like there is something simple I am missing but I am at a loss for what to do. I'm not sure if this is a hardware related problem or a problem related to my installation. Anyone see a similar problem or know why my computer would do this to me? For the record, my hard drive IS recognized by my BIOS.

---

### Post by damphoud on 2008-06-22
Can you give specs on the system.

---

### Post by Qrikko on 2008-06-22
Does it load in grub (i.e. after your bios pop some splash you get a message that grub is loading)?

if so, can you choose a kernal (or even does grub get past this) what happen after?

Does you get to the Ubuntu loading screen?

can you CTRL+ALT+F1 (should get a list of how modules are being loaded)

hmm.. I think it's all initial questions I can think about..

but basically what happen after you try to reboot, does it just stop at Grub/before grub/at the loading screen or something? :)


Hmm I re read the post.. I think I understand better and it render my questions pretty useless :)

---

### Post by damphoud on 2008-06-22
> **Qrikko said:**
> Does it load in grub (i.e. after your bios pop some splash you get a message that grub is loading)?

if so, can you choose a kernal (or even does grub get past this) what happen after?

Does you get to the Ubuntu loading screen?

can you CTRL+ALT+F1 (should get a list of how modules are being loaded)

hmm.. I think it's all initial questions I can think about..

but basically what happen after you try to reboot, does it just stop at Grub/before grub/at the loading screen or something? :)

I guess it doesn't find any boot image on the hd (what it sounds like).


edit: oops didn't see your edit lol... too quick to reply.

---

### Post by patrickrclark on 2008-06-22
> **damphoud said:**
> Can you give specs on the system.

The ubuntu drive is a 320GB Western Digital SATA 1 drive. I run an AMD Athlon 64 3500+ (single core) 939 on an ASUS A8R-MVP Crossfire Motherboard with an ATI Radeon x1800XT. 1 GB of Corsair RAM. A Creative X-Fi XtremeMusic if that counts for anything.

> **Qrikko said:**
> Does it load in grub (i.e. after your bios pop some splash you get a message that grub is loading)?

if so, can you choose a kernal (or even does grub get past this) what happen after?

Does you get to the Ubuntu loading screen?

can you CTRL+ALT+F1 (should get a list of how modules are being loaded)

hmm.. I think it's all initial questions I can think about..

but basically what happen after you try to reboot, does it just stop at Grub/before grub/at the loading screen or something? :)


Hmm I re read the post.. I think I understand better and it render my questions pretty useless :)

no splash, nothing. after BIOS it just attempts to boot from DHCP on my LAN card.

---

### Post by Qrikko on 2008-06-22
yeah, hmm.. annoying :P

I guess that your system find your harddrive, try to boot, don't find the installed os and go on to next thing in the boot priority list.. 

so for some reason there is no record in MBR from grub can it be?

sorry I don't have a solution just know just starting to brainstorm a bit :P maybe if we can think about some possible problems we could find solutions to them..

but it feel like grub could well be the problem..

you can boot from the live cd and mount the partition (the one you installed on /)

if you know where it is (if you have a sata disk I am betting my money on /dev/sda1 else /dev/hda1)

to see if you have the file system on it..

all I can think about right now.. if that is the case then it seem likely that it's something making grub not load

---

### Post by patrickrclark on 2008-06-22
> **Qrikko said:**
> yeah, hmm.. annoying :P

I guess that your system find your harddrive, try to boot, don't find the installed os and go on to next thing in the boot priority list.. 

so for some reason there is no record in MBR from grub can it be?

sorry I don't have a solution just know just starting to brainstorm a bit :P maybe if we can think about some possible problems we could find solutions to them..

but it feel like grub could well be the problem..

you can boot from the live cd and mount the partition (the one you installed on /)

if you know where it is (if you have a sata disk I am betting my money on /dev/sda1 else /dev/hda1)

to see if you have the file system on it..

all I can think about right now.. if that is the case then it seem likely that it's something making grub not loadI don't see sda1 or hda1 in /dev/. the only directories I see are fd, pts, and shm. does that mean there is something missing?

---

### Post by damphoud on 2008-06-22
hes asking when your running live cd, are you able to mount your sata drive to see the files. and it should be under /media/disk/

---

### Post by patrickrclark on 2008-06-22
> **damphoud said:**
> hes asking when your running live cd, are you able to mount your sata drive to see the files.

yes, I can see the files on my sata drive.

---

### Post by Qrikko on 2008-06-22
Ah, then it's good (if you read the post before I edited)

so we are almost sure it is grub related then?

---

### Post by patrickrclark on 2008-06-22
> **Qrikko said:**
> Ah, then it's good (if you read the post before I edited)

so we are almost sure it is grub related then?that's what it sounds like. is there a way to install grub while on the cd boot screen (not in the live boot)?

---

### Post by damphoud on 2008-06-22
This may seem trivial now, but have you tried booting specifically to your sata drive from boot menu?

---

### Post by patrickrclark on 2008-06-22
> **damphoud said:**
> This may seem trivial now, but have you tried booting specifically to your sata drive from boot menu?

I just tried this and got nothing but a blinking cursor at the bottom left corner of the screen...for about 15 minutes, after which I just shut the computer off.

---

### Post by damphoud on 2008-06-22
Maybe try a WD support cd, and run some kind of drive consistency test.

---

### Post by patrickrclark on 2008-06-22
Well, I reinstalled Ubuntu, this time going into advanced and setting the boot loader to install on sda1. then when it booted I saw the grub screen and got Error 22: No such partition when I attempted to boot Ubuntu 8.04. I'm going to retry on sda0 now.

---

### Post by patrickrclark on 2008-06-22
What I did in the last post was install on the partition I had already installed upon rather than deleting the old partitions and making new ones. Anyway, Ubuntu is installed now and I keep getting the same GRUB error (Error 22: No such partition). after I press a key it takes me to the boot menu with Ubuntu, Ubuntu recovery, and memtest86 listed as options. My grub was pointing to (hd1,0) and I tried editing it in the boot menu to (hd0,1). This returned the same error. Before I went into grub in a terminal and set root(hd1,0) I got the screen that said "Grub loading please wait" and then shortly after it printed "Error 22". Does this help any?

---

### Post by patrickrclark on 2008-06-22
Just ran super grub disk and used its thing to fix the mbr. It said it was successful but I still get the error 22 when I try to boot.

---

### Post by patrickrclark on 2008-06-23
Bump. Does anyone know how I may fix this?

---

