---
title: "install stalls at 15% checking filesystems WD MyBook USB Drive"
date: 2008-02-23
forum: Installation &amp; Upgrades
---

### Post by Beowulf.1000 on 2008-02-23
Tried installing Ubuntu 7.10 i386 Desktop to a (friend's)  Western Digital MyBook external USB storage drive.  First used GParted to split the drive so as to add a ext3 "/" and a swap partition. During install, it gets to 15% install progress then stalls as it shows "checking filesystems".  Any solutions?

I am pretty savvy at computing and have installed Linux and Ubuntu to perhaps a dozen PCs, including a pen flash drive, dual sata system, etc., but this one has me at a loss.  I am thinking maybe this USB drive has some built in operating system in its hardware or something that just does not want to allow the install?

As always, this is a case of a friend wanting me to spend two days of my time installing Linux in a non-standard way, sigh. I am ready to give up, just tell him to put a spare internal drive in his tower system and use Linux that way.  His tower system is an Acer Aspire with VISTA that no longer gives him internet-- two house mates using his Vista system ended up giving him a zillion spy ware programs that likely funked it and then his antispyware ended up leading to loss of internet drivers, etc. He was quite amazed that the live Ubuntu CD gave him instant internet, AND instant openoffice, gimp, etc.

If this is doable, I would like to put linux on his USB storage device, but if not I can let it go.

---

### Post by Pumalite on 2008-02-23
Do md5sum on iso, burn at 4x or less in good quality CD-R media, check for integrity of the CD before installation. Clean the lens in your burner, just in case.

---

### Post by Beowulf.1000 on 2008-02-23
Tried that (burner forced speed increase to 16x), did verify data, did check of CD after live boot. All was good.

> **Pumalite said:**
> Do md5sum on iso, burn at 4x or less in good quality CD-R media, check for integrity of the CD before installation. Clean the lens in your burner, just in case.

---

### Post by Pumalite on 2008-02-23
Sorry, I understood all IS good. Try the Alternate CD. The other thing is Western Digital MyBook comes with Microsoft software pre installed. Maybe you should DBan the drive first and then partition it.

---

### Post by tke1384 on 2008-02-23
I'm having the same issue.  I've tried two different USB drives, one with a laptop HD in it and one with a SATA drive in it using a USB connection to the computer.  Both has same issue you have.  I pulled the SATA drive out of the external and installed it in my tower and am still having the same issue.  I've been a linux user for shoot 7 years now and have installed loads of different distributions but have never had the trouble I'm having with ubuntu.  So far I'm really not impressed.  Let me know if you find a solution and if I find anything I'll post a link for you.

---

### Post by Beowulf.1000 on 2008-02-23
We gave up on the USB drive. I I put an extra PATA ide drive in his system, Vista was on a sata drive. This worked really good. Ubuntu went on the pata (ide) drive and did not even ask about grub, just put grub on the ide drive, leaving vista sata drive alone. had to go into bios and tell it to boot ide drive first, works great. Best thing is even if vista is reinstalled grub and linux should be good to go.

he is liking ubuntu, he is fed up with Vista.  :)

i think it is funny how things have flipped-- years ago Linux was less friendly than Windows, now it is the reverse!

What he really liked was how easy it was to install new stuff, also streamtuner install with one command (well two actually, we had to get xmms also).


> **Pumalite said:**
> Sorry, I understood all IS good. Try the Alternate CD. The other thing is Western Digital MyBook comes with Microsoft software pre installed. Maybe you should DBan the drive first and then partition it.

---

### Post by Pumalite on 2008-02-23
Glad you worked it out. Good luck.

---

