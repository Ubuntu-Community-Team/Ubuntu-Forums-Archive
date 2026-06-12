---
title: "install 18.04: misleading dialog"
date: 2021-03-13
forum: Installation &amp; Upgrades
---

### Post by mringer on 2021-03-13
In a previous thread, I was told I should abandon L-UB 16 & change to 18 or 20. I loaded the Live 
DVD and after a few steps, the screen:  Type of installation appears. It offers (my numbers):

1. Erase 16 & reinstall. Warning: this will delete all your programs, documents [etc] & any other files.

2. Erase whole disk. Warning: [ ditto ] ... any other files in all operating systems.

3. Encrypt diak

4. Use LVM  ** NO ** warning !

5 something else.

and I think this dialog is misleading. Surely (1) will only delete your files if  /home  is on the root partition?
Anyway I chose (1) and it said:

partition #5  will be formatted as   ext4  .

This partition does not exist & cannot be created as my disk is DOS formatted & already has 4  primary 
partitions:   windows ,  swap ,  root ,  /home  .  Also I dont want any partition reformatted  as   ext4  
because windows needs to access  root and  /home  and I am told that  ext2fs  cannot read  ext4 .

So I backed out & chose  (5).  Then it took me a long time to get past the error message:

You must choose a partition for the  root  drive

because it doesnt tell you how to do this.

Please could this part of the dialog be improved? Thank you.

---

### Post by GhX6GZMB on 2021-03-13
I'm not a member of the team, but I seriously doubt that anyone is going to put effort into 18.04.

---

### Post by guiverc on 2021-03-13
Lubuntu 18.04 LTS was provided with two installer options, the main ISO used the `ubiquity` installer, which was the same installer as used by other flavors of Ubuntu so the screens & operation were identical (*with exception that Kubuntu put a skin over theirs so it looked slightly different but acted the same*).

The alternate ISO for Lubuntu 18.04 LTS used the *debian* *installer*, but really was intended for users who had <768MB of RAM on their boxes; as they couldn't run the *live* ISO and run the `ubiquity` installer at the same time, and it got around this issue by not being *live*.

@ml9104 is correct, Lubuntu 18.04 LTS reaches EOL next month so there is no need to fix it.
- [https://lubuntu.me/bionic-5-released/](https://lubuntu.me/bionic-5-released/)
- [https://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/](https://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/)

Also the *upstream* (*main* Ubuntu) have announced `ubiquity` is being replaced anyway ([https://discourse.ubuntu.com/t/refreshing-the-ubuntu-desktop-installer/20659](https://discourse.ubuntu.com/t/refreshing-the-ubuntu-desktop-installer/20659)) with the new look already published so we can comment ([https://discourse.ubuntu.com/t/new-installer-design/21298](https://discourse.ubuntu.com/t/new-installer-design/21298)) so if you have suggestions about the `ubiquity` replacement, I'd suggest go there (you can check to see if it has the issue you're concerned about; comments there would likely be **actioned**)

Lubuntu switched to the `calamares` installer mid-2018 and the last five releases (those after 18.04, ie. 18.10 -> 20.10) have used it, so we won't use `ubiquity` again, and you're talking about a release that's in it's last days of full-support (*support by the Lubuntu team ends April 2021*).

FYI: Lubuntu is a desktop release, and we have no *snap* only releases, so only use the *year.month* format, eg. 18.04.  Ubuntu reserves the *yy* format for *snap* only releases such as Ubuntu Core 18, having done so since 2016.  (*also* *if not obvious, I am a Lubuntu team member*)

---

### Post by grahammechanical on 2021-03-13
> Erase 16 & reinstall. Warning: this will delete all your programs, documents [etc] & any other files.

That option indicates to me that the installer has detected an existing install of Lubuntu. Choosing that option would indeed result in the erasure and formatting of all partitions being used by Lubuntu. I was not aware that Linux could be installed on a Microsoft formatted partition. It is possible to use a Microsoft formated partition as a data partition that can then be accessed by both Windows and Linux.

Are you sure that you only have 4 partitions. What version of Windows do you have? In the past on MBR partitioned hard drives Microsoft would use the 4 primary partitions allowed. To install Linux the user would need to delete one of those Windows partitions (perhaps there for recovery) and convert it into an extended partition and then install the Linux distribution into logical partitions inside the extended partition. I think that it is possible that you do have more than 4 partitions on that hard drive.

Regards

---

### Post by yancek on 2021-03-14
>  and I think this dialog is misleading. Surely (1) will only delete your files if  /home  is on the root partition?

If you have a separate /home partition, you need to ensure that the format box for that partition is NOT checked or it will be overwritten.

>  Also I dont want any partition reformatted  as   ext4  
because windows needs to access  root and  /home  and I am told that  ext2fs  cannot read  ext4 .


A default windows install will not read or write a Linux filesystem.  What third party software are you using?  Accessing files on a Linux filesystem partition is just as bad an idea as accessing files on a windows partition.  Just asking for trouble.  If you need to share data, have a separate data partition.

---

