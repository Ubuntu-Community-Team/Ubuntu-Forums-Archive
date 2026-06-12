---
title: "No internet + broken fglrx"
date: 2011-03-04
forum: Installation &amp; Upgrades
---

### Post by Howy on 2011-03-04
So I was just updating my kernel, as usual. But once again, it didn't run DKMS so it didn't add fglrx to the kernel. From previous experience, I just reinstalled it from the Xterm i got on boot. But this time, I have a problem... It doesn't connect to the internet. I am running it in a chroot right now, with internet connection on the LiveCD. The LCD works fine, and there are no issues in it. But when I try to run something like apt-get in the chroot, it can't get a connection. Neither does ping. I'd expect it to inherit the connection from the LCD, but it obviously doesn't.
So, does anyone have a clue on how to make it connect to the internet?
Or should i download the package manually through the LCD and install it in the chroot with dpkg?
Eventually, is there any way to add fglrx to the kernel without reinstalling?

Note that I only mounted the partition of the OS and chrooted into it. I didn't do anything more fancy.

---

