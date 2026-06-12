---
title: "Error 17: Cannot Mount Partition"
date: 2008-07-04
forum: Installation &amp; Upgrades
---

### Post by Firebucket on 2008-07-04
I installed Ubuntu 8.04 onto my Portable HDD (GRUB is also installed to the External HDD to). My BIOS can boot from the the drive, because GRUB loads. When I select Ubuntu 8.04, it says Error 17: Cannot mount selected partition. I've tried changing the hda0,0 thing but I don't know what to change it to. Can anyone help

---

### Post by WailingWailer on 2008-07-04
I have done the same thing, and once I came to the grub and when I chose Ubuntu it said about some error (I don't remember which). But now I have another problem - when I start my computer it starts like there's no USB HDD. It does this on two computers. What could be wrong?

edit: i installed grub one more time and i have exactly the same problem.

---

### Post by VMC on 2008-07-04
Welcome to the both of you. WailingWailer, since this is Firebucket topic let's get him fixed up first. Just folow along and maybe you can fix yours as well.

We need a few things to look it. Open up a Terminal from Applications > Accessories > Terminal. Type the following:

```
sudo fdisk -l
cat /boot/grub/menu.lst
```

Copy and paste the outputs back here.

---

### Post by WailingWailer on 2008-07-04
Well, I have solved problem for myself (which is exactly the same problem), so it should for Firebucket too.

When you come to grub at start up press c to go to command line.
Then type:
```

find /boot/grub/stage1
boot (hdx,y)     [x,y is what you got before]
setup (hdx,y)

```
Press Esc. Then choose Ubunt 8.04 and press e. Change (hdx,y) to the numbers you have set before. That should do it.

---

### Post by eklavya on 2008-12-11
If u have done -
"find /boot/grub/stage1
sudo grub
root (hd0,0)
setup (hd0)
exit"
and get error 18
and
"on doing ...
find /boot/grub/stage1
boot (hdx,y)     [x,y is what you got before]
setup (hdx,y)"
 u get message saying kernel not loaded or sumthin as it happened in my case. Read on.. 

Ok,this is how I managed to solve the problem.
1)find /boot/grub/stage1

 note down the output eg:(hd2,0)

2)now go the the my computer like icon for linux found in "places".(navigate to the place where all disk drives r displayed)

3)now double click on all the drives u think could have the grub file.(that way they get automounted in media)

4)Now enter the "ext3 ones"(use gparted to find the formatting type)  1 by one and find the boot->grub->menu.lst
5)In ur terminal type: sudo  su(for ubuntu) or su for others(u r the root now)

6)navigate to the menu.lst as found above and open it.
 See if it has the same statements found on ur login screen,if not search the other drives for the correct menu.lst.

7)Now u will see a line having the word "root and say (hd0,0)"

 just replace this with the output of "find" from above.

Yep ur prob should have been solved by now.

Cheers!

---

