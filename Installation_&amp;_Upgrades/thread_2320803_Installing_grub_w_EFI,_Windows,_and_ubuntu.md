---
title: "Installing grub w/ EFI, Windows, and ubuntu"
date: 2016-04-17
forum: Installation &amp; Upgrades
---

### Post by cpdondo on 2016-04-17
OK, folks, I need some help.  I'm trying to install Ubuntu amd64 on a Lenovo stick computer.  I have it installed, I have managed to install grub to the main boot partition so that it comes up.

But.....  It comes up to 

grub>

I seem to remember that there is a way to manually scan the system for other OSs and have grub build the menu, but I can't find it.

I've tried 

dpkg-reconfigure grub-efi-ia32

but that just installs it in the MBR, and does not scan the storage devices.

So...

What is the magic that will get grub to build the menu automatically by scanning the installed OSs?

---

### Post by cpdondo on 2016-04-17
OK solved.

update-grub

did the trick,

And how do I mark the thread solved?????

---

