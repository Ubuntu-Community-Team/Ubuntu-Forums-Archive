---
title: "How to Restore GRUB after installing Windows"
date: 2007-06-26
forum: Installation &amp; Upgrades
---

### Post by davidme on 2007-06-26
Here is my situation:

1)I Installed Ubuntu Feisty 7.04 

Some time late decided I still need windows for gaming, so I inserted Gparted live cd and resized my /home partition and created a 20 gig Primary NTFS partition.

2) Install windows on to the new 20 gig partition. Now windows is the only thing that boots. 

3)To get my Ubuntu back and Windows as dual boot, I did this:

Boot with gparted live cd. Issue this:

su
grub (enter)
find /boot/grub/stage1
root (hd0,0)
setup (hd0)
quite

Thinking that that is it, I rebooted only to find out that Ubuntu is the only things that boots and in the grub only Ubuntu is listed.

5)I inserted windows cd and went to Fix installation console menu: FIXMBR and FIXBOOT

6) Now Windows XP is the only thing that boots, I repeated step 3 and I am back to Ubuntu being the only thing that boots.

Help !!!

---

### Post by confused57 on 2007-06-26
> **davidme said:**
> Here is my situation:

1)I Installed Ubuntu Feisty 7.04 

Some time late decided I still need windows for gaming, so I inserted Gparted live cd and resized my /home partition and created a 20 gig Primary NTFS partition.

2) Install windows on to the new 20 gig partition. Now windows is the only thing that boots. 

3)To get my Ubuntu back and Windows as dual boot, I did this:

Boot with gparted live cd. Issue this:

su
grub (enter)
find /boot/grub/stage1
root (hd0,0)
setup (hd0)
quite

Thinking that that is it, I rebooted only to find out that Ubuntu is the only things that boots and in the grub only Ubuntu is listed.

5)I inserted windows cd and went to Fix installation console menu: FIXMBR and FIXBOOT

6) Now Windows XP is the only thing that boots, I repeated step 3 and I am back to Ubuntu being the only thing that boots.

Help !!!

You could try adding an entry to your menu.lst to boot Windows...open a terminal, determine which is your Window's partition with:
```
sudo fdisk -l
```
-l is a small "L"

Then to add an entry to your menu.lst:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

add your Window's entry to the very end of the file...for example if Windows is on /dev/sda3, you entry would be:
```
title   Windows XP
root  (hd0,2)
savedefault
makeactive
chainloader  +1
```
quit & save

/dev/sda4   =   (hd0,3)
/dev/sda6   =   (hd0,5)

---

### Post by divague on 2007-06-26
reinstall Grub, like you explained in 3)

Boot ubuntu, edit you /boot/grub/menu.lst, and add windows to the list of operating systems. These are the lines you should add:

title Microsoft Windows XP
root (hd?,?)
makeactive
save default
chainloader +1

---

### Post by davidme on 2007-06-27
That worked, thank you.

However, I do not understand why 

/dev/sda4 = (hd0,3)

and not /dev/sda4 = (hd0,4)

---

### Post by merlinus on 2007-06-27
Numbering for these things starts at 0, not 1.

So hd0 is your first (and maybe only) hard disk. 0 is the first partition.

So /dev/sda4 is (hd0,3).

-merlin

---

### Post by davidme on 2007-06-27
One more thing that I needed to do was

change 

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu


to

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

As after all the changes the menu still was not appearing.

Excellent. Thank you.

---

### Post by ihristov on 2007-06-27
davidme, do you have an option in the thread to mark it as "solved". If you have such option, please do. I see some other threads that are marked as "solved", so I assume only the original poster has the right to do this.

---

