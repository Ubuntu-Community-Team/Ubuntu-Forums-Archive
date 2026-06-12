---
title: "Can't install Ubuntu 11.04 from USB stick"
date: 2011-06-10
forum: Installation &amp; Upgrades
---

### Post by gergc on 2011-06-10
I am trying to clean install from a USB stick onto an Acer Aspire One ZG5. Here are the steps I have followed:
 - Downloaded ubuntu-11.04-desktop-i386.iso from [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
 - Downloaded Universal-USB-Installer-1.8.5.3.exe from [http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer.exe](http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer.exe) and run it
 - Selected 11.04 in USB Installer, pointed to ISO, left persistence at 0MB and run it on a freshly FAT32 formatted USB stick

When the Aspire One boots from the USB stick, it displays "SYSLINUX 4.04 EDD 2011-04-18 Copyright (C) 1994-2011 H. Peter Anvin et al", followed by a flashing cursor on the next line.

1) I cannot type anything (read on some forums that typing "help" should work, but I cannot)
2) MD5 check of ISO is correct
3) I have also tried using unetbootin-win-549.exe to create the bootable stick, but the result is the same (although slightly older version of SYSLINUX)

---

### Post by oldfred on 2011-06-10
Welcome to the forums.

There are several reported bugs. I thought they had fixed them with the newer versions.

syslinux errors help/enter works:
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779)
Delete ui in syslinux.cfg
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382)
in the directory from "isolinux.cfg" to "syslinux.cfg"
Try replacing the file vesamenu.c32 on the USB disk drive with that one "/usr/lib/syslinux/vesamenu.c32" of Ubuntu Maverick system or use UNetbootin than works fine.

---

### Post by sikander3786 on 2011-06-10
Welcome to the forums.

Also, make sure that the downloaded image is healthy as well ;)

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by ratcheer on 2011-06-10
I had the exact same problem two days ago. My USB stick had been freshly formatted and my downloaded ISO MD5 sum matched. But mine would run up into the "Install Software" phase, then fail. After several attempts, I formatted the stick again, re-downloaded the ISO, and tried again. That time, the install ran to successful completion.

I can only surmise that, in spite of everything checking out, something was wrong with the image after it was copied to the stick.

Tim

---

### Post by ppv on 2011-06-10
When creating the USB drive in windows can you start the program with administrator privileges and create a USB drive.

---

### Post by gergc on 2011-06-10
Thanks everyone for the fast replies.

@oldfred:
1) help/enter doesn't work because I can't type ANYTHING in.
2) I don't get any error messages, it's not quite the same as bug #617779. I just a flashing prompt after the SYSLINUX line. I tried the change to syslinux.cfg anyway, but the result was the same.

Interesting to read those suggestions. After using universal USB creator, the contents of both the isolinux.cfg and syslinux.cfg are exactly the same except in syslinux the "ui gfxboot bootlogo" is commented out, but in isolinux.cfg it is uncommented. Anyway, I tried both.

@sikander3786 I wrote in the OP that I had already checked the MD5 hash :P

@ppv Not sure what you mean. I am an administrator on my windows box and don't have any trouble creating the bootable USB stick. It just doesn't work.

As I followed the instructions on the Ubuntu download page to the letter, I'm keen to try and figure out what might be causing this problem. I don't think there's anything special about the Acer as it is already running an older version of Ubuntu. All the network interfaces have stopped working, so I'm having to use the windows box to try and update the Acer.

---

### Post by aggoyder on 2011-06-17
I have just had the exact same experience trying to boot an Acer Aspire One GZ5 with a USB prepared on a windows desktop to the same procedure you used.

Have you made any progress ? Might it be worth trying an earlier version - I am just trying to replace Linpus that has now degraded to make the netbook unusable!

EDIT: I have just successfully booted my Windows desktop with the USB, so it looks like an Acer Aspire related issue ?

Thanks
A

---

