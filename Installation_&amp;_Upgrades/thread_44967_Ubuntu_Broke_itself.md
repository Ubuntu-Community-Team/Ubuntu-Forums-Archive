---
title: "Ubuntu Broke itself??"
date: 2005-06-28
forum: Installation &amp; Upgrades
---

### Post by crummer32 on 2005-06-28
Last night I was on Ubuntu and it said it had an update to the Kernal or something I said ok and it downloaded and installed an update and said everything went ok. For the rest of the night I used windows. This morning I tried going back into Ubuntu and it said it couldnt mount the specified partition or something like that (I dont remember the exact wording)

What happened? Any Ideas on how to fix it?

---

### Post by mingus on 2005-06-28
[QUOTE=crummer32] . . .it said it couldnt mount the specified partition or something like that (I dont remember the exact wording)

What happened? Any Ideas on how to fix it?[/QUOTE]

That's just not enough to go on.  Pls reboot, note exactly where the error occurred and what the message was, and post that back here.

---

### Post by crummer32 on 2005-06-28
OK I went back and got the full error message so Here Goes...

When I choose the OS it immediately goes to this screen...

> 

Booting 'Ubuntu, kernel 2.6.10-5-AMD64-Genaric Default

Root (hd0,2)

Filesystem type unknown, partition type 0x5

Kernel /boot/vmlinuz root=/dev/hda3 ro console=ttyo Quiet Splash

Error 17: Cannoy mount selected partition

Press any key to continue... 

When I hit a key it shoots be back to the OS select screen.

---

### Post by Morimando on 2005-06-28
a) it doesn't use the initrd that it used previously any more
b) somehow it didn't build the support for the FS of the root partition into the kernel any more

What you need to do is enter the Ubuntu environment via a Knoppix LiveCD (chroot and mount all drives including /proc then) and then make the initrd as needed (or configure your own kernel with the needed FSs built in).

---

