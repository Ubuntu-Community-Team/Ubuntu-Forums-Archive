---
title: "USB Keyboard"
date: 2005-11-10
forum: Installation &amp; Upgrades
---

### Post by Xevor on 2005-11-10
Hi,

I am new here and also to Linux.

I just received my Ubuntu CD and I wanted to install it but now there is a problem.

I only have a wireless USB keyboard and when the Installation starts you need to enter "SERVER" or "DEFAULT" and since my USB keyboard is not loaded I can't type anything. Is it possible to make some changes so my USB keyboard will be loaded? 

Actually its a little strange because my keyboard works when you can enter "DEL" or "F1" to skip the memory test or entering the BIOS setup.

Hopefully there is someone who can help me with this because I can't wait to install this OS.

---

### Post by earobinson on 2005-11-10
This is a bug (actualy I was wrong it is not a bug) with the installer, I would bugzilla it if I was you.

---

### Post by steelerguy on 2005-11-10
I had the same problem, I had to hook up an old PS/2 keyboard to get past that point.  Once installed, I had to again hook the old keyboard up to use the Grub menu.  To top it all off, gdm freezes if I use any of the menus and if I just type my username and password the window manager locks up.  Not a good first experience with Ubuntu.

---

### Post by Xevor on 2005-11-10
It works now.

I went to BIOS and there I saw something with: "Support USB Devices". This was disabled and when I enabled it I could type again in the installation.

I was busy with installing and then I had to choose a partition where to install the program but it looks like the partition will be formatted before installing the program. I can only select a partition and continue. Is there any way to skip the format of the partition?

Thanks!

---

### Post by earobinson on 2005-11-10
When this happened to me I went into my sis's room and punked her keyboard

[QUOTE=Xevor]It works now.

I went to BIOS and there I saw something with: "Support USB Devices". This was disabled and when I enabled it I could type again in the installation.

I was busy with installing and then I had to choose a partition where to install the program but it looks like the partition will be formatted before installing the program. I can only select a partition and continue. Is there any way to skip the format of the partition?

Thanks![/QUOTE]

Good to know for next time, thx

---

### Post by Xevor on 2005-11-10
> I was busy with installing and then I had to choose a partition where to install the program but it looks like the partition will be formatted before installing the program. I can only select a partition and continue. Is there any way to skip the format of the partition?

Anyone? :(

---

### Post by earobinson on 2005-11-11
Im not sure I understand, but I think you want to install ubuntu to a partition that has data all ready on it?

If so I do not think this is possiable, you could resize the partition then make a new blank one to install ubuntu to however. (But last time you proved me wrong so maybe you can do it again lol)

(Sorry for the late reply I failed to read the other half of your last post)

---

