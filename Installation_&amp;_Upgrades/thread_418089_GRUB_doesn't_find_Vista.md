---
title: "GRUB doesn't find Vista"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by tormodfoss on 2007-04-22
I have Vista on my computer and have just installed Ubuntu, I didn't have any problems installing it and Ubuntu works perfect, but when I want to boot Vista Grub doesn't find it. Any solutions?

---

### Post by pepsi_max2k on 2007-04-22
Grub probably got the command for loading vista wrong. What's your partition setup like? One hard drive or two? Take a look at /boot/grub/menu.lst and find the option for Vista. You'll prolly have to change that a bit, but i couldn't tell you what to without knowing your partition setup and current grub menu.lst content.

---

### Post by dingofarmer on 2007-04-22
boot off of the vista cd and choose to fix the boot partition it will then correct the commands, I had the same problem on my laptop.

---

### Post by pepsi_max2k on 2007-04-22
> **dingofarmer said:**
> boot off of the vista cd and choose to fix the boot partition it will then correct the commands, I had the same problem on my laptop.

surely that won't fix grub, just overwrite it? and then no boot in to ubuntu?

---

### Post by tormodfoss on 2007-04-22
I've got one HD with Vista at partition 3. Can't find the content on the grub menu as I'm quite new to using the command line.

---

