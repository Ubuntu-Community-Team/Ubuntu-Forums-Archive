---
title: "Sdb sda"
date: 2014-06-06
forum: Installation &amp; Upgrades
---

### Post by richard58 on 2014-06-06
Hello,

I am wondering if there is a way to invert my main disk which is a MSATA SSD Samsung EVO 840 (SDB) to SDA. I am currently running Ubuntu but during installation it can only install on my second drive (just typical Hard drive 7200PM) which is SDA. I would like to install it on my SSD and Ubuntu seems to be able to install only on SDA ? It gives me an error message when I install on my SSD

I can't find anything in the bios nor can I invert cables because it is different 

Cheers

---

### Post by oldfred on 2014-06-06
I doubt it will resolve issue, UEFI/BIOS enumerate drives. Grub has a couple to tools:
There is a drivemap command to swap drive order with grub, but not sure that would solve your problem.  Usually used with Windows:
[http://www.gnu.org/software/grub/manual/html_node/drivemap.html](http://www.gnu.org/software/grub/manual/html_node/drivemap.html)
There is also a file you can create - device map file, just about obsolete:
[http://www.gnu.org/software/grub/manual/html_node/Device-map.html](http://www.gnu.org/software/grub/manual/html_node/Device-map.html)

What is the error you are getting?

---

### Post by grahammechanical on 2014-06-06
The designations sda, sdb, sdc, etc., relate to the numbering in the motherboard of the SATA ports. I found this out when I purchased a second hard drive. Ubuntu is able to install to hard drive other than sda. We use the "Something Else" option to direct which hard drive to install Ubuntu to. Be aware that the installer defaults to install Grub (bootloader) into sda. You may wish to change that.

From this link I understand that SSDs plug into SATA ports.

[http://www.samsung.com/global/business/semiconductor/minisite/SSD/global/html/about/whitepaper02.html](http://www.samsung.com/global/business/semiconductor/minisite/SSD/global/html/about/whitepaper02.html)

Grub/Ubuntu uses a UUID (Universally Unique Identifier) for each HDD/partition and not the terms "sda" and "sdb" so changing the ports should not break booting.

Regards

---

### Post by echotech2 on 2014-06-07
I don't quite understand "The designations sda, sdb, sdc, etc., relate to the numbering in the motherboard of the SATA ports."  I currently have only one disk (an SSD) attached to this computer and it doesn't seem to matter which SATA port on the motherboard it is attached to  (presently SATA3) it is SDA.  

  OK, I just connected an HD and tried several motherboard ports (motherboard has 6 SATA ports) and the HD is always SDB.

  I'm probably missing or misunderstanding something in that statement as my caffeine level has not yet reached optimum value.

--Dave

---

### Post by oldfred on 2014-06-07
Your system must always make the mSATA drive as sda then.

On my system the drive order is the port order on motherboard. But I skipped a port. So when I plug a flash drive in, it it sde. But if I reboot the flash drive becomes sdb and every other drive moves up one. So I have to be very careful or check which drive is which if plugging in flash drives.

We have seen some that randomly seem to switch and it is which drive comes up to speed first.

---

