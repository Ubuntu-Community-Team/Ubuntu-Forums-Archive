---
title: "Problems with new machines"
date: 2007-06-15
forum: Installation &amp; Upgrades
---

### Post by shoran on 2007-06-15
I have been installing Ubuntu 6.06 on older PIII's with no problems over the last few days.  My student group and I are preparing a large internet cafe for a public event that we are helping with.  We got 12 new HPs donated and suddenly all I get is a message that reads "Uncompressing LInux.... OK... booting from kernel" 

Is there something with the core 2 or the preinstalled Vista that is getting in the way?  Can anyone offer some suggestions.  I saw some earlier theads about /noapic, but they just took us to another crash point.

Any suggestions for these new machines?

---

### Post by kidders on 2007-06-16
Hi there,

Since your post has gone unanswered for an entire day, I thought I'd offer some basic suggestions ... I don't have a specific solution though. :-(

** - I -**
Many people have their BIOS configured specifically for Windows ... sometimes, this can cause problems booting other operating systems, but without actually sitting in front of one of your boxes, I couldn't really guess what (if anything) might be wrong.

** - II -**
Using the "noapic" kernel option to get to the other crash point sounds promising. What's the next problem? (It might be something I know how to handle.)

** - III -**
Whatever is wrong may or may not be specific to the Ubuntu distribution. If all you need is something free & safe to give lots of people internet access for a day or two, I would suggest giving one more distro a quick try. There are a few major Linux subgroups (Ubuntu belongs to the Debian-like family) ... perhaps one of the others (eg a Red Hat-like distro, such as Mandriva) might not fall victim to the same glitch.

FYI, the "Uncompressing Linux" message you mentioned is normal. Needless to say though, it should only be visible for a few moments!

---

### Post by Pumalite on 2007-06-16
> **kidders said:**
> Hi there,

Since your post has gone unanswered for an entire day, I thought I'd offer some basic suggestions ... I don't have a specific solution though. :-(

** - I -**
Many people have their BIOS configured specifically for Windows ... sometimes, this can cause problems booting other operating systems, but without actually sitting in front of one of your boxes, I couldn't really guess what (if anything) might be wrong.

** - II -**
Using the "noapic" kernel option to get to the other crash point sounds promising. What's the next problem? (It might be something I know how to handle.)

** - III -**
Whatever is wrong may or may not be specific to the Ubuntu distribution. If all you need is something free & safe to give lots of people internet access for a day or two, I would suggest giving one more distro a quick try. There are a few major Linux subgroups (Ubuntu belongs to the Debian-like family) ... perhaps one of the others (eg a Red Hat-like distro, such as Mandriva) might not fall victim to the same glitch.

FYI, the "Uncompressing Linux" message you mentioned is normal. Needless to say though, it should only be visible for a few moments!

How did you partitioned the disk?. If you are using Vista, and want to install in the same disk, then you have to partition FROM Vista.

---

