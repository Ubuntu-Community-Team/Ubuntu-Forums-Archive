---
title: "Not able to boot ubuntu from usb"
date: 2011-10-19
forum: Installation &amp; Upgrades
---

### Post by stekre on 2011-10-19
I have made a bootable usb stick by using unetbootin. I have used a 11.10 iso. But when I restart i won't boot from the usb stick.
My win7 usb boot stick works fine, so seems like I have set the correct bios settings.

Do anyone have any ideas?

---

### Post by CleveRuse on 2011-10-19
> **stekre said:**
> I have made a bootable usb stick by using unetbootin. I have used a 11.10 iso. But when I restart i won't boot from the usb stick.
My win7 usb boot stick works fine, so seems like I have set the correct bios settings.

Do anyone have any ideas?

Well ill just piggy-back u then (i was gonna start my own thread but ill just paste it here).....

 Look guys, I need serious help. I'm completely lost. While attempting a fresh installation of Ubuntu 11.10 (Oneiric Ocelet) from a bootable USB stick, I received a notification that read something like this:

"An attempt to configure 'apt' to install additional packages from the cd failed"

Then once the install is complete, I'm prompted to restart my comp. But I then realize that my comp is still set to boot from USB as priority, so I re-edit my BIOS to boot from 'Hatachi 356##$%$5' (wutever) first, but afterwards, after restarting my comp, I get stuck on a blank screen with my cursor just blinking away in the top left corner (i can't type anything). It just hangs there indefinitely! WTF! Is that because of the apt error? Like I I don't have all the necessary applications to even boot up? How do I resolve this? I can still boot from USB bit there's not enough space to actually do anything ....so I'm pretty much stuck! I was connected to WiFi, so retrieving packages shouldn't be an issue.

If u all deem it necessary to ridicule my lack of thechnological prowess, lol -fine ....as long as u also help me! ....but if ur not gonna help me, please take it somewhwhere else;)

Note: I'm also trying to download other Ubuntu versions to try but everytime I try to download, halfway thru I'm told I don't have enough space. Says I only have 10.3MB left ....but I'm running this from my SD, which I know has way more space on it. So i use 'Disk Usage Analyzer' and sure enough, I still have 7.7GB left on my SD ....but then my '/' folder is 100% full with almost 29GB and /cdrom is 83% full with 24.2GB! If more space is needed, why isn't it taken from the 7.7GB first?

Wuts going on how do i fix it?

---

### Post by youngunix on 2011-10-19
> **stekre said:**
> I have made a bootable usb stick by using unetbootin. I have used a 11.10 iso. But when I restart i won't boot from the usb stick.
My win7 usb boot stick works fine, so seems like I have set the correct bios settings.

Do anyone have any ideas?

I would double check that BIOS is set to boot from USB.
if you correctly set the BIOS to boot from the usb and it's not booting then it could be one of the following:

1. Corrupt ISO file.
2. used wrong settings (unetbootin)
3. format the usb as FAT32, and try again

> **CleveRuse said:**
> Well ill just piggy-back u then (i was gonna start my own thread but ill just paste it here).....

 Look guys, I need serious help. I'm completely lost. While attempting a fresh installation of Ubuntu 11.10 (Oneiric Ocelet) from a bootable USB stick, I received a notification that read something like this:

"An attempt to configure 'apt' to install additional packages from the cd failed"

Then once the install is complete, I'm prompted to restart my comp. But I then realize that my comp is still set to boot from USB as priority, so I re-edit my BIOS to boot from 'Hatachi 356##$%$5' (wutever) first, but afterwards, after restarting my comp, I get stuck on a blank screen with my cursor just blinking away in the top left corner (i can't type anything). It just hangs there indefinitely! WTF! Is that because of the apt error? Like I I don't have all the necessary applications to even boot up? How do I resolve this? I can still boot from USB bit there's not enough space to actually do anything ....so I'm pretty much stuck! I was connected to WiFi, so retrieving packages shouldn't be an issue.

If u all deem it necessary to ridicule my lack of thechnological prowess, lol -fine ....as long as u also help me! ....but if ur not gonna help me, please take it somewhwhere else;)

Note: I'm also trying to download other Ubuntu versions to try but everytime I try to download, halfway thru I'm told I don't have enough space. Says I only have 10.3MB left ....but I'm running this from my SD, which I know has way more space on it. So i use 'Disk Usage Analyzer' and sure enough, I still have 7.7GB left on my SD ....but then my '/' folder is 100% full with almost 29GB and /cdrom is 83% full with 24.2GB! If more space is needed, why isn't it taken from the 7.7GB first?

