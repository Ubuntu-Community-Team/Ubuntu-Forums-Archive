---
title: "Forcing Windows 7 Boot in Wubi Install (9.10)"
date: 2010-04-14
forum: Installation &amp; Upgrades
---

### Post by wilsun on 2010-04-14
I recently did a Wubi install of 9.10 on my netbook that initially ran Windows 7 Starter. I wanted to speed up the booting process so I went into Windows and set the OS selection list waiting time to be 0 and the default OS to be ubuntu. I did this assuming that there is a way to force OS selection list to be brought up during boot; I think I was wrong.

So now, I'm stuck booting directly into 9.10 (not even a full install!). Is there a way to either modify the Windows boot file to reset the selection list timer or to force the list to be brought back out?

(Gateway LT2104)

Thanks.

EDIT: I should note that editing the grub files within the wubi install would only make changes to the GRUB loader, which has no effect on the actual Windows loader.

---

### Post by Mark Phelps on 2010-04-14
I'm guessing the netbook does not have an internal CD drive, but can it support booting from an external CD drive?

IF it can, then go to the link below, download and burn a Win7 Repair CD, boot from that, and run Startup Repair three times.

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")

That will wipe out the GRUB code in your MBR, so you will have to restore that later.

---

### Post by wilsun on 2010-04-14
> **Mark Phelps said:**
> I'm guessing the netbook does not have an internal CD drive, but can it support booting from an external CD drive?

IF it can, then go to the link below, download and burn a Win7 Repair CD, boot from that, and run Startup Repair three times.

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

That will wipe out the GRUB code in your MBR, so you will have to restore that later.


Would this work if I burn the image to a flash drive?

---

### Post by LordSmight on 2010-04-14
If your system supports booting from flash drives or SD cards then it will most definitely work.

---

