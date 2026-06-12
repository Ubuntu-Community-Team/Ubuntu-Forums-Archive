---
title: "Unable to install ubuntu"
date: 2011-05-20
forum: Installation &amp; Upgrades
---

### Post by AlphaNeil on 2011-05-20
Here is my situation.

I was dual-booting Windows 7 and Ubuntu 10.10 till recently. Then I had to reinstall Windows. 

After re-installation of Windows I did not try to restore Grub and deleted Ubuntu partitions on disk thinking that I'll install newer Natty version.

But now when I try to install Ubuntu 11.04 using pen drive it gets stuck in bios showing message "Verifying DMI pool data ...."

I also tried to boot GParted, memtest and Windows 7 with the same pen drive.

Same thing occured with GParted and memtest but Windows 7 installation did not stuck and went as usual. So I guess it's not hardware.

What could be the problem?

---

### Post by ajgreeny on 2011-05-20
If it gets stuck in the BIOS at the "Verifying DMI pool data" it is certainly not the fault of ubuntu, nor probably windows as neither OS has done anything at that stage to affect the computer.

Maybe installing windows has in some way affected the BIOS, but for the life of me, I can't see how it would do that.  Are you saying that nothing can boot at the moment, or is it only if the USB drive is attached that the freezing problem occurs?

---

### Post by AlphaNeil on 2011-05-20
Thanks for replying.

There is no problem with the bios or anything else, as everything is working just fine.

I am having problem while booting usb drive only and I think that too while installing linux distro.

I am not saying its a fault of Ubuntu. What I think is it may be some linux related thing, may be something left from previous installation.

---

### Post by jerrrys on 2011-05-20
This issue can be caused by any of the below reasons.
 
[LIST=1]
[*]Corrupt boot files on the computer.
[*]Settings for hard disk drive are not correct.
[*]Floppy diskette or CD in computer causing issue.
[*]Boot devices not set properly.
[*]BIOS corrupt or misc. setting not set properly.
[*]Connections loose or disconnected.
[*]Bad Hard disk drive or other bad hardware.
[/LIST]

---

### Post by webofunni on 2011-05-20
is this just for pendrive installation ? are u able to boot using a CD ?

---

### Post by AlphaNeil on 2011-05-20
Sorry for the late reply but I was trying it off CD and surprisingly it worked. 

To create usb installation disk I had used "universal usb installer" as suggested on ubuntu site. Maybe something going wrong there.

---

