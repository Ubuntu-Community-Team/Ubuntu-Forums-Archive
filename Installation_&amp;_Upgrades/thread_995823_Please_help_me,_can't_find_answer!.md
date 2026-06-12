---
title: "Please help me, can't find answer!"
date: 2008-11-28
forum: Installation &amp; Upgrades
---

### Post by bostock73 on 2008-11-28
So i'm trying to get ubuntu installed onto my external hardrive. 
I'm not a n00b when it comes to this stuff; yes my laptop is bootable from an external hardrive etc etc. 

Only thing is, when linux is installed i go to boot from my external but i get this error: Non system disk, or disk error. replace and strike any key when ready. 

I've heard this is because my external hardrive is too 'big' to boot from, or there are no boot files present. 

The only thing i can think of is where to install the MBR when completing the ubuntu installation; but i make sure i select my EHD and no my primary HD.

PLEASE RESOLVE THIS FOR ME. 

thanks guys.

---

### Post by Pumalite on 2008-11-28
What did you do to install Grub to the external MBR?

---

### Post by bostock73 on 2008-11-28
i'm new to linux. When you say grub, you mean the option that allows linux to boot?

This is probably what im missing. I installed it off an iso. What have i done wrong?

---

### Post by Pumalite on 2008-11-28
Do you know how to type in a Terminal?

---

### Post by Pumalite on 2008-11-28
Find what /dev is your USB. Do it in the Terminal running:
sudo fdisk -lu
(if you have one drive; your external probably will be /dev/sdb)
Install with a Live CD if you can boot one
At the partitioner; choose your external drive.
In step 7 of the installation; go to 'Advanced Tab' and replace (hd0) for your external drive(/dev/sdb1?)
Then continue the installation.
Before reboot edit /boot/grub/menu.lst (of your external drive)
And make 'groot' and 'root' (hd0,0)
Reboot, goi into BIOS and make your USB first in the boot order.

---

### Post by bostock73 on 2008-11-28
ok so i got everything upto the advanced option.
changed hd0 to sdb (which is my ehd).

But now, when i boot i get this message

Grub loading stage 1.5.
grub loading, please wait...
error 18


whats this?
thankyou so mmuch for your help

---

### Post by Pumalite on 2008-11-28
[http://users.bigpond.net.au/hermanzone/p15.htm#18](http://users.bigpond.net.au/hermanzone/p15.htm#18)

---

### Post by bostock73 on 2008-11-28
i got you dude.
Only thing is, i cannot understand the create a small boot sector at the start of the hd bit.

I understand why it needs to be there, just not how to go about making it! too complicated!

Could you simplify it for me please?

---

### Post by Pumalite on 2008-11-28
Make a 200 MB /boot partition at the beginning of the drive. Use Gparted Live CD:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.
Guides:
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

### Post by bostock73 on 2008-11-28
how do i actually go about doing that?
i make it then what? how do i tell it to go to the start of the disk?

how do i put my boot files in there?

too vague

---

### Post by Pumalite on 2008-11-28
You have to learn to use a partitioner to do what you want to do. Read carefully the Documentation. It's all there.

---

