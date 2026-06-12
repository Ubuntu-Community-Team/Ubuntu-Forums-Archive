---
title: "Grub mess"
date: 2008-11-13
forum: Installation &amp; Upgrades
---

### Post by dakkar9999 on 2008-11-13
Ok, after intalling Ibex and trying for a while, I was getting a lot of lock up and all, so I decided to go back to 8.04.

But my 8.04 install was a wubi.  I decided to transfer the wubi install to its own hd using lubi.

Configuration as follow.

/dev/sda = boot window and wubi
/dev/sdb = storage hd
/dev/sdc = my newly transfered 8.04 install

If I choose to boot from  /dev/sdb, I have press escape then point to the new ubuntu 8.04 install (default would load the old wubi install).  Then I get a grub error 15.  If I press e to see the lines it shows root()ubuntu...

If I manually insert (hd0,0) then boot, it boots ok in the new install.

But if I try to save my changes by going through the terminal 

sudo grub
root (hd0,0)  it tells me that it's a 017 partition (or something like that, I'm writing from memory) and it can't save the change.


If I change the boot drive to /dev/sdc, I encounter the same problem, except I am presented with the new install as the first grub instead of the window/wubi grub.  I also get the grub error 15.  Then, if I manually change the root target (hd0,0), it does boot.

Lastly, the grub is now very messy, wich multiple entries for windows and ubuntu.

What are your suggestions?

Thanks!

---

### Post by caljohnsmith on 2008-11-13
Go ahead and boot into your new sdc Ubuntu install, open a terminal (applications > accessories > terminal), and do:
```
gksudo gedit /boot/grub/menu.lst
```
And then you can edit your menu.lst so that the Ubuntu entries use (hd0,0). Also be sure to change the "# groot=(hdX,Y)" line to also use (hd0,0). Once you are sure your new sdc Ubuntu works OK, you could go ahead and uninstall your Wubi version by going to "Add/Remove Programs" in the Windows Control Panel, and then you shouldn't get any option to boot Ubuntu from the Windows boot loader menu. Let me know how it goes. :)

---

### Post by dakkar9999 on 2008-11-13
Yup!  You did it again!  Thanks!

I'm starting to know my way around Grub thanks to you and the Ubuntu community!

---

### Post by caljohnsmith on 2008-11-13
Yes, you are obviously catching on really fast with this Grub stuff. Glad you were able to successfully move your Wubi installation over and get it working; that's no small feat. Anyway, cheers and have fun with it. :)

---

