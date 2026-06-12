---
title: "Change installation kernel"
date: 2005-04-19
forum: Installation &amp; Upgrades
---

### Post by rejser on 2005-04-19
Is there an option in the base install so one can change default kernel? (for example,686 instead of 386)

---

### Post by laka on 2005-04-19
You can just use Synaptic. You'll find it under System -> Administration -> Synaptic Package Manager.

---

### Post by rejser on 2005-04-19
did that. But is there more to do than just download?

(maybe change the menu.lst)

Should I reinstall grub? I changed menu.1st to include the new kernel. But not working. the best I get is

kernel panic - not syncing: VFS: Unable to mount root fs on unknown block (0,0)

Is the ext3-module missing from a standard install kernel?

(ps, I run kubuntu)

---

### Post by Nob on 2005-04-19
[QUOTE=rejser]did that. But is there more to do than just download?

(maybe change the menu.lst)

Should I reinstall grub? I changed menu.1st to include the new kernel. But not working. the best I get is

kernel panic - not syncing: VFS: Unable to mount root fs on unknown block (0,0)

Is the ext3-module missing from a standard install kernel?

(ps, I run kubuntu)[/QUOTE]
 in grub, you need to edit grub.conf file in /boot/grub
and be carefull, in grub, for example, hda1 is hd0,0 - and so on.... hdc4 = hd2,3 :)

---

### Post by az on 2005-04-19
[QUOTE=rejser]did that. But is there more to do than just download?

(maybe change the menu.lst)

Should I reinstall grub? I changed menu.1st to include the new kernel. But not working. the best I get is

kernel panic - not syncing: VFS: Unable to mount root fs on unknown block (0,0)

Is the ext3-module missing from a standard install kernel?

(ps, I run kubuntu)[/QUOTE]

When you install a new kernel, you get an updated menu list, so it is not neccessary to change it for yourself.

You should always have the optionof booting back into your old kernel.

---

### Post by laka on 2005-04-19
That's right, you shouldn't have to change your grub.conf - so maybe the problems is that you did?

---

### Post by scarymonkey on 2005-04-19
I get a similar error. I notice that when using synpatic to install linux-686 and dependancies I get the following

Setting up linux-image-2.6.10-5-686 (2.6.10-34) ...
cpio: (0xffffe000): No such file or directory
cpio:   /lib/ld-linux.so.2 (0xb7feb000): No such file or directory

I believe this could be the reason why trying to use the 686 kernel on reboot results in kernel panic. My knowledge of linux is too weak to actually fix this at the moment. I am just glad I left the 386 kernel installed to boot to.

---

