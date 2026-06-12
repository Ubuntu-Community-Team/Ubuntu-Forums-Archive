---
title: "USB install works fine until I change anything..."
date: 2008-01-18
forum: Installation &amp; Upgrades
---

### Post by shaunconn on 2008-01-18
HI

I've installed 7.10 on a USB stick, as per these instructions:

[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

And it works fine.  Right until I change anything (add a user, change a password, update video drivers).  Once I make a change, next time I boot, I get "No boot sector found".

To fix it I boot from cd, install lilo and run lilo -M on the USB drive, and then it boots once.

Anyone got any suggestions on what I'm doing wrong?

Shaun

---

### Post by wolfen69 on 2008-01-18
i also have a flash drive install of gutsy which works great. the thing is, i found out it is not a perfect science by any means. it is probably not your fault that it is not working. i found that sometimes it works and sometimes it doesnt. the best thing you could do is just re-install it until you get it working. it took me a few tries, but i finally have a persistant gutsy flash drive.

btw, how big is your flash drive? on the site it says you can use a 1gb drive, but you wont be able to make and save changes. 4gb flash drives are cheap now. get one if you can.

---

### Post by shaunconn on 2008-01-18
Hi

Its a 4Gb drive, and I don't think its the install.  I've re-installed 6 times so far, and it boots perfectly each time, until I make a change.

So I'm assuming its something to do with it not liking changes, but not sure where to look!?

Maybe I should try another distro?

:-(

Shaun

---

### Post by shaunconn on 2008-01-19
Hi

I don't know if this helps, but I can reproduce the problem perfectly now...  Once I've built the drive, ran syslinux, etc, it boots first time - so I know there is a boot sector.

When I reboot, it always fails with "No boot sector on USB drive", and my only option is to boot from CD.

I've tried grub (no luck), and even copied the mbr.bin manually, but the same thing always happens.  Its as though ubuntu is overwriting the boot sector when it shuts down, so that it doesn't restart....

Any ideas, anyone?


Shaun

---

