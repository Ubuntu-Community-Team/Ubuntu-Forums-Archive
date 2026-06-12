---
title: "start failed"
date: 2005-09-03
forum: Installation &amp; Upgrades
---

### Post by hugoc on 2005-09-03
I have W2K and Ubuntu in my pc and I tried create a new partition but it failed, when I start ubuntu it can't do it because ocurred a "Kernel syncing" problem . What I can do to rescue my documents stored in my personal folders created in ubuntu? Thank for your help.

---

### Post by xmastree on 2005-09-03
Do you have a live CD? You could boot from that and maybe get to the documents.

---

### Post by hugoc on 2005-09-03
yes, I have but i CAN'T view folders and i don't knopw the commands for find it?

---

### Post by xmastree on 2005-09-03
I guess you'll need to mount the hard drive containing your work.

Boot up from the live CD, and make a folder in your home folder. Call it something like mounted.
Then, run this command:
```
sudo mount -t ext3 /dev/hda5 /home/mounted
``` And go look in that folder you just created. If it worked you'll be able to see your files.
I'm guessing that your linux partition is /dev/hda5, it may be different.

Having got that far, you need to find somewhere to back them up, like a thumb drive or a CDR.

---

### Post by hugoc on 2005-09-03
I did it but no functioned. I will give more information. When I start Ubuntu y recevie nest message:

Starting Ubuntu....
chroot:relocation error:/lib/tls/i686/cmov/libc.so.6: symbol_dl_starting_up,
version GLIBC_PRIVATE not defined in file ld-linux.so.2 with link time reference
Kernel panic-not syncing: Attempted to kill init!


Please tell me what I can do!!

---

