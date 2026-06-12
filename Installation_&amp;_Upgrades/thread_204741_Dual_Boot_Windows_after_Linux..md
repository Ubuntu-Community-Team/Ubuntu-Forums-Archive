---
title: "Dual Boot: Windows after Linux."
date: 2006-06-27
forum: Installation &amp; Upgrades
---

### Post by gommle on 2006-06-27
I want to install Windows XP so i can dual boot, but i've heard Windows deletes GRUB? So what exactly is the easiest way to install Windows now, while keeping my stuff in Ubuntu and being able to boot both OSes?

I got enough unallocated space to install it without resizing any partitions.

Im running Ubuntu 6.06 if that matters.

---

### Post by Ubuntuud on 2006-06-27
Install windows, and after that, install grub again.

---

### Post by Raistlin355 on 2006-06-27
It has been my experience with dual-booting (all of my systems are dual boot as I have a family of pc gamers) that you must install windows first then linux, I don't believe that there is a way to install windows after linux is installed and be able to use it.  You are correct in thinking that windows takes over the boot loader.

---

### Post by gommle on 2006-06-27
Thanks.

So what are the steps to reinstall grub?

From what ive read in the forums, you boot the install disk and enter rescue mode, then write some commands?

Edit: I found this: [http://ubuntuforums.org/showpost.php?p=117829&postcount=2](http://ubuntuforums.org/showpost.php?p=117829&postcount=2)

Thats it right?

---

### Post by ajmoncrief on 2006-06-27
It is better to install linux after windows, but that doesnt mean that it is impossible to do the other way around.  I know this can be done b/c Ive done it before, try googling dual boot windows linux

---

### Post by kavanutz on 2006-06-27
[QUOTE=gommle]Thanks.

So what are the steps to reinstall grub?

From what ive read in the forums, you boot the install disk and enter rescue mode, then write some commands?

Edit: I found this: [http://ubuntuforums.org/showpost.php?p=117829&postcount=2](http://ubuntuforums.org/showpost.php?p=117829&postcount=2)

Thats it right?[/QUOTE]

yes, that will update the master boot record that windows will wipe out after you install it.

... but, from rescue mode you may have to mount the / partition and chroot into it  before running the grub command

---

