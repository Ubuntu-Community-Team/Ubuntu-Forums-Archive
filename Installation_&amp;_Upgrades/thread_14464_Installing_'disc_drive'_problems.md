---
title: "Installing 'disc drive' problems"
date: 2005-02-07
forum: Installation &amp; Upgrades
---

### Post by dueyfinster on 2005-02-07
I have already downloaded ubuntu for install, and have tryed to install it, but it looks for drivers for my cd drives, on a floppy (but I dont have a floppy disk drive on my pc). It will not let me continue until I resolve this problem. Any Ideas?

---

### Post by dueyfinster on 2005-02-07
please help!

---

### Post by alastair on 2005-02-07
Not much idea I'm afraid - but the genarl idea would be to give as much information as you can to make it easier for people to help e.g.

How are you installing? Not CDROM? CDROM?
Have you >1 CDROM?
What type of CDROM is it? Do other Linux dists work?
Is it possible to skip this step?
What about installing in "expert" mode (check the "F" buttons on install)? Try "noprobe" perhaps.

---

### Post by dueyfinster on 2005-02-08
I am installing a NEC DVD RW and a Samsung  CDRW, this is my first linux distro and no you cannot skip the step (unfortunately).

---

### Post by dueyfinster on 2005-02-09
Please Help!

---

### Post by dueyfinster on 2005-02-09
please help!

---

### Post by alastair on 2005-02-09
There's a real chance no one wil be able to solve this. You and your h/w are remote, support is hard ...

When I asked for details of your CDROM - I didn't really mean model. What's the config - internal IDE1 secondary?  IDE2 master? SCSI? USB?

Are you installing /from/ CDROM? Does it 'know' how to read the/a CDROM at first? (assuming the install is from a CDROM)?

What Ubuntu is this? Have you tried the latest LiveCD - hoary?

---

### Post by ploum on 2005-07-04
[QUOTE=dueyfinster]I have already downloaded ubuntu for install, and have tryed to install it, but it looks for drivers for my cd drives, on a floppy (but I dont have a floppy disk drive on my pc). It will not let me continue until I resolve this problem. Any Ideas?[/QUOTE]
 I have the same problem here. The installation doesn't detect my CD-Rom drive (altought I'm booting from it !)

NEC DVD+RW ND-3530-A  on simple IDE cable, as long as I can see.

The problem is still present with a OLD Warty cd-install !

---

### Post by ploum on 2005-07-04
That's very strange. In The BIOS, I've 4 options with different behaviours on this problem.

The option is called "SATA Operation"

1) RAID Autodetect/AHCI  -> Windows works, Ubuntu Kernel Panic

2) RAID Autodetect/ATA -> Ubuntu works but without CD-rom. Windows BSOD at boot

3) RAID on  -> Windows works, Ubuntu Kernel panic

4) Combination -> Windows BSOD at boot, Ubuntu Kernel panic


Anyone with an idea to have a working dual boot here ?

---

