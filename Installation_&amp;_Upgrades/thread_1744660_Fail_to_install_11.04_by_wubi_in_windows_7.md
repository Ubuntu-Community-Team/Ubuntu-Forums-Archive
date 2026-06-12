---
title: "Fail to install 11.04 by wubi in windows 7"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by dadaj on 2011-04-30
I plan to learning ubuntu 11.04  with wubi feature to be dual boot with windows 7.  Thanks the great idea of wubi as it will not harm my computer  information. I downloaded the ubuntu 11.04 amd64 CD on 28th Apr and  attempted to install it with wubi in windows 7. however, the  installation process would be stopped after the files copied to  destination from CD or even from VirtualCD mounted by deamon.

I would appreciate whatever advice for checking why the process to be stopped at that point.

---

### Post by Jasonix on 2011-04-30
> **dadaj said:**
> I plan to learning ubuntu 11.04  with wubi feature to be dual boot with windows 7.  Thanks the great idea of wubi as it will not harm my computer  information. I downloaded the ubuntu 11.04 amd64 CD on 28th Apr and  attempted to install it with wubi in windows 7. however, the  installation process would be stopped after the files copied to  destination from CD or even from VirtualCD mounted by deamon.

I would appreciate whatever advice for checking why the process to be stopped at that point.
What do you mean? When it finishes, it will ask to reboot and you do as told and enter ubuntu and it will finish installation.

---

### Post by Paddy Landau on 2011-04-30
I wonder if you are confusing two things.

You install Wubi in Windows as if it were just another Windows program. Get the [Wubi download]("http://www.ubuntu.com/download/ubuntu/windows-installer") from the website. You do not download a CD to do this.

On the other hand, if you install Ubuntu, then you have to [download and burn a CD]("http://www.ubuntu.com/download/ubuntu/download") (or USB stick).

Wubi is great for learning Ubuntu. But, I have to warn you that it is both slow and unreliable, so do not depend on it for long-term use.

---

### Post by dadaj on 2011-04-30
> **Jasonix said:**
> What do you mean? When it finishes, it will ask to reboot and you do as told and enter ubuntu and it will finish installation.

Jasonix: 

I mean the installation process did not go through the whole process to the end of the reboot notification windows appeared.

Thanks for your quick reply..:)

---

### Post by rvchari on 2011-04-30
> **dadaj said:**
> I plan to learning ubuntu 11.04  with wubi feature to be dual boot with windows 7.  Thanks the great idea of wubi as it will not harm my computer  information. I downloaded the ubuntu 11.04 amd64 CD on 28th Apr and  attempted to install it with wubi in windows 7. however, the  installation process would be stopped after the files copied to  destination from CD or even from VirtualCD mounted by deamon.

I would appreciate whatever advice for checking why the process to be stopped at that point.

if u really wish to learn natty then use usb stick to learn it. i am a long time linux user and i have maverick running perfectly. still on natty release date, i downloaded the iso and created a usb live, now i am getting the feel of natty with its new unity interface thru usb without disturbing my maverick. the day i feel natty will run all my current programs with ease, i ll go for clean install...
till then usb live stick is another good way to learn...

---

### Post by dadaj on 2011-04-30
> **Paddy Landau said:**
> I wonder if you are confusing two things.

You install Wubi in Windows as if it were just another Windows program. Get the [Wubi download]("http://www.ubuntu.com/download/ubuntu/windows-installer") from the website. You do not download a CD to do this.

On the other hand, if you install Ubuntu, then you have to [download and burn a CD]("http://www.ubuntu.com/download/ubuntu/download") (or USB stick).

Wubi is great for learning Ubuntu. But, I have to warn you that it is both slow and unreliable, so do not depend on it for long-term use.

Paddy Landau:

I have attempted to install ubuntu 11.04 to a partition called driver G: with a CD, but the installation process did not provide a option to dual boot with windows 7 or let me choice the partition that i planned to install ubuntu.  and then i try using wubi but it also did not work for my computer.

Thanks for you advice, detail and helpful

---

### Post by Paddy Landau on 2011-04-30
> **rvchari said:**
> ... use usb stick to learn it.
USB stick is fine, but it is sooooo slow.

> **dadaj said:**
> I have attempted to install ubuntu 11.04 to a partition called driver G: with a CD...
There is no such thing as a partition called driver G:. I'm wondering what you mean?

A hard disk or USB drive is split into *partitions*. Each partition can contain something different. For example, one partition may contain Windows, another may contain just data, another may contain Mac OSX, and another may contain Ubuntu.

