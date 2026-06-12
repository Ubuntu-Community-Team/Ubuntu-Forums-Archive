---
title: "Upgrade broke my install of Ubuntu"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by DaveGiant on 2011-10-14
I upgraded my computer with the update manager.

It went horrifically wrong. I had like 4 errors. I then got a message which said that my computer may now be unusable. This message did not fill me with confidence.

I restarted my computer and bam. Dead.

I restarted again it said that I had a - crap I forget - compression or decompression error. One of the two.

I restarted again and I can boot into the previous version of Linux. Both the default version and safe mode version of the latest version are broken and show the same de/compression error message.

Question. Before I wipe my computer again... I literally installed Ubunutu 3 days ago...

Is there any way I can fix the install from the previous version of Linux?

---

### Post by matt_symes on 2011-10-14
Hi

What is the exact error message. Post it here.

Kind regards

---

### Post by DaveGiant on 2011-10-14
Thanks for replying. The prefix for this thread should be ubuntu, not solved. I misclicked...

Message
> Uncompression error
 -- system halted

---

### Post by coffeecat on 2011-10-14
> **DaveGiant said:**
> The prefix for this thread should be ubuntu, not solved. I misclicked...

Changed it for you. :)

---

### Post by matt_symes on 2011-10-14
Hi
> 
                             Uncompression error
 -- system halted                      When exactly are you getting this error ? After the grub menu screen but before you get to the login screen ?

I am wondering if you have a corrupted initramfs. If so you might want to chroot into your drive from a liveCD/USB and rebuild it.

Kind regards

---

