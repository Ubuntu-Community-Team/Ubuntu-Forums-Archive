---
title: "Boot failure"
date: 2010-11-22
forum: Installation &amp; Upgrades
---

### Post by Maaku on 2010-11-22
Hi all,

I have recently saw the light, and decided that I wanted to go Ubuntu. So, I downloaded the Windows Installer of Ubuntu 10.04 and proceeded to install Ubuntu.

From previous experience, I was very confident in installing it, so I had no troubles during installation.

Restarted and selected Ubuntu in Window's boot loader and that began to start. I successfully logged into Ubuntu and did some exploring. I made it more personal by setting up themes and the appearance settings.

I then received a notification about an update, and with that, I went ahead with it. It installed a lot of things, and that happened the last time I had Ubuntu on my machine, so I was OK with that.

It finished, and asked me to restart, and so I did. Without going to Window's boot loader it just displayed a command-prompt like window with "grub rescue>".

It also says "error: no such device: " with a long line of numbers; that looks like a MD5 or SHA1 key.

I thought it was just an error, and decided that I had to get back into Windows to search on it. I shut down the machine by doing it manually and it did the same. I cannot get back into Windows, because the boot loader does not appear.

My computer is a laptop that has Windows Vista on it. I have installed Ubuntu before, and decided that I need it again to give it another go.

The last errors I did have with it were pretty much the same however I could shutdown and choose which OS to boot into.

I have done some searching, but I am a little worried as I have my work on that laptop. Most of the work is projects and assignment work for college. I am very fustrated and confused as to why this is happening, and come to this community for support.

I will be absolutely appreciated if someone can help me.

Thanks,
Maaku.

---

### Post by wilee-nilee on 2010-11-22
The fix may be as simple as reloading the Vista bootloader. But to just have the best information, click on the bootscript in my signature. Follow the directions to generate a text file from running the script. Come back too the thread open a reply and click on the # in the reply panel and paste the all of text from that generated file in between the code tags.

---

### Post by Maaku on 2010-11-22
> **wilee-nilee said:**
> The fix may be as simple as reloading the Vista bootloader. But to just have the best information, click on the bootscript in my signature. Follow the directions to generate a text file from running the script. Come back too the thread open a reply and click on the # in the reply panel and paste the all of text from that generated file in between the code tags.

I do not have a LiveCD or LiveUSB. I think this problem is more serious than it sounds, because I just did the **ls **command and it returned "(hd0)". I am literally stuck on this screen, and most of the commands are not working as it retruns "Unknown command". I am not able to open a terminal either.

---

### Post by wilee-nilee on 2010-11-22
> **Maaku said:**
> I do not have a LiveCD or LiveUSB. I think this problem is more serious than it sounds, because I just did the **ls **command and it returned "(hd0)". I am literally stuck on this screen, and most of the commands are not working as it retruns "Unknown command". I am not able to open a terminal either.

Okay, it may seem bad but it probably isn't, did you get a grub update in Ubuntu? And did you say yes to install it to the MBR sda or hd0?

Personally I am hesitant to give you commands or advise when I don't have all the facts.

Do you have a Vista recovery disc? 
And can you burn a cd? 
And is your computer have a cd/dvd reader

---

### Post by Maaku on 2010-11-22
> **wilee-nilee said:**
> Okay, it may seem bad but it probably isn't, did you get a grub update in Ubuntu? And did you say yes to install it to the MBR sda or hd0?

I am not sure what it was, but now that you mention it, I did this update and it asked something like "Continue without installing GRUB?", I cannot remember what I did.

As far as I remember, I cannot recall having anything ask about the MBR.

---

### Post by wilee-nilee on 2010-11-22
> **Maaku said:**
> I am not sure what it was, but now that you mention it, I did this update and it asked something like "Continue without installing GRUB?", I cannot remember what I did.

As far as I remember, I cannot recall having anything ask about the MBR.

I added more questions can you burn a cd or do you have a recovery disc for vista or install disc for vista.

---

### Post by Rubi1200 on 2010-11-22
Hi Maaku and welcome to the forums :)

From your description, this is a Wubi install that involved an update not allowing you to boot either Windows or Ubuntu.

This is a known issue which can be resolved by reinstalling/restoring the Windows bootloader.

