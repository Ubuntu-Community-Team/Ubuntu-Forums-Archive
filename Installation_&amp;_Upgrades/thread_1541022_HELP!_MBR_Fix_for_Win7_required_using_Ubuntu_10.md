---
title: "HELP! MBR Fix for Win7 required using Ubuntu 10"
date: 2010-07-28
forum: Installation &amp; Upgrades
---

### Post by aerbag on 2010-07-28
Hi All,

I made the MOST basic of errors and now i need help! I had ubuntu 9 installed on a partition of my netbook HD that was primarily running w7. I was running out of disk space and decided to remove the ubuntu partition as a short term measure - however i didnt change any of my GRUB settings so now i can boot into anything... 

in only get a GRUB RESCUE> prompt on trying to boot.  From searching the internet I've come to the conclusion that my MBR is F%^ked and need to restore it... 

I've downloaded ubuntu 10 and can run it from a mem stick, but i cannot get the ms-sys package to install - i keep getting the following error. 

ubuntu@ubuntu:~$ sudo apt-get install ms-sys
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ms-sys
ubuntu@ubuntu:~$ 


Is there another way of removing GRUB completely? Or is there something else that I can try to successfully install ms-sys? 

any and all hints would be GREATLY appreciated...

thanks,

---

### Post by endotherm on 2010-07-28
pop in your windows disk and boot off it. when prompted enter recovery console and run these commands:
```

fixboot
fixmbr

```that shoudl do ya.
the alternative is to instal ms-sys (no longer in the repos as you have discovered). you can download it here:
[http://ms-sys.sourceforge.net/#Download](http://ms-sys.sourceforge.net/#Download)

---

### Post by aerbag on 2010-07-28
no such thing as a windows boot disk on my netbook - i dont even have a cd drive on it! and regardless i'd have to pay ~50 sterling to get replacement disks from acer :-(

---

### Post by aerbag on 2010-07-28
K i think i've made a bit of progress... I think i have ms-sys installed now, but i cannot find an option to write a win7 MBR, there is an option for win2003 (vista?) any ideas?

---

### Post by wilee-nilee on 2010-07-28
> **aerbag said:**
> no such thing as a windows boot disk on my netbook - i dont even have a cd drive on it! and regardless i'd have to pay ~50 sterling to get replacement disks from acer :-(

Here is a link to a W7 recovery disc that will get you to the correct command line with the correct BootRec.exe /fixmbr command. You will need a external cd reader to burn the ISO to and to read the cd to boot it and run the command.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

Here is the instructions on what to do, with a http link for help on getting to the command line in W7 from the cd, just run the highlighted command

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr** (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
BootRec.exe /FixBoot (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

To be honest if your planning on using W7 for future use you will want to get a install disc, and the OEM version from acer might be the answer, mine for XP from them was 20$ US, but I have standard DVD install disc for my W7 upgrade.

Acer offers a free xp download from the web I suspect they have a download for other MS OS.
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)

---

### Post by oldfred on 2010-07-28
From most linux and Ubuntu you can install lilo which works like the windows boot loader:

per meierfra. mbr.bin may cause problems in some cases better to use lilo
Restore basic windows boot loader - universe enabled from Ubuntu or liveCD
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

per kansasnoob Note: If I use Lilo to restore a Windows MBR using my "installed" Ubuntu I always like to remove the package "lilo" when done just to prevent some later "conflict" with grub updates, this of course is as easy as "sudo apt-get remove lilo".

---

### Post by aerbag on 2010-07-28
hi lads, 

thanks for the tips, i'll have a blast at them now. will the win7 install disk, work if i load the iso onto a mem key?


on a different note - i just tried to resize my main hd to give me a section that i could load load ubuntu onto, so that i could try updating grub that way. but the action failed when i tried it using the bundled ubuntu partition manager

---

### Post by wilee-nilee on 2010-07-28
I don't think that the ISO will load to a thumb, post 6 though will get you the MS reading mbr back if you follow the directions. At least get you back into Windows.

If you can get a W7 install DVD though it can be loaded to a thumb for install/repairs with their program.
[http://wudt.codeplex.com/](http://wudt.codeplex.com/)

This is just a link but you can go to the MS store and get this same program.

---

### Post by aerbag on 2010-07-31
hi guys, 

got all sorted... it was all very easy once i got the external DVD drive... the repair literally took 20 seconds! 

Thanks again :-)

---

### Post by Mark Phelps on 2010-08-01
> **endotherm said:**
> pop in your windows disk and boot off it. when prompted enter recovery console and run these commands:
```

fixboot
fixmbr

```that shoudl do ya.
the alternative is to instal ms-sys (no longer in the repos as you have discovered). you can download it here:
[http://ms-sys.sourceforge.net/#Download](http://ms-sys.sourceforge.net/#Download)
You really need to READ what the OP says ...

First of all, netbooks do NOT have optical drives, so there's no way to boot off a disk.

Second of all, those are WinXP commands, which no longer exist in Win7.

Fortunately, someone else who KNEW what they were saying told them the proper way to do it and the proper commands.

---

### Post by endotherm on 2010-08-03
> **Mark Phelps said:**
> You really need to READ what the OP says ...

First of all, netbooks do NOT have optical drives, so there's no way to boot off a disk.

Second of all, those are WinXP commands, which no longer exist in Win7.

Fortunately, someone else who KNEW what they were saying told them the proper way to do it and the proper commands.
well someone woke up cranky this morning.
well if you wanna do this...

1) the op did not mention that he did not have an optical until post 3. READ it yourself. netbook does not necessarily mean no optical. people on these forums ask for disks specifically as it is a good test of legit ownership, and an indication that we are not breaking the CoC by assisting the op.
2) perhaps my windows skills are a little out of date. so sorry. mea culpa.
3) I read the ops post, noticed he was having trouble finding ms-sys, and provided the sought information. far more than you have done barging into a solved thread throwing poorly founded allegations. how many of your 3700 some odd posts are equally unhelpful?

---

