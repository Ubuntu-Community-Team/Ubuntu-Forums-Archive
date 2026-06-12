---
title: "Wine Configuration"
date: 2006-07-01
forum: Installation &amp; Upgrades
---

### Post by jtull89 on 2006-07-01
I am using Wine 0.9.12 for Ubuntu. From Sourceforge. Whenever I try to launch winecfg to start it up for the first time, I get error messages in the terminal:

[IMG]http://img.photobucket.com/albums/v82/jtull89/wineerror.png[/IMG]

Of course, it's pretty obvious that the problem is with the drives, however, I can't edit the drives. I click on the drives in the drives menu, and nothing is highlighted. Also, whenever I click "browse", the following error appears in the terminal:

err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\greg\\Desktop"'.


I used to be able to use "browse" for C:, and also I could successfully change C: with the "path" field, but I could never select the drives. Just so you know, in trying to solve it I've tried uninstalled and reinstalled wine many many many times through various repositories. Well, only two repositories, and sourceforge.net.

The drives are configured as follows :sad: :

C:       /dev/hda2
D:       /media/win
E:       /media/cdrom0
H:       /home/greg
Z:       /

It's worth noting that "/dev/hda2" is my main windows partition, "/media/win" is how it's registered in the Linux file system, and D: is my Windows XP restore partition. I don't know what H: and Z: are, but they don't appear in "My Computer" under Windows.

EDIT: The last two error messages in the image provided only appear when I switch to the "drives" tab.

---

### Post by kripkenstein on 2006-07-01
You say you are using 0.9.12, did you try the latest wine version (0.9.16)?

---

### Post by jtull89 on 2006-07-02
Yes. It is also worth noting that I have kernel version 2.6-25, in addition to 2.6-23

EDIT: I just found that I can select drives by clicking on the drive names, as opposed to the paths. :oops: However, whenever aI change C: to /media/win, and I apply the changes and close, I still get the error messages that I get at the beginning.

EDIT 2: I no longer have the "Z:" drive, since I removed it.

EDIT 3: Solved! I just used the default fake partition settings.

---

