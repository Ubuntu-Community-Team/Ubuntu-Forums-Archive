---
title: "GRUB Error 1 What to do?"
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by flamezero86 on 2008-06-04
When I try to Start Unbuntu Error 1 comes up and says something about the menu.lst file has to be abosulute pathfile of blocklist. What do I do so I can boot Unbuntu?

---

### Post by logos34 on 2008-06-04
There's probably a typo in menu.lst.

Mount your root partition from the ubuntu livecd, and check.  You can either double-click on it in Places>Computer, then go to /boot/grub/menu.lst, or manually mount it in the terminal:

sudo mkdir /media/ubuntu

sudo mount -t ext3 /dev/sda1 /media/ubuntu

gksudo gedit /media/ubuntu/boot/grub/menu.lst


Copy it and post it.

---

### Post by flamezero86 on 2008-06-04
I don't understand that well, I'm still a novice at this thing

---

### Post by logos34 on 2008-06-04
What ubuntu are you running? Hardy?

Try this:

Reboot and select ubuntu on the grub menu, then press 'e' to edit.  Write down exactly what it says on root line, kernel and initrd lines.  Post it.  Maybe all you need to do is make a minor correction to one of those to get you into ubuntu.  

Also, can you boot the recovery kernel?

---

### Post by flamezero86 on 2008-06-05
Yes I am runnung Hardy, what do you mean by making a minor correction, as in what do I do?

---

### Post by logos34 on 2008-06-05
[error 1]("http://users.bigpond.net.au/hermanzone/p15.htm#1") means there's probably an error in menu.lst file, which is the file grub bootloader accesses at startup in order to find the kernel image and mount root partition.

You need to look it over and correct it.  But to do so you need to mount root partition from the livecd.

So either try the methods above, or if you're uncomfortable with the command line/terminal, load the desktop on the livecd and go to Places>computer>double-click on the ubuntu linux partition in the side pane, then navigate to /boot/grub/menu.lst.  Copy and paste it so we can help.

---

### Post by Fial on 2008-06-22
I'm having the same problem, when I go to edit, this is what I see:

find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel normal mode
intrd /ubuntu /install /boot /initrd.gz
boot

---

