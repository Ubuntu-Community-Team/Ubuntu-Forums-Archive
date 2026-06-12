---
title: "problem after kernel update"
date: 2005-06-17
forum: Installation &amp; Upgrades
---

### Post by ibrown on 2005-06-17
I've just done an update which updated the kernel. Now, when I reboot the system hangs before bringing up X. I suspect this is because I have the Nvidia kernel drivers ... and I also have a custom network driver installed.

Problem is I cannot now log-in to fix these things or to stop these modules loading. The update does not seem to give me the option to go back to the previous kernel either (this is a bti disturbing!)

I can boot in recovery mode but then I cannot get past the log-in. It's possible I set a root password and then forgot all about it because I always use sudo - stoopid I know.

Does anyone have any idea what I can do here. If I could just get it to boot to a console prompt without loading the nvidia drivers then I think I could fix it.

Ian

---

### Post by jerrykenny on 2005-06-17
hi  ibrown,


can you get hold of a "Gnoppix" live cd or similar. ?

try to log in with gnoppix, see if your old kernel is still there, and alter your menu.lst so your old kernel will be default,  or at least will be available. . . . 

Alternately,  if your boot manager is grub,  try to edit grub during boot . . . try pointing it to  /boot/vmlinuz-2.6.10-etc    very tricky as your doing it blind and you also need to give it the right initrd.img .


re the recovery mode password,  try     sudo passwd root

---

### Post by intangible on 2005-06-17
Try booting a live cd, then open a terminal, **sudo sh**, mount your hard drive like this:
**mkdir /myhda1**
**mount /dev/hda1 /myhda1**
then
**chroot /myhda1**
now your root directory is /myhda1, so everything acts like it is your normal system... so you can do:
**passwd root**
Log out of everything and restart, you should now have a new root passwd.

---

### Post by ibrown on 2005-06-18
Thanks for the hints. I had already tried searching for an older kernel, but there only appears to be the most recent one there.
In the grub command line typing /vmlinuz- followed by tab completes all the way to /vmlinux-2-6-10.5.gz (or something like that).

So, next step is to download a knoppix CD and try that method.

Like I said, I'm pretty sure the issue is that the kernel modules have not been re-compiled for this new kernel. I know how to do that for the module I installed, but how do I go about doing it for the nvidia drivers that ubuntu installed itself?

Ian

---

### Post by ibrown on 2005-06-18
Thanks for the help, it's working now.

I had a gentoo live cd which I used to change the "nvidia" in xorg.conf to "nv" and removed nvidia from /etc/modules. That allowed me to boot again.

Then, I recompiled my sk98lin module. Recompiled the alsa source module (needed for the creative media sound card). Then, I selected re-install inthe package manager for the nvida drivers and changed the entries in /etc/modules and xorg.conf back to what they were before.

whew ... messy but it all works again.

I am disturbed though that the update manager updated my kernel and deleted the old one. This meant there was no chance to go back to a working system. It should be possible to do the update and also keep the last known working kernel along with its modules on the system.
Also, I would have thought it would have recognised that the nvidia drivers would need re-compiling and done that automatically.

Ian

---

