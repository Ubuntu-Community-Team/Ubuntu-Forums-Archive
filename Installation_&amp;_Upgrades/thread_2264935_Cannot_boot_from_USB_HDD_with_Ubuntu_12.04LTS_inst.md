---
title: "Cannot boot from USB HDD with Ubuntu 12.04LTS installed"
date: 2015-02-11
forum: Installation &amp; Upgrades
---

### Post by andrew198 on 2015-02-11
This probably has been answered before, but I cannot find a thread specific to my problem. If so, I appolgise.
I have an old laptop (Advent 5712) on which is installed Windows 7. I want to install Ubuntu 12.04LTS on a USB hard drive, which can be removed at any time without the Windows MBR having been overwritten (to enable me to boot into Windows without external HDD attached).


I have created bootable flash drive (memory stick) with Ubuntu on it. That's OK, it works.
I format the USB HDD in Windows to NTFS (to get rid of any residual remnants of Linux partitions previously installed on there).
I set the BIOS bootup order to USB HDD, then internal HDD, then USB flash drive. This will ensure on re-boot it will not boot to USB flash drive as a first choice.
On boot up, I can tell the system what device to boot to first (ie. over-riding the normal boot order): I select USB flash drive.
I do an Ubuntu installation on the USB HDD following the instructions as per:
[http://www.linuxbsdos.com/2013/10/23/how-to-install-ubuntu-13-10-on-an-external-hard-drive/](http://www.linuxbsdos.com/2013/10/23/how-to-install-ubuntu-13-10-on-an-external-hard-drive/)
The "Device for boot loader installation" I set to /dev/sdb (my USB HDD).
The only diference was I made the swap partition logical.
So far, all goes well. Everything installs.
Upon restarting after installation, lots of information flashes on the screen (too quick to read), then it reboots straight into Windows.
If I then remove the internal HDD from the BIOS boot menu, and remove the USB flash drive (so it can only boot from external HDD), it says no Operating System found.


So it cannot boot from the Ubuntu HDD. Examining the Ubuntu HDD using live Ubuntu on flash drive, the partitions are there.


I've also tried to create Ubuntu USB HDD with an initial /boot partition (sdb1) and putting the bootloader installation into there. It still does not work.


Please, where am I going wrong?


My next stage would be to shrink the Windows partition on the internal HDD, freeing up space for an extra partition and installing Ubuntu on there as a dual boot PC. But I want to try out Ubuntu on USB HDD first.


Many thanks and extremely frustrated :) .

---

### Post by oldfred on 2015-02-11
May be best to see details. 

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

   Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by andrew198 on 2015-02-11
Thanks for your reply oldfred.


The URL for Boot-Info is:
[http://paste.ubuntu.com/10174250/](http://paste.ubuntu.com/10174250/)

---

### Post by oldfred on 2015-02-11
Some older BIOS and/or some USB boot do not work from larger drives. With older BIOS it was a known issue of a 137GB boot limit. So either / (root) or a /boot had to be fully withing the first 137GB of the drive so all files were within limit. We have seen similar issues with somewhat newer systems and USB boot.
I normally suggest a 25GB / partition at beginning of drive and use rest of drive as /home, /mnt/data or other partitions like a shared NTFS or backup from other drive.

About half of users I have suggested just using gparted to shrink / to less than 100GB have found that works. Then they can move /home or reinstall or create a data partition if it works. Some have had to reinstall. The shrink should be fairly quick as there is not much data yet, so a quick test.

You do show boot files beyond 100GB on drive.
```
  158.229862213 = 169.898020864  boot/grub/grub.cfg                             1
 158.229843140 = 169.898000384  boot/grub/core.img                             1
  48.135692596 = 51.685306368   boot/vmlinuz-3.13.0-32-generic                 1
  48.135692596 = 51.685306368   vmlinuz                                        1
 252.307281494 = 270.912880640  boot/initrd.img-3.13.0-32-generic              2
 252.307281494 = 270.912880640  initrd.img                                     2


```

---

### Post by andrew198 on 2015-02-11
Oh dear oldfred, I (being a pessimist) thought that your answer would be too good to be true :( .
I did a total reformat/reinstallation. Root directory of 25GB. Swap of 4GB and /home as 250GB.


I'm afraid, still no operating system recognised. New Boot-Info URL:
[http://paste.ubuntu.com/10175949/](http://paste.ubuntu.com/10175949/)

---

### Post by oldfred on 2015-02-11
What choice in BIOS are you using to boot USB drive?

My old desktop required me to choose hard drive and then choose USB flash drives. They were seen as hard drives from BIOS. BIOS did have many USB boot choices like hard drive, floppy, CD etc but none of those ever worked.

---

### Post by andrew198 on 2015-02-11
The BIOS (in boot menu) actually shows manufacturer and part# and (if USB device) "USB" for each device attached.
So flash drive is seen as: "USB HDD: Verbatim STORE N GO - (USB2.0..."
USB HDD: "USB HDD: Seagate Expansion - (USB 2.0..."
Internal HDD: "SATA HDD: WDC WD3200LPVX...."

It clearly boots to the USB flash drive OK. And I've tried different USB ports.
Also, irrespective of set boot order, I can press F12 and select which device I want to boot from for a specific boot up.


Very specific.

---

### Post by oldfred on 2015-02-11
Not sure why then BIOS is not seeing drive.

Some Se agates had proprietary bits that have created issues. But drive looks normal from Summary report and looks like a standard MBR that BIOS should let you boot. No different than flash drive's MBR.

---

### Post by andrew198 on 2015-02-11
I can confirm that attaching the USB HDD with the Ubuntu disto installed on it boots up perfectly on another laptop. So it's the original laptop: total cheap Dixon's rubbish!


The next stage is to destroy my Windows MBR by installing Ubuntu on the spare partition on the internal HDD and dual booting :) . Well nothing would surprise me on that laptop. I do have Acronis True Image backup of Windows which includes the MBR, so hopefully all will not be lost.

I'll heed your warning oldfred. I've now shrunk the Windows partition so that the /boot will be around 130GB from the start of the drive (I'll make /boot 500MB, so it'll all be contained within that 137GB constraint).

---

### Post by andrew198 on 2015-02-11
Dual boot works perfectly.
Once again thanks for your help oldfred. Much appreciated.


I'll close the thread now. Problem solved (sort of).

---

### Post by oldfred on 2015-02-12
You are welcome. 
Glad you got it working one way or the other. :)

---

