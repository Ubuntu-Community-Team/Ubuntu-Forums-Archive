---
title: "Dual Boot - No CD-Drive"
date: 2010-04-26
forum: Installation &amp; Upgrades
---

### Post by croudiez on 2010-04-26
I am currently using an Eee PC 1005HA with Ubuntu installed. I'd like to dual boot with Windows XP. How can I do this without a CD drive? I have an external hard drive that I used to install Ubuntu in the first place and a Windows XP install CD with key.

---

### Post by labinnsw on 2010-04-28
I think you are looking for [this]("http://www.ubuntu.com/getubuntu/download-wubi")

---

### Post by Mark Phelps on 2010-04-28
OK, the wubi reference mystifies me because, from what I can tell, the OP wants to install XP, not Ubuntu inside XP...

If you have the ability to boot from USB, you could try migrating the XP files to an USB stick and boot using that.

But, since you can't install MS Windows from inside Ubuntu, I don't have any other solutions.

---

### Post by kat3c on 2010-04-28
You could do this, I've used it many times, works fine (only tried with 32-bit installs though...)

[Flash drive Ubuntu install]("http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/")

---

### Post by labinnsw on 2010-04-28
> **Mark Phelps said:**
> OK, the wubi reference mystifies me because, from what I can tell, the OP wants to install XP, not Ubuntu inside XP...


You are in fact right. Don't know how I missed it. My apologies.
As far as I am aware, Windows requires at least a CD drive (external, virtual or otherwise) to install.

---

### Post by kat3c on 2010-04-28
Sorry, upon re-reading your post, I now realize you are wanting to install XP after Ubuntu, which I haven't done, but I've seen is not as straightforward, especially with the bootloader, you'd want to keep Grub, but I've never installed in this order, so can't tell you how straightforward that is.

Here is a help page detailing how install windows after ubuntu:

[windows after ubuntu]("https://help.ubuntu.com/community/WindowsDualBoot")

But, you'd still want to make a usb install drive for xp.  I Googled, and there is a bewildering array of ways/opinions, here's just one:

[XP USB install]("http://en.kioskea.net/faq/3065-installing-windows-xp-from-a-usb-key")

Good luck

---

### Post by kat3c on 2010-04-28
You know, if you have an external drive and want to actually install xp and have both systems on the hard drive, (versus having xp on a usb drive and always booting into that when you use xp), you could install from that, just on booting, go into BIOS, change boot priority to external device, reboot with external drive attached and xp install disc in, and you should be able to install it.  I would have all partitions already set up and know where I'm going to install xp (I'd think after the Ubuntu partition, or partitions will get renumbered and Grub may not know where to find things, but I've never done an install of Windows after Ubuntu, so....)

Then reboot, go to BIOS, reset boot priority to hard drive, and cross fingers.  First, read the help page from previous post on installing Windows after Ubuntu and dealing with bootloaders......

---

### Post by kat3c on 2010-04-28
Ignore last post, thought you had and external CD/DVD drive, not hard drive........

---

### Post by labinnsw on 2010-04-28
Deleted.

---

### Post by varunendra on 2010-04-28
To the Admins/Moderators,

Why don't you people introduce a feature like "Automatically saving drafts" while a user is trying to answer a post?
I just wrote almost a whole length of tutorial before the power-cut ditched me.

Damn, i've to do it again !

---

### Post by varunendra on 2010-04-28
Okay, I'm back ! Let's start again.

There are tutorials on the net about Installing XP through USB pendrive  using Bart's PE. I haven't tried it though.

What I tried successfully (including some hitches & glitches during  the process) was to install XP through DOS.
I used a pendrive to boot into DOS. I made it bootable using HP's tools  or simply trying "sys" command- don't remember exactly.

Here's what SHOULD work (worked for me) (would of-course need the BIOS  being able to boot off USB):


