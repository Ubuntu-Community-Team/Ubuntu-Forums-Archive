---
title: "How To: dual boot w/ W7"
date: 2009-12-19
forum: Installation &amp; Upgrades
---

### Post by Orion_PKFD on 2009-12-19
Hi guys,
 
I got an Asus laptop and I want to install ubuntu on it, and mantain windows 7 (I'll need both OSs). Dual boot, right? (I hope thats the "term")
 
As I've never done such a thing, I'm asking your help to do this because I dont want to break my new laptop!:lolflag:
 
If you know about a tutorial step-by-step or can give me light on this, I'd appreciate that VERY much!
 
Best regards

---

### Post by darkod on 2009-12-19
I think this should do it:
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

Just be careful in step 4, in the top colored line it will show the current partitions/OS situation, and on the bottom the one that will be created. There is gray slider dividing the space for win7 and ubuntu. Slide it left/right to adjust the partitions sizes as per your liking.

---

### Post by FluteFreak on 2009-12-19
Similarly, I'm trying to install on an Asus 1005HA running XP which has two large NTFS partitions and two much smaller. I do not get the screen option as described in the above link to allow Ubuntu Remix 9.10 to co-exist with Windows, only to erase Windows entirely or to do advanced tasks that appear to want to wipe out windows as well.

The partitions are: /sda/dev1 : Windows XP home 72.1 GB
                    /sda/dev2 : 72.1 GB (this partition was created on a reinstall of Windows XP, not at my direction)
                    /sda/dev3 : Windows 2000/NT/XP 4.9 GB
                    /sda/dev4 : 47.1 MB

If I try to format the dev2 partition with Linux, I get an indication that a boot identification is necessary.

I'm stuck. Any guidance? Thanks.

---

### Post by darkod on 2009-12-19
> **FluteFreak said:**
> Similarly, I'm trying to install on an Asus 1005HA running XP which has two large NTFS partitions and two much smaller. I do not get the screen option as described in the above link to allow Ubuntu Remix 9.10 to co-exist with Windows, only to erase Windows entirely or to do advanced tasks that appear to want to wipe out windows as well.

The partitions are: /sda/dev1 : Windows XP home 72.1 GB
                    /sda/dev2 : 72.1 GB (this partition was created on a reinstall of Windows XP, not at my direction)
                    /sda/dev3 : Windows 2000/NT/XP 4.9 GB
                    /sda/dev4 : 47.1 MB

If I try to format the dev2 partition with Linux, I get an indication that a boot identification is necessary.

I'm stuck. Any guidance? Thanks.

From the info you provided (by the way it's /dev/sda not sda/dev), you already have 4 primary partitions on the hdd. Linux numbers the primary partitions 1-4 and logical partitions from 5 onwards. Any hdd is limited to 4 partitions, but in case you need more there is something called extended partition that was introduced. Inside you can have more logical partitions, that is how you can have more than 4 on a hdd.
But if you have reached the limit of 4 partitions the ubuntu installer can see that and it will not offer the same options. This is because it can't just shrink existing partition and create a 5th partition. On the other hand, it can't delete a partition for you because that's risking your data.
Sorry for the longer post. I wanted you to understand.
You have to make a decision where you want to install ubuntu? But you can't keep all partitions, you need to delete at least one. All data on it WILL BE LOST!
Make your plans, when you reach a decision a can tell you how to do it, not to make this any longer right now. :)

---

### Post by FluteFreak on 2009-12-19
Thanks for the response.

Before reading it, I stumbled on another post that indicated that I could "delete" the unused NTFS partition, which I did, and then was able to specify its use for Linux (along the lines of what you indicated which was that only 4 partitions can exist. I wasn't able to create a swap partition, but Ubuntu proceeded with the install. Can I now go back and create a swap partition?

---

### Post by darkod on 2009-12-19
> **FluteFreak said:**
> Thanks for the response.

Before reading it, I stumbled on another post that indicated that I could "delete" the unused NTFS partition, which I did, and then was able to specify its use for Linux (along the lines of what you indicated which was that only 4 partitions can exist. I wasn't able to create a swap partition, but Ubuntu proceeded with the install. Can I now go back and create a swap partition?

Depending how you did it. What I would have suggested after deleting the partition was to tell the installer to Use Largest Available Free space. That way it would create both root and swap inside that unallocated space. And it creates them both inside extended partition.
If you also created another primary, now you have again 4 and there is no way to create swap partition even if you have unallocated space on the disk.

---

### Post by FluteFreak on 2009-12-19
Well, maybe I should wipe out the hard drive and start over! Maybe I'll get it right this time.

---

### Post by darkod on 2009-12-19
> **FluteFreak said:**
> Well, maybe I should wipe out the hard drive and start over! Maybe I'll get it right this time.

It's up to you. When you said you deleted the unused ntfs partition I assumed you are talking about /dev/sda2. That's enough space for ubuntu to work in, no need to delete the whole drive. But do it this way:
1. Boot with the ubuntu cd, Try Ubuntu option, open Gparted (in System-Administration), and delete the partition you created for ubuntu (don't know it will be called /dev/sda2 too now). Leave that space as unallocated. Click on the big green tick mark in the toolbar to execute that command.
2. After that close Gparted and reboot. Now select the Install Ubuntu option, and in step 4 tell it to Use Largest Available Free space. That will be the space freed by deleting the partition. Ubuntu will set itself into that space just nicely.
That's it.

When working with Gparted and partitions, make sure you are deleting the right one. You can LOSE DATA if you delete wrong partition obviously.

---

### Post by FluteFreak on 2009-12-19
Well, I was going to try that, but the bootloader seems to take over and even when I tell the BIOS to boot from the CD, the hard drive takes over without booting from the CD.

Update: Went into BIOS and set it again, re-saved again, and it now has booted from the CD version.

---

### Post by FluteFreak on 2009-12-19
> **darkod said:**
> It's up to you. When you said you deleted the unused ntfs partition I assumed you are talking about /dev/sda2. 

That's right.

> **darkod said:**
> That's enough space for ubuntu to work in, no need to delete the whole drive. But do it this way:
1. Boot with the ubuntu cd, Try Ubuntu option, open Gparted (in System-Administration), and delete the partition you created for ubuntu (don't know it will be called /dev/sda2 too now). Leave that space as unallocated. Click on the big green tick mark in the toolbar to execute that command.

Did that.


> **darkod said:**
> 2. After that close Gparted and reboot. Now select the Install Ubuntu option, and in step 4 tell it to Use Largest Available Free space. That will be the space freed by deleting the partition. Ubuntu will set itself into that space just nicely.
That's it.

That choice isn't available ["Use Largest Available Free space."]I seem to be right back where I started from. The dev/sda2/ partition still shows as being allocated to Ubuntu 

> **darkod said:**
> When working with Gparted and partitions, make sure you are deleting the right one. You can LOSE DATA if you delete wrong partition obviously.

Thanks, I got that part right.

Thanks you so much for investing time with me on this. I REALLY appreciate it!

---

### Post by darkod on 2009-12-19
If it shows being allocated you didn't delete it. Make a screenshot of Gparted and post it. You can make screenshots in Applications-Accessories (I think). Just set like a 3 second delay so the take screenshot window doesn't show over Gparted. :)

---

### Post by FluteFreak on 2009-12-19
So I went throught the process a second time and I guess this time I did it right and I did delete the partition; I selected the option you suggested above and the re-installation is continuing. I see that it is setting up two partitions, including the swap partition. I also notice that the file system that was automatically selected is ext4. I was of the impression that noob's like me should stick with ext3. But it looks like we're on a roll now thanks to your help.

---

### Post by darkod on 2009-12-19
Excellent. Don't worry, ext4 is just fine. In fact, it is the newest filesystem coming with 9.10.

---

### Post by Orion_PKFD on 2009-12-19
> **darkod said:**
> I think this should do it:
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)
 
Just be careful in step 4, in the top colored line it will show the current partitions/OS situation, and on the bottom the one that will be created. There is gray slider dividing the space for win7 and ubuntu. Slide it left/right to adjust the partitions sizes as per your liking.
 
I should select "install" or the 1º option? I want dual boot W7 and ubuntu.
 
Another thing, I have W7 64-bit so I should install ubuntu 64 bit? What is the best choice?
 
And how about swap? What is that and I need to configure something like that?
 
Best regards

---

### Post by FluteFreak on 2009-12-19
> **darkod said:**
> Excellent. Don't worry, ext4 is just fine. In fact, it is the newest filesystem coming with 9.10.

Yes indeed, downloading update files now. All is well. Thanks so much.

Sorry to threadjack. It seemed that the dual boot installation was a common theme. Good luck to Orion_PKFD!

---

### Post by darkod on 2009-12-19
> **Orion_PKFD said:**
> I should select "install" or the 1º option? I want dual boot W7 and ubuntu.
 
Another thing, I have W7 64-bit so I should install ubuntu 64 bit? What is the best choice?
 
And how about swap? What is that and I need to configure something like that?
 
Best regards

The Try Ubuntu option is first to run it from the cd and see how it's working, how do you like it, whether all hardware will work fine, etc. You should have internet access working, you can go online, test sound, etc.
Once you are happy how it's working then again you boot with the cd and select Install Ubuntu, and continue with the process. Depending on your specific situation, in most cases if you use the guided side-by-side install and use the gray divider to choose how much space you want left for windows, and how much space to be dedicated to ubuntu, you should be fine.
Swap is like the swap file that windows uses, when it doesn't have enough memory for all tasks it moves some processes to swap. Only in linux it's a partition and not just a file. If you use the guided install it will create it automatically, no need to worry about it. Only if you are using manual partitioning and creating partitions, you need to create it yourself.

PS. Use 64bit, it doesn't really matter. If you have 4GB or more ram use 64bit otherwise 32bit system can only use 3.5GB of the memory max. That's both for windows and linux.

---

### Post by EdWh on 2009-12-19
From- EdwH.   I have Ubuntu and Win XP on the same drive and keep windows only for emergency use and to use the Acronis - Disk mangement program. This program allows me to do anything I want with my hard drive.   It will even delete, when running the program in windows the linux partition while the drive is running and allow me to set up all new partitions and swap spaces and format all linux partitions with R 3.    Only one problem and that is the boot sector has to be changed to a windows boot only before deleting the Linux partitions. :guitar:so grub is gone until the new install from the ubuntu cd.   This can be done using emergency boot diskette and using Fdisk to change to windows boot only.   However I have not used it in so long I forgot the command to rewrite the sector.  I am sure someone here can help you if you need the command.   I set up my hard drive ahead before using the Ubuntu cd and just find the sector and put ad
slash to tell where to install Ubuntu.   For $50.00 bucks the program is fantastic it will even allow you to open the hard drive such as the boot sector and write to it manually but I am not that inept to dangerous for me.     Ed.

---

### Post by Orion_PKFD on 2009-12-19
Ok, then i'll go for 64bit version
 
On step 4 appears:
 
[SIZE=1][COLOR=#99CC00]**Editor's Note:**[/COLOR] [/SIZE]*[SIZE=1]This option will ONLY appear if you have another operating system installed, such as Microsoft Windows. Remember that, after the installation, the Windows boot loader will be overwritten by the Ubuntu boot loader![/SIZE] *
 
What this is means???
 
If I install from the CD straithforwardly, will I need to worry about the swap?
 
Thanks and sorry for he ignorance:confused:

---

### Post by darkod on 2009-12-19
> **Orion_PKFD said:**
> Ok, then i'll go for 64bit version
 
On step 4 appears:
 
[SIZE=1][COLOR=#99cc00]**Editor's Note:**[/COLOR] [/SIZE]*[SIZE=1]This option will ONLY appear if you have another operating system installed, such as Microsoft Windows. Remember that, after the installation, the Windows boot loader will be overwritten by the Ubuntu boot loader![/SIZE] *
 
What this is means???
 
If I install from the CD straithforwardly, will I need to worry about the swap?
 
Thanks and sorry for he ignorance:confused:
It just means that the option to install it side-by-side will appear only if you have another OS present, which is logical because only then they can be side-by-side, next to each other. And the bootloader part means that Grub2 bootloader will be installed on the MBR instead of windows bootloader but that's fine too. Grub2 can boot both linux and windows while the windows bootloader can boot only windows.
As I said, ubuntu installer will create the swap partition itself, don't worry about it.

---

### Post by Orion_PKFD on 2009-12-20
I installed it, but after ubuntu loads a message appears saying that the hard disc has health problems and an icon appears at the top, and says that hard disk has several parts damaged, or something like that.
 
Why is that so?
 
Regards

---

### Post by darkod on 2009-12-20
Look at post number #5 here:
[http://ubuntuforums.org/showthread.php?t=1343410](http://ubuntuforums.org/showthread.php?t=1343410)

That command is suppose to give you some results confirming or denying that the hdd has problems. Sometimes the message you received can be wrong. On the other hand, your hdd might really have problems.

---

### Post by Orion_PKFD on 2009-12-20
When I type it, appears this:

$ sudo smartctl -t long /dev/sda
sudo: smartctl: command not found

---

### Post by darkod on 2009-12-20
Sorry, it seems you have to install the tools first. In terminal try with:
sudo apt-get install smartmontools (not sure if this is the correct command)

There is also a graphical version that you can install with:
sudo apt-get install gsmartcontrol

If you install the graphical version I'm not sure where you can call it, probably Applications-System Tools. Look around in the menus. That will open graphical interface, you don't have to execute it in terminal.

---

### Post by Orion_PKFD on 2009-12-20
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  bsd-mailx mailx postfix
Suggested packages:
  procmail postfix-mysql postfix-pgsql postfix-ldap postfix-pcre sasl2-bin
  resolvconf postfix-cdb
The following NEW packages will be installed:
  bsd-mailx mailx postfix smartmontools
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory


Dont know why:confused:

---

### Post by Bartender on 2009-12-20
Never mind...

---