More details here:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
> **[COLOR=DarkRed][SIZE=3]Grub Update results in "No Such Disk":[/SIZE][/COLOR]**
A late July 2010 Grub 2 update is causing a "**[COLOR=DarkRed]no such disk[/COLOR]**"  error for some users of WUBI, resulting in an unbootable system. If the  system doesn't display the original Windows menu, the most likely cause  of the failure is that Grub 2 was installed in the MBR and/or on the  Windows partition. To correct this, restore the Windows bootloader using  this link:
[[COLOR=DarkGreen]How to restore the Ubuntu/XP/Vista/7 bootloader[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1014708")

Whether the failure is due to improper user selections or Grub 2's  failure to recognize a Wubi install, it has been reported in the  following bug and users can review it for status updates and recovery  options when they become available:
[https://bugs.launchpad.net/wubi/+bug/610898]("http://www.webupd8.org/2010/05/fix-symbol-grubputs-not-found-when.html")

By the way, wilee-nilee was on the right track because you will need to restore the Windows bootloader to fix this.

---

### Post by Maaku on 2010-11-22
> **wilee-nilee said:**
> I added more questions can you burn a cd or do you have a recovery disc for vista or install disc for vista.

Yes, my laptop has a DVD burner and reader. No, I do not have any recovery disks. My goal is to get out of this screen somehow without touching Windows or opting for a recovery. I have too much work on there and I cannot afford to delete it.

---

### Post by Maaku on 2010-11-22
> **Rubi1200 said:**
> Hi Maaku and welcome to the forums :)

From your description, this is a Wubi install that involved an update not allowing you to boot either Windows or Ubuntu.

This is a known issue which can be resolved by reinstalling/restoring the Windows bootloader.

More details here:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

I will have a look at this and report back with the results. Thank you both for your support.

---

### Post by Rubi1200 on 2010-11-22
> **Maaku said:**
> Yes, my laptop has a DVD burner and reader. No, I do not have any recovery disks. My goal is to get out of this screen somehow without touching Windows or opting for a recovery. I have too much work on there and I cannot afford to delete it.
I am not sure you understand; we are definitely NOT telling you to restore the whole Windows installation!!

The goal is to restore ONLY the bootloader for Windows.

If you do not have the Vista recovery disks, try and borrow from someone.
Alternatively, download and burn a recovery disk from NeoSmart:
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

If that is not possible, we have another solution. But please do not take action without asking here first since we do not want you to lose any important work or documents.

---

### Post by wilee-nilee on 2010-11-22
Okay here is the easiest way to do this download the recovery and just run the command I highlight follow the directions to get to the recovery console=terminal.
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr** (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
BootRec.exe /FixBoot (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

I love the tutorials but they can be confusing to new users.;)

Just run this command in the booted recovery disc for vista burn it to a cd, then reboot to vista.
```
**BootRec.exe /fixmbr**
```

I don't like giving instructions without knowing more but from your confirmation of a grub update and your description I think we are alright here.

---

### Post by Maaku on 2010-11-22
> **Rubi1200 said:**
> I am not sure you understand; we are definitely NOT telling you to restore the whole Windows installation!!

The goal is to restore ONLY the bootloader for Windows.

If you do not have the Vista recovery disks, try and borrow from someone.
Alternatively, download and burn a recovery disk from NeoSmart:
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

If that is not possible, we have another solution. But please do not take action without asking here first since we do not want you to lose any important work or documents.

I pretty much do understand, if you cannot tell, I am in panic mode and often say what I do not want to happen as a result of it.

During this moment, I do not know anyone who is available to allow me to borrow one. I need a better solution.

---

### Post by Maaku on 2010-11-22
> **wilee-nilee said:**
> Okay here is the easiest way to do this download the recovery and just run the command I highlight follow the directions to get to the recovery console=terminal.
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr** (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
BootRec.exe /FixBoot (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

I love the tutorials but they can be confusing to new users.;)

Just run this command in the booted recovery disc for vista burn it to a cd 
```
**BootRec.exe /fixmbr**
```

I am doing this now and will report back with the results. Thank you once again.

---

### Post by Rubi1200 on 2010-11-22
My thanks too to wilee-nilee for a more complete description of the steps required to fix the problem.

---

### Post by wilee-nilee on 2010-11-22
> **Maaku said:**
> I am doing this now and will report back with the results. Thank you once again.

I know that panic although its been a long time since it was with a OS, mine is in my college studies. I recognized this panic so I just had to give the straight information, to lock down what needs to be done. Thanks Rubi1200 we are all working together here.;)

---

### Post by wilee-nilee on 2010-11-22
> **Rubi1200 said:**
> My thanks too to wilee-nilee for a more complete description of the steps required to fix the problem.

Courtesy of oldfred I just copied his set, I knew it already but it is perfectly concise.;)

---

### Post by Maaku on 2010-11-22
Okay, I found a CD that had "Ubuntu 10.04.1" written on it, so I inserted that and booted from the CD-rom, it has loaded into Ubuntu and has came up with an installation window. Will this mean I have two installations of Ubuntu if I do this one?

---

### Post by oldfred on 2010-11-22
I do not know if this will work or not. Since we want to boot windows we just need to jump to the windows partition to boot it.

from grub prompt.

set root=(hd0,1)
chainload +1
boot

This also has instructions on booting wubi from rescue mode:
[https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode)
or
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

---

### Post by Maaku on 2010-11-22
> **oldfred said:**
> I do not know if this will work or not. Since we want to boot windows we just need to jump to the windows partition to boot it.

from grub prompt.

set root=(hd0,1)
boot

This also has instructions on booting wubi from rescue mode:
[https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode)
or
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

I just changed the settings to boot from IDE0 and that grub rescue screen appeared again, and I have tried that. The first command works, however "boot" is not a command, apparently: "Unknown command 'boot'".

I am going to go back into the CD rom and wait for a response to my last reply.

---

### Post by wilee-nilee on 2010-11-22
> **Maaku said:**
> Okay, I found a CD that had "Ubuntu 10.04.1" written on it, so I inserted that and booted from the CD-rom, it has loaded into Ubuntu and has came up with an installation window. Will this mean I have two installations of Ubuntu if I do this one?

Run the script as originally suggested so we can see whats up. I think the command from the Vista cd will work but the script would be really helpful here.

You can possibly do a manual boot in as oldfred has posted, and really we want oldfred in on this no matter what.;)

So since we have two others that are very good at this I will just sit back and watch and learn, good luck.;)

