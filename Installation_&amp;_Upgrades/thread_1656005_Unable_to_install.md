---
title: "Unable to install"
date: 2010-12-30
forum: Installation &amp; Upgrades
---

### Post by Moustache Chef on 2010-12-30
Hello, I have a very big problem here. First a little background information. I tried searching this forum but didn't find anyone with similar situation.

I have installed Ubuntu and it's variations many, many times on different computers, and once in my current desktop PC. Right now I am in a situation where I want to install Ubuntu 10.04.01 (or any version, really) but I cannot.

I have tried to install both 32-bit and 64-bit versions, I have tried Ubuntu 10.04.1 and 10.10, I have tried to install with Wubi (currently running Windows 7 64bit), I have tried to burn the images to CD and created an USB installer, nothing works, it's always the same. Installer starts, I put in "Install Ubuntu", and the screen goes blank. **Nothing but a white little cursor blinking in upper left corner of screen. And I cannot type in anything.**

Previously I had Ubuntu 10.04 installed with Wubi, and it worked. Right now, nothing works. Anything helpful appreciated. I can provide some system info if needed.

---

### Post by supershin on 2010-12-30
It sounds like you downloaded the server edition instead of the desktop. The server doesn't have a gui, it command line only. Check that out.

---

### Post by Moustache Chef on 2010-12-30
I have downloaded both the desktop installation and alternative installation, and none of them work for me. Neither USB or CD worked, and I have installed Ubuntu, Xubuntu, Lubuntu and Kubuntu succesfully before, using the very same methods I am using now.

---

### Post by IWantFroyo on 2010-12-30
It might be an acpi problem. That hits a few bits of hardware, but not all, which would explain the sudden Ubuntu problem. I know that if you install within windows, and restart, select Ubuntu, then press e while over generic, you get a screen with some lines of stuff in it. Find something that looks like this: /boot/vmlinuz-2.6.35-........=/dev/sda
change it to:
/boot/vmlinuz-2.6.35-........=/dev/sda.....=/dev/sda ro acpi=off noapic
or if you're not installing in windows, I think you can just go into grub and type acpi=off and boot.

---

### Post by Moustache Chef on 2010-12-30
Hey and thanks for your post. My main problem is that the installer freezes before it actually does anything. I just tried to install Linux Mint Julia, downloaded the linuxmint-10-gnome-cd-amd64.iso file and burned it to CD. I booted the CD, and it threw in a couple of lines and said "Ready." Then my computer went idle and nothing happened. 

Aww so frustrating, especially when I have never ever had any problems installing any Linux distro before :(

---

### Post by supershin on 2010-12-31
Could be a hardware problem, most likely hard drive. Did you reformat the partition before doing the install.
[COLOR="Red"]
NOTE: FORMATTING A PARTITION ERASES ALL DATA ON THAT PARTITION.[/COLOR]

---

