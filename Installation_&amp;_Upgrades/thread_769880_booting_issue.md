---
title: "booting issue"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by rhaven on 2008-04-26
Hi,

I ran the following command grub-install "(hd0)" && update-grub. 

This updated me to grub 1.96. Now however I can't get windows to boot. I know I need to edit grub.cfg but no mater what I do I cant get the system to boot windows. This is what my menu.lst entry for windows looks like. 

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

my grub.cfg entry looks like this

menuentry "Microsoft Windows XP Professional" {
	root=(hd0,1) ##grub 2 uses 1 instead of 0##
	savedefault
	makeactive
	chainloader +1
}


If it is not possible to launch windows from 1.96. Can I chainload to grub legacy from grub 2, or revert everything back to grub legacy?

Thank you

---

### Post by rhaven on 2008-04-27
Hi,

After some more searching I came accros [http://ubuntuforums.org/archive/index.php/t-565124.html](http://ubuntuforums.org/archive/index.php/t-565124.html)

I followed those same steps and it works

---

