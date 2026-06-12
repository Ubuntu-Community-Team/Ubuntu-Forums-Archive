---
title: "Modify GRUB boot list?"
date: 2007-03-26
forum: Installation &amp; Upgrades
---

### Post by otto888 on 2007-03-26
is there any way to modify GRUB boot list so my XP (the booter thinks its vista:confused: )is on top?

---

### Post by Stickymaddness on 2007-03-26
> **otto888 said:**
> is there any way to modify GRUB boot list so my XP (the booter thinks its vista:confused: )is on top?

Edit /etc/boot/grub/menu.lst :)

---

### Post by floke on 2007-03-26
Edit the grub file:

sudo nano /boot/grub/menu.lst

And change the 'default' number to the Vista boot sequence. The first one on the list is 0

Always backup grub first:

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup

---

### Post by otto888 on 2007-03-26
I don't see the boot folder(I look in filesystem cause I can't see my Linux drive for some odd reason:confused: :confused: :confused: ) I have 6.10

---

### Post by otto888 on 2007-03-26
> **Steve.K said:**
> Edit the grub file:

sudo nano /boot/grub/menu.lst

And change the 'default' number to the Vista boot sequence. The first one on the list is 0

Always backup grub first:

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
could you explain how to? (my "vista" is at the very bottom)

---

### Post by floke on 2007-03-26
At the end of the first paragraph/section of the menu.lst file is a line starting with 'default' - its usually set to 'default 0' - which means that grub will boot up the first kernel/OS on the list. To set this to Vista you need to count through the Kernels/systems on your hard drive (starting with 0!) and change the 'default' number so that it points to Vista.

If you can't get to it via your PC then use a LiveCD. Go to system/administration/system monitor and check your HD to see which partition Linux lives on. Lets assume its called hda1 (though it might be sda1 or something).

So, to change grub you need to first mount the partition. So create a directory on your desktop: from the terminal type 'cd ~/Desktop' - then 'mkdir here'. This should create a directory called 'here' on the desktop.

Then mount the Linux partition to it:

sudo mount /dev/hda1[or whatever it is] ~/Desktop/here

... then open up grub for editing

sudo nano ~/Desktop/here/boot/grub/menu.lst

And make the changes to the 'default' line so it points to Vista

Save. Reboot. And all should be well.

If you have pointed grub to the wrong place simply follow the above steps to change the number.

Hope this helps.

---

### Post by otto888 on 2007-03-26
> **Steve.K said:**
> At the end of the first paragraph/section of the menu.lst file is a line starting with 'default' - its usually set to 'default 0' - which means that grub will boot up the first kernel/OS on the list. To set this to Vista you need to count through the Kernels/systems on your hard drive (starting with 0!) and change the 'default' number so that it points to Vista.

If you can't get to it via your PC then use a LiveCD. Go to system/administration/system monitor and check your HD to see which partition Linux lives on. Lets assume its called hda1 (though it might be sda1 or something).

So, to change grub you need to first mount the partition. So create a directory on your desktop: from the terminal type 'cd ~/Desktop' - then 'mkdir here'. This should create a directory called 'here' on the desktop.

Then mount the Linux partition to it:

sudo mount /dev/hda1[or whatever it is] ~/Desktop/here

... then open up grub for editing

sudo nano ~/Desktop/here/boot/grub/menu.lst

And make the changes to the 'default' line so it points to Vista

Save. Reboot. And all should be well.

If you have pointed grub to the wrong place simply follow the above steps to change the number.

Hope this helps.
is there a way to auto boot "Vista" in like.....1 sec? I can still access linux by pressing down very fast:)  ( I share a PC and my friend hates the boot loader:( )

---

### Post by JohnPhys on 2007-03-27
If you've set the default to vista (so that vista is the os that boots if you don't hit anything), you can just change the "timeout" line in the menu.lst file so that it's as many seconds as you want the bootloader to wait before booting the default.  It can probably only take integer values, so don't set it lower than 1!

---

### Post by floke on 2007-03-27
Yes, you can set it to 0 if you like - you can also uncheck the 'hidemenu' option so that the grub menu is hidden altogether.

---

### Post by arashiko28 on 2008-05-08
I have just installed Xubuntu, but I have Ubuntu on the same drive. Now, the GRUB points them both as Ubuntu and set Xubuntu as default. I want to change it back to Ubuntu to be the default, now Ubuntu shows under other OS's and Xubuntu has 2 extra entries, safe mode and memtest, BUT even guessing that should place 3 on the default, here's the catch, the xubuntu GRUB includes the first ubuntu installation, but the Ubuntu GRUB file, only shows it's own, I'm afraid of changing it and messing it... The first ubuntu installation has (0,0) as root and the Xubuntu (0,5) this is how I know who's who... can I change the names of the OS's????

---