---

### Post by oldfred on 2010-11-22
See my edit and try it with a chainload +1. that is a normal grub command but I do not know if it works on a rescue mode.

---

### Post by Maaku on 2010-11-22
> **wilee-nilee said:**
> Run the script as originally suggested so we can see whats up. I think the command from the Vista cd will work but the script would be really helpful here.

You can possibly do a manual boot in as oldfred has posted, and really we want oldfred in on this no matter what.;)

So since we have two others that are very good at this I will just sit back and watch and learn, good luck.;)

So, should I install Ubuntu again? I inserted a Ubuntu CD that I got a while back and changed the settings to boot the CD rom and it is showing the installation screen where you select your language and can either try or install Ubuntu.

The thing is, won't I then have two installations of Ubuntu?

---

### Post by wilee-nilee on 2010-11-22
> **Maaku said:**
> So, should I install Ubuntu again? I inserted a Ubuntu CD that I got a while back and changed the settings to boot the CD rom and it is showing the installation screen where you select your language and can either try or install Ubuntu.

The thing is, won't I then have two installations of Ubuntu?

go to the live session=**TRY** download the bootscript in my signature, run it and post the text.

---

### Post by Rubi1200 on 2010-11-22
To be honest, I do not see how adding an extra Ubuntu install really helps here.

I have advised users with this exact problem in the past (see the links in my original post) and it has never once failed to fix the problem.

If you cannot download and burn the Vista recovery CD for some reason we can tell you how to reinstall a Windows-like bootloader called Lilo which may resolve the issue. I say may because I have never seen it done that way, only with the actual fixmbr option from a Windows recovery CD.

