---
title: "installed 11.10 386 on ASUS eeePC 904HA"
date: 2011-12-30
forum: Installation &amp; Upgrades
---

### Post by nariub on 2011-12-30
after using the alt-install disc (it is a laptop and i wanted an encrypted HD)
Network Manager wasnt managing the wireless.. 
the network was still working
update-manager updated
software-center didnt acknowledge the network existed..
 
found /etc/networking/interfaces had an entry for wlan0
commented these lines out..  rebooted..
NetworkManager is now managing all the interfaces as expected...
and software center now works...

last thing is ..
When i boot up
i get 
error: no video mode activated
then the computer boots right up ...
it seems to be cosmetic..  i have seen where i can stop the error by making 05_debian_theme non-executable..  

anybody got a real answer?

---

### Post by BC59 on 2011-12-30
Try using an Ubuntu 11.10 LiveCD to see if booting with it, your system is working. If it's working without problem, consider a normal installation.

---

### Post by nariub on 2011-12-30
Thanks,
I do not believe i will pursue your suggestion though.
the video mode error seems cosmetic.

---

### Post by nariub on 2012-04-27
Suspect the alternative iso is not properly setting the video mode in the kernel.
had the exact same issue on an 11.10 x86_64 install onto an E6510 

only things in common were 11.10 alternative disc, and Intel embedded graphics.

if the problem persists on the 12.04 alt disc, I plan to try 

sudo vi /etc/default/grub

on line with "quiet splash"
add
"quiet splash i915.modeset=1"

---

### Post by nariub on 2012-04-30
Hmm,
  i915 modeset did not fix it either.

new install with 12.04 amd64 alt disc, full disc encryption, has
error: no video mode activated

same as 11.10.  desktop disc without full disc encryption does not display this behavior.

upgrade from 10.04 full disk encryption to 12.04 full disk encryption does not display this behavior either.

---

### Post by nariub on 2012-05-22
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/699802/comments/24](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/699802/comments/24)

a font issue?
cant find stuff in /usr/share/grub

makes sense as this is in the encrypted LVM.

Will try the workaround to copy *.pf2 from /usr/share/grub to /boot/grub/

---

### Post by nariub on 2012-06-04
oddly,
the video mode error seems to have worked itself out without my intervention
noticed over the weekend that it was not doing it anymore.

curious.

---

