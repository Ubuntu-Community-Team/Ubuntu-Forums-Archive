---
title: "Grub error on boot up can't get into any OS"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by jao on 2007-10-20
Hi I'm new to Linux. I tried installing it but ran into a lot of problems with my ATi card. I haven't had a sucessful install of it yet but now there's a GRUB error when I boot the system up. 

How can I get rid of the Linux corrupted install? Is there a way to bypass it and allow Vista to boot up?

Grub loading please wait...
Error 17

I've tried burning the supergrub image and booting from it but it doesn't seem to work. I can't boot from ubuntu cuz it never installed properly.

---

### Post by wanchai on 2007-10-20
How did you actually install, or attempt to install Linux? How did you partition your system?

Can you boot from your Ubuntu Desktop CD? If so, you should be able to install Grub from there, then mount your Linux partition and make sure that boot/grub/devices.map and boot/grub/menu.lst contain what you want. You can use fdisk -l (as root) to find out which partitions you have, and with vol_id you can figure out those UUID that you will find in Grub's menu.lst.

You can find some good tips in here: [http://ubuntuguide.org/]("http://ubuntuguide.org/").

You really need two computers, one that you work on, and one that's connected to the Internet so you still have Google and the forums.

---

