---
title: "how to change the startup to text mode"
date: 2010-02-16
forum: Installation &amp; Upgrades
---

### Post by snake_eyes on 2010-02-16
Hello,

I'm using in the server 8.4 and installed the package startupmanager which is GUI, through this package I can show the text during boot, unlike in the 9.10, I checked the "show the text during boot" same I did in the 8.4 bu It's not showing the text and still show the splash...

My question is how to change it direct from shell instead of the stupid GUI :)

Cheers,

---

### Post by konqueror7 on 2010-02-16
you can change it in your */boot/grub/menu.lst*...

you remove the 'splash' flag on the kernel entry...

---

### Post by snake_eyes on 2010-02-16
I don't have /boot/grub/menu.lst in my Ubuntu 9.10 :(

---

### Post by darkod on 2010-02-16
In Grub2 it's in /etc/default/grub

It has a line like GRUB_CMD.... ="quiet splash"

Delete it there and run:
sudo update-grub

---

### Post by konqueror7 on 2010-02-16
did you fresh installed? sorry for the misunderstanding,,,

8.04 and 9.10 have different GRUB version, so startupmanager only currently functions with the older GRUB version (still available in 9.04)...

anyway, heres the updated documentation for GRUB2, which applies to 9.10,,,[GRUB2]("https://help.ubuntu.com/community/Grub2")

hope it helped...

---

### Post by snake_eyes on 2010-02-16
> **darkod said:**
> In Grub2 it's in /etc/default/grub

It has a line like GRUB_CMD.... ="quiet splash"

Delete it there and run:
sudo update-grub

Yes, I found this line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash", I should delete the whole line or it's enough to delete the quoted ?

---

### Post by darkod on 2010-02-16
> **snake_eyes said:**
> Yes, I found this line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash", I should delete the whole line or it's enough to delete the quoted ?

No, no, just the splash word. I'm not too experienced with these options but the other person said delete the splash option and that's where you delete it. Even if the quotes are empty, the whole line has to remain in the file I think. Empty quotes will mean no options are added.

PS. Befor deleting anything there, you can test first how you like it and whether that's what you need. In the grub menu instead of hitting Enter hit 'e'. That will show the lines with commands for booting ubuntu. Delete the splash there first, maybe even quiet if that helps to get the full text while booting if that's what you want.
If you don't get grub menu at boot hit Shift to show it but you have to time it before ubuntu starts loading.

---

