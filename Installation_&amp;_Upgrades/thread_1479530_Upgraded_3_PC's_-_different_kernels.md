---
title: "Upgraded 3 PC's - different kernels"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by randyklein99 on 2010-05-10
I just upgraded 3 PC's (a 32 bit netbook, 32 bit laptop, 64 bit desktop).  Both the 32 bit netbook and 64 bit desktop are running the 2.6.32-22-generic kernel, but the 32 bit laptop is running 2.6.31-14-generic kernel.

Anyone know how that happened?  How do I update the kernel to 2.6.32-22-generic?

---

### Post by Sef on 2010-05-10
>   How do I update the kernel to 2.6.32-22-generic? 	

System > Administration > Update Manager

---

### Post by oldfred on 2010-05-10
2.6.31-14-generic kernel is Karmic Koala.

Run this to confirm:
```

 lsb_release -a
```

---

### Post by randyklein99 on 2010-05-10
I'm running into other problems now.  The kernel was installed but grub was defaulting to .31.  I updated grub to grub2 which (I think) chose the latest kernel as default.  Now laptop won't boot off kernel.  I'm trying to repair grub and go back to .31

---

### Post by oldfred on 2010-05-10
did you do an upgrade and said to keep the old menu.lst from grub legacy. that then requires you to manually enter a new entry for the new kernel. You can copy an old entry and update it to the new kernel and boot. Then run update-grub.

I still like grub2, but it is new and different. A few do not get over the differences or have some problem and are not willing  to deal with it.

---

### Post by randyklein99 on 2010-05-11
I was able to repair/figure out grub2 and get it to default to .31 kernel, so grub is no longer an issue.  But now I need to work out why the .32 kernel is not working on the laptop and netbook.  From the forums here, I'm not alone in this regard and it seems it may be intel graphics based.

---

### Post by davidmohammed on 2010-05-11
if you've got an intel graphics card, then the usual fix is to either add i915.modeset=1 or i915.modeset=0 to your boot

(when grub starts press e and add the above before "quiet splash")

---

### Post by randyklein99 on 2010-05-11
> **davidmohammed said:**
> if you've got an intel graphics card, then the usual fix is to either add i915.modeset=1 or i915.modeset=0 to your boot

(when grub starts press e and add the above before "quiet splash")

Yes, the i915.modeset=1 kernel parameter allowed me to boot.  It just seems the system is a little slower than with the .31 kernel.  But that may just be me.

so what does that parameter doing?

---

### Post by davidmohammed on 2010-05-11
it enables kernel mode setting (kms) - google the wikipedia definition!

basically intel graphics is screwed up with the lucid kernel and all upstream kernels.  There is hope that some fixes are coming soon - probably will have to wait a few months though.

Some of the upstream xorg-edgers graphics are better if you are willing to experiment (various threads on how to add this ppa).

---

### Post by movieman on 2010-05-11
> **davidmohammed said:**
> basically intel graphics is screwed up with the lucid kernel and all upstream kernels.

What's wrong with it? My netbook is working fine with some crappy Intel graphics chip.

---

### Post by davidmohammed on 2010-05-12
this page will explain all...
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes]("https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes")

---

### Post by randyklein99 on 2010-05-12
> **davidmohammed said:**
> this page will explain all...
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes]("https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes")

yep, that's the page i followed.  Workaround A is what I ended up doing.  thanks for all the help.  I'll have to look at the upstream xorg-edgers graphics.

---

