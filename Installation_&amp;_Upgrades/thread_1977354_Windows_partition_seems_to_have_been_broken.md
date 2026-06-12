---
title: "Windows partition seems to have been broken"
date: 2012-05-10
forum: Installation &amp; Upgrades
---

### Post by subprogie on 2012-05-10
I have recently installed backtrack on my computer alongside windows 7. when I went back to boot into windows it said  &quot;error:no such device: letters and numbers. error:no such partition.  press any key to continue..._&quot;  I know all of my windows is still there because when I boot into backtrack the hard drive is mounted and I can see everything there. I do not have a windows recovery cd. Also testdisk doesn't seem to run it says it isn't installed when I try to run it, then when I install it, it says its already installed.  Any help is appreciated, I desperately need my windows partition for the rest of my school.  I can not use the buttons for some reason in the post box so here is the link for my boot info script.  [http://paste.ubuntu.com/979241/](http://paste.ubuntu.com/979241/)  Thanks for any help.  by the way, sorry if this is in the wrong place, I know this issue has come up before, but I didn't know if I tagged on to an old post if it would be noticed.

---

### Post by subprogie on 2012-05-10
I am begging for help here folks, can someone at least take a look at my results and see if they see anything that jumps out at them?

---

### Post by jacob.david on 2012-05-10
I presume the grub is working fine and displays both ubuntu and windows and you only have problem when you choose windows. You can give it a try by executing the below command after booting into ubuntu
{code}
sudo update-grub
{code}
If it doesn't work then run the bootinfo script as described in the thread [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280) and paste the output here.

---

### Post by wilee-nilee on 2012-05-10
If you have a windows install or recovery disc you can reload [FONT=Verdana]the sda's mbr. Boot it to the repair command line and run this command. You have overwritten the windows bootloader in the sda's mbr, this will see if it is bootable from a windows bootloader, and get you in when needed, I think it will.

```
bootrec.exe /fixmbr
```If this works you can boot from the sda drive to see if it boots with the windows bootloader.[/FONT] [FONT=Verdana]

Here is a link on getting to the windows repair.[/FONT] [FONT=Verdana]

[/FONT]                                     [SIZE=3][COLOR=#000000][FONT=Times New Roman, sans-serif][FONT=Verdana][http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

Lets have someone look at this that is familiar with gpt partitioning, you have this in sdb.[/FONT] 
[/FONT][/COLOR][/SIZE]

---

### Post by subprogie on 2012-05-10
that is another point worth mentioning. I am not really sure how sdb got into the mix. It appears that I have stepped a little too far outside of my comfort zone on this install. It is late here, and I will attempt to fix the mbr in the morning, but by any means other readers feel free to post alternative solutions in case that does not resolve the issue. thank you for the response guys.

---

### Post by darkod on 2012-05-10
Why did you use gpt table on /dev/sdb? If you install uubntu and grub2 on gpt disk, you need to create a small 1MB partition with NO filesystem, and with the bios_grub set on it. This is because grub2 can't fit on the MBR of gpt disks and needs little bit more space on a small partition.

You do have one small partition /dev/sdb1 but it appears to have swap filesystem, and it needs not to have any filesystem. Also, the bios_grub flag is not set.

What you could do as a quick fix, is install grub2 to /dev/sda since it seems you have a broken grub2 on /dev/sda anyway (I guess that is giving you the message no such partition).

I don't know if backtrack works the same as ubuntu and if you can boot it in live mode, but in ubuntu you would install grub2 to the mbr of /dev/sda from live mode with:
sudo mount /dev/sdb2 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

Make the first disk, /dev/sda, first option to boot from and it should work. /dev/sda doesn't need the small partition because it has msdos table.

---

### Post by subprogie on 2012-05-10
Ok Darko, I did what you suggested. However the problem is still occurring,  how do I make sure the /dev/sda is the first to boot? here is my current disk analysis or whatever. here is my latest disk analysis, sorry but the code box made it look painfully hard to read so i have just included the link. [http://paste.ubuntu.com/980477/](http://paste.ubuntu.com/980477/)

---

### Post by darkod on 2012-05-10
You need to look around in your options in BIOS.
There are two different options. One specifies the device, like cd-rom, hdd, usb, etc.
The other specifies only the HDDs, in which order they should be checked for bootloader. In this setting you need to have the first disk as first option. They are both 500GB so if you can't tell them apart, only switch them in the order.

I noticed that now you have syslinux bootloader on /dev/sdb. How did that happen?

I am not even sure hot BT works exactly, is it in the same way as ubuntu. Maybe you wanna check their forums if there are some.

---

### Post by subprogie on 2012-05-10
Well, I have booted from both disks, the one with the grub that wont let me into windows is the same, still cant get in. The other one says something about no operating system on it. From what i understand that is where this operating system is on though, I think it just uses my first drive to access it.   Also, backtrack is an ubuntu variation.

---

### Post by wilee-nilee on 2012-05-10
> **subprogie said:**
> Well, I have booted from both disks, the one with the grub that wont let me into windows is the same, still cant get in. The other one says something about no operating system on it. From what i understand that is where this operating system is on though, I think it just uses my first drive to access it.   Also, backtrack is an ubuntu variation.

You have grub in the sda's mbr, you need the windows bootloader there to boot it from that HD, here is a list of commands I got from a mod on the forums to reload the mbr and rebuild the bcd if needed I would just try the command I posted earlier first. This is only to get you booting windows from that drive at this point.

 [FONT=Verdana, sans-serif][SIZE=1]1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. [/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=1]2) Select the command prompt (console) and type in the following commands: [/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=1]**BootRec.exe /fixmbr** (#updates MBR master boot record...do not run if you still want grub) [/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=1]chkdsk /r [/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=1]BootRec.exe /FixBoot (#updates PBR partition boot) [/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=1]BootRec.exe /ScanOs [/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=1]BootRec.exe /RebuildBcd [/SIZE][/FONT] 
 [FONT=Verdana, sans-serif][SIZE=1]
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html) [/SIZE][/FONT]

---

### Post by oldfred on 2012-05-10
You can follow wilee-nilee's instructions to install/repair a Window install from a Windows repairCD or Full install disk.

But to get grub to correctly install in sdb you need the bios_grub partition. It only needs to be 1MB and has to be unformated with the bios_grub flag in gparted or from gdisk it should show that it is ef02. You can also use Disk utility and set the partition type to BIOS boot.

I also added an efi partition even thought I am booting with BIOS, as I hope to get a new system soon and may use SSD on new system. Easier to have efi set up as it has to be the first partition.

```
fred@fred-Precise:~$ sudo gdisk -l /dev/sdd
GPT fdisk (gdisk) version 0.8.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdd: 117231408 sectors, 55.9 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 85A657E7-D379-4592-B060-E8EA09953D80
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 117231374
Partitions will be aligned on 2048-sector boundaries
Total free space is 3821 sectors (1.9 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          616447   300.0 MiB   EF00  
   [COLOR=Red]2          616448          618495   1024.0 KiB  EF02  [/COLOR]
   3          618496        58925055   27.8 GiB    0700  04
   4        58925056       117229567   27.8 GiB    0700  Quantal

```

---

### Post by subprogie on 2012-05-10
Would you mind being a little bit more specific as to how to do that using disk utility. I don't particularly care for being spoonfed, but I have messed things up bad enough and I just want to make sure that I understand properly.  or are the commands at the beginning of your code block what i should be putting in?

---

### Post by subprogie on 2012-05-10
I am a little bit confused, so please do be patient with me. From what I understand my grub is missing something that boots me into windows. I have downloaded partition manager, and disk utility because I can understand it better seeing it that way. Command is not really my friend. anyway. Could someone break it down dumb style a little and explain what I am trying to accomplish to fix this here.   Also, is there any way that just throwing in the live cd and trying to reinstall, then fix it when I get to the part where I can manipulate the partitions?

---

### Post by wilee-nilee on 2012-05-10
> **subprogie said:**
> I am a little bit confused, so please do be patient with me. From what I understand my grub is missing something that boots me into windows. I have downloaded partition manager, and disk utility because I can understand it better seeing it that way. Command is not really my friend. anyway. Could someone break it down dumb style a little and explain what I am trying to accomplish to fix this here.   Also, is there any way that just throwing in the live cd and trying to reinstall, then fix it when I get to the part where I can manipulate the partitions?

So be sure to quote who you're talking to we want you up and running, without any confusion.

My comments are for fixing the windows bootloader in the HD it is in, so that it can boot on its own if you have that HD first in the bios to be read.

This will not help the backtrack install, only get you back into windows. Many who use two HD's and windows in one like having the windows bootloader booting windows, so if you change the install in the sdb HD you can still boot windows independently.

So grub will boot windows as well normally if set up correctly, that is what oldfred and darkod have been trying to help with.

So to conclude here if you have grub correct in the sdb drive you will have a choice of the Linux install and windows in its menu, if you boot from that HD, and if you boot from the sda you will go straight to windows.

You change the order of which drive is read first in the bios, and there is a per session key prompt as well on powering on that will give you a menu to choose the HD without changing the bios order.

---

### Post by subprogie on 2012-05-10
> **oldfred said:**
> You can follow wilee-nilee's instructions to install/repair a Window install from a Windows repairCD or Full install disk.

But to get grub to correctly install in sdb you need the bios_grub partition. It only needs to be 1MB and has to be unformated with the bios_grub flag in gparted or from gdisk it should show that it is ef02. You can also use Disk utility and set the partition type to BIOS boot.

I also added an efi partition even thought I am booting with BIOS, as I hope to get a new system soon and may use SSD on new system. Easier to have efi set up as it has to be the first partition.

```
fred@fred-Precise:~$ sudo gdisk -l /dev/sdd
GPT fdisk (gdisk) version 0.8.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdd: 117231408 sectors, 55.9 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 85A657E7-D379-4592-B060-E8EA09953D80
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 117231374
Partitions will be aligned on 2048-sector boundaries
Total free space is 3821 sectors (1.9 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          616447   300.0 MiB   EF00  
   [COLOR=Red]2          616448          618495   1024.0 KiB  EF02  [/COLOR]
   3          618496        58925055   27.8 GiB    0700  04
   4        58925056       117229567   27.8 GiB    0700  Quantal

```

ok, I have a 1MB partition on the sdb, and it says it is a linux swap partition, is that the one i should change to say BIOS boot?  it appears that there is already swap space as a 3rd partition so I wouldnt be loosing the swap space.

---

### Post by oldfred on 2012-05-10
From Ubuntu liveCD or USB you should be able to use gparted or disk utility.

That would be fine, but make sure it is unformated also. You can use gparted and right click and change flag to bios_grub. 

Attached is screen shot from Disk Utility.

Then you can reinstall grub from the liveCd. # is comment do not copy or type.

sudo mount /dev/sdb2 /mnt
#If grub 1.99 with Natty or later uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sdb

Then in BIOS set it to boot from the drive that is sdb, or use one time boot key to boot sdb. Run this and it should update the grub menu.

sudo update-grub

---

### Post by subprogie on 2012-05-10
> **oldfred said:**
> From Ubuntu liveCD or USB you should be able to use gparted or disk utility.

That would be fine, but make sure it is unformated also. You can use gparted and right click and change flag to bios_grub. 

Attached is screen shot from Disk Utility.

Then you can reinstall grub from the liveCd. # is comment do not copy or type.

sudo mount /dev/sdb2 /mnt
#If grub 1.99 with Natty or later uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sdb

Then in BIOS set it to boot from the drive that is sdb, or use one time boot key to boot sdb. Run this and it should update the grub menu.

sudo update-grub

do I need to do the gparted flag as bios grub and the disk utility, or just one or the other? sorry to be redundant just want to make sure i am following you

---

### Post by oldfred on 2012-05-10
No, just two ways to set bios_grub setting or flag or whatever they call it. Each app seems slightly different.
You can use gparted if you are familiar with it. I normally use gparted to set it at the same time I create the partitions.

attached is gparted version. note partition cannot be formated. So gparted shows warning icon.

---

### Post by subprogie on 2012-05-11
> **oldfred said:**
> From Ubuntu liveCD or USB you should be able to use gparted or disk utility.

That would be fine, but make sure it is unformated also. You can use gparted and right click and change flag to bios_grub. 

Attached is screen shot from Disk Utility.

Then you can reinstall grub from the liveCd. # is comment do not copy or type.

sudo mount /dev/sdb2 /mnt
#If grub 1.99 with Natty or later uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sdb

Then in BIOS set it to boot from the drive that is sdb, or use one time boot key to boot sdb. Run this and it should update the grub menu.

sudo update-grub

I did this, and everything remains the same on the HD that has the grub on it. (I am assuming that it is sdb even though it is in the first HD spot which doesnt make sense to me) however, the second hard drive which use to say something about operating system not present, now goes to something to the tone of no device, grub rescue or something like that.

here is a new boot-repair log, in case that helps to show where everything is now. [http://paste.ubuntu.com/981068/](http://paste.ubuntu.com/981068/)

---

### Post by darkod on 2012-05-11
> **subprogie said:**
> I did this, and everything remains the same on the HD that has the grub on it. (I am assuming that it is sdb even though it is in the first HD spot which doesnt make sense to me) however, the second hard drive which use to say something about operating system not present, now goes to something to the tone of no device, grub rescue or something like that.

here is a new boot-repair log, in case that helps to show where everything is now. [http://paste.ubuntu.com/981068/](http://paste.ubuntu.com/981068/)

It says at the top the bootloader is looking for /mnt/root/boot/grub which is not correct. I guess you misspelled it, oldfred wrote /mnt/boot and you might have put /mnt/root.

Try this modification of his commands:
sudo mount /dev/sdb2 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb

@oldfred, I am not so convinced about grub2 since Natty using --boot-directory since few times I have given the command like that, the users reported it not working. I believe it's still --root-directory. However, if you DO have separate /boot partition, I remember a case it was vice-versa, the --root-directory will not get you anywhere and you need to use --boot-directory. But that was a case with separate /boot.

---

### Post by oldfred on 2012-05-11
I now I seem to have inconsistent results with command also. Part may be with grub 1.99 it now seems to need the same version to reinstall or else you have to do the full chroot.

This discusses the change with grub 1.99
[https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2)
> 
In Grub 1.99, introduced with Ubuntu 11.04, Natty Narwhal, a new switch is available which more clearly defines where the *grub*  folder is placed. The command above will still work with Grub 1.99, but  the following command is preferred by the developers. The target  directory in the command is the command into which the grub folder will  be installed. By default, and without the switch, the location is */boot/grub*. In these instructions, since the Ubuntu partition is mounted on /mnt, the target would be */mnt/boot/grub*. 
sudo grub-install --boot-directory=/mnt/boot /dev/sdX


---

### Post by darkod on 2012-05-11
> **oldfred said:**
> I now I seem to have inconsistent results with command also. Part may be with grub 1.99 it now seems to need the same version to reinstall or else you have to do the full chroot.

This discusses the change with grub 1.99
[https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2)

I was saying to use cd with the same version as the installed system, and it still didn't work. I don't know if they listened about the cd version. :)

I would stick to the old switch, unless separate /boot is involved in which case the new approach may be tried.

---

### Post by oldfred on 2012-05-11
Cannot disagree, they do say the old on is supposed to work. 

Even thought it is only two lines and (to me) easily copied or typed from a liveCD, I now suggest Boot-Repair, partially as it also can run the boot-info script as well as make most simple repairs. 
I still also may suggest Super-grub as it can boot into a broken system, that then you can repair from inside your install.

---

### Post by subprogie on 2012-05-11
> **darkod said:**
> It says at the top the bootloader is looking for /mnt/root/boot/grub which is not correct. I guess you misspelled it, oldfred wrote /mnt/boot and you might have put /mnt/root.

Try this modification of his commands:
sudo mount /dev/sdb2 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb

@oldfred, I am not so convinced about grub2 since Natty using --boot-directory since few times I have given the command like that, the users reported it not working. I believe it's still --root-directory. However, if you DO have separate /boot partition, I remember a case it was vice-versa, the --root-directory will not get you anywhere and you need to use --boot-directory. But that was a case with separate /boot.

I did this and everything remains the same. I dont want to be a pessimist but what are the odds that I am just up a creek here, I am creeping up on deadlines for school, and I am trying to decide if I should start working on other options as far as that goes.   That being said, I really do appreciate all the help you guys are providing and like I said i don't want to sound like a brat or whatever. This is a pretty impressive community to spend so much time helping out

---

### Post by darkod on 2012-05-11
Already mentioned, but with two disks you need to make sure you are booting from the correct disk also. If you reinstall grub2 to /dev/sdb, make sure that is the disk you are booting from.

It has happened that people keep booting the broken grub from another disk.

---

### Post by subprogie on 2012-05-11
When i boot to my other harddrive it says error:file not found, grub rescue.

---

### Post by oldfred on 2012-05-11
Your pastebin from before showed grub1.97-1.98 in the MBR which is from 10.10 or thereabouts. But kernel is 3.2 which is Ubuntu 12.04 and uses grub 1.99? Are you using the most current liveCD to reinstall grub2?

---

### Post by subprogie on 2012-05-11
I am just using whatever came with my backtrack live cd

---

### Post by oldfred on 2012-05-11
Do not know what backtrack uses, the older grub may work, but do not know enough details to really know.

I might try to full chroot uninstall grub totally and reinstall.

chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Another option is to use Supergrub which sometimes will boot a system bypassing grub. Then you could totally reinstall from inside your install.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by subprogie on 2012-05-11
well, I know it is kind of a messy way to fix things, but i just installed Ubuntu 12 alongside everything else, and when it put its grub on there it let me back in. So i guess that counts as solved heh. 

Anyway, thank you all so much for your help and advice. It is awesome that people are committed to helping out the Ubuntu community here. I look forward to learning more about the linux world so maybe I can end up on the helping end rather than the help me end.

also, i dont know how to mark this as solved...

---

