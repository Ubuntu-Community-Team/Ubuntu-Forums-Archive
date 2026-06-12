---
title: "After installing Karmic, can't boot Windows 7"
date: 2009-10-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rmx.dave on 2009-10-19
Hi all,

This might be an easy question. I've been away from Ubuntu for a while, since 8.04, and it seems that GRUB is a little different now. 

Here's my setup:
2 hard drives
hd0: 500GB SATA (100GB Win7 partition and 400GB data partition)
hd1: 200GB IDE (formatted to Ext4 and home of Karmic)

After the install nothing would boot. I inserted my Windows 7 disc to see if I could repair the MBR and get back into Windows, but it said that there were no operating systems on my machine. After fiddling around with my BIOS I got it to boot from the IDE drive but now I need a way for GRUB to see Windows 7 and allow me to boot from it. 

I can access the drives and mount them from within Ubuntu, and no data looks like it was lost. I think that somehow the MBR got touched during the install and now my computer doesn't know there's an OS on that drive.

Anyone know what I should do?

---

### Post by wilee-nilee on 2009-10-19
If you still have grub at the boot-up go to a terminal in Koala and run sudo update-grub

---

### Post by rmx.dave on 2009-10-19
Thanks. When I boot, it says "Loading GRUB" but it doesn't give me any option to esc or do anything. It just says that it's loading and after about 20 seconds the Ubuntu logo comes up.

EDIT: I just ran update-grub in a terminal and got this message:
Your /usr is broken, please fix it before call this wrapper!

---

### Post by rmx.dave on 2009-10-19
Okay I got update-grub working (I had to reinstall the grub-pc package), but it only sees the Linux images, no Windows.

---

### Post by rmx.dave on 2009-10-19
Okay well here's what I think is happening.

If I disconnect the 200GB hdd that holds Ubuntu and try to boot, GRUB still loads (and says disk error). What's more is that when I run the Windows 7 disk, it now sees my Windows 7 installation on C:\ (the 100GB part) and says it should be booting properly.

I think somehow I installed Grub only to that 400GB partition. So even though the correct bootloader for Win 7 is on the C:\ partition, I need to remove GRUB from the other partition. 

Any thoughts?

---

### Post by wilee-nilee on 2009-10-20
Since your using 2 hard drives I have never used more then on HD so I would wait for help though. You might try this forum there are lot of knowledgeable dual-booting multi HD users there. [http://www.ostalk.org/](http://www.ostalk.org/) I would not try to hit and miss fix this in that it makes it much harder to help you, wait for some qualified advice.

---

### Post by rmx.dave on 2009-10-20
Got it working late last night. 

Not sure exactly what I did, but I installed GRUB 1.5 and that created a menu.lst file and I was able to configure the boot options from there.

I can tell that its still looking to my 2nd NTFS partition for GRUB 2, and THEN it goes to my Ext4 drive to load GRUB 1.5. It takes a little longer to boot but I'll leave it this way until I upgrade my hard drives later next year.

Thanks!

---

