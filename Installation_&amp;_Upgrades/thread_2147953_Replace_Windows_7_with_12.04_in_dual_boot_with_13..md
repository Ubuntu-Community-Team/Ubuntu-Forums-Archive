---
title: "Replace Windows 7 with 12.04 in dual boot with 13.04 _Help with Partition &amp; Install"
date: 2013-05-23
forum: Installation &amp; Upgrades
---

### Post by Rekhillbill on 2013-05-23
Hello,

I want to install 12.04 on current Windows 7 partition in dual boot with 13.04.

  I would like to share data between 12.04 & 13.04.

Also, I would like to recover the 9 GB of disk space occupied by HDRecovery.

Please see following images of current partitions:

[ATTACH=CONFIG]242940[/ATTACH]

[ATTACH=CONFIG]242941[/ATTACH]

My Toshiba laptop is an AMD64 bit OS system with 3.6 GiB of memory.

Will the 12.04 installation automatically use the swap file created by the original "dual boot" 12.10 installation?

My 13.04 is an upgrade.

I have Windows7 running on 13.04 in an Oracle VirtualBox, version 4.2.12 r84980, and everything is working OK.

I have 12.04.2-desktop-amd64.iso installed on a bootable USB and I've tested it.

  It is working OK and I used the USB "trial / test" to obtain the Disk Utility image above.

Any recommendation on what to do next would be greatly appreciated?

Also, I have never "partitioned" a hard drive on any OS, so I am more than a little apprehensive!

Thanks,
Best,
Bill

---

### Post by Bucky Ball on 2013-05-23
*Thread moved to **Installation & Upgrades**.*

As for using existing partitions; if you have an existing /swap (and /home) choose 'Something Else' when installing the second OS then mark /swap and /home to use but NOT ticked to format. That way the new install will use the existing /swap and /home.

The 'Something Else' option gives you basically Gparted. You can have a look in there now in your current install and see what it can do and identify any partitions you want to keep (write them down; sda1, sdb2 or whatever you want). When you are doing the install they will be clearly visible and marked with their mountpoint names so just DON'T TOUCH 'EM! They won't be set to use or format by default (but I always check anyway). Always good to make a plan and write it down before going into this so when you get there you know exactly what you're doing. If you have a good backup, there is nothing to fear. Good luck. ;)

* Just post back if you hit any brickwalls or have other questions.

---

### Post by Rekhillbill on 2013-05-24
Bucky Ball

Ok.  I am on my way.  I used GParted to format the 9.01 GiB HDDRecovery patition to ntfs and now my VirtualBox Windows 7 can see the new /Data patition with about 46.88 MiB of data remaining.  This is a bit confusing, as I thought when you "format" a partition, all the data is removed?  Also, while Windows 7 can "see" the remaining data 13.04 can not, even with show hidden files checked?

I would appreciate understanding in "simple" terms why 13.04 can not see the 46.88 MiB of remaining data?

My concern now is with the Grub.

The Grub still believes Windows 7 is present, when I have already formated the Windows 7 partition to ext4.

I understand from an Ask Unbuntu thread that this is the issue:

> "...Grub2 looks for the Windows boot files for detecting Windows entries.  Though you removed Windows 7, the Windows 7 boot files aren't removed  (which are "Boot" folder and "bootmgr" file). And as Windows 7 boot  files are there, grub2 simply assumes that, there are Windows 7  installation also. Hence the dual entry..."

I understand from the same Ask Unbuntu thread that this is the solution:

> "...Mount the /dev/sda1 drive. *(I assume you can do that very easily*). Then in that drive look for a folder named Boot and a file named bootmgr. Remove both the folder and file. Then run update-grub2 command again..."

My problem is I don't know how to "...mount the /dev/sda1 drive..." so that I can "see" it in 13.04 to remove the folder named Boot and the file named bootmgr?

That option is "whited out" in GParted, when I right click on the /dev/sda1?  I understand from the Help that GParted does not know where to "mount" the /dev/sda1 and "neither do I"?

Also, I am uncertain, if that is really the best approach to removing the presents of Windows 7 boot files from the Grub?

I have 126.17 GiB formated ext4, where Windows 7 was installed, that I would like to divide up between room for the new install of 12.04 and 12.04 /home.

The reason for this is that I read that having a separate partition for the /home protects the data when you upgrade or gives you the option of just installing the new version overwriting the old verions?

Is this what you would recommend?

If not, please give me your suggestions / recommendations?