### Post by theminority5 on 2011-06-22
I was trying to make a bootable usb from Windows which was giving me the exact problem you were having. I then created the boot from Ubuntu 10.10 using Disk Utility and it worked!

---

### Post by UncleBoxy on 2011-07-05
Like others above, I used both unetbootin and usbcreator to create my USB drive.  They completed successfully, but when trying to boot with the newly formatted/created drive, it would either give me one line of the SYSLINUX screen with a flashing cursor and no ability to type anything OR it would give me the BusyBox interface.

Using busybox, I tried doing ```
init= /dev/sdb1
``` but it didn't work (and I honestly don't know if it wanted a specific vm-linuz or init-rd or whatever).

Anyway, the only solution that has worked for me is to format my USB drive using Disk Utility (in Ubuntu).  Then go to Startup Disk Creator and use that to create my USB drive.  That worked.

The source .iso file was on a shared disk between windows and ubuntu, so that wasn't the issue.

---

### Post by paweltbg94 on 2011-07-06
Is there no any option, to make this work? Actually I don't have access to PC with Ubuntu OS. I'm using Acer Aspire One netbook and have same problem (freeze after syslinux logo, with cursor). Tried 11.04 server, 10.10 server, also the newest stable debian. I've tested both tools - latest Unetbootin and latest Universal USB Installer on Windows 7 Home Premium - and both failed. **Is it a syslinux issue on Acer netbooks ?** Deleting ui from syslinux.cfg doesn't work for me.

//EDIT: Maybe different way. Is it possible to modify the usb stick with ubuntu iso to start installation immediately after boot without load syslinux ?

---

### Post by wlsfj on 2011-07-13
I got the exact problem as you were having:
{{It displays "SYSLINUX 4.04 EDD 2011-04-18 Copyright (C) 1994-2011 H.  Peter Anvin et al", followed by a flashing cursor on the next line.}}

- downloaded Utuntu 11.04 iso
- tried both usb_creator and universal usb installer to create the usb boot drive
- none of them worked

Still not sure where the problem is.  Is Utuntu iso file or use creator?  

I haven't tried 10.04.  Maybe it is worth trying.

---

### Post by Lubalin on 2011-07-13
This appears to be specific to the Aspire ZG5. I've installed 11.04 on a different Aspire One model with no problems. The same USB stick hangs at the Copyright screen when loading. As do two different sticks, one created on another PC, another created on Mac OSX (which, as an aside, was painful to do).

As I now have two Aspire One netbooks, one with Ubuntu 11.04, and the ZG5 stuck with Linplus Lite, can anyone confirm that a USB stick created with the machine running Ubuntu should work with the ZG5?

If so, can anyone talk me through it?

---

### Post by ozwoofer on 2011-07-13
sounds like you have the exact same proble m that i am having on a hp mini 210-2000. all i get is the flashing line (cursor). i tried with 10.04 and it did the same thing. id love to hear a solution.

---

### Post by C.S.Cameron on 2011-07-13
If neither usb-creator nor Unetbootin are working you can try booting the iso using grub2.
There are a few guides available, I find the MultiBootUSB script the easiest.

---

### Post by Lubalin on 2011-07-13
I'm not *massively* technical, so that sounds tricky. Is it something you can point me towards? Does it involve a usb stick and an iso?

In the meantime, I am currently downloading 11.04 on ubuntu to stick on a usb, which I will try with the ZG5 tomorrow to, in theory, determine conclusively if that is a solution.

If not, then I'll try the aforementioned option, and then I'm out of ideas.

---

### Post by joshtothedawson on 2011-07-28
I'm suffering the same problem too. I've got an Acer Aspire One D250 and it will just hang on the SysLinux screen. Looks as though there must be an Acer problem..

---

### Post by joshtothedawson on 2011-07-28
i assume you've been trying to use WIndows to create the disk? i had the exact same problem with my Acer Aspire One D250 and when I created a startup disk in Ubuntu itself, it worked first time. I'm not sure what's wrong with making the disk in Windows, but something isn't right.

