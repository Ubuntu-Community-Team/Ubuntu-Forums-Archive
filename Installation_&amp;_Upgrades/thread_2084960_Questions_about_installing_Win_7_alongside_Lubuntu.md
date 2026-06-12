---
title: "Questions about installing Win 7 alongside Lubuntu 12.10"
date: 2012-11-16
forum: Installation &amp; Upgrades
---

### Post by redbikemaster on 2012-11-16
I had several questions regarding what the title of this thread says. I have a machine with a (SATA) 1TB hard drive running Lubuntu 12.10. It has never had Windows on it, so no recovery disc. I already have a Win 7 install disc.

My questions are:
1. I have ~190GB of data on the drive under Lubuntu. What is the recommended way to back this data up? The biggest hard drive I have lying around is 80GB, and is IDE. I really don't want to have to burn a bunch of DVDs (190/4.7=40.425!) I don't want to have to burn 41 DVDs! Also, my internet connection is junk, so backing up over a network isn't an option, really.
2. Obviously I'd need to create a partition that is NTFS since my drive is currently Ext4. Can I do that without disturbing the Lubuntu side of things?
3. How do I get GRUB back up and running? I can't seem to discern exactly how to do that. Also, if I do everything, and I only see Windows at first, do I just need to reinstall GRUB?

I can't think of any other questions right now, but if I do, I'll edit this post to reflect the additions.

Thanks guys (and gals)!

---

### Post by oldfred on 2012-11-17
You should have a way to backup if you data is important. Even if it is another drive. I like to have Windows in one drive and Ubuntu in the other and copy/backup data from each to the other.

Windows default install is two partitions a hidden 100MB boot/repair partition and the main install. The separate boot partition is primarily if you want to encrypt your main install c: and may let you get to a repair console if main install is corrupted. But you can install to one partition. Just make the repairCD so you have another way to repair Windows when needed.

Windows will only boot, install to , or repair boot of a primary (sda1 thru sda4) partition formated NTFS with the boot flag if installing in BIOS/MBR mode. 

Lot different if efi. If you happen to have drive formarted to gpt partitioning Windows will only boot with UEFI or you have to totally reformat to MBR(msdos) and that erases everything. There may be a way to convert.

You should just need to reinstall the grub2 boot loader to the MBR.

You need to have the current Lubuntu liveCD to reinstall grub2. If you want a gui use Boot-Repair.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.Install in Ubuntu liveCD or USB or:
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

    
Ways to install grub2 to MBR from liveCD.
       [https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

            How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2) by talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

### Post by redbikemaster on 2012-11-17
Stink.

I certainly don't have money for another drive right now (computer parts in use now were bought during a time of prosperity [read: before I started college]).

Guess I should wait then. Thanks though.

---

