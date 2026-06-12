---
title: "No option to boot into root shell"
date: 2011-12-22
forum: Installation &amp; Upgrades
---

### Post by Los Frijoles on 2011-12-22
So, after forgetting a "-a" when trying to add a group to myself I have removed my admin privileges on my system. So, naturally I thought..hmm the only way to fix this is to boot into the root shell. Problem: When I start my computer I don't get the fancy grub selection screen that lists the various kernels, the memtest, and ...the boot into root shell option. How can I make this show up? At the moment it just jumps from the BIOS screen right to the purple loading screen with Ubuntu in the middle and the dots beneath.

---

### Post by jsmtrd on 2011-12-22
Logging in as root is not an option in ubuntu. In ubuntu you always put sudo infront of a command you wont to run as root. Does sudo work for you? You could try something like ```
sudo ls
``` at the command line. It should ask you for your password then run the command as root.

---

### Post by Los Frijoles on 2011-12-22
The sudo command isn't working anymore (and neither are my updates or anything else that required admin privileges) since I am no longer part of the admin group. On my other computer (which runs Ubuntu 11.10 like this one) there is an option on the boot menu to log in to a root rescue shell, but for some reason this computer that I have messed up my account on doesn't even have the same boot screen.

EDIT: Used boot-repair-disk and it magically fixed the problem with seeing the boot menu. Apparently the default on Ubuntu when you only have one installed OS is to hide the boot menu (and a few minutes ago I found out about holding down shift during the whole process which also would have sped things up). Also, for anyone who happens across this looking for advice about getting locked out of sudo I found [this]("http://ubuntuforums.org/showthread.php?t=1376802") to be helpful.

---

