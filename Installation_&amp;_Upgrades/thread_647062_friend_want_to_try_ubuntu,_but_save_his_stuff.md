---
title: "friend want to try ubuntu, but save his stuff"
date: 2007-12-21
forum: Installation &amp; Upgrades
---

### Post by nephish on 2007-12-21
lo there gents, 

need to know where on a windows computer, if the hard drive is mounted with an Ubuntu live cd, i can find a users My Documents. 

the hard drive of said computer is disc when mounted, i want to salvage all the stuff off of it to a usb drive, then start with a fresh install on this guys computer. 

i have not messed with a windows computer in over 8 years, 

please, any tips would be great. 
thanks

---

### Post by sstusick on 2007-12-21
To find the user's My Documents folder? The directory on XP is: C:\\Documents and Settings\<user name>\My Documents

Hope this helps.

---

### Post by taurus on 2007-12-21
You need to mount your windows partition first from Ubuntu LiveCD before you can access it.  Assuming it's /dev/sda1, try

Applications -> Accessories -> Terminal
```
sudo mkdir /media/windows
sudo mount -t ntfs /dev/sda1 /media/windows
gksudo nautilus
```
Now, all your windows stuff will be in /media/windows[/code]

---

### Post by nephish on 2007-12-22
got every thing i needed, thanks all !

---