---

### Post by KBD47 on 2011-07-31
OK guys, here is how I, a Linux novice, got my Acer Aspire One KAV60 to work on Ubuntu with live persistent usb. First I had used Mint 9 to create a live usb of that version with the usb creator in its applications menu. Mint 9 ran like a dream from live persistent usb on my Acer. So I decided to try and use Mint 9 running from a portable CD/DVD player on my Acer and use it to create a live Ubuntu usb. You will need the Ubuntu iso downloaded onto your computer (You can create an Ubuntu usb from another computer using this method with the live cd and having the iso downloaded). Ubuntu 10.04 is the iso I used. Other methods might be easier, but this is how I did it. Using the live Mint 9 cd I went to create usb under "all applications", once the window comes up you can choose "other" for your source iso, which takes you to a menu that has "Acer" on it (if you are doing this on your Acer), click on "Acer", then click on "documents and settings", then "user name", then "desktop" or wherever you downloaded the iso. I had to enlarge the window to get to the select button, but once selected I was back to the download window and I could select Ubuntu under the iso menu. I then plugged in my usb and set the partition for 1 gig (on a 4 gig usb) and then copied it. (If you have anything on the usb you will need to click on the erase button before copying the software onto it.)
   Now Ubuntu live persistent usb is working for me, I'm actually using it right now on my Acer, but every start up it hangs on "try" or "install". I click on "try" then I click on the close window button and get a window asking if I want to "end" which I do. It then takes awhile but Ubuntu finally finishes loading. 
  Linux Mint 9 has none of these hiccups with the live persistent usb on my Acer, but I really wanted to try out Ubuntu and I'm hoping I can use it on the next computer I buy.
KBD47

---

### Post by Microsoft Hater on 2011-07-31
I can confirm that this issue:

{{Screen displays "SYSLINUX 4.04 EDD 2011-04-18 Copyright (C) 1994-2011 H. Peter Anvin et al [new line] Boot:", followed by a flashing cursor on the next line.}}

Persists on Dell laptops as well. 

I have double checked the md5sum, and used 2 separate USB sticks that have each successfully run Ubuntu 10.04. 

Not even getting to the install screens - is 11.04 worth it right now?

Going to download the file again and hope for the best.

---

### Post by KBD47 on 2011-07-31
I'm hoping for a more stable version of Ubuntu Unity down the road. I tried 11.04 on my Acer last week using a non-persistent bootable usb. 11.04 would not launch Firefox, in searching the net I've found other people have had this problem with Unity. I also tried Mint 11 which worked, except that it was slow on my netbook. I think I'm probably better off with the slightly older LTS releases.
KBD47

---

### Post by _mongol on 2011-08-14
I also had this problem on my first try. After the first try I tried to find the problem and I noticed my Firewall(Comodo) had labeled USB-Installer as Not trusted application and my antivirus(Avast) was suspicious about a single file, Autorun.inf.  So, I disabled my Antivirus(Avast) and Firewall(Comodo) for the duration of the installation and tried again. When I put the usb to my netbook, it booted correctly and problem was fixed.

---

### Post by retchid on 2011-08-14
Had same problem ACER aspire one SSD version

bad image on USB stick reinstalled on USB then it worked 

another time - refused to install bad partitions - remove partitions on disk - installed

Last time got fed up after getting no boot  - installed Opensuse using USB - no problems ever since

---

### Post by Skrrp on 2011-08-19
> **gergc said:**
> When the Aspire One boots from the USB stick, it displays "SYSLINUX 4.04 EDD 2011-04-18 Copyright (C) 1994-2011 H. Peter Anvin et al", followed by a flashing cursor on the next line.

I had exactly the same problem, using unetbootin on Windows and Ubuntu and pendrivelinux on Windows.

The solution mentioned earlier of using Ubuntu's boot disk creator utility was the only way I could get it to work. 

