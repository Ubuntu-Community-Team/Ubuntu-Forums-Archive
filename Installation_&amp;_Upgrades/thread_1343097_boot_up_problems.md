---
title: "boot up problems"
date: 2009-12-01
forum: Installation &amp; Upgrades
---

### Post by silbermm on 2009-12-01
After installing ubuntu 8.04 and rebooting, I get this error:

Starting up ...
[  40.275539] i8042.c: No controller found.
Loading, please wait...
   Check root= bootarg cat /proc/cmdline
   or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/743d2a68-3f97-4e3bac4c-770d12186bb9 does not exist. Dropping to a shell!



When I do an ls /dev/disk/by-uuid/ I can see that it is not the same string as the one above... Any thoughts on how to fix this?

---

### Post by darkod on 2009-12-01
You can download the script from the link in my signature, and depending where it's saved execute it, for example if on desktop:
sudo bash ~/Desktop/boot_info_script*.sh

It will create results.txt file that will show a lot info about your boot process. Copy the content of that file here. Please wrap it with CODE tags, use the # button from the toolbar, to make it easier to read.

---

### Post by silbermm on 2009-12-01
problem is that I can't get to the desktop, or anywhere for that matter, to download the script and run it...

---

### Post by darkod on 2009-12-01
No problem. A very good feature of the ubuntu cd is that you can boot with it, select Try Ubuntu option and that will give you fully working ubuntu from the cd. You know what to do from there. Most people who get problems booting the computer use the cd and Try Ubuntu option. It even gives you internet access so you can run the script and post the results without rebooting your computer.
And if we can notice the problem and give you some advice, you can do the commands while still in it. :)

In fact, that's how you repair grub2. I was waiting for the results first to tell you that.

---

