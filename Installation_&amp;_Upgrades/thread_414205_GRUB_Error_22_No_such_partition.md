---
title: "GRUB Error 22: No such partition"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by theseeker on 2007-04-19
I just finished a clean install of Feisty. My system is dual boot linux/winXP. 
When the system starts, it loads normally Grub, I am able to toggle between Ubuntu, Ubuntu (recovery), memtest and Windows XP selections, but when I choose to boot Ubuntu, the following message appears:
Error 22: No such partition. 

To my surprise, when I choose to boot Windows XP, it boots normally!

Here is my /boot/grub/menu.lst:
```

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=9663cdaf-020e-4c52-897d-ffd3fc90cd3f ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=9663cdaf-020e-4c52-897d-ffd3fc90cd3f ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows NT/2000/XP
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

```
 
A second surprise comes when I boot from the Ubuntu Feisty alternate install CD, choosing the "Boot from first hard disk" selection. It loads Grub, and when I choose Ubuntu boot selection, it continues as it should in the first place! 

My system consists of 3 hard drives, 1 IDE and 2 SATAs.
I attach screenshots of what gparted shows below. 

I would appreciate your help. 

Thanx!

---

### Post by askreet on 2007-04-19
The only thing that comes to mind is that GRUB works off boot order for the hard disk numbering.  The only disk that doesnt have a valid index 2 (hdX,2) partition is the middle on, perhaps it should read (hd0,2)?  Boot into grub and press E over the menu option that doesn't work to try tinkering with it.  Once you get it working, edit the file from within Ubuntu.

Best of luck!
-Kyle

---

### Post by theseeker on 2007-04-19
Well, problem solved!

I changed root (hd1,2) to (hd0,2) and everything is fine now. 

Thanx a lot Kyle! :popcorn: 

Going to check Feisty's new features now!

---

### Post by askreet on 2007-04-21
Glad to hear that worked for ya.  I've had problems with Ubuntu's menu.lst generation before :)

Have fun!

---

### Post by chinita96 on 2007-04-22
Hi, I am actually having the same problem and when I did try the 'e' edit and typed in hd0,2 nothing happened. It still gives me the same error. My windows partition doesn't even show up on the grub list. This is after I just upgraded to Feisty and did a reboot. Grub just shows all the new ubuntu options and anyone I select I get the same "no such partition". I did notice the hd1,2 looked weird that's why I tried editing it to 0,2 and still nothing. I'm stuck. Is there anything else I could try?

Thanks.

---

### Post by lajevardi on 2007-12-10
Hi there,
I've the same problem here. I have installed Ubuntu(6.06LTS), when I restart system there was no grub menu! I have searched forums and found the solution to install grub manually.
> 
sudo grub
find /boot/grub/stage1
root (hd1,3)
setup (hd1)
quit

I have restart my system and the grub menu did appear. but when I choose Ubuntu to boot there's a Error 22 that is saying:
> no such a partition.
root (hd1,3)
So i decide to edit by pressing 'e' key. I have changed it to root (hd0,3) and it clearly began to boot.
Ubuntu is loaded from hard drive, I try to modify grub again, changing root(hd1,3) to root(hd0,3) and the terminal responses:
> 
grub> find /boot/grub/stage1
 (hd1,3)
grub> root (hd0,3)
Error 22: No such partition
grub>


I'll be so grateful..

---

### Post by theseeker on 2007-12-10
try editing the /boot/grub/menu.lst file instead!

---

### Post by lajevardi on 2007-12-10
I have edit menu.lst.. now it's ok. thanks for your help.
but there's another problem when i try to boot windows xp, this error appears:
> NTLDR is missing.

---

