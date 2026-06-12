---
title: "Server update from 10.04 to 12.04 wrong kernel?"
date: 2012-04-30
forum: Installation &amp; Upgrades
---

### Post by zorglubx on 2012-04-30
After having 3 flawless upgrades of ubuntu server 10.04 to 12.04 the 4'th did go quite wrong.

Like someone else here, I had an issue with the bootloader, ending up in grub prompt.
I booted on the super_grub2_disk_hybrid_1.99b1.iso and enabled LVM, then search for bootimages.

I successfully got into my system, and things seems pretty okay.
Though I have this on the login screen:
Welcome to Ubuntu 12.04 LTS (GNU/Linux 2.6.32-23-generic-pae i686)

Instead of the other server I have updated (successfully):
Welcome to Ubuntu 12.04 LTS (GNU/Linux 3.2.0-24-generic-pae i686)

My grub is still "unrepaired" but the OS is running, obviously I would love to get it repaired before I need to reboot next time.
Can you explain why I am running an old kernel, after the upgrade.. nothing while updating looked to be going wrong, except a thing with phpmyadmin, that I was going to fix afterwards.

---

### Post by zorglubx on 2012-04-30
The kernel problem, I think I have solved with running:
apt-get install linux-image

And aftewards:
update-grub

Output is: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-24-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-24-generic-pae
Found linux image: /boot/vmlinuz-2.6.32-41-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-41-generic-pae
Found memtest86+ image: /memtest86+.bin
done

I just hope it can boot properly now, unfortunately I am not able to test it right now.

Is there a place I can check for logs on the update process, to see if anything else went wrong?

---

