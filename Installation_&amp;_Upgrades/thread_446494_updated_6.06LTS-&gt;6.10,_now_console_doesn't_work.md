---
title: "updated 6.06LTS-&gt;6.10, now console doesn't work"
date: 2007-05-17
forum: Installation &amp; Upgrades
---

### Post by mabus42 on 2007-05-17
i upgraded from 6.06LTS to 6.10 rather successfully and can login fine via the gnome interface, but when i ctrl+alt+f1 to get to the console (or any of the other console tty's) the screen is all messed up and you can't see anything save for some flickering pixels.  when i switch back to the gnome console all is well.  otherwise, all of my network services ported fine and all other configurations.

this is installed on a dell optiplex gx110
pentium3 667MHz
256MB RAM
intel 82810E graphics

---

### Post by mabus42 on 2007-05-17
update... when booting into the recovery mode, this problem is not exhibited and i can use the console on tty1/2/3/4/5 just fine.  this is kernel  2.6.17-11-386

thanks

---

### Post by mabus42 on 2007-05-17
Well, for what its worth I did get the console working for the default grub kernel.

Basically i just told it not to use the splash screen... I also got rid of the quiet flag so that i see more verbose output of the startup on the console.

I changed /boot/grub/menu.lst from this:

title           Ubuntu, kernel 2.6.17-11-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-386 root=UUID=0a3f6a30-0b3f-443f-bdc7-70
20e552a903 ro **quiet splash** rootflags=data=writeback
initrd          /boot/initrd.img-2.6.17-11-386
savedefault
boot


to this:

title           Ubuntu, kernel 2.6.17-11-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-386 root=UUID=0a3f6a30-0b3f-443f-bdc7-70
20e552a903 ro rootflags=data=writeback
initrd          /boot/initrd.img-2.6.17-11-386
savedefault
boot

---