[LIST=1]
[*]**Format the primary active partition and any other partition as  FAT32**.
[*]**Copy the I386 folder from CD to the other fat32 partition**  (DOS won't read NTFS or linux partitions). Now it's upto you how you do  it. I used another PC to transfer the folder from CD to the target PC.
[*]**Make a pendrive DOS bootable** using some tools or "sys"  command - I don't remember how I did it. Maybe just formatting the drive  on a PC running XP- with "Create MS-DOS Startup Disk" checkbox checked  would do the job.
[*]**Do remember to include "smartdrv.exe" **file among other DOS  files. Without it, you may end up spending hours before the first stage  of installation (only copying of files) is finished. You can get  "smartdrv.exe", or a whole bootable floppy image [here]("http://www.allbootdisks.com/disk_contents/98.html"). If  you download the floppy image, choose "Win98 Startup Disk Without  Ramdrive". It includes "smartdrv.exe".
[*]**Boot into DOS** through the pendrive. **Run smartdrv**  ```
smartdrv
```It won't return any text output. Entering  "smartdrv" command again will show its status. ***[You can skip step 3  if you are able to boot the system into DOS using some other way. But  don't forget to run smrtdrv before proceeding further.]***
[*]**Go to the I386 folder** on the harddisk.
[*]There's a file "**winnt.exe**" that starts the setup from DOS.  On the command prompt, you've to enter:```
**winnt**
```
[*]It'll start the setup. First it'll ask you the **path of source  files** which should be already displaying in the target field. So_  you just have to press enter_.
[*]_After copying of some initial files, it may look like hung_  (no disk activity, no prompts,.. nothing). Just be patient for 10-30  min.
[*]IF YOU ARE LUCKY ENOUGH, it will again show up some progress - the  copying of selective files this time. It'll take its time to complete,  then the system will restart by itself.
[*]Thereafter the setup will continue as normal (only the  "formatting" option would be replaced by "convert to NTFS" option)._ At  this stage, converting to NTFS is a good idea_. Taking general inputs  from you, setup will finish as usual and You'd be a happy man!
[/LIST]
 
If, for any reason (including your impatience) the system hangs for real  on step 9, THEN IT MEANS YOU ARE NOT LUCKY ENOUGH (yeah I know it'd be  understood). In this case, you'll need to bear some more headache, and  we'll proceed from step 9:

[LIST=1]
[*]After entering the command: "winnt", setup will start and you must  let the copying of initial files finish.
[*]Then, if you are sure the system has hung, restart it manually.
[*]**Boot into DOS again**. DO NOT LET IT BOOT FROM HARDDISK !  (It'll at first make you happy  showing some progress, then make you go nuts!!) [**A better solution:**  _**format the pendrive **again and **make it an "Ubuntu Startup  Disk**" if u like GUI for next steps_]
[*]**Goto C: drive** where there should be a temporary folder now  created named **$Win_nt$.~LS** . In this folder there'll be an  incomplete copy of I386 folder.
[*]**Copy all the files & subfolders from the source I386 folder  to this $Win_nt$.~LS\I386 folder. **You canuse following  command:```
xcopy /e /y D:\I386  C:\$Win_nt$.~LS
``` (assuming that  source I386 folder is on D: drive and you have the xcopy command  available. It is available in the Win98 floppy image, also seperately on  the site I gave the link of. But if you are using Ubuntu USB Live,  there's no point using DOS at this stage, right?)
[*]After all the files & folders are copied into the $Win..  folder, just plug out the bootable USB drive and restart - letting the  PC boot from its own harddisk this time.
[*]After restart, the setup should resume as usual and goto the  finish as usual.
[/LIST]
 Hope it helps.
Once XP is installed, you can install Ubuntu on top of it through  pendrive or whatever methods guys tell you - making it a dual boot  system.

Easy ! isn't it !!!!:twisted:

---

### Post by wilee-nilee on 2010-04-28
Your best bet is to get a usb DVD/CD player and install with a standard disc. You could easily mess up your system as it is, and have problems that could be fixed but maybe not. Also use a legit XP disc not a torrent.

---

### Post by oldfred on 2010-04-28
I found all these sites:

Copy Windows XP to usb
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)
Please note this tutorial works on all computers not just the Asus EEE PC.
[http://www.eeeguides.com/2007/11/installing-windows-xp-from-usb-thumb.html](http://www.eeeguides.com/2007/11/installing-windows-xp-from-usb-thumb.html)
USB install of XP
[http://komku.blogspot.com/2008/11/install-windows-xp-using-usb-flash-disk.html](http://komku.blogspot.com/2008/11/install-windows-xp-using-usb-flash-disk.html)
[http://www.ngine.de/article/id/8](http://www.ngine.de/article/id/8)
non-commercial all versions of windows
[http://wintoflash.com/home/en/](http://wintoflash.com/home/en/)

---

### Post by labinnsw on 2010-04-29
He/She has Windows on a CD and wants to install it without a CD-Drive. That is just not possible.

The first thing necessary is to get a CD drive or get someone with a CD drive to make a copy of the CD on some other media. (one option would be USB) 

By the way, legit or not, Microsoft allows only one copy of the disc as back-up, or so I was told.

---

