---
title: "Error updating fresh install of Xubuntu 14.04.3"
date: 2015-09-26
forum: Installation &amp; Upgrades
---

### Post by kevinu2 on 2015-09-26
Hi,

I got this error message whilst updating a fresh installation of Xubuntu 14.04.3:

"Preparing to unpack .../onboard_1.0.1-0ubuntu1_i386.deb ...
Unpacking onboard (1.0.1-0ubuntu1) over (1.0.0-0ubuntu4) ...

(gtk-update-icon-cache-3.0:7530): GdkPixbuf-WARNING **: Cannot open pixbuf loader module file '/usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache': No such file or directory

This likely means that your installation is broken.
Try running the command
  gdk-pixbuf-query-loaders > /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
to make things work again for the time being."

Actually this error occured twice.

Should I be concerned about it?!

Thanks!

---

### Post by grahammechanical on 2015-09-26
Only if on restart the OS is indeed broken should you be concerned.

Write down the command that is recommended. If the system is broken then at the Grub boot menu select Advanced options for Ubuntu>recovery mode>Root and enter that command. Then type exit and when back at the recovery menu select Resume.

I run the development version of future releases of Ubuntu. I have been doing this for about three years. I have seen that warning a few times and only once has the OS been broken. But I do keep a record of that command written somewhere handy.

Regards.

---

### Post by kevinu2 on 2015-09-26
Thanks for your reply. There is no obvious problem with the system on reboot.

When I try to execute that command at a normal terminal window I get " permission denied". If I preface the command with "sudo" I am not asked for my password and still get "permission denied". I am a bit of a newbie so sorry if I am making some basic errors!

---

### Post by kevinu2 on 2015-09-26
Actually - my system may be "broken". I tried to install VirtualBox from the Software Centre and got error messages - including an "internal error" when trying to report the error! Not my day. A bit disappointed with Ubuntu really - I thought this version would be very stable. :(

---