Acer Aspire One (something).

---

### Post by alfmarius on 2011-08-25
Well this is the most frustrating issue I've had with Ubuntu ever and is _not_ good regarding signals it sends to new users coming from for example windows.

I primarily use Win7, but am also an experienced linux user. First I tried getting the iso to my usb pen using Universal USB Installer. That just didn't work at all. So then I used UltraISO to "burn" the iso to the pen. That got me to the step that people have trouble with here.

I tried 3 different usb pens on 3 different computers, so I have hard time seeing this as other than a ubuntu/syslinux bug/issue.

I had to give up in the end (I **hate **that) and try doing it from another laptop I have with Ubuntu 10.04. Using the "startup disk creator" I managed to get the ISO over to the pen. But then the headake.. To even get past the syslinux screen I first had to comment out the last line in syslinux.cfg (the ui gfxboot line) and then when the boot came I could finally type something. The only thing that got me further was typing "help" and only then press enter to start boot. Well something started, but now the ubuntu logo has been "loading" for 10 minuttes without anything happening!

This really sux. I found it easier to install slackware 15 years ago!

I think I speak for many people when I say that my primary way of installing linux is by preparing an USB pen from a Windows platform. This stuff should just work off the bat!

..ok, its a free product, I'm not "allowed" to complain, but still...

Hope some genius is looking into this, cause after 5 hours of banging my head agains the wall I just had enough..

***Edit***: I downloaded the 10.04.3 iso instead ([http://releases.ubuntu.com/lucid/ubuntu-10.04.3-desktop-i386.iso.torrent](http://releases.ubuntu.com/lucid/ubuntu-10.04.3-desktop-i386.iso.torrent)). It worked right of the bat like it's supposed to! This reminds me of what we used to say.. "Fixing 100 bugs, introducing 200 new ones"

---

### Post by KBD47 on 2011-08-25
This can and should be fixed. Linux Mint works great from a USB and is built on Ubuntu so surely this can be fixed in Ubuntu. And Kubuntu also works great from a USB.

---

### Post by alfmarius on 2011-08-26
> **KBD47 said:**
> This can and should be fixed. Linux Mint works great from a USB and is built on Ubuntu so surely this can be fixed in Ubuntu. And Kubuntu also works great from a USB.

Well apparently this bug applies to Mint as well:
[http://ubuntuforums.org/showthread.php?t=1831676](http://ubuntuforums.org/showthread.php?t=1831676)

Keep this thread alive and maybe someone will look into it ;)

---

### Post by KBD47 on 2011-08-26
Not sure that is exactly the same problem. I could boot up Ubuntu, but it would hang every time on the 'try' or 'install' screen from persistent live usb. With just a live usb Natty would boot but become buggy, Firefox would not launch from the taskbar. Never had any of those problems from persistent or live usb with Mint or Kubuntu. Some of these problems may be due to certain hardware, but when one flavor of Ubuntu works fine, and another doesn't, there is a bug in the software IMO.

---

### Post by phouka on 2011-08-28
Hello all. I'm a new-ish Ubuntu user. New-ish because while I've run it on my desktop machine for two years now, I'm taking a Fundamentals of Linux course and trying to get Ubuntu up and running on my Asus netbook. I'm running into much the same problem described here.

Asus EEE PC 1015PE netbook
Windows 7 Starter
1 Gb RAM
CPU N550 (quad) @ 1.5 GHz

I have a flash drive that I've tried creating first as 11.04, then reformatted and created as 10.04.3. I've got two problems, and they happen with both versions.

The first is the Ubuntu issue described by others. If I try to boot my desktop system off the flash drive, I get an error message "unknown keyword in config file: gfxboot" and then it brings up a boot prompt followed by "vesamenu.c32: not a COM32R image."

I ran the md5sum on both .iso files I downloaded, and they're good. I can't get the posted script to run, but that's my unfamiliarity with the command line and directory structure.

Following directions I found elsewhere, I can get past that message if I hit <TAB>, wait for my choices, and then type in "live". However, the boot hangs at the Ubuntu 5 dot screen and never reaches the console.

On the Asus netbook, I'm even more frustrated, because I cannot get to the BIOS. The function keys bring up a "Windows Boot Utility" or "Advanced Boot Options" which only show Windows options. Once booted to Windows, the flash drive is clearly visible. I've searched online but can't find any documentation that will get me past the Windows Boot Utility to the BIOS itself.

I can, if I must, run Ubuntu under VM Player or Wubi, but I really was hoping to have a bootable Ubuntu partition on my netbook - if only to prove I can actually create a boot and install drive.

Any suggestions?

---

### Post by alberto1976 on 2011-08-28
> **gergc said:**
> I am trying to clean install from a USB stick onto an Acer Aspire One ZG5. Here are the steps I have followed:
 - Downloaded ubuntu-11.04-desktop-i386.iso from [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
 - Downloaded Universal-USB-Installer-1.8.5.3.exe from [http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer.exe](http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer.exe) and run it
 - Selected 11.04 in USB Installer, pointed to ISO, left persistence at 0MB and run it on a freshly FAT32 formatted USB stick

When the Aspire One boots from the USB stick, it displays "SYSLINUX 4.04 EDD 2011-04-18 Copyright (C) 1994-2011 H. Peter Anvin et al", followed by a flashing cursor on the next line.

1) I cannot type anything (read on some forums that typing "help" should work, but I cannot)
2) MD5 check of ISO is correct
3) I have also tried using unetbootin-win-549.exe to create the bootable stick, but the result is the same (although slightly older version of SYSLINUX)

