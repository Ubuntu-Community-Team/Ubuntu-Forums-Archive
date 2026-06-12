---
title: "XP/ Ubuntu Dual boot issues (Installed Ubuntu can't boot either)"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by o32 on 2008-11-02
Hi there.

I've decided to try out linux for the first time and i'm having trouble. I've search the forum for answers but they all appear to be specific to the person asking the question and i don't want to risk losing files using code from other threads.

I have one hard drive that is partitioned for XP (25gig) and the remaining 900gig was an empty ntfs partition. I resized this partition using the installer and installed ubuntu.

After installation when i boot the computer GRUB loads fine but when i select any of the Ubuntu options I get the message" Error 17: Cannot mount selected partition" and to cap it all off if i attempt to load XP all i see is the message "Starting Up..." along with a blinking cursor and it hangs, I have left it for an hour with no change.

EDIT: I've downloaded the superGRUB cd and made it back to XP. Still having difficulties otherwise.

I hope i've provided enough details. Thanks in advance.

---

### Post by caljohnsmith on 2008-11-02
How about trying this on start up: when you get the Grub menu, select the first Ubuntu entry, press "e" to edit it, select the line that says "root (hdX,Y)" where X and Y are numbers, press "e" to edit it, change it to "root (hd0,Y)", press return to save the change, then press "b" to boot. Based on the info you gave, I think that will probably be all it takes to boot Ubuntu. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent.

So if it works, when you get into Ubuntu, just do:
```
gksudo gedit /boot/grub/menu.lst
```
And change the line that says "#groot=(hdX,Y)" to use the (hd0,Y) that worked to boot Ubuntu. Save, quit gedit, then run:
```
sudo update-grub
```
And you should be all set, at least about booting Ubuntu. See if you can get this far, and if not, then please post:
```
sudo fdisk -lu

```
Let me know how it goes. :)

---

### Post by o32 on 2008-11-02
Thanks, now i just have to sort out the XP problem.

---

### Post by caljohnsmith on 2008-11-02
Open up your menu.lst again and add the following at the end:
```
title Windows
root (hd0,0)
chainloader +1
```
And let me know if that works. If it doesn't, the please post the output of:
```
sudo fdisk -lu
```
And we can work from there.

---

### Post by o32 on 2008-11-02
Success!

---

