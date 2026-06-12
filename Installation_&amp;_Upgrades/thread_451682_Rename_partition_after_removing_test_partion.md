---
title: "Rename partition after removing test partion"
date: 2007-05-22
forum: Installation &amp; Upgrades
---

### Post by justinae on 2007-05-22
I repartitioned my hard drive so I could test my video card and got it to work. Since I obviously wanted to keep that partition I used Gparted Live CD to remove the original partition and resize the test one.

My partitions now look like this:
/dev/hda3 is ext3
/dev/hda2 is extended
       /dev/hda5 is linux-swap

When I boot up I get a menu that asks me which operating system I want to load. The old one doesn't exist anymore ( I tested and it said no partition exist). So my questions are:

1. How can I remove the prompt to choose an operating system?
2. Can I rename my partitions so they are:
hda1 ext3
hda2 extended
hda3 linux-swap
and if I do that would that effectively remove the OS choice prompt?

many thanx!

---

### Post by bulldog on 2007-05-22
I don't think you can rename them,but why should you?

---

### Post by justinae on 2007-05-22
yeah renaming isn't the top priority, it's mostly just cause i'm OCD and want them to be numbered starting at 1, but the boot option menu I want to go away.

---

### Post by bulldog on 2007-05-22
If you want to boot into your OS without seeing grub,you have to edit the menu.lst.
Boot ubuntu and open the menu.lst with a texteditor.
```
gksudo gedit /boot/grub/menu.lst
```
Find the section which says 'hidden menu' and remove the # in front of it,save the file and you're done.

---

### Post by justinae on 2007-05-22
I opened up the file and it says:

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.

I can just remove it but is there some reason that Debian installer is putting it in there automatically when that partition doesn't even exist? What is Debian installer? and can I edit that?

---

