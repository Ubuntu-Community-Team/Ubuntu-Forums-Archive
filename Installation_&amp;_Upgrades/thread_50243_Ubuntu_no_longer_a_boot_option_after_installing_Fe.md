---
title: "Ubuntu no longer a boot option after installing Fedora"
date: 2005-07-19
forum: Installation &amp; Upgrades
---

### Post by cinematography on 2005-07-19
Ubuntu is still in one piece and on my computer. I just can't get to it because the Fedora booter didn't include it as an option. Could someone please help me with this problem.

---

### Post by mingus on 2005-07-19
[QUOTE=cinematography]Ubuntu is still in one piece and on my computer. I just can't get to it because the Fedora booter didn't include it as an option. Could someone please help me with this problem.[/QUOTE]

If you search the Forums, you will find several threads on this question.

Here is one short-hand solution; there are others . . .

* Boot into Fedora.  
* Get into a terminal as root.  
* Mount the disk partition where Ubuntu's root (/) is installed (unless you used a separate partition for Ubuntu's /boot, in which case mount that partition).  For example:
#mkdir /ubuntu
#mount /dev/xxx /ubuntu   (where xxx is the partition number, like hda2)
* Use a text editor to open /ubuntu/boot/grub/menu.lst.
* Look down the file for the stanza where Ubuntu is booted, probably the first.  It will have lines that start with "root", "kernel", "init", etc.
* Copy those lines.
* Now open the menu.lst counterpart in Fedora; I'm guessing that it will be in Fedora's /boot/grub/ directory also, but you may need to search for it.
* You will see stanza's like in the Ubuntu file.  Paste what you copied into the file and save it.

When you reboot, the grub Fedora installed will show Ubuntu on the menu.

This procedure assumes you did not add or delete partitions on the disk in *front*  of where Ubuntu is installed, changing the partition sequence.  But OK if you added partitions after Ubuntu.

---

### Post by cinematography on 2005-07-19
It's hard to search for something when you don't know what you're searching for. Thank you very much for the help. I'll try it and see how it works out.

---

### Post by mingus on 2005-07-19
[QUOTE=cinematography]It's hard to search for something when you don't know what you're searching for.[/QUOTE]

Good point   :)

---

### Post by cinematography on 2005-07-19
Excellent! Your instructions worked perfectly! Thank you very much. :)

---

### Post by mingus on 2005-07-19
[QUOTE=cinematography]Excellent! Your instructions worked perfectly! Thank you very much. :)[/QUOTE]

You are quite welcome.

---

