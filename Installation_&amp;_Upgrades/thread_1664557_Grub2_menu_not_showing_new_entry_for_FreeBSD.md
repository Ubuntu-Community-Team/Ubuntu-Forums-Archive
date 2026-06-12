---
title: "Grub2 menu not showing new entry for FreeBSD"
date: 2011-01-11
forum: Installation &amp; Upgrades
---

### Post by pennypecker on 2011-01-11
Hello,

   I've just installed  FreeBSD 8.1 on /dev/sda4 (FreeBSD slice), without installing the boot loader from FreeBSD (I've selected None when prompted for boot loader in sysinstall). Now I want to use my existing Grub2 from already installed Ubuntu 10.10 to boot FreeBSD also. After some reading, I've added to the end of /etc/grub.d/40_custom: 

menuentry "FreeBSD 8.1-RELEASE amd64" {
	set root=(hd0,4)
	chainloader +1
}

After running sudo update-grub, grup.cfg file shows my new entry. 
[LIST]
The problem is that after restart, I don't see the new entry in the grub menu.
[/LIST]
[LIST]
Another question, If i used chainloader +1, that means I need to have the FreeBSD bootloader installed also on /dev/sda4 right? For chainloading booloaders?
[/LIST]
I didn't get to that step, I first want to see the entry in the menu. 
Any idea what I might be missing/misdoing? (I also checked for blank spaces in the menuentry like the wiki for grub2 says)

Thanks for any suggestions

---

### Post by pennypecker on 2011-01-11
Me again,

   I solved the issue. 
The problem was the I had [_burg_]("https://help.ubuntu.com/community/Burg/") (the brand new grub) in use not grub. I figured that when I used "sudo grub-install /dev/sda" command that correctly positioned all the entries I had in 40_custom file.
   With burg, I modified the file /etc/burg.d/40_custom to get the same effect. 
Hope this info may help somebody.

---

