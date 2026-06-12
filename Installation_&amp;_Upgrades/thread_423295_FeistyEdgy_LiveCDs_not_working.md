---
title: "Feisty/Edgy LiveCDs not working"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by nhornick on 2007-04-25
I know this seems to be a popular topic of discussion at the moment, but I've been searching the forums for a few days now and it doesn't seem like anyone has my particular problem.

  I'm trying to install Feisty on a Dell Inspiron 6000 from the livecd, and it dumps me into the initramfs prompt. casper.log lists some unsuccessful mount attempts on /dev/sda* and then says "unable to find a medium containing a live file system." Checking the CD for defects has the same result. I tried noacpi in the boot options, no help. I also selecting 'install with alternate driver cd', no help there either. I have no floppy drive. I tried the alternate install cd, it tells me somewhat more explicitly that it can't mount my cdrom drive. I tried to manually mount the cdrom drive (seems to be on /dev/scd0), but no luck there either (Mounting /dev/scd0 on /cdrom failed: Invalid Argument). It seems to be hardware related, but the only posts I can find from others with the same hardware are 'everything worked great'.
  So, I figured I'd try Edgy, but that livecd also fails, with similar messages.

  Anyone have any ideas?

---

### Post by zvacet on 2007-04-26
Did you burn it right?

[https://help.ubuntu.com/community/BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto")

---

### Post by nhornick on 2007-05-08
Yes. I burned several versions of the livecd (desktop, alternate, edgy), and all were bootable and passed checks on another pc.

---

### Post by tns on 2008-02-27
bump.

Same here. Trying to install on an inspiron 6000. The boot process aborts and says "Invalid or corrupt kernel image." I verified the md5sum before burning, and the disks work on my machines.

Has anyone else seen this?

---

### Post by maheshjagadeesan on 2008-03-08
I have one of the CDs shipped by Canonical, and I can't install Ubuntu on my Inspiron 1525 either. It stops with the initramfs problem, and dumps me at the ash prompt

---

### Post by HeXaDeC on 2008-03-09
Same problem here on Dimension 8300. :(

---

