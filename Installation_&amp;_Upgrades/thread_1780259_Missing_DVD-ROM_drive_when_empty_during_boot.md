---
title: "Missing DVD-ROM drive when empty during boot"
date: 2011-06-11
forum: Installation &amp; Upgrades
---

### Post by rtslater on 2011-06-11
Hello,

I am completely new to Ubuntu/Linux and am having trouble getting my DVD-ROM drive to work. I've tested a few things, and it seems that if there is a CD in it when I boot, then it works fine, but if there is nothing in it then Ubuntu won't list the device. The DVD-ROM is master on a PATA cable and the CD-RW is slave (yes I know it's getting old now...) Drives worked fine under Windows XP.

I don't know very much about the boot process, but the following from kern.log seemed relevant:

[B]Booting with a CD:

[/B]ata1.00: ATAPI: SONY DVD-ROM DDU1615, FYS1, max UDMA/33
ata1.01: ATAPI: SONY    CD-RW  CRX230ED, 4YS1, max UDMA/33
ata1.00: configured for UDMA/33
ata1.01: configured for UDMA/33[B]

Booting without a CD:[/B]
ata1.00: ATAPI: SONY DVD-ROM DDU1615, FYS1, max UDMA/33
ata1.01: ATAPI: SONY    CD-RW  CRX230ED, 4YS1, max UDMA/33
ata1.00: failed to IDENTIFY (I/O error, err_mask=0x2)
ata1.00: revalidation failed (errno=-5)
ata1.00: failed to IDENTIFY (I/O error, err_mask=0x2)
ata1.00: revalidation failed (errno=-5)
ata1.00: limiting speed to UDMA/33:PIO3
ata1.00: failed to IDENTIFY (I/O error, err_mask=0x2)
ata1.00: revalidation failed (errno=-5)
ata1.00: disabled
ata1.01: failed to set xfermode (err_mask=0x40)
ata1.01: configured for UDMA/33

Can anyone help explain what is going on, and what I can do to fix it?

Thanks.

---

### Post by foresthill on 2011-06-11
What happens if you boot up with no disc in the drive, then insert a disc when you get to the desktop?

Inserting a disc should cause the drive to be "mounted" and you SHOULD be able to see the drive at that point.

This is normal for Linux. It's just how it's set up. I'm not sure of all the precise reasons, but that's the way it is.

---

### Post by rtslater on 2011-06-11
The CD-RW drive creates and removes an icon when I put a cd in and take it out. If the DVD was loaded when booting then it does the same. If the DVD was empty when booting then nothing happens, and nothing is listed for it under disk drives in system settings. It seems to completely disable the drive.

---

### Post by foresthill on 2011-06-11
Hmmm. Interesting. That should not be happening.

Does the drive work OK in Windows? The reason I ask is that there are some really crappy optical disc drives out there. I have gone through probably a half dozen drives of various brands in the past few years. 

And when they go bad, not recognizing there's a disc in the drive is usually the first symptom, 

So with what little I have to go on, I would suspect a bad DVD drive at this point.

---

