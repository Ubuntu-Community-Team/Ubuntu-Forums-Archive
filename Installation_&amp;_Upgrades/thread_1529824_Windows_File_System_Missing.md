---
title: "Windows File System Missing"
date: 2010-07-12
forum: Installation &amp; Upgrades
---

### Post by vchapman on 2010-07-12
I have installed ubuntu 10.4 as a dual boot with Windows 7. I thought, because of a previous experience, that my music and pictures were ok in the windows file system because I would be able to access them. Well I can't. I don't even see the the Windows c: drive. I know its still there because I can boot windows.

So what do I need to do to make the c: volume / drive reappear. 

TIA

---

### Post by walle1357 on 2010-07-12
Wait a sec. Are you saying that the C drive wont come up in Windows? or you cant find it in ubuntu?

---

### Post by vchapman on 2010-07-12
> **walle1357 said:**
> Wait a sec. Are you saying that the C drive wont come up in Windows? or you cant find it in ubuntu?


Can't find it in Ubuntu.

---

### Post by cavalier911 on 2010-07-12
Open pcmanfm if on lubuntu, nautilus/places on left column if ubuntu. On the left pane all your partitions should be listed.You have to click on the partition to automount so you can view the content on the right side.This applies to linux filesystem partitions too. Otherwise add an entry in your fstab with ntfs3g for ntfs to mount when you boot.

---

### Post by vchapman on 2010-07-13
> **cavalier911 said:**
> Open pcmanfm if on lubuntu, nautilus/places on left column if ubuntu. On the left pane all your partitions should be listed.You have to click on the partition to automount so you can view the content on the right side.

This works except it is only temporary for the login session.


> This applies to linux filesystem partitions too. Otherwise add an entry in your fstab with ntfs3g for ntfs to mount when you boot.
I need to be able to mount the windows file system when I boot. Unfortunately, your information for how this is done is a bit beyond my pay grade. So if you don't mind I need some step by step instructions on how to do this. Thank you.

In doing some more searching I've come across something called  ntfs-config. Does that work for me?

---

### Post by cavalier911 on 2010-07-13
Open terminal

**Enter**  keypress after all commands

```
sudo fdisk -l
```The partitions with Id 7 System  HPFS/NTFS are Windows format

Make note of the Device for the NTFS partitions you want automounted

Partitions mounted to a folder in /media show on the Desktop. In my example I'm calling the folder WinMnt.

```
sudo mkdir /media/WinMnt
```So for example only let's say fdisk indicated the NTFS partition is device /dev/sda1 

Lets test mount /dev/sda1 to /media/WinMnt
```
sudo mount /dev/sda1 /media/WinMnt
```An icon called WinMnt will appear on your Desktop, click it to see and verify that is what you want automounted. If it's not let's unmount and try another partition.
```
sudo umount /media/WinMnt
```Once you narrow which partition(device) to add to /etc/fstab to automount
lets determine it's unique UUID

```
sudo blkid
```Find the UUID across from your partition.

Lets test it.

```
sudo mount   UUID="your.UUID" /media/WinMnt
```Verify mount on Desktop, then unmount.

```
sudo umount /media/WinMnt
```Edit /etc/fstab

```
sudo nano -B /etc/fstab
```Arrow down cursor below all entrys.

You can right click copy the UUID and middle click mouse wheel button or click right and left buttons at the same time on laptop to paste the UUID into nano.

[B]UUID="your.uuid"  /media/WinMnt ntfs-3g defaults,locale=en_US.UTF-8 0 1
[/B] 
When your finished:  Ctrl+x,y,enter

Click Up arrow to to reopen nano,verify your change was saved.

Test the /etc/fstab

```
sudo mount -a
```If WinMnt is on Desktop your done.

Reboot 

If your editing in nano and make a mistake press n instead of y and no changes will be made.In addition for safety by adding the -B switch to nano a backup of the original file is made with a ~ on the end. By renaming the fstab to fstab.old and removing the ~ from fstab~ you restore the original fstab.Main thing to remember is to not edit files without a backup copy.

_Look here for more detail:_ [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by Osni on 2010-07-14
Thanks cavalier911, this is exactly what I was looking for ;).  Will try that when I get home.

I have two questions though...

My language is set to Brazilian Portuguese, do I have to change ```
locale=en_US.UTF-8 0 1
``` to ```
locale=pt_BR.UTF-8 0 1
```?

To let fstab auto mount this partition every time I start linux, do I just need to add **auto,** before defaults, like this?
```
**UUID="my.uuid"  /media/Data ntfs-3g auto,defaults,locale=en_US.UTF-8 0 1**
```

---

### Post by jocko on 2010-07-14
> **Osni said:**
> Thanks cavalier911, this is exactly what I was looking for ;).  Will try that when I get home.

I have two questions though...

My language is set to Brazilian Portuguese, do I have to change ```
locale=en_US.UTF-8 0 1
``` to ```
locale=pt_BR.UTF-8 0 1
```?

To let fstab auto mount this partition every time I start linux, do I just need to add **auto,** before defaults, like this?
```
**UUID="my.uuid"  /media/Data ntfs-3g auto,defaults,locale=en_US.UTF-8 0 1**
```
I would try without any locale setting. That should work fine in most cases, so:
```
UUID="my.uuid"  /media/Data ntfs-3g auto,defaults 0  1
```

---

### Post by Osni on 2010-07-14
> **jocko said:**
> I would try without any locale setting. That should work fine in most cases, so:
```
UUID="my.uuid"  /media/Data ntfs-3g auto,defaults 0  1
```

Thanks jocko, but since I don't fully understand what this locale means and a quick **locale -a** gave me C, POSIX, pt_BR.utf8 and pt_PT.utf8, I'll just stick with that ;).

This is what I added to my fstab, and is woking like a charm:
```
# Mounts /dev/sda2 to "/media/Data" at startup
UUID="DC14C7B314C78EC8" /media/Data ntfs-3g auto,defaults,locale=pt_BR.utf8 0 2
```Thanks for all the info cavalier911 and jocko!

vchapman, sorry for bloating your thread :popcorn:.

PS.: If someone happens to be with the same doubts as vchapman and me, I strongly suggest reading cavalier911's link ([https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)) and [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131).

---

