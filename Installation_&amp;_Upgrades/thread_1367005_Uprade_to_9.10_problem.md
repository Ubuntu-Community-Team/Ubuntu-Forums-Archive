---
title: "Uprade to 9.10 problem"
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by tao83 on 2009-12-29
Hi,
I'm fairly new to linux and I recently updated/upgraded our Ubuntu server from 9.4 to 9.1 through the GUI (I've done this in the past).

What I didn't realise until now is that during the upgrade when prompted if I should keep or replace the "menu.lst" file, I've always opted to keep it. (I believe this is the mistake that's caused all the problems).

Now, when I completed the upgrade from 9.4 to 9.1 and the system rebooted, the problems started (see attached screenshot of the bootup errors).

From searching through Launchpad site, I believe the mountall is having problems because the bootup is based on the old (un-updated) menu.lst so the choices listed are old kernels: presently display kernel 2.6.24-19-server, however, when I ran the command "uname -r" it's showing 2.6.31-14-generic.

So, it seems that I need to edit the grub config file (menu.lst) to reflect the appropriate kernel (2.6.31-14-generic) which is needed for 9.1 to mountall properly.

However, I can't seem to edit the file, I've tried the command: "sudo gedit /boot/grub/menu.lst" but it gives the error:

(process:6975): GTK-WARNING **: Locale not supported by C library. Using the fallback 'C' locale.

(gedit:6975): GTK-WARNING **: Cannot open display:

I've been booting from a live disc and going into Recovery section but other than that I'm stuck on how to actually fix this.

I've searched through Launchpad and tried many of the suggestions that seemed to be similar to my dilemma but none of them worked properly:

[LIST]
[*][https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/447747](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/447747)
[*][https://bugs.launchpad.net/ubuntu/+bug/128313](https://bugs.launchpad.net/ubuntu/+bug/128313)
[/LIST]
Any help or feedback would be much appreciated!
Thanks!

---

### Post by tao83 on 2009-12-29
Update:
It looks like it's a problem with the locale settings. I've attached the error when I run the command: locale

---