Wuts going on how do i fix it?

are you using an SD card or SSD ?

maybe your SD/SSD can only use a certain amount of space even though it says it has more, the rest is probably reserved.

---

### Post by collisionystm on 2011-10-19
> **stekre said:**
> I have made a bootable usb stick by using unetbootin. I have used a 11.10 iso. But when I restart i won't boot from the usb stick.
My win7 usb boot stick works fine, so seems like I have set the correct bios settings.

Do anyone have any ideas?

Try this program
[http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)

Omgubuntu claims there is a Linux version that just came out

---

### Post by bohemian9485 on 2011-10-19
I used Unetbootin to create linux boot usb and I've no problem with installation so far. I've tried Ubuntu 10.04 LTS, 11.04, Kubuntu 10.04, BT5 and BT5R1 ISOs with Unetbootin and all my USBs run smoothly. One important thing is you have to format your USB using FAT32 file system

---

### Post by MoonLitOwl on 2011-10-19
> **collisionystm said:**
> Try this program
[http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)

Omgubuntu claims there is a Linux version that just came out

I'm having the same issue as the OP is. It booted from my usb the first time with no problems.

But after that, it will just freeze on the bloody Ubuntu loading screen. I shut down my pc several times, check my bios... nothing works.

I also tried that linuxlive usb yesterday. Again, worked the first time but after that it stopped loading.

This is frustrating. I found about Ubuntu on another forum, loved the way it looked and felt when I was able to mess with it, and would like to continue using it but if I can't get it to load without having to re-download it every day, I'm going to look someplace else for a new os.

My usb is already in the FAT32 format as well, with 29gigs left on it.

(I'm on windows 7 atm).

---

### Post by stekre on 2011-10-20
> **youngunix said:**
> I would double check that BIOS is set to boot from USB.
if you correctly set the BIOS to boot from the usb and it's not booting then it could be one of the following:

1. Corrupt ISO file.
2. used wrong settings (unetbootin)
3. format the usb as FAT32, and try again


I have tried the usb stick on another pc (eee 901) and that pc boots from the usb stick. So to sum it up:

PC boots from win7 usb stick
Linux usb stick is bootable (tested on other pc)
PC won't boot from linux usb stick

There is some setting on the linux usb stick that makes the pc unable to boot from it.

---

### Post by stekre on 2011-10-20
To the other people not coming past the boot screen, try reseting your bios to default settings. That have worked for me when having the same kind of problem.

---

### Post by drs305 on 2011-10-20
> **stekre said:**
> 
There is some setting on the linux usb stick that makes the pc unable to boot from it.
At what point does it fail - i.e. what do you see or what error messages do you get when you try to boot off the USB?

Can you boot a LiveCD (have that capability)? 

If not, do you have a Grub menu when you boot? We may be able to boot the ISO file from the Grub command prompt.

---

### Post by stekre on 2011-10-20
> **drs305 said:**
> At what point does it fail - i.e. what do you see or what error messages do you get when you try to boot off the USB?

Can you boot a LiveCD (have that capability)? 

If not, do you have a Grub menu when you boot? We may be able to boot the ISO file from the Grub command prompt.

Nothing happens at boot, it goes directly into win7 which is currently installed. Even when I push F12 and select usb-hdd as boot device it can't find it.

The win7 boot usb boots directly into the setup program.

It's a gigabyte ga-ma785gmt-ud2h motherboard.

I can't boot livecd either.

---

### Post by MoonLitOwl on 2011-10-20
> **stekre said:**
> Nothing happens at boot, it goes directly into win7 which is currently installed. Even when I push F12 and select usb-hdd as boot device it can't find it.

The win7 boot usb boots directly into the setup program.

It's a gigabyte ga-ma785gmt-ud2h motherboard.

I can't boot livecd either.

Mine will either go directly into Win7, or just freeze on the loading Ubuntu screen.

I'll try resetting my bios back to default (I assume I then shut down the comp, and once it's back on change the bios once again to load from a usb?) 

I'll let ya'll know how it goes. :D

---

### Post by stekre on 2011-10-26
Just want to let you know that a motherboard firmware update fixed the problem. The usb stick then popped up as a hd in bios and was able to boot from it.

But strange that the win7 boot stick worked but not the ubuntu boot stick, before I updated.

---