Usually, a USB disk has only one partition. Modern Windows computers usually have three partitions: one for the Windows recovery (which Windows hides from you), one for the Windows system (which Windows usually calls "C:"), and one for the Windows data (which Windows usually calls "D:").

Windows users know these partitions as C:, D:, E:, ... However, those are "logical" names (Ubuntu also gives them logical names). Their real names are based on the physical drive.

Typically -- but there are exceptions -- the first physical drive is called **sda**. The first partition on it is called sda1, the second sda2, and so on. The second physical drive (which could, for example, be a USB stick) is called **sdb**. The first partition on it is called sdb1, the next sdb2, and so on. The next drive is called **sdc**, and so on.

If you wish to install Ubuntu (instead of Wubi), I suggest you do this:

[LIST=1]
[*]Boot from a Live CD (or USB stick if you have one, because it's faster). Try out Ubuntu to see whether it works. Can you access the Internet, for example?
[*]If it all works, then you can install Ubuntu on your computer. It will shrink the partition where Windows is stored, and create a new partition where it will install itself. This will allow you to dual boot. (This is the easiest way, if Wubi does not work for you. You can manually decide how to partition your drive, but you need to know what you're doing to do that.)
[/LIST]
If you have any problems with step 1 or step 2, post again.

---

### Post by dadaj on 2011-04-30
> **rvchari said:**
> if u really wish to learn natty then use usb stick to learn it. i am a long time linux user and i have maverick running perfectly. still on natty release date, i downloaded the iso and created a usb live, now i am getting the feel of natty with its new unity interface thru usb without disturbing my maverick. the day i feel natty will run all my current programs with ease, i ll go for clean install...
till then usb live stick is another good way to learn...

Thanks rvchari:

It seem quite interesting that using usb stick without affecting the original information system. two question, can i share the data of windows 7? and how large of the usb space i should prepare for the smooth running of natty?

more information will be appreciated

Thanks you for sharing great experience. nice and smart advice ^^

---

### Post by dadaj on 2011-04-30
> **Paddy Landau said:**
> USB stick is fine, but it is sooooo slow.


There is no such thing as a partition called driver G:. I'm wondering what you mean?

A hard disk or USB drive is split into *partitions*. Each partition can contain something different. For example, one partition may contain Windows, another may contain just data, another may contain Mac OSX, and another may contain Ubuntu.

Usually, a USB disk has only one partition. Modern Windows computers usually have three partitions: one for the Windows recovery (which Windows hides from you), one for the Windows system (which Windows usually calls "C:"), and one for the Windows data (which Windows usually calls "D:").

Windows users know these partitions as C:, D:, E:, ... However, those are "logical" names (Ubuntu also gives them logical names). Their real names are based on the physical drive.

Typically -- but there are exceptions -- the first physical drive is called **sda**. The first partition on it is called sda1, the second sda2, and so on. The second physical drive (which could, for example, be a USB stick) is called **sdb**. The first partition on it is called sdb1, the next sdb2, and so on. The next drive is called **sdc**, and so on.

If you wish to install Ubuntu (instead of Wubi), I suggest you do this:

[LIST=1]
[*]Boot from a Live CD (or USB stick if you have one, because it's faster). Try out Ubuntu to see whether it works. Can you access the Internet, for example?
[*]If it all works, then you can install Ubuntu on your computer. It will shrink the partition where Windows is stored, and create a new partition where it will install itself. This will allow you to dual boot. (This is the easiest way, if Wubi does not work for you. You can manually decide how to partition your drive, but you need to know what you're doing to do that.)
[/LIST]
If you have any problems with step 1 or step 2, post again.

Thanks Paddy Landau:

You are very nice and patient man. 

For  first step, I use the option of the ubuntu 11.04 amd64 CD to try ubuntu and it start natty. My notebook can access the internet through wireless router after opening ubuntu desktop. Firefox can access internet. 

For second step, When I choice to install ubuntu, it provide two options for me. one is "replace windows 7" that mean erase all data of my 250GB harddisk. the another one is "other" that allow me to allocate how large the space of the partitions. 

There are four partitions when I choice "other": 

/dev/sda1            1MB 
/dev/sda2  ntfs   104MB 
/dev/sda3 ntfs 692914MB                    (windows 7 is installed in this partition)
/dev/sda4 ntfs 187037 MB                 (I use this partition to save data but the partition size should be 130GB, the other free space is formatted and assigned to be G:  my goal is install ubuntu in this free space)

which partition I should choice for "Device for boot loader installation"?

---

### Post by Paddy Landau on 2011-04-30
> **dadaj said:**
> ... can i share the data of windows 7?
Ubuntu will easily read and write any FAT32 and NTFS system (note that Windows uses NTFS).

However, Windows cannot access ext4 (Ubuntu uses ext4).

So, if you store data on an NTFS partition, both systems can read and write it. Your Ubuntu system will be able to access your Windows system, but your Windows system will not be able to access your Ubuntu system.

> **dadaj said:**
> how large of the usb space i should prepare for the smooth running of natty?
A Live USB of just 1Gb will run OK, and you can install Ubuntu from it. However, to use it as a stand-alone system (which I don't really recommend), you would be advised to get a USB of at least 8Gb.

> **dadaj said:**
> There are four partitions when I choice "other": 

/dev/sda1            1MB 
/dev/sda2  ntfs   104MB 
/dev/sda3 ntfs 692914MB                    (windows 7 is installed in this partition)
/dev/sda4 ntfs 187037 MB                 (I use this partition to save data but the partition size should be 130GB, the other free space is formatted and assigned to be G:  my goal is install ubuntu in this free space)

which partition I should choice for "Device for boot loader installation"?

[LIST]
[*]/dev/sda1: This is probably something to do with Windows recovery. Do not touch it.
[*]/dev/sda2: Also probably something to do with Windows recover. Do not touch it.
[*]/dev/sda3: As you say, Windows 7.
[*]/dev/sda4: This creates problems. Let me explain...
[/LIST]
For historical reasons, a hard drive can have only four partitions. Ouch!

But, there is a way around this.

A partition can be of three different types.

[LIST=1]
[*]Primary: A primary partition is just a partition.
[*]Extended: An extended partition is a special partition that can contain other partitions.
[*]Logical: A logical partition is just a partition, but inside an extended partition.
[/LIST]
So, you can have as many partitions as you like by using an extended partition.

Because your hard drive already has four partitions -- they are probably primary partitions -- you will need to change one of them to extended.

But, before we proceed, I need to check whether this is really the case.

So, please:

[LIST=1]
[*]Boot into Ubuntu from your Live CD (or USB).
[*]Open a terminal (sorry, I don't know how to do that from 11.04 -- it has changed since 10.04, which I use. I will find out and post here).
[*]Type the following command:
```
sudo parted --list
```
[*]Copy the results and post them here.
[/LIST]

Once we know how your disk is structured, we can help you make the required changes.

---

### Post by Paddy Landau on 2011-04-30
I said I'd post when I found out how to open a terminal in 11.04.

[LIST=1]
[*]On the launcher bar (the sidebar on the left), look for the grey icon with a magnifying glass and a plus-sign.
[*]Click it.
[*]Start typing "terminal" (just the first "t" will be enough).
[*]Click on the icon saying "Terminal".
[/LIST]

When you have entered the command [FONT=Courier New]sudo parted --list[/FONT] you can copy the results in order to paste them.

[LIST=1]
[*]Highlight the results with your mouse.
[*]Right-click the results and select "Copy" (do not press Ctrl-C, because that has a special meaning in Terminal).
[*]Find Firefox in the launcher bar and click it.
[*]Come back to this thread, sign in, and post the results. (Hint: when pasting the results, highlight the results and click the "#" button to place "code" codes around the results. This makes it easier for us to read.)
[/LIST]

---

### Post by bcbc on 2011-04-30
> **dadaj said:**
> Thanks Paddy Landau:

You are very nice and patient man. 

For  first step, I use the option of the ubuntu 11.04 amd64 CD to try ubuntu and it start natty. My notebook can access the internet through wireless router after opening ubuntu desktop. Firefox can access internet. 

For second step, When I choice to install ubuntu, it provide two options for me. one is "replace windows 7" that mean erase all data of my 250GB harddisk. the another one is "other" that allow me to allocate how large the space of the partitions. 

There are four partitions when I choice "other": 

/dev/sda1            1MB 
/dev/sda2  ntfs   104MB 
/dev/sda3 ntfs 692914MB                    (windows 7 is installed in this partition)
[COLOR="Red"]/dev/sda4 ntfs 187037 MB                 (I use this partition to save data but the partition size should be 130GB, the other free space is formatted and assigned to be G:[/COLOR]  my goal is install ubuntu in this free space)

which partition I should choice for "Device for boot loader installation"?
If windows has assigned two "drives" to /dev/sda4 then likely you have setup dynamic drives in windows. These are a windows only logical volume, not accessible by Ubuntu (with or without Wubi).

You can check the wubi log file %temp%\wubi-11.04-rev211.log and it should show an error after it runs bcdedit if you are trying to install to a dynamic drive.

---

### Post by dadaj on 2011-04-30
> **Paddy Landau said:**
> I said I'd post when I found out how to open a terminal in 11.04.

[LIST=1]
[*]On the launcher bar (the sidebar on the left), look for the grey icon with a magnifying glass and a plus-sign.
[*]Click it.
[*]Start typing "terminal" (just the first "t" will be enough).
[*]Click on the icon saying "Terminal".
[/LIST]

When you have entered the command [FONT=Courier New]sudo parted --list[/FONT] you can copy the results in order to paste them.

[LIST=1]
[*]Highlight the results with your mouse.
[*]Right-click the results and select "Copy" (do not press Ctrl-C, because that has a special meaning in Terminal).
[*]Find Firefox in the launcher bar and click it.
[*]Come back to this thread, sign in, and post the results. (Hint: when pasting the results, highlight the results and click the "#" button to place "code" codes around the results. This makes it easier for us to read.)
[/LIST]


Thanks Paddy Landau:

ubuntu@ubuntu:~$ sudo parted --list
Model: ATA FUJITSU MHZ2250B (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  1049kB  1016kB  primary
 2      1049kB  106MB   105MB   primary  ntfs         boot
 3      106MB   63.0GB  62.9GB  primary  ntfs
 4      63.0GB  250GB   187GB   primary  ntfs


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label 

Sorry for late reply

---

### Post by dadaj on 2011-04-30
> **bcbc said:**
> If windows has assigned two "drives" to /dev/sda4 then likely you have setup dynamic drives in windows. These are a windows only logical volume, not accessible by Ubuntu (with or without Wubi).

You can check the wubi log file %temp%\wubi-11.04-rev211.log and it should show an error after it runs bcdedit if you are trying to install to a dynamic drive.

Thanks bcbc:

I will check it later

---

### Post by Paddy Landau on 2011-05-01
Right. You will need to shrink sda4 to 130Gb, then create a new partition to hold Ubuntu in the remaining 57Gb.

However, because of the limit of 4 partitions per drive, you need to  create an extended partition, moving sda4 into it. Although simple, this requires a few steps (sorry, it's a hardware limitation and there's no way around it).

You do not want to mess  with sda1, sda2 or sda3.

The following steps may seem complicated. That's because of the limit of four partitions on a disk. But it isn't complicated. Just follow the steps.

**You cannot do this without making a backup.**

We'll do this step by step.

[LIST]
[*]The most important step: **Back up**.
[/LIST]
[INDENT]
[LIST=1]
[*]Back up your data on sda4 (probably your D: drive in Windows).
[*]Just in case of mistakes, also back up all your other data.
[*]Check that your backup really does contain all your data, especially the data on sda4.
[*]You may need to investigate the Windows logical G: drive that bcbc mentioned; if necessary, get rid of it. (I have not come across these Windows logical drives before, so I cannot advise you on it.)
[/LIST]
[/INDENT]
[LIST]
[*]Adjust your partitions (replace sda4 with an extended partition; create three new logical partitions inside it). Note: If you make a mess-up, click the big Undo button. All these changes are reversible *until* you press Apply; after that you can't undo.
[/LIST]
[INDENT]
[LIST=1]
[*]Boot from your Live CD (or USB).
[*]Start GParted (click on the Applications button; start typing "gparted"; click it to start).
[*]You will see your partitions listed.
[*]Delete /dev/sda4:
[LIST]
[*]Right-click /dev/sda4 and select *Delete*.
[/LIST]
 
[*]Create an extended partition to hold the new partitions:
[LIST]
[*]From the menu, choose *Partition > New*.
[*]*Free space preceding*: zero
*New size*: the maximum you can
*Create as*: Extended Partition
*Label*: anything you like (it's for your information only).
[*]Add.
[/LIST]
 
[*]Create a replacement for your old sda4:
[LIST]
[*]Right-click the new extended partition and select *New*.
[*]*Free space preceding*: zero
*New size*: 130000 MiB
*Create as*: Logical Partition
*Filesystem*: **ntfs**
*Label*: anything you like (this will be your data partition)
[*]Add
[/LIST]
 
[*]Create your Ubuntu partition:
[LIST]
[*]Right-click the new extended partition and select *New*.
[*]*Free space preceding*: zero
  *Free Space Following*: the size of your computer's RAM in MB (e.g. if you have 4Gb RAM, enter 4000)
  *Create as*: Logical Partition
*Filesystem*: **ext4**
  *Label*: anything you like (this is for your 130Gb partition)
[*]Add
[/LIST]
 
[*]Create Ubuntu's swap space:
[LIST]
[*]Right-click the new extended partition and select *New*.
[*]*Free space preceding*: zero
  *New Size*: the maximum you can
  *Create as*: Logical Partition
*Filesystem*: **linux-swap**
  *Label*: Swap
[*]Add
[/LIST]
 
[*]Apply the changes:
[LIST]
[*]Press the big Apply button.
[/LIST]
 
[/LIST]
[/INDENT]
[LIST]
[*]Restore your data
[/LIST]
[INDENT]
[LIST=1]
[*]Boot into Windows.
[*]Reboot (Windows often needs a double-boot after changing partitions.)
[*]Restore your data onto your newly-changed partition (probably D: drive).
[/LIST]
[/INDENT]Finally, you can install Ubuntu. When you do so, you will need to choose your partitions **manually**, not automatically. Be sure to use the **ext4** partition for Ubuntu; and use the **linux-swap** partition for the swap area. Please post back if you're not sure how to go about it.

---

### Post by dadaj on 2011-05-01
> **Paddy Landau said:**
> Right. You will need to shrink sda4 to 130Gb, then create a new partition to hold Ubuntu in the remaining 57Gb.

However, because of the limit of 4 partitions per drive, you need to  create an extended partition, moving sda4 into it. Although simple, this requires a few steps (sorry, it's a hardware limitation and there's no way around it).

You do not want to mess  with sda1, sda2 or sda3.

The following steps may seem complicated. That's because of the limit of four partitions on a disk. But it isn't complicated. Just follow the steps.

**You cannot do this without making a backup.**

We'll do this step by step.

[LIST]
[*]The most important step: **Back up**.
[/LIST]
[INDENT]
[LIST=1]
[*]Back up your data on sda4 (probably your D: drive in Windows).
[*]Just in case of mistakes, also back up all your other data.
[*]Check that your backup really does contain all your data, especially the data on sda4.
[*]You may need to investigate the Windows logical G: drive that bcbc mentioned; if necessary, get rid of it. (I have not come across these Windows logical drives before, so I cannot advise you on it.)
[/LIST]
[/INDENT]
[LIST]
[*]Adjust your partitions (replace sda4 with an extended partition; create three new logical partitions inside it). Note: If you make a mess-up, click the big Undo button. All these changes are reversible *until* you press Apply; after that you can't undo.
[/LIST]
[INDENT]
[LIST=1]
[*]Boot from your Live CD (or USB).
[*]Start GParted (click on the Applications button; start typing "gparted"; click it to start).
[*]You will see your partitions listed.
[*]Delete /dev/sda4:
[LIST]
[*]Right-click /dev/sda4 and select *Delete*.
[/LIST]
 
[*]Create an extended partition to hold the new partitions:
[LIST]
[*]From the menu, choose *Partition > New*.
[*]*Free space preceding*: zero
*New size*: the maximum you can
*Create as*: Extended Partition
*Label*: anything you like (it's for your information only).
[*]Add.
[/LIST]
 
[*]Create a replacement for your old sda4:
[LIST]
[*]Right-click the new extended partition and select *New*.
[*]*Free space preceding*: zero
*New size*: 130000 MiB
*Create as*: Logical Partition
*Filesystem*: **ntfs**
*Label*: anything you like (this will be your data partition)
[*]Add
[/LIST]
 
[*]Create your Ubuntu partition:
[LIST]
[*]Right-click the new extended partition and select *New*.
[*]*Free space preceding*: zero
  *Free Space Following*: the size of your computer's RAM in MB (e.g. if you have 4Gb RAM, enter 4000)
  *Create as*: Logical Partition
*Filesystem*: **ext4**
  *Label*: anything you like (this is for your 130Gb partition)
[*]Add
[/LIST]
 
[*]Create Ubuntu's swap space:
[LIST]
[*]Right-click the new extended partition and select *New*.
[*]*Free space preceding*: zero
  *New Size*: the maximum you can
  *Create as*: Logical Partition
*Filesystem*: **linux-swap**
  *Label*: Swap
[*]Add
[/LIST]
 
[*]Apply the changes:
[LIST]
[*]Press the big Apply button.
[/LIST]
 
[/LIST]
[/INDENT]
[LIST]
[*]Restore your data
[/LIST]
[INDENT]
[LIST=1]
[*]Boot into Windows.
[*]Reboot (Windows often needs a double-boot after changing partitions.)
[*]Restore your data onto your newly-changed partition (probably D: drive).
[/LIST]
[/INDENT]Finally, you can install Ubuntu. When you do so, you will need to choose your partitions **manually**, not automatically. Be sure to use the **ext4** partition for Ubuntu; and use the **linux-swap** partition for the swap area. Please post back if you're not sure how to go about it.
Thanks [Paddy Landau]("http://ubuntuforums.org/member.php?u=572807"):

I like taking a Ubuntu tutorial class ^^.. 

I  went through the backup part. There is a little problem about  the size of linux-swap and ext4 in the part of partition recreated ? I guess that the size of swap is 4000 and the remaining would assign to Ubuntu root system. Is it right?

There is my new partition table:
ubuntu@ubuntu:~$ sudo parted --list
Model: ATA FUJITSU MHZ2250B (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  1049kB  1016kB  primary
 2      1049kB  106MB   105MB   primary   ntfs            boot
 3      106MB   63.0GB  62.9GB  primary   ntfs
 4      63.0GB  250GB   187GB   extended
 5      63.0GB  199GB   136GB   logical   ntfs
 6      199GB   204GB   4194MB  logical   linux-swap(v1)
 7      204GB   225GB   21.0GB  logical   ext4   (ubuntu planned install in this partition. 20Gb is it enough ?)
 8      225GB   250GB   25.6GB  logical   ext4   (i want separate /home in a partition )


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label

Thanks

---

### Post by dadaj on 2011-05-01
> **Paddy Landau said:**
> Right. You will need to shrink sda4 to 130Gb, then create a new partition to hold Ubuntu in the remaining 57Gb.

However, because of the limit of 4 partitions per drive, you need to  create an extended partition, moving sda4 into it. Although simple, this requires a few steps (sorry, it's a hardware limitation and there's no way around it).

You do not want to mess  with sda1, sda2 or sda3.

The following steps may seem complicated. That's because of the limit of four partitions on a disk. But it isn't complicated. Just follow the steps.

**You cannot do this without making a backup.**

We'll do this step by step.

[LIST]
[*]The most important step: **Back up**.
[/LIST]
[INDENT]
[LIST=1]
[*]Back up your data on sda4 (probably your D: drive in Windows).
[*]Just in case of mistakes, also back up all your other data.
[*]Check that your backup really does contain all your data, especially the data on sda4.
[*]You may need to investigate the Windows logical G: drive that bcbc mentioned; if necessary, get rid of it. (I have not come across these Windows logical drives before, so I cannot advise you on it.)
[/LIST]
[/INDENT]
[LIST]
[*]Adjust your partitions (replace sda4 with an extended partition; create three new logical partitions inside it). Note: If you make a mess-up, click the big Undo button. All these changes are reversible *until* you press Apply; after that you can't undo.
[/LIST]
[INDENT]
[LIST=1]
[*]Boot from your Live CD (or USB).
[*]Start GParted (click on the Applications button; start typing "gparted"; click it to start).
[*]You will see your partitions listed.
[*]Delete /dev/sda4:
[LIST]
[*]Right-click /dev/sda4 and select *Delete*.
[/LIST]
 
[*]Create an extended partition to hold the new partitions:
[LIST]
[*]From the menu, choose *Partition > New*.
[*]*Free space preceding*: zero
*New size*: the maximum you can
*Create as*: Extended Partition
*Label*: anything you like (it's for your information only).
[*]Add.
[/LIST]
 
[*]Create a replacement for your old sda4:
[LIST]
[*]Right-click the new extended partition and select *New*.
[*]*Free space preceding*: zero
*New size*: 130000 MiB
*Create as*: Logical Partition
*Filesystem*: **ntfs**
*Label*: anything you like (this will be your data partition)
[*]Add
[/LIST]
 
[*]Create your Ubuntu partition:
[LIST]
[*]Right-click the new extended partition and select *New*.
[*]*Free space preceding*: zero
  *Free Space Following*: the size of your computer's RAM in MB (e.g. if you have 4Gb RAM, enter 4000)
  *Create as*: Logical Partition
*Filesystem*: **ext4**
  *Label*: anything you like (this is for your 130Gb partition)
[*]Add
[/LIST]
 
[*]Create Ubuntu's swap space:
[LIST]
[*]Right-click the new extended partition and select *New*.
[*]*Free space preceding*: zero
  *New Size*: the maximum you can
  *Create as*: Logical Partition
*Filesystem*: **linux-swap**
  *Label*: Swap
[*]Add
[/LIST]
 
[*]Apply the changes:
[LIST]
[*]Press the big Apply button.
[/LIST]
 
[/LIST]
[/INDENT]
[LIST]
[*]Restore your data
[/LIST]
[INDENT]
[LIST=1]
[*]Boot into Windows.
[*]Reboot (Windows often needs a double-boot after changing partitions.)
[*]Restore your data onto your newly-changed partition (probably D: drive).
[/LIST]
[/INDENT]Finally, you can install Ubuntu. When you do so, you will need to choose your partitions **manually**, not automatically. Be sure to use the **ext4** partition for Ubuntu; and use the **linux-swap** partition for the swap area. Please post back if you're not sure how to go about it.
**Thanks Paddy Landau**:

After rebuilding partition, windows 7 fail to boot. it provides two options for me: one is "Launch startup repair(recommended). another one is "start windows normally".  The second choice won't work. it go to a blue screen. it say "A problem has been detected and windows has been shut down to prevent damage your computer.......(following information is omitted)"

After googling, there is a sugestion for repair windows 7 bootsect by booting from  windows 7 CD. using the repair tool inside boot directory inside CD. and the command is "bootsect /nt60 SYS". However, It also won't work. 

but it provides some messages:
\Device\Harddisk0\Partition2
Could not open the volume device: the system cannot find the file specified.
No bootcode was successfully updated.

Could I recover to boot windows 7?

---

### Post by Paddy Landau on 2011-05-01
> **dadaj said:**
> I guess that the size of swap is 4000 and the remaining would assign to Ubuntu root system. Is it right?
The swap should be the size of your RAM, whatever that is. So, if you have 4Gb RAM, then yes, 4000 for the swap.

> **dadaj said:**
> There is my new partition table:
(ubuntu planned install in this partition. 20Gb is it enough ?)
(i want separate /home in a partition )
Ubuntu programs need not even 8Gb. My root has filled only 5.2Gb despite installing many programs. You can make it 8Gb; that will be plenty.

(Unlike with Windows partitions, it's easy to change your mind later with Linux partitions. If you wish, you can try it now with GParted; simply resize the two partitions, root's /dev/sda7 and home's /dev/sda8, and apply.)

> **dadaj said:**
> After rebuilding partition, windows 7 fail to boot...
I'm sorry, I can't imagine how that happened. You appear to have done all the right things.

I suggest you use the Windows suggestion, "Launch startup repair(recommended)". Unfortunately, I'm no longer an expert with Windows and its problems (the problems are why I left Windows in the first place).

I'm hoping someone else will read this thread and help you recover Windows. Also, please search the forums (especially the [Absolute Beginner Talk forum]("http://ubuntuforums.org/forumdisplay.php?f=326")) for a solution. If you don't find a solution, please start a new thread in the Absolute Beginner Talk forum asking for help with recovering your Windows 7. You can point to this thread if you like.

Once your Windows is working again, post back here so that we can continue with your Ubuntu installation.

---

### Post by dadaj on 2011-05-01
> **Paddy Landau said:**
> The swap should be the size of your RAM, whatever that is. So, if you have 4Gb RAM, then yes, 4000 for the swap.


Ubuntu programs need not even 8Gb. My root has filled only 5.2Gb despite installing many programs. You can make it 8Gb; that will be plenty.

(Unlike with Windows partitions, it's easy to change your mind later with Linux partitions. If you wish, you can try it now with GParted; simply resize the two partitions, root's /dev/sda7 and home's /dev/sda8, and apply.)


I'm sorry, I can't imagine how that happened. You appear to have done all the right things.

I suggest you use the Windows suggestion, "Launch startup repair(recommended)". Unfortunately, I'm no longer an expert with Windows and its problems (the problems are why I left Windows in the first place).

I'm hoping someone else will read this thread and help you recover Windows. Also, please search the forums (especially the [Absolute Beginner Talk forum]("http://ubuntuforums.org/forumdisplay.php?f=326")) for a solution. If you don't find a solution, please start a new thread in the Absolute Beginner Talk forum asking for help with recovering your Windows 7. You can point to this thread if you like.

Once your Windows is working again, post back here so that we can continue with your Ubuntu installation.
[Paddy Landau]("http://ubuntuforums.org/member.php?u=572807") 

Never mind, everything can be reinstalled again. ^^ 

and thanks your supporting, I will be back....^^

---

### Post by Paddy Landau on 2011-05-01
> **dadaj said:**
> Never mind, everything can be reinstalled again. ^^
Thank goodness I asked you to back up first!

Good luck.

---

### Post by dadaj on 2011-05-01
> **Paddy Landau said:**
> Thank goodness I asked you to back up first!

Good luck.

Finally, I delete all new partitions created by Gparted and restart computer. windows 7 can startup in normal way.

---

### Post by Paddy Landau on 2011-05-01
Fantastic.

I'm sorry about the complication. I don't understand why it happened, or why deleting the extra partitions should have solved the problem. Did you do anything else to solve it?

Please do the command [FONT=Courier New]sudo parted --list[/FONT] again so that I can check what's happening with your partitions.

By the way, when you post your results, please would you highlight them and press the # key (see the screenshot below). It makes it easier to read.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=190688&stc=1&d=1304269223[/IMG]

---

### Post by dadaj on 2011-05-01
I attempted to follow the suggestion of this link [http://www.thpc.info/how/use_gparted_to_resize_windows_7_vista_partition.html#hlp](http://www.thpc.info/how/use_gparted_to_resize_windows_7_vista_partition.html#hlp) to recover windows 7 but all failed.


```
ubuntu@ubuntu:~$ sudo parted --list
Model: ATA FUJITSU MHZ2250B (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  1049kB  1016kB  primary
 2      1049kB  106MB   105MB   primary  ntfs         boot
 3      106MB   63.0GB  62.9GB  primary  ntfs


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label                                  


```

---

### Post by dadaj on 2011-05-02
Paddy Landau:

Finally, **Ubuntu 11.04 was installed** after converting dynamic  parition to basic partition in windows 7 and create extended and logical  partitions with windows 7 build-in command: diskpart. In fact, I cannot  achieve it myself without your detail and patient instruction given.  Following is the step I had went through.

[LIST=1]
[*]I download a FREE partition software from this link [http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm). It can convert dynamic partition to basic partition without damaging windows 7.
[*]Open terminal windows by run CMD command as a administrator.
[LIST=1]
[*]type "diskpart" open diskpart environment
[*]type "list disk" to find out unallocated disk space
[*]type "select disk X"   (X mean disk number. my disk number is 0. )
[*]type "create partition extended"
[*]type "create partition logic size=130000"  (I create a 130Gb partition for data store)
[*]type "create partition logic size=4000" (create swap)
[*]type "create partition logic size=8000" (create space for ubuntu system)
[*]type "create partition logic" (the remaining space will assign to "/home")
[/LIST]
[*]restart windows and boot from Ubuntu CD
[*]select install ubuntu
[*]I select assign space on myself
[LIST=1]
[*]the partition created for ubuntu assign to "/"
[*]the partition created for /home assign to "/home"
[/LIST]
[*]start install process
[*]finish & reboot to windows
[*]download a FREE software call easybcd [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)
[LIST=1]
[*]choice add new entries
[*]choice Linux tab and select Grud2
[*]label Ubuntu Natty
[*]Apply
[/LIST]
[*]restart windows & choice ubuntu natty in windows boot menu
[/LIST]
 This is new partition table:

```

Model: ATA FUJITSU MHZ2250B (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  106MB   105MB   primary   ntfs            boot
 2      106MB   63.0GB  62.9GB  primary   ntfs
 3      63.0GB  250GB   187GB   extended                  lba
 5      63.0GB  199GB   136GB   logical   ntfs
 6      199GB   204GB   4194MB  logical   linux-swap(v1)
 7      204GB   212GB   8389MB  logical   ext4
 8      212GB   250GB   38.1GB  logical   ext4


```

Paddy Landau
Thank you very very much

---

### Post by Paddy Landau on 2011-05-02
Fantastic! I'm so glad you managed to solve your problems.

So, now you have Windows and Ubuntu (not Wubi) both installed. I hope you enjoy Ubuntu.

Well done for your persistence and patience.

There is a fantastic tutorial on how to use 11.04. Try these two links:
[The Raving Rick: My Effort at Writing Help for Unity]("http://theravingrick.blogspot.com/2011/04/my-effort-at-writing-help-for-unity.html")
[The Power User's Guide to Unity]("http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity")

Please mark the thread solved, to help other people who may have the same problem.

---

### Post by dadaj on 2011-05-02
Thanks your further learning direction....^^

time to homework..

---