### Post by Mr_JMM on 2012-11-17
I've just done some rejigging of a drive so I'll chip in here with how I did this without another drive to back up to (actually, I was too lazy as it's a network drive and would have taken too long).

It sounds like you have 2 or 3 partitons as it's only got Lubuntu on it.

Proceed as follows (but note that loss of info, whilst remote is a possibility):
1. Plan out your partitions now. THe basic will be:
[LIST]
[*]Windows Boot (as per OldFred) - sda1
[*]Windows - sda2
[*]Extended - Rest of disk - sda3
[*]Linux Swap - same as you have now though anything from 2GB to (RAM + 1GB), your preference.
[*]Lubuntu /root (Logical, inside Extended - sda5)
[*]Lubuntu /home (Logical inside Extended - sda6)
[/LIST]

OR

[LIST]
[*]Windows Boot (as per OldFred) - sda1
[*]Windows - sda2
[*]Linux swap or root - sda3
[*]Extended - Rest of disk - sda4
[*]Linux Swap* or root, whatever isn't sda3 - sda5
[*]Lubuntu /home - sda6
[/LIST]
*same as you have now though anything from 2GB to (RAM + 1GB), your preference.
Some people prefer to put swap at the end of the disk, adjust accordingly.

[EDIT] As I don't know how windows will want the partitions created here's an idea: Just create the one windows partition, format it as ntfs so you have that, and your extended partitions (with your data in it). Now install windows and point it to the ntfs partition and let it divide it up as it sees fit. This may not work as expected though. I've never installed windows 7. Be cautious here.
[EDIT 2] It seems that you can choose not to have this Windows boot partition. Simply do as above, create ONE partition for ntfs and windows will not create the smaller one. Apparently.

If you want to share data you might have to use Fat32 for /home so windows can see it or install something that allows windows to read/write ext4/ partitions. Or, just to be even more confusing, have yet another partition inside sda4 and split home and data up. Home as ext4, only needs to be 5-10GB but whatever you're comfortable with and data as the rest formatted as fat32. You can use samba to link everything up. Of course, these last steps aren't an issue if you're separating windows data (pictures, documents etc.) from Linux ones.

Now the complicated bit:
1. shrink the partition on the drive
2. Create the new extended partition.
3. Create a new home partition at end of drive.
4. Copy all data from current home to new home.
5. You can now delete the original and create the 2 primary partitions for windows (you can create the 3rd as swap or Lununtu root and just have home (and swap or root) in exended.
6. Resize the new extended partition to fit the space if required.
7. Edit any other partitions as required.
I recommend you use a live Gparted disk or Parted Magic live USB to do all of this and allow a couple of hours at least (moving data and moving a partition can take a long time).

Clear as mud! Sorry, I know this is convaluted but it allows you to keep the data without the ability to back it up to another drive. This is considerably easier with a blank drive.

---

### Post by redbikemaster on 2012-11-17
Sorry, if I'm being ridiculous, I've just never done this and don't want to foul everything up. 
What is meant by Logical inside Extended?

On Step 1, does that mean the partition I am currently running on?

I appreciate all the help.

---

### Post by Mr_JMM on 2012-11-17
I've just edited my post to give better explinations...

A drive (most) can only have a maximum of 4 partitions which are either 4 primary (default) or three default followed by an extended. An extended partition can have lots (over a 100) smaller partitions within it called Logical partitions.
When you create the partitions, GParted will give you the choice of selecting primary (your first 3) and extended (the forth).
Extended partitions have to be the last partition but the order of the logical partitions within it is entirely up to you.
The simplest is my first layout list so the extended partition (in this case the 3rd) is your "Lubuntu" partition and will contain /swap, /root and /home (and /data if you choose). (I'll see if I can throw up an image for you in a bit)

Just so we can be specific can you past the result of ```
sudo fdisk -l
``` ?

[EDIT] I've put an image of one of my spare systems to show you. It's a bit messy and the partition numbers are yet to be adjusted to be neater. You can see that the first three are dedicted to F'ing Dell and Windows. You're final system will just have the first two as windows (I gather from OldFred's post that Windows 7 needs a 100MB boot partition). (just thought of another way, will update my post again in a minute).

You can see that sda4 is "extended" and sda 5-11 sit inside it.

---

### Post by redbikemaster on 2012-11-17
Thanks for the quick help.

Here's the code output:
```

redbikemaster@Beast:~$ sudo fdisk -l
[sudo] password for redbikemaster: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00005f4e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1936752639   968375296   83  Linux
/dev/sda2      1936754686  1953523711     8384513    5  Extended
/dev/sda5      1936754688  1953523711     8384512   82  Linux swap / Solaris

```

This is starting to make sense now. I really appreciate it.

---

### Post by Mr_JMM on 2012-11-17
Ok, that makes things clearer, thank you.

BTW: Are you ok to reinstall Lubuntu? If not, let me know and I'll modify the following but it does get trickier.

Wait, something looks odd. You have an extended partition already. This is great, it makes things a little easier, however it looks like the only thing in it is the swap partition in which case is home and root all on sda1? Can you clarify that for me?

I'll carry on based on that being the case:
1. Shrink sda1 down to around 10GB larger than the amount it's currently showing as used. From what you said that'd ba around 170GB.
2. Assuming the ONLY thing in the extended partition (sda2) is swap then just delete the whole thing - it's easier.
3. Create a new extended partition. If you know how big you want the windows partition to be and it's bigger than 180GB (or whatever you shrink sda1 to) then great, simply deduct it from 1000 and that's how big you make the extended.
4. Inside the extended create your other partitions. Depending on what you want to do with root, home. data etc you may be adding a third partition (primary) between sda1 and the extended partition.
5. Once you've done this you can open a file browser (this is where a LiveUSB of Parted Magic is fantastic and you really should do this if you can, a dvd will work too) to copy all your picture, documents, music etc folders from sda1 to the newly created home / data partition. This will take a long time. If you're on my time line (US currently till Xmas) then you may want to let it run over night.
6. Once files are copied you can delete sda1.
7. Create a new primary partion at the beginning of the disk and format as ntfs.
If your desired windows partition size is smaller than 170GB (based on your usage stated) then you'll have a gap. You can either make life easy and just give windows all the space or you'll have to expand the extended partition to fit. This will again take SEVERAL hours, best guess would be 3-4 hours.
8. Once done, install windows remembering to ensure it only uses the allocated ntfs space (it's important to format this first. If you want the windows boot / recovery partition then don't format this space (don't create an NTFS partition, leave it as unallocated but make sure you have only used two partitions for linux use including the extended).
9. Once installed, reinstall Lubuntu allocated the partitions for /root and /home. Do NOT check the format box for the home partition otherwise it'll erase everything.

It's 1am here so I may be going to bed soon. I'll help out tomight as much as possible otherwise I'll check in tomorrow. I've subscribed to this thread.

TO EVERYONE ELSE:
If I've missed something or there's a quirk about Windows 7 that is relevant then PLEASE jump in.

---

### Post by redbikemaster on 2012-11-17
> **Mr_JMM said:**
> Ok, that makes things clearer, thank you.

BTW: Are you ok to reinstall Lubuntu? If not, let me know and I'll modify the following but it does get trickier.

Wait, something looks odd. You have an extended partition already. This is great, it makes things a little easier, however it looks like the only thing in it is the swap partition in which case is home and root all on sda1? Can you clarify that for me?

It's 1am here so I may be going to bed soon. I'll help out tomight as much as possible otherwise I'll check in tomorrow. I've subscribed to this thread.

TO EVERYONE ELSE:
If I've missed something or there's a quirk about Windows 7 that is relevant then PLEASE jump in.

The only thing I have about reinstalling Lubuntu is I don't want to lose my apps and config files, but I guess those would be backed up?

I installed Lubuntu using all the default settings, so I have no explanation for the anomaly you spotted.
*Here's a photo of my drive in Disks*
[ATTACH]227291[/ATTACH]


I'm in the Mountain Time Zone, so it's midnight here. This doesn't need to be done tonight, so go ahead and head to bed. I'll be doing the same.

---

### Post by Mr_JMM on 2012-11-17
Whilst not impossible to avoid, assume you're going to be reinstalling the apps. The settings for the apps are safe (they're stored in /home/yourUserName folder (often referred to simply as home).

In order to avoid that you will have to manually edit files changing the UUID's and other info so that Lubuntu can find itself after we do all this and trust me, it be one very lost little puppy.

There are guides around here that will tell you how you can back up the apps you've added and provide scripts so the install is automated. This will make it a lot less painful and only minor tweaking will be required. Forgive me, in an effort not to confuse this thread any more than I have, can I let you search that info out?

If you're up for it, it might be worth making a start and getting to the stage where you're moving files as you can let that run over night. Are you able to make a DVD or live usb of Parted Magic? You can use the Lubuntu DVD as well, I just prefer Parted Magic on a USB.

If I don't get back here again tonight, will catch you tomorrow.

---

### Post by redbikemaster on 2012-11-17
No prob, I'll find those.

See you tomorrow.

---

### Post by oldfred on 2012-11-17
To get a list of apps.

       from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

---

### Post by redbikemaster on 2012-11-17
That is officially awesome. Thanks, oldfred and lovinglinux!

---

