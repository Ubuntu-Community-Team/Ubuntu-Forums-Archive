---
title: "Changing default locations for folders"
date: 2014-03-24
forum: Installation &amp; Upgrades
---

### Post by ahpitre on 2014-03-24
I have a dual boot Windows 8/ Ubuntu 13.04 computer. I store all my documents in a Data partition. Ubuntu can access this partition, but, it's default folders for pictures, music, documents, and downloads, are in the same partition where Ubuntu is installed Is there a way to change this? What I want is for Windows and Ubuntu to use the same Data partition and the same folders for my files, that way I can create and edit files in either OS and the files are in the same location.

---

### Post by Mark Phelps on 2014-03-24
> What I want is for Windows and Ubuntu to use the same Data partition and the same folders for my files,

IF you mount folders from Windows while running Ubuntu, you risk corrupting the Windows filesystem.  Windows can't read the Linux filesystem, so that rules out using it.

What you want is a separate DATA partition, formatted in NTFS, to hold those folders and files.

Both Linux and Windows can read/write NTFS partitions.

---

### Post by coffeecat on 2014-03-24
> **ahpitre said:**
> I store all my documents in a Data partition. Ubuntu can access this partition, but, it's default folders for pictures, music, documents, and downloads, are in the same partition where Ubuntu is installed Is there a way to change this? What I want is for Windows and Ubuntu to use the same Data partition and the same folders for my files, that way I can create and edit files in either OS and the files are in the same location.

Assuming that your Data partition is NTFS so that both Ubuntu and Windows can read/write to it, delete all your default folders in your Ubuntu home: pictures, music, etc. (You only need do this if the names are the same as the folders you have created on your Data partition.) Then simply create symlinks to the Data partition folders in your home folder. Then, if you open your Ubuntu home folder you will see symlink folders (ordinary folder icons with an arrow) which will open in the linked folders in your Data partition. Your Data partition needs to be mounted to the same mountpoint each time you boot up, so you may wish to mount the Data partition with a line in /etc/fstab to ensure consistency.

For Windows, simply create shortcuts in your home to the folders in the Data partition. Again, you may have to delete, move or rename the default folders in your Windows home, if the names are the same.

---

### Post by ahpitre on 2014-03-24
Precisely, that is what I have, a Data Partition in NTFS. Windows uses it as the location for my files, documents, music, pictures, etc. I can also access it in Ubuntu. I use LibreOffice in both, so, I would like to make Ubuntu's default folders for pictures, documents, etc., be the same as Windows (the folders in the Data Partition).

---

### Post by ahpitre on 2014-03-24
Will these links be used by Ubuntu apps as the default location for storing their files?

---

### Post by coffeecat on 2014-03-25
You can name symlinks in Ubuntu whatever you want. A folder in your Data partition named "My_Pictures" can have a symlink to it in your Ubuntu home folder named "Data_Partition_Pictures". I don't know about Windows shortcuts, but I'm sure the same applies.

Quick tip for creating symlinks in the GUI is you don't want to use the terminal. This is in Ubuntu with Unity - I don't know whether this works in desktops such as Xfce or KDE.

[list=1][*]Open a file browser window to the Data partition and a second one to your Ubuntu home folder.
[*]Right-click on the folder in your Data partition that you want to link to and select "Make Link". Let's assume the folder was "Videos". A link will appear in the Data partition named "Link to Videos". Now drag and drop that across to your home folder. You can now rename "Link to Videos" in your home folder to whatever you want - presumably "Videos". And you can now delete the link in the Data partition as it wont be of any further practical use. 
[*]Voila - you have a symlink in your home folder. Repeat for anything else you want to link.[/list]

As far as default locations for storing files, you'll have to set that up individually for each app - it's easy enough in LibreOffice under Tools -> Options. Some apps use hidden default folders and you can do the same thing so long as you are careful about folder naming and copying the pre-existing contents of hidden default folders to a temporary location before you create your symlinks so that you can then move them to the corresponding folders in Data. For example, Thunderbird and Xchat create .thunderbird and .xchat folders in home by default for all your saved stuff and configurations. I have symlinks named the same in my home linked to folders in my data partition. I was careful to backup the contents of .thunderbird and .xchat before setting up the symlinks otherwise I would have lost all my emails and xchat logs.

A word of warning. Be careful when deleting default folders in your Ubuntu home - ditto in Windows. Check to see what they contain first, as in the thunderbird example I give. If you delete the default Downloads folder, Firefox will get confused until you redirect it back to the symlink you create called Downloads - or it did a few years ago when I first did this. You'll also lose the pretty special icons on Music, Pictures and the like when you delete the default icons. I'm sure there's a way of applying them to the symlink folders, but I haven't looked into this.

And a repeat word of warning. You data partition needs to be mounted on the same mountpoint each time you boot up otherwise the links will break.

---

### Post by ahpitre on 2014-03-28
This works OK, but as soon as I reboot my computer, the links are broken and no longer work. I need to go to folders, select the Data partition it opens, then, if I go back to my links they work. Does anybody know why this is happening? The data partition is always mounted the same way.

---

### Post by coffeecat on 2014-03-28
> **ahpitre said:**
> This works OK, but as soon as I reboot my computer, the links are broken and no longer work. I need to go to folders, select the Data partition it opens, then, if I go back to my links they work. Does anybody know why this is happening? The data partition is always mounted the same way.

A reminder.

> **coffeecat said:**
> Your Data partition needs to be mounted to the same mountpoint each time you boot up, so you may wish to mount the Data partition with a line in /etc/fstab to ensure consistency.


> **coffeecat said:**
> 
And a repeat word of warning. You data partition needs to be mounted on the same mountpoint each time you boot up otherwise the links will break.

The data partition is not mounted until you click on it in the file browser. If you want the data partition mounted automatically each time you boot and obviate the need to click in the file browser each time, you have to edit /etc/fstab.

This guide should help:

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

### Post by ahpitre on 2014-03-28
Your advice on mounting automatically via editing /etc/fstab worked great. Thanks for your help.

---

### Post by Clint_Avalos on 2014-09-09
HI, I have a similar situation but instead of sharing partitions Im sharing my dropbox folder between various windows and ubuntu machines. My problem is the same though in that Im trying to get my ubuntu default directories inside my dropbox so that both windows and ubuntu share the same user folders, ie: documents, music, pictures, etc...

Im on Ubuntu 14.04. Would anyone happen to have a solution for this scenario?

Thanks!

UPDATE: I posted this before trying to use symlinks and just deleting the default folders and recreating the links seemed to work just fine.

---

