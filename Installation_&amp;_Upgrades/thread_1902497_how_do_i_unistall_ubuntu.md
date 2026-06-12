---
title: "how do i unistall ubuntu"
date: 2011-12-30
forum: Installation &amp; Upgrades
---

### Post by ibunta on 2011-12-30
i installed ubuntu 6.10, my system is 64 bit and the ubuntu is 32 bit, I read that this could be the reason that my network card is not detecting a lan connection, how can i unistall ubunta til i get the right 64 os. windows will not open in daul boot.

---

### Post by whatthefunk on 2011-12-30
You should really install a newer version of Ubuntu.  6.10 is no longer supported and there could be serious security risks.  I think 10.04 is the oldest version that is still supported.

Also, you can install a 64 bit version of ubuntu.

---

### Post by ibunta on 2011-12-30
is there anyway to unistall ubuntu until i get a newer version, i cannot boot windows, i would like to reinstall back up but it does not boot from dvd, it is set to boot from dvd 1st in bios

---

### Post by 73ckn797 on 2011-12-30
You could download Ubuntu 10.04 LTS, burn the iso file you downloaded (verify the download by verifying the md5sum) to a disk (at slowest speed), boot from it into "Try Ubuntu". Go to Administration/System/gparted. Delete the Ubuntu partition. Expand the Windows partition over the old Ubuntu partition.

Or, install 10.04 over the Ubuntu partition. If you install over  the partition the installation will create a new boot menu and should show the Windows install also. 

There are also ways to  perform the first steps I mention and boot from the Windows disk to repair the installation and create a new MBR.

You can use this link to find further info that I do not have readily available now: [http://www.googlubuntu.com/](http://www.googlubuntu.com/)

---

### Post by Mark Phelps on 2012-01-01
If you can't boot from the optical drive, then how did you install Ubuntu in the first place?

Also, are you sure you installed Ubuntu to its own partition? Or did you install it from inside Windows using Wubi?

---

