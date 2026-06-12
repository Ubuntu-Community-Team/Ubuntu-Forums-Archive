---
title: "DUAL BOOT - Can`t boot W8 nor UBUNTU"
date: 2013-09-13
forum: Installation &amp; Upgrades
---

### Post by edd13 on 2013-09-13
Hi

I am having lots of problems with ubuntu and can`t boot my windows. At the moment I can`t not boot windows or ubuntu and would like to understand why.
I have asus P8Z77-V LX UEFI mobo, CSM (Compatibility Suport Mode) is set to ENABLED and UEFI and Legacy OpROM, Security Boot is disabled and OS Type is OTHER OS

I am only able to run Ubuntu through the usb disk and can only get to W8 via recovery usb (where I can only access CMD, reset, etc) but can do anything on W8 and it is my main goal to recover windows.

Is there a way to recover W8? I don`t want to reinstall the OS again otherwise I will lose everything.

Please I am terrible with linux so explain things in a very easy and clean way please take it easy....

This is the BOOT INFO SUMMARY that i have from the live ubuntu usb > [http://paste.ubuntu.com/6102442](http://paste.ubuntu.com/6102442)

PLEASE SOMEBODY HELP ME!!!

---

### Post by edd13 on 2013-09-13
Please let me know if you guys need more information to resolve this issue

Thanks

---

### Post by Mephisto Pheles on 2013-09-13
First of all don't panic. I know that's easier said than done. I've been there too so I know how it feels, especially the first time.

I'm no expert in this, other people here will be able to help you better than I can, so please be patient and wait till somebody can help you.

---

### Post by edd13 on 2013-09-13
I hope so...

thanks anyway

---

### Post by CeejRab on 2013-09-14
Hello Edd13,

Youre in a pickle eh? Yikes. I did the same thing believe it or not! But good news for you is that i can help (i hope!), whereas i didnt have anyone to help me! 

First off, as said before, dont panic, its ok! Linux is your friend, i actually switched from windows 7 to ubuntu 12.04 LTS because after using it for a recovery i fell in love and its so much better than windows. But anyway im not a salesman... Especially for freeware like linux, haha. 

Ok so your main goal is to restore your windows 8. To do this you need to remove grub and fix the windows MBR (Master Boot Record) and windows boot loader. This will allow you to boot your windows partition and operating system. To do this, linux is your best buddy! 

Step 1: Hold the Control Key, the ALT key, and press the "T" key. This will open a new terminal window. If this is too difficult, just press the windows button on your computer keyboard and type "terminal" in the search bar that pops up. Once terminal opens, type the following command in step 2 (without quotes) 

Step 2: in terminal, type "sudo apt-get update" and press enter

Step 3: type "sudo apt-get install -y Lilo"

Step 4: if a prompt comes up, just press enter or click OK

Step 5: type "sudo fdisk -l" to see your partitions. Now, choose the partition that windows is on and see what it's called. If you have a SATA HD the main drive should be "sda". All partitions of that drive will be "sda1" "sda2" and so on, because the numbers represent the partition. If your drive shows as "sdb" or "sdc", use that instead of "sda". We want the main hard drive to get its boot loader fixed, so in the next step you don't need to type the partition number, just the main drive location (sda, sdb, or whatever your drive is called.)

Step 6: type "sudo lilo -M /dev/sda mbr" (replace the "sda" part with whatever your drive is called as stated before. If it is "sda" then leave it that way in the command. Press enter. 

This should be it, just type "exit" in the terminal window and it will close. Then reboot your computer from the main HD and it should boot windows normally. If this doesnt work, you can try the less friendly and descriptive approach which i derived this method from at the following website [here]("http://thenewtech.tv/how-to/use-ubuntu-and-lilo-to-restore-the-windows-mbr"). 

I hope this works for you, and i trust this was somewhat of a help! Keep calm and linux on!

-Christian

---

### Post by Bucky Ball on 2013-09-14
*Thread moved to **Installation & Upgrades**.*

You might have more luck here. 

* Just looking at your boot info script: Win8 is safely there on sdc, and for some reason you've partitioned sda with a /swap and three EXT4 partitions but doesn't look like you've installed Ubuntu (hopefully I'm wrong). You need to install the grub to sda, that will then find Win on sdc and all should be good. Your Win bootmgr is installed on /dev/sdc1. It's already there and should be picked up by grub without issues. 

Try this:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Or this:

[http://robertbeal.com/562/rebuilding-grub2-grub-cfg-from-ubuntu-live-cd](http://robertbeal.com/562/rebuilding-grub2-grub-cfg-from-ubuntu-live-cd)

You need to install grub to /dev/sda. Also, this could help and works in a jif:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Save a lot of screwing around. I'd try that first, perhaps. You can install directly into a Live session (from CD or USB) as long as you can get online.

To boot to Win and reassure yourself it's there (and possibly backup your precious data), get to the BIOS after boot and try booting from /dev/sdc (which may be something like hd2,0 in BIOS).

* Hate to say it, but I will: this is a perfect example and warning to all to ALWAYS backup valuable personal data before installing on or manipulating partitions. 

Good luck. ;)

---

### Post by CeejRab on 2013-09-15
Good point, I'm assuming the conditions are good enough to use lilo but things may be more complicated. 

Edd13, any additional info on your situation would be appreciated so that we can diagnose your problem and help you get back up and running ASAP. 

I also would definitely recommend backing up your documents. If you can run the live USB and view your computer's HD, locate you documents and files in the windows partition and back them up to another external hard drive if they are too valuable to lose. Also, for the future, frequent backups to an external drive are a good idea in case situations like this come up ;) 

PS: if you do use Gparted to view your partitions, be careful not to make any changes or you could lose everything if you don't know how to use it! 

All the best, 

-Christian

---

### Post by Bucky Ball on 2013-09-15
Sorry, radically edited my post after taking the time to look at the bootinfoscript results. ;)

---

### Post by edd13 on 2013-09-20
Hi guys sorry about the late response

Anyway i do appreciate your time and dedication to help me solving this issue but I guess I could not wait to use my PC due to personal stuff...I think is too late now to recover my W8 as I already installed W8 on the ssd where ubuntu was firstly installed.
The bad news is I lost some important docs but a friend of mine told me I can still recover w8 because its original ssd was not touched...anyway don`t know hoe to do it. I tried hirens boot cd but files were not there. I guess now I got rid of ubuntu and will run ubuntu on my VM instead.

Thanks

---

### Post by Bucky Ball on 2013-09-20
Could you mark this thread as solved from thread tools at the top right of the page thanks? Good luck.

---

