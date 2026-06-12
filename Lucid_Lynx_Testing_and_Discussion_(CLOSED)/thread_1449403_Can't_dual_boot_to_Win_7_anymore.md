---
title: "Can't dual boot to Win 7 anymore"
date: 2010-04-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by seattle vic on 2010-04-07
I'm using Lucid (10.04) and for some reason today, when I tried to dual boot to Windows 7, nothing happened and the machine basically did a cold start and sent me back to the grub menu.

Here's what I currently have in grub for the windows boot:

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,0)'
	search --no-floppy --fs-uuid --set 1a04c0e504c0c54b
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###


Could this be an issue with the MBR?

---

### Post by Mark Phelps on 2010-04-08
Since Lucid is still in beta testing, you should be posting your questions to the beta testing forum: Development & Programming, Lucid Lynx Testing.

I'll be asking the Mods to move this thread there.  Look there for replies.

---

### Post by philinux on 2010-04-08
Moved to lucid testing.

---

### Post by kansasnoob on 2010-04-08
Please post the full output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by seattle vic on 2010-04-08
I actually got frustrated and decided that I really wasn't using win 7 for anything but the occasional game, so I loaded 10.04 on the 1st drive and of course it did fix the grub stuff for both drives.

However, now I have a question re: grub 2.  If you're not supposed to edit grub.cfg like we used to edit menu.cfg, what do I do to get the order of boot-up options changed.  Now the default is drive 1, but I want it to be drive 2.

---

### Post by clhsharky on 2010-04-08
HI

You can learn about grub2 here

[https://help.ubuntu.com/community/GRUB2](https://help.ubuntu.com/community/GRUB2)

till some one can be more helpful than I.


Sharky

---