Read the comments here by forum member bcbc (who really knows his stuff when it comes to Wubi installs)
[http://ubuntuforums.org/showpost.php?p=9932481&postcount=7](http://ubuntuforums.org/showpost.php?p=9932481&postcount=7)
The first paragraph is the one I am referring to as the rest of his comments are about a slightly different problem with Wubi installs.

---

### Post by wilee-nilee on 2010-11-22
Personally we are now at 24 posts, this is where I leave I have to disconnect. This is a easy fix with just getting the information needed in the script...geez:confused:

---

### Post by oldfred on 2010-11-22
You can only install wubi once. If you have a liveCD it is offering to do a full install to separate partitions. But you need to boot windows first as you should shrink the windows partition from inside windows if you even want to do a full install.

If you have a liveCD and can boot into it, then you can install lilo which will let you boot your windows.

Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

---

### Post by Maaku on 2010-11-22
> **wilee-nilee said:**
> go to the live session=**TRY** download the bootscript in my signature, run it and post the text.

I cannot do that because I still cannot access Windows or Ubuntu. I found a installation disk for Ubuntu 10.04.1, should I try installing another one? Because if I do it that way, atlest, I will have access to the terminal.

But, my question is: will this cause more problems having two installations?

---

### Post by Maaku on 2010-11-22
I cannot run that script in the try now thing. It says "Permission denied".

---

### Post by oldfred on 2010-11-22
The instructions say to run it from command line with 

sudo bash 

 sudo bash ~/Desktop/boot_info_script*.sh 

or if in downloads:

 sudo bash ~/Downloads/boot_info_script*.sh

---

### Post by wilee-nilee on 2010-11-22
n

---

### Post by Maaku on 2010-11-22
Managed to execute that script, here is the output:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #256 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda3/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    24,563,384    24,563,322  27 Hidden HPFS/NTFS
/dev/sda2    *     24,563,712    90,652,671    66,088,960   6 FAT16
/dev/sda3          90,652,672   156,299,263    65,646,592   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       7938ab2a-49a0-4c48-a608-58a2fd8fd23e   ext4                                     
/dev/sda1        20E0FA48E49BED2A                       ntfs       PQSERVICE                     
/dev/sda2        1AA02B3DA02B1F2F                       ntfs       ACER                          
/dev/sda3        52EE2190EE216D83                       ntfs       DATA                          
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

```

---

### Post by wilee-nilee on 2010-11-22
w

---

### Post by bcbc on 2010-11-22
or since you're on Ubuntu, just install lilo:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
``` (ignore warnings relating to different use of lilo)

There has been a recent update to grub that is affecting wubi users again (but only those who installed to a partition other than windows). e.g. /dev/sda2 contains /wubildr, but /dev/sda3 contains the /ubuntu/disks/root.disk.

The fix is (as mentioned already) to reinstall the windows bootloader, but lilo does the job if you only have an Ubuntu live CD.

---

### Post by Maaku on 2010-11-22
> **oldfred said:**
> You can only install wubi once. If you have a liveCD it is offering to do a full install to separate partitions. But you need to boot windows first as you should shrink the windows partition from inside windows if you even want to do a full install.

If you have a liveCD and can boot into it, then you can install lilo which will let you boot your windows.

Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

It's one problem after another. I did the first command and this is what it returned: "WARNING: kernal & initrd not found in the root directory (/vmlinuz & /initrd.img)
WARNING: Do NOT reboot or LILO may fail to boot if your kernel+initrd is large.
WARNING: Please read /usr/share/doc/lilo/README.Debian"

I do not know what's going on, or what I am even doing.

---

### Post by bcbc on 2010-11-22
Those are the warnings oldfred and I mentioned... it relates to booting linux.
Just ignore them and run the second command.

PS apologies to other users for jumping in on this thread - I really just wanted to mention that there has been a recent grub update and we will be seeing many of these grub rescue prompt problems on wubi installs.

---

### Post by wilee-nilee on 2010-11-22
> **bcbc said:**
> Those are the warnings oldfred and I mentioned... it relates to booting linux.
Just ignore them and run the second command.

PS apologies to other users for jumping in on this thread - I really just wanted to mention that there has been a recent grub update and we will be seeing many of these grub rescue prompt problems on wubi installs.

No man everybody is welcome, especially you, with wubi. personally all I wanted was this persons computer working, but got a little to attached to actually getting it done.;)

Thanks for the heads up and I will copy those lilo commands for future needs.

---

### Post by Maaku on 2010-11-22
Okay, so I have managed to fix the problem and can get into Windows now. I still want to give Ubuntu a chance, so I will ask before I do anything until I am confident enough. I have this update thing that has came up again, and I think this is what caused the problems. I have starting installing those now.

---

### Post by Maaku on 2010-11-23
So far so good, nothing bad has happened apart from several unexpected shutdowns. Not sure why that is happening, but it did this before on Windows; I think it's a heat issue.

When I load up my PC, it takes me to the GRUB boot loader where I can select various versions of Linux, and I am able to click on the Windows boot loader. How can I make it so the Windows boot loader appears and not GRUB?

Just in case that fails, I will still be able to enter Windows.

Thanks for all your help and support. It is very much appreciated and has saved me a lot of time. I was not fully cooperative with you, and I am really sorry.

---

### Post by Rubi1200 on 2010-11-23
We are all pleased that you have managed to get things sorted out :)

If you believe the problem has been resolved satisfactorily, please mark this thread Solved using the Thread Tools near the top of the page.

---

### Post by Maaku on 2010-11-23
> **Rubi1200 said:**
> We are all pleased that you have managed to get things sorted out :)

If you believe the problem has been resolved satisfactorily, please mark this thread Solved using the Thread Tools near the top of the page.

Absolutely, however I do not want to create another thread for something that is closely tied to what my problems were. Thanks for reminding me though. I am now getting a little bit used to Ubuntu, just trying to install LAMP. One of the reasons I want Ubuntu, it is awesome for programming.

---

### Post by sperman13 on 2010-11-29
Hey guys, 
 
I had the same problem with the Grub loader when I installed the update and I did the lilo fix and i restarted my computer and things looked good it brought me to the screen where I can choose either Ubuntu or Windows XP and naturally then I can choose what version of Ubuntu I want to run. But now when I click Ubuntu a black screen flashes that says something like "hd0: No Wubildr" Im not sure exactly what it said but I know for sure it said No Wubildr. 
 
:S I'm so confused! I know since I have the USB with Ubuntu I can just reinstall ubuntu but I'd rather not lose all my files :(

---

