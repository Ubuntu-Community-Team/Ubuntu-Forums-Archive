---
title: "Latest update: broken boot - can't enter LUKS passphrase"
date: 2008-10-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by TheFinePrint on 2008-10-10
I am able to write this by using "use last successful boot", which results in broken graphics driver (module-version != kernel version).  That is however not the issue.

The issue is that I cannot authenticate.  I have a keyscript that first looks for a special usb-key with a keyfile.  This fails (but works with the last kernel/initrd), although I am sure the script runs.  I am also sure that the USB works,etc.  With regards to the passphrase I can't enter it.  Usually I get asterixes when I type the password, but now it doens't indicate anything.

Clearly something is broken with either the kernel or initrd when used with cryptsetup.  How to rectify?

---

### Post by TheFinePrint on 2008-10-10
I just tried updating to the latest kernel - 2.6.27-7.  Still having the same problem.  In fact I can only get a normal boot (with normal screen resolution, etc) by explicitly booting 2.6.27-5 (or presumably older).

Remaking the initrd-image for all kernels didn't change anything.

Any suggestions to either what did this, or better yet how to fix it? Is anything USB-related removed from the ...-6 and ...-7 initrd or kernel?

---