I had exactly the same problem  on my brand new Sony Vaio laptop/netbook (Y series). In my case, creating the usb on a Linux box and using unetbootin (the ubuntu disk creator did not work) fixed the problem.

---

### Post by phouka on 2011-08-29
Great! What's a unetbootin?
 
Off to research. :-D

---

### Post by gigigadda on 2011-10-15
resolved!
make a startup disk option from ubuntu/kubuntu NO from windows.
sorry for my english.

---

### Post by Cyphear on 2011-11-21
Hope I'm not bringing this up from the dead, but I wanted to share what fixed it for me.

Formatting my drive as FAT16 fixed this for me.  I had to do this from Linux.  XP only let me format it as FAT32.

This was on a Dell Server by the way.

---

### Post by parovelb on 2011-11-30
Same issue here. Neither 10.04 or 11.10 won't do. After the installation process the system just loops in infinity. No errors anywhere. The flash drive installation was done with pendrivelinux, the iso files were checked. Deleting "ui" from isolinux.cfg does not help. Annoying....:confused:

However running the system directly from the stick it does work well. Next I will try to install it right through the desktop icon "install Ubuntu 11.10", which I suppose is part of the "taste sample".

-------------
lenovo s205

---

### Post by parovelb on 2011-11-30
in relation to my previous post I have to say the installation was flawless. However the result "restart the system" turned out to be the same = endless looping like there is no \boot, no system no disk :P

grub menu is now just a distant dream....

---

### Post by Gretha on 2011-12-13
@gergc (#1)

I can confirm your experience, individually both with xubuntu 11.10 and with gparted, each on a separate live usb stick, MD5SUMs OK, and tested 10 days ago on an Acer Aspire One D255E.

We normally use MSI netbooks, and the same usb sticks perform flawlessly on these.

What happened to work -- whether by design or by accident, I don't know --, was pressing F11 repeatedly during the boot sequence of the Acer Aspire One.  It started the live xubuntu session, from which xubuntu could be installed permanently on the hard drive of the Acer. Since installation, the xubuntu installation runs fine, without any start-up problems.

Note that, on this Acer Aspire One, it is F2 which starts the boot setup and F12 (not F11) which calls up the boot menu enabling you to set the boot device priority.

---

