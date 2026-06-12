---
title: "Dual Boot: Ubuntu/Win2003"
date: 2005-06-07
forum: Installation &amp; Upgrades
---

### Post by dazed_and_confused on 2005-06-07
Hi,

I'm relative newbie to linux, have win2003 installed on first partition, trying to install ubuntu on second partition of the same drive so that ntldr goes on mbr and lets me choose which os to boot.  (I tried putting grub on mbr, and this is bad since windows automatically replaces it with ntldr to make linux unbootable)

I tried the same thing with debian by following guide at [http://www.aboutdebian.com/dualboot.htm](http://www.aboutdebian.com/dualboot.htm).  This worked perfectly, then i tried to replicate the same thing with ubuntu, nothing worked.  Problems included:
                -When installing ubuntu, grub puts itself onto mbr even tho i type in second partition (/dev/hda2)
                -If u screw up the grub step during installation on purpose, it let's u use lilo instead, but lilo crashes with no explanation
                 -Trying to manually set up lilo to go on second partition doesn't work for some reason.  (executes without error messages but doesn't work)

The only working configuration i was able to achieve, was putting grub onto floppy and then inserting it everytime i want to load linux.

Any input appriciated, please excuse the verboseness.

---

### Post by Seti on 2005-06-08
Usually the easiest way is to install Windows first, and linux later. This is because Windows is incapable of detecting another OS is there and adding to NTldr.
If possible, do it this way:

1. Make your partitions using cfdisk (or the patitioner that is on the Ubuntu installer)
make a primary partition (/dev/hda1) for Windows. This is the only place you can put Windows for this to work AFAIK. Then make another partition for swap; 500-700 MGB if you require it (/dev/hda2). The next partition will be an extended partition. It will be /dev/hda3, and that is where you will put logical partitions for linux. You can make one that is around 4 MGB for / (root), it will be /dev/hda5. You can even make more logical partitions, like for your /home, for example.

2. Install Windows. Setup will know where to put C:.

3. Install linux. It will detect Windows and add an entry to grub.lst accordingly.

---

### Post by dazed_and_confused on 2005-06-08
I realize that this is possible, however, the problem is that windows can change the mbr not just when it's installed, but when it's already up and running, this has happened to me once already.  Also i realize that ntldr doesn't automatically detect linux and add it, the question is how to manually force it to.

---

### Post by FLeiXiuS on 2005-06-08
I wouldn't worry to much of the NTLDR, Grub should handle all of your booting needs.  Once windows is installed, yes it can fiddle with the MBR but a majority of the time it won't even touch it unless told to do so.  You should be fine.

---

### Post by Genesius on 2005-06-08
I had the same problem with dual-booting. What I did:

1) reinstall Ubuntu with GRUB in root, NOT MBR
2) Go to [http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm) and download bootpart.
3) Run bootpart in Windows. It will detect your partitions & write the necessary modifications to boot.ini, which will allow you to dual-boot from NTLDR.

---

### Post by mingus on 2005-06-08
[QUOTE=dazed_and_confused]Hi,

                -When installing ubuntu, grub puts itself onto mbr even tho i type in second partition (/dev/hda2)[/QUOTE]

Are you using the command?

$sudo grub-install /dev/hda2

---

