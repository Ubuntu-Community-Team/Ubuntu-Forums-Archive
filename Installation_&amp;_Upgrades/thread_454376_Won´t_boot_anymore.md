---
title: "Won´t boot anymore"
date: 2007-05-25
forum: Installation &amp; Upgrades
---

### Post by MrZehl on 2007-05-25
Hello,

Ie installed VectorLinux on an other partition so my boot manager is overwritten. Since then I can boot Ubuntu anymore. Ie replced Vector Linux by PCLinuxOS but it didn recognise the Ubuntu installation.

What do I have to do to get Ubuntu booting again? Can I edit GRUB from the livecd? I don want to install Ubuntu all over again.

---

### Post by rillip on 2007-05-25
It's not really clear what boot loader the other distro is using.  If it's using grub, you can just edit the menu.lst and add ubuntu, if you know what partition it's insalled on.  If it's using something else, you can install grub from within any of the distros and it should auto-detect all of them.

---

### Post by MrZehl on 2007-05-25
> **rillip said:**
> It's not really clear what boot loader the other distro is using.  If it's using grub, you can just edit the menu.lst and add ubuntu, if you know what partition it's insalled on.  If it's using something else, you can install grub from within any of the distros and it should auto-detect all of them.

It&#347; GRUB on the bootsector of hda. 
Ubuntu is on sda1. Where do I find menu.lst and what line should I add?
Is there anything else I have to do if I add the line to menu.lst to get it in the bootsector or so?

---

### Post by rillip on 2007-05-27
The menu.lst is in /boot/grub

Here's what my entry looks like:

title           Ubuntu, kernel 2.6.15-28-k7
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-28-k7 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.15-28-k7
savedefault
boot

You'll want to change your Kernel number to match what you're using.  You can find that running 

uname -a

You see that root is pointed to hd0,2.  I'm honestly not sure if this line is important; root is actually mounted on hda3, as you can see on the line with the Kernel.  I'd try just ignoring that for now.  It'll either give you an interesting error message we can work with, or will work,  If really neccessary, I'm sure there's a grub manual out there that describes what the line does, but you'll have to look for it.

Hope that helps

---

### Post by MrZehl on 2007-05-29
Ubuntu boots but seems to be really damaged. The boot process isn't finished. It stops at checking my disks and I'm trown to bash. I get some error messages. The most important is:

Apt-get isn't installed. You can install it by typing apt-get install apt. 

It is quite clear that I can't install apt-get if I don't have apt-get. Can I fix this with the livecd, so I can apt-get install --fix-broken?

---

### Post by rillip on 2007-05-31
Frankly, I'd reinstall Ubuntu if you're getting all these errors.  You should back up the other entries in your menu.lst and then add them back when done (if they don't show up) so that you can boot into the others as well.

---