How much space is recommended for 12.04?  Looking at the 12.04 install would suggest to me that all I would need at a minimum is about 5 GiB?

I would greatly appreciate any help.

Thanks,
Best,
Bill

---

### Post by Bucky Ball on 2013-05-24
Try this:

```
sudo update-grub
```

Reboot. Windows gone?

---

### Post by Rekhillbill on 2013-05-24
I ran the above code in Terminal with the following results:

[ATTACH=CONFIG]242999[/ATTACH]

I then re-booted and the Windows 7 loader was "still" listed as the last option on the Grub on /dev/sda1.

I will say that I had created two other options for booting Windows in lieu of the original Windows 7 Normal Boot.

One was for booting into Windows Safe Mode and the other for booting into Windows Safe Mode wtih Networking.

Both of those boot options were removed with the sudo update-grub code.  But the "original" normal Windows 7 boot remains.

Not sure what to do next.  I am all ready to install 12.04 LTS Precise Pangolin, but I am thinking that is not a good idea with the Windows 7 boot loader still showing up in the Grub?

Please let me have your thoughts?

Thanks,
Bill

---

### Post by Bucky Ball on 2013-05-24
Boot from the LiveCD, launch Gparted, right click any partitions there to make sure they are unmounted (should be by default), delete everything leaving free space only (delete the partitions you don't want and make that free space). Install 12.04.

This can also be achieved during install. When you get to the partitioning section of the install choose 'Something Else'. You can wipe everything in there and then create the partitions you are going to need (make a plan). A simple setup:

/ = OS, 15-20Gb fine;
/home = Your stuff, large as you like;
/swap = 2Gb fine.

Try that.

---

### Post by fantab on 2013-05-25
Using Gparted DELETE ALL NTFS Partitions. If you have saved DATA on it then BACK it UP. Since you will be using only Ubuntu/LInux, there is no point having NTFS partitions around. If I were you I would back up all my data and recreate all the partitions just the way I want it and reinstall Ubuntu.

I dual boot 12.04 and 13.10 and here's how my partitons look:
20GB Primary Ext4 13.10 /
20GB Primary Ext4 12.04 /
4GB  Primary SWAP
All the remaing GB Primary Ext4 for myDATA.

---

### Post by Rekhillbill on 2013-05-25
fantab,

That sounds like the best approach.

But, I' ve spent quite a bit of time getting the Oracle Virtualbox to work with Windows 7 installed and working OK, too.

I am not anxious to have to do that all over again.

The only reason for keeping the ntfs where the HDDRecover was loacted in the 9.01 GiB partition ( /dev/sda3 ) at the far right side was to have a ntfs data partition for Windows 7.

The only reason for keeping the 1.46 GiB ntfs partition ( /dev/sda1 ) at the far left was that it contained the boot data for the Grub?

I may not understand correctly where the boot data for the Grub is keeped?

Is the boot data for the Grub located in /home?

If that 1.46 GiB ntfs partition ( /dev/sda1 ) is only the boot for Windows 7, then I can delete it, right?

Since I formated /dev/sda2, the former Windows 7 partition to ext4, I would no longer need to keep the 1.46 GiB ntfs Window 7 boot?

After deleting the 1.46 GiB ntfs (boot) and running sudo update-grub, I sould have a Grub that does not include a Windows boot loader?

Please confirm that my "assumptions" above are correct?

Thanks,
Bill

---

### Post by fantab on 2013-05-25
Like I said, since you will be removing Windows7, which must have come pre-installed, there is no point in any Windows related information on that disk. You can safely remove all those NTFS. Its lousy filesystem anyway.

The Ubuntu BOOT information will be saved in '/' partition with the rest of the system files.

I don't use Virtual Box of any kind but I am sure it can be easily be setup in Ubuntu. If you want to use Virtual Box or such then increase the Ubuntu partition size from 20GB to 30GB.

---

### Post by Bucky Ball on 2013-05-25
@fantab: Setup looks good but you've tied your hands a bit if another install takes your fancy by having four primary partitions. You know Ubuntu will work fine inside an extended? ;)

(Sorry, off-topic. #-o)

---

### Post by fantab on 2013-05-25
> **Bucky Ball said:**
> @fantab: Setup looks good but you've tied your hands a bit if another install takes your fancy by having four primary partitions. You know Ubuntu will work fine inside an extended? ;)

(Sorry, off-topic. #-o)

I have three machines. That was just a laptop with one HDD. ;-)

@Rekhillbill: You can make the last partition as EXTENDED and within it create a LOGICAL partition with 'All the remaining GB'.

---

### Post by Rekhillbill on 2013-05-26
fantab & Bucky Ball

I have installed 12.04.2 Precise Pangolin from an USB ubuntu-12.04.2-desktop-amd64.iso.

I used the "Something Else" option to select /dev/sda2 as the install device.

I then went back to the "three" options for install and selected "Install 12.04 along side 13.04 in a dual boot"

The installation went smoothly except for the sudo update-grub.

When I needed to reboot to finalize the installation of 12.04 the Grub did not include the boot loader for 12.04.  So, after booting up 13.04, I immediately ran sudo update-grub and rebooted again.  Actually I needed to "manually" turn off the computer, but when I started again the Grub included the 12.04 boot loader and all went well with finalizing and updating of 12.04.

13.04 Raring Ringtail is working OK, too.

I am writing this post from 13.04.  Please see the following screen pic for the location of 12.04 ( /dev/sda 7 ) and the location of 13.04 ( /dev/sda5 ):

[ATTACH=CONFIG]243054[/ATTACH]


Now I have an issue with gksu nautilus in attempting to give myself ( bill ) permission to use the 1.46 GiB /dev/sda1, 98 GiB /dev/sda2 and the 9.01 /dev/sda3 devises so that I can read / write data to them?

Please see the following screen pic for the gksu natulilus error:

[ATTACH=CONFIG]243055[/ATTACH]


Any suggestion of what to do to give myself ( bill ) permission to read / write to the folders would be appreacited?

Thanks,
Bill

---

### Post by Rekhillbill on 2013-05-26
I forgot to mention another selection option while I was in the "Something Else" installation option.

I resized the space for 12.04 to about 30 GiB.  The remainder of /dev/sda2 was shown at about 105 GiB.

Thanks,
Best,
Bill

---

### Post by Rekhillbill on 2013-05-26
Another point, too, concerns deleting the 1.46 GiB /dev/sda1 and the 9.01 GiB /dev/sda3 partitions.

GParted Help suggested that if I deleted a partition, I might have a problem with the Grub during boot.

The Help warned that I might not be able to boot the OS again, so I decided to just re-format the partitions from ntfs to ext4.

Maybe this was not necessary?

Maybe I can still delete these two partitions?

But, since this is my "first" attempt at doing anything with partitions either in Windows or Ubuntu, I though is a good idea to play it safe.

I would appreciate any comments on this subject, too.

Thanks again,
Best,
Bill

---

### Post by Bucky Ball on 2013-05-26
You've come a long way. If you delete the partition with the OS you will have problems but the other two should be fine. Again, they need to be unmounted to delete them so best to do it using Gparted on the LiveCD.

Why do you want to run Nautilus as root? But yea, that is an issue. You might be better off posting about that in a new thread with a descriptive title. (We are 15 posts deep in a thread with an unrelated title.) Post a link back here if you like.

---

### Post by Rekhillbill on 2013-05-26
Thanks again Buck Ball, I'll mark this Thread Solved and open another for the other issues with a link back.

But, I am going to do a bit of "research" on permissions first.

Best,
Bill

---

### Post by Rekhillbill on 2013-05-28
[SIZE=3]In response to Bucky Ball's following question:
[/SIZE]
> [SIZE=3]Why do you want to run Nautilus as root? But yea, that is an issue. You  might be better off posting about that in a new thread with a  descriptive title. (We are 15 posts deep in a thread with an unrelated  title.) Post a link back here if you like.         [/SIZE][SIZE=3]

Please see the  following thread: 

[http://ubuntuforums.org/showthread.php?t=2149100](http://ubuntuforums.org/showthread.php?t=2149100)

After some research, I found that I did not have to run / use [ gksu nautilus ] to change the permissions for /dev/sda1, 2 & 3.[/SIZE] :P

[SIZE=3]Best,
Bill[/SIZE]

---

### Post by Bucky Ball on 2013-05-28
Yep, sudo in and be root for that one command or session. Not good to be root permanently. Unsafe.

Please refrain from using large text in your posts. Stick to the defaults (unless you have an excellent reason). Please note, from the CoC:

> Use color and font properties for highlighting portions of your text, and not for all of the text in your post. Please use the default font color and properties unless you need to highlight or draw attention to a part of your post. ALL CAPS is interpreted as screaming. [size=2][COLOR=pink]Funky[/size][/COLOR] non-uniform font size/color is difficult for those who are visually impaired. _*If you are having problems with reading the font, please adjust your browser.*_

If you have vision issues please adjust your browser. ;)

---

