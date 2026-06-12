---
title: "Will only boot to grub rescue when I upgraded (wubi installed) 10.04 to 10.10."
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by tjanss on 2010-10-11
Installed Ubuntu 10.04 a week ago or so (using wubi.)
Tried to upgrade to 10.10 from within Ubuntu using the update manager.
Now the PC will only boot to grub rescue.

When booting, this is what i get:
[FONT=Courier New][COLOR=Navy]error: no such device: cd200414-0606-4d7d-8c08-004e9b5dc92d.
grub rescue>[/COLOR][/FONT]

Three commands work: [FONT=Courier New][COLOR=Navy]ls[/COLOR][/FONT], [FONT=Courier New][COLOR=Navy]set[/COLOR][/FONT] and [FONT=Courier New][COLOR=Navy]insmod[/COLOR][/FONT].
The [FONT=Courier New][COLOR=Navy]ls[/COLOR][/FONT] command only yields: [FONT=Courier New][COLOR=Navy](hd0)[/COLOR][/FONT]
(no partitions like (hd0,1), (hd0,5), etc.)

I have no idea what to do... Any help would be greatly appreciated!

(Using an Asus UL30A without optical drive. Have managed to create a Live USB, which I'm currently using.)

---

### Post by Megaptera on 2010-10-11
Hi,
I think answer #4 at this similar thread may help you:

[http://ubuntuforums.org/showthread.php?t=1593269&highlight=wubi](http://ubuntuforums.org/showthread.php?t=1593269&highlight=wubi)

---

### Post by tjanss on 2010-10-11
Thanks! This solved my issue.

In short, this is what was recommended:
[LIST=1]
[*]Boot using an Ubuntu Live CD or USB.
[*]Open command shell.
[*]Enter: [COLOR="Navy"][FONT="Courier New"]sudo apt-get install lilo[/FONT][/COLOR]
[*]Enter: [COLOR="navy"][FONT="Courier New"]sudo lilo -M /dev/sda mbr[/FONT][/COLOR]
[*]Reboot. The windows boot loader should now be restored.
[/LIST]

---

### Post by Megaptera on 2010-10-11
You're welcome, glad it worked.

---

### Post by cimperski on 2010-10-11
I have similar problem, but my error says ELF header smaller than expect. anyone knows what I could do? I don't want to lose all data on my disk..

---

