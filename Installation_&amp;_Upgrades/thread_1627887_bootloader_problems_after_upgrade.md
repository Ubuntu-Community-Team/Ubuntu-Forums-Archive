---
title: "bootloader problems after upgrade"
date: 2010-11-21
forum: Installation &amp; Upgrades
---

### Post by walkdoggie on 2010-11-21
I'm running a wubi installed on Windows 7.
Today I ran updates in ubuntu and installed them. One of the updates asked me if I wanted to update grub. I checked it and went on.
So then I reboot and get dumped straight to this grub rescue terminal.
I poked around forums and found lots of solutions, but my situation seems more messed up than most people.
I get this in the grub shell:

error: no such device: (bunch of numbers)
grub rescue>

so then I do an ls and grub shows:

(hd0)

which is weird since I know there are at least three partitions on my disk. Shouldn't I see (hd0,1), (hd0,2), etc?
Also if I run ls /boot, or ls (hd0) or ls (hd0)/boot it says:

error: unknown file system

If I run set it says:

prefix=(hd0)/boot/grub
root=hd0

Can anyone shed some light on what is going on? Do I need to create a liveCD now and try to fix things that way?

---

### Post by carl4926 on 2010-11-21
Get Supergrubdisk
Boot from it and boot to windows

Then do this:
> download the file "wubildr": [wubildr]("http://launchpadlibrarian.net/36920146/wubildr") 
Don't try  to open the file. Move the file to "C:\"  to replace  the faulty "C:\wubildr".  (to get to "C:\" go to "My Computer" or  "Computer" and  double click the "C:drive") 
If Wubi is not on the C:drive, you might  need to  place wubildr  into the partition containing Wubi. So if  Wubi is not on the C:\drive,  repeat the above instructions,  using  the drive letter of the partition  containing Wubi in place of "C:". 


---

### Post by bcbc on 2010-11-22
You need to reinstall the windows bootloader. When you run a grub-update it prompts you to choose a device (/dev/sda ring a bell) and then if you select it, it installs grub to the drive MBR. Which is great on a normal Ubuntu install, but doesn't work for wubi.

If you have XP, boot a windows disc to a repair prompt and run "fixmbr". From vista/7 run "bootrec.exe /fixmbr"

You can also use install lilo from an ubuntu live CD you would run:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
(ignore warnings as they relate to a different use of lilo)

---

### Post by walkdoggie on 2010-11-22
So the bootloader that wubi uses isn't grub?

---

### Post by wilee-nilee on 2010-11-22
> **walkdoggie said:**
> So the bootloader that wubi uses isn't grub?

Follow bcbc they know whats up, they will explain the grub and wubi setup.

---

### Post by bcbc on 2010-11-22
> **wilee-nilee said:**
> Follow bcbc they know whats up, they will explain the grub and wubi setup.
Hey wilee-nilee, thanks for the positive comments. :)

> **walkdoggie said:**
> So the bootloader that wubi uses isn't grub?

Wubi does use grub as a bootloader. But wubi cannot boot directly from the drive MBR. Instead it boots ubuntu via the windows boot manager using the wubildr. 

So you need to have the windows boot loader in the drive MBR.

---

### Post by walkdoggie on 2010-11-22
OK. I got the supergrubdisk, but it wouldn't boot to either windows or linux for me. Trying the boot to windows option booted to a windows diagnostic tool. Trying linux just stalled on the opening screen, when I hit esc it had errors saying it couldn't find things. Booting from a live CD had the same problems as booting using supergrubdisk.
Then I tried the windows 7 repair disk, ran the boot repair option. No dice. Ran dos cmd "bootrec.exe /fixmbr", it said completed successful, but after that it still booted to the diagnostic utility.
So I went back to the supergrubdisk, and edited the windows command (which was booting to (hd0,0) and changed it to (hd0,1) and voila! I tried copying over the wubildr file, but that didn't work either.
But then I found that it wasn't a permanent change, so I again did the supergrubdisk but edited the second windows option which changes the setting permanently, changed it to hd0,1 and now I'm golden.

So it would seem that I'm still booting off of grub instead of the windows boot utility. I guess that's ok... I didn't do anything stupid did I?

---

### Post by bcbc on 2010-11-22
> **walkdoggie said:**
> OK. I got the supergrubdisk, but it wouldn't boot to either windows or linux for me. Trying the boot to windows option booted to a windows diagnostic tool. Trying linux just stalled on the opening screen, when I hit esc it had errors saying it couldn't find things. Booting from a live CD had the same problems as booting using supergrubdisk.
Then I tried the windows 7 repair disk, ran the boot repair option. No dice. Ran dos cmd "bootrec.exe /fixmbr", it said completed successful, but after that it still booted to the diagnostic utility.
So I went back to the supergrubdisk, and edited the windows command (which was booting to (hd0,0) and changed it to (hd0,1) and voila! I tried copying over the wubildr file, but that didn't work either.
But then I found that it wasn't a permanent change, so I again did the supergrubdisk but edited the second windows option which changes the setting permanently, changed it to hd0,1 and now I'm golden.

So it would seem that I'm still booting off of grub instead of the windows boot utility. I guess that's ok... I didn't do anything stupid did I?
I know nothing about supergrubdisk. It probably set the bootflag on the diagnostic partition when you ran it. The windows bootloader boots whatever partition has the boot flag set.

You're not booting off grub - but if you think you are run the [bootinfoscript]("http://bootinfoscript.sourceforge.net") - it will tell you all you need to know.

PS that wubildr you downloaded is for Ubuntu 9.10

---

### Post by wilee-nilee on 2010-11-22
> **bcbc said:**
> Hey wilee-nilee, thanks for the positive comments. :)

Hey I'm a closet wubi fan I know basically how to run it. don't tell anybody though I will deny it.;)

I used to try to get people to dual boot but hey whatever works is what I try anymore.

---

### Post by bcbc on 2010-11-22
> **wilee-nilee said:**
> Hey I'm a closet wubi fan I know basically how to run it. don't tell anybody though I will deny it.;)

I used to try to get people to dual boot but hey whatever works is what I try anymore.

With this latest grub update, I'm scratching my head why the developers would unleash another round of wubi borkage - so I'm considering switching to the dark side ;) 

The irony is that the grub update is supposed to be a wubi cosmetic fix to suppress the grub bootloader install screen :confused:
But it only works if you installed wubi to the same partition as windows.

---

### Post by wilee-nilee on 2010-11-22
> **bcbc said:**
> With this latest grub update, I'm scratching my head why the developers would unleash another round of wubi borkage - so I'm considering switching to the dark side ;) 

The irony is that the grub update is supposed to be a wubi cosmetic fix to suppress the grub bootloader install screen :confused:
But it only works if you installed wubi to the same partition as windows.

Yeah when I see it not in C I don't know what to say. I just try and comfort the users and wait for you to login, and then say listen to this user. Your undoubtedly the most knowledgeable user about wubi that is a regular.

I have bootscripts saved that I did wubi installs just to generate so I can at the least see a working setup.

---

