---
title: "cannot see host-ntfs partition"
date: 2012-07-14
forum: Installation &amp; Upgrades
---

### Post by insert20 on 2012-07-14
hi guys.. im just new to ubuntu cant seem to find any related topic to mine..

i just recently installed ubuntu 12.04 in my pc alongside with windows 7 and everything seem perfect.. i dual boot on it and its fine...

But i cant see my other partition which is the host partition and it is formatted as ntfs and i can see it if i boot in windows 7..

i tried exploring the file system folder and home but cant see any trace of files from my other partition... it was the partition where i installed ubuntu 12.04 alongside with windows..

i updated my ubuntu and still no results... 

i can see my other partition except for the host partition which i only see it everytime i boot to windows 7

please help me thanks guys

---

### Post by Karlchen on 2012-07-14
Hello, insert20.

Are we really talking about a Ubuntu Wubi installation? I.e. the whole Ubuntu installation really lives in a file which is named \ubuntu\disks\root.disk (Windows notation) ?

If this is the case, then open a terminal window.
Inside the terminal window execute the commands ```
cd /host
ls -al
```You should see the content of the appropriate Windows partition.

Kind regards,
Karl

---

### Post by OM55 on 2012-07-14
Hello insert20,

If you installed a side-by-side installation (not a Wubi installation), your host NTFS drive(s) are not mounted by default, so initially will not show on your file system.

if you use gnome-fallback-session (classic Gnome menus on Ubuntu 12.04) all you need to do is go to the 'Places' menu and you should see your drive(s) at the bottom of the list. Clicking on the name will mount the drive and open Nautilus at the root of that drive.

You can also mount them manually:
```
sudo mount <your drive's name> <mount point>
```- The mount point is an empty folder in your current file system where the mounted drive root will be placed. You can create an empty folder and use that as a mount point.

- The device name of a disk is something in the form of  '/dev/sda1'. You can find your device name by:
```
sudo fdisk -l
```If you use the 'places' menu option of gnome-fallback-sessions classic Gnome menu, the mount point will be under the /media directory.

If you want to auto-mount a drive during boot, you will need to edit your /etc/fstab file.
You can find the info here: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by insert20 on 2012-07-15
> **Karlchen said:**
> Hello, insert20.

Are we really talking about a Ubuntu Wubi installation? I.e. the whole Ubuntu installation really lives in a file which is named \ubuntu\disks\root.disk (Windows notation) ?

If this is the case, then open a terminal window.
Inside the terminal window execute the commands ```
cd /host
ls -al
```You should see the content of the appropriate Windows partition.

Kind regards,
Karl


Thanks Karl for the reply..
I've seen the contents of my partition.. but i cant mount it... (see attached file for screenshots)
by the way it was installed by a live usb..

---

### Post by insert20 on 2012-07-15
> **OM55 said:**
> Hello insert20,

If you installed a side-by-side installation (not a Wubi installation), your host NTFS drive(s) are not mounted by default, so initially will not show on your file system.

if you use gnome-fallback-session (classic Gnome menus on Ubuntu 12.04) all you need to do is go to the 'Places' menu and you should see your drive(s) at the bottom of the list. Clicking on the name will mount the drive and open Nautilus at the root of that drive.

You can also mount them manually:
```
sudo mount <your drive's name> <mount point>
```- The mount point is an empty folder in your current file system where the mounted drive root will be placed. You can create an empty folder and use that as a mount point.

- The device name of a disk is something in the form of  '/dev/sda1'. You can find your device name by:
```
sudo fdisk -l
```If you use the 'places' menu option of gnome-fallback-sessions classic Gnome menu, the mount point will be under the /media directory.

If you want to auto-mount a drive during boot, you will need to edit your /etc/fstab file.
You can find the info here: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)


Thanks for your reply! 
im not sure if i did it right... please refer to the attached file for screenshots.. i cant mount it it says it is busy... it is already mounted... the file system is mounted but the ntfs partition part cannot be seen...
thanks for the help!

---

### Post by coffeecat on 2012-07-15
@insert20, since you can cd into your /host folder, it means that you have a wubi installation. It also means that your host partition is already mounted so there is nothing to mount. Indeed, the host partition needs to be mounted for a wubi installation to run at all, and that happens during the boot process.

Open a file browser window and click on "File System" in the left pane. Look for the host folder in the main pane and open that. There is your Windows host partition folder structure. You have read-write access so please be **very** careful. Essential system files which are hidden in Windows are visible in Ubuntu.

---

### Post by OM55 on 2012-07-15
> **insert20 said:**
> Thanks for your reply! 
im not sure if i did it right... please refer to the attached file for screenshots.. i cant mount it it says it is busy... it is already mounted... the file system is mounted but the ntfs partition part cannot be seen...
thanks for the help!


Your 'mount' command is missing the mount point (the last parameter).
But regardless, it does say that the partition is already mounted, so it is a moot point.

Hmmm... Did you try to look for the mounted NTFS drive under the '/media' directory?
That is where all the system mounts go by default. The mount name (i.e. the directory name under /media) would be the volume name. So if your partition label is 'DATA', when mounted you would see it as the directory: /media/DATA

---

### Post by Morbius1 on 2012-07-15
> **coffeecat said:**
> @insert20, since you can cd into your /host folder, it means that you have a wubi installation. It also means that your host partition is already mounted so there is nothing to mount. Indeed, the host partition needs to be mounted for a wubi installation to run at all, and that happens during the boot process.

Open a file browser window and click on "File System" in the left pane. Look for the host folder in the main pane and open that. There is your Windows host partition folder structure. You have read-write access so please be **very** careful. Essential system files which are hidden in Windows are visible in Ubuntu.
This appears to be the correct answer as one would expect from coffeecat. To make things easier use the following command:
```
nautilus /host
```When it opens to that location bookmark it: **Bookmarks > Add Bookmark**. You will now have a shortcut on the left side panel of nautilus labeled /host. You can even rename it to WinC or something more to your liking. And as cofeecat mentioned above it does mount with write access so be careful.

---

