---
title: "Confusion, Complications, but no conclusion. T_T"
date: 2008-07-13
forum: Installation &amp; Upgrades
---

### Post by Brokentubes on 2008-07-13
I recently tried for the installation of Ubuntu. Now, before we continue to what exactly my complication is, allow me to list my
hardware.

CPU: Pentium 4 2.93ghz
RAM: 1gb DDR2
HDD1: ST 177gb
HDD2: Maxtor 32gb
HDD3: Recovery

Now, I installed (At least from what the installation told me) Ubuntu on my second Hard Drive (Maxtor 32gb). All was well and
dandy, I restarted and completed the installation. But upon one
final reboot into the OS itself, it shot me into the Grub menu.

Then the problems started, it couldn't find a specific file. Some of you might now this as "Error15: File not found". Anyways I went into grub to see if I could find where exactly these files were residing. I tried:

```
find /grub/stage1
```

No luck, another File not found. Then I tried:

```
find /boot/grub/stage1
```

Still not luck, so I went into grub and changed
the root HD back and forth to see if it would actually
boot. Upon guessing it booted from "HD1,0" which is odd
considering that most people boot straight from "HD0,0".

Anyways, finally it was booting. I was planning to permanently 
change the root to it's proper location in the terminal.

But of course with my luck, which is none. It went straight into
busybox, now excuse me on my knowledge. But this is where I went
completely lost I have no idea to do from here and require some
fine assistance if possible. :confused: 

Thank you
~Brokentubes :)

---

### Post by Pumalite on 2008-07-13
Try editing your boot line at Grub. Hit 'e' and 'e' again. Try different partitions ( hd0,0), etc until you can boot.'b' to boot. Then edit your menu.lst accordingly.

---

### Post by Brokentubes on 2008-07-13
> **Pumalite said:**
> Try editing your boot line at Grub. Hit 'e' and 'e' again. Try different partitions ( hd0,0), etc until you can boot.'b' to boot. Then edit your menu.lst accordingly.

I tried that, I think I also wrote that in my original post.

But yes, I've tried so. But upon doing so it then pushes
me into busybox.

---

### Post by Brokentubes on 2008-07-13
Sorry, but any help would be appreciated...

---

