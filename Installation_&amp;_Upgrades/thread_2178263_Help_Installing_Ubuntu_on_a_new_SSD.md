---
title: "Help: Installing Ubuntu on a new SSD"
date: 2013-10-02
forum: Installation &amp; Upgrades
---

### Post by henry18 on 2013-10-02
I am unable to find answers among the community search as a complete noob any guidance will be greatly appreciated. 
I purchased a refurbished Asus laptop preloaded with Win8 with no key or disk. I have an optical drive though. I would like to replace the hard drive for an SSD. How do I step-by-step install Ubuntu as my sole OS? Any guidance again will be greatly appreciated.

---

### Post by sanderj on 2013-10-02
Remove HDD, put in SSD.
Download the Ubuntu ISO, burn it to a DVD, or - better - write it to a USB stick using UNETBOOTIN
Boot from the DVD or USB stick, live-run Ubuntu, see that it works, and then click install
Follow the installation procedure.
Reboot into Ubuntu
Happiness

---

### Post by oldfred on 2013-10-02
If a new system with pre-installed Windows 8, you may want to turn off secure boot and fast boot before removing hard drive. Ubuntu will boot with secure boot on, but easier without it.

You will then with a new drive have the choice of UEFI install or BIOS/Legacy/CSM based install. How you boot install media from UEFI/BIOS menu is how it installs.

Even if installing with BIOS, you may want to pre-partition with an efi partition as that is difficult to add later and you then could convert to UEFI. If in BIOS mode you can also use gpt, not the 30 year old MBR(msdos) partitioning. Windows only boots from gpt with UEFI, but Ubuntu can use gpt with either BIOS or UEFI if correct supporting partitions efi or bios_grub are on drive. If you use MBR then you will only be able to boot with BIOS unless you erase and reformat drive.
       GPT Advantages (older but still valid)  srs5694 post #2:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

Link in my signature has lots of links to example UEFI installs if UEFI desired. Otherwise there are many links on installing with BIOS.

---

### Post by henry18 on 2013-10-02
Thank you for your help! I need to catch up with my PC acronyms for dummies. Win8 rubs me the wrong way and I need a better alternative not Microsoft. I hope the mfgs someday will offer/distribute turnkey Linux as they do Win to general consumers like myself.

---

### Post by oldfred on 2013-10-02
UEFI is the new boot loader that replaces the 35 year old BIOS. 
 UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

      
 GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

 MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/Extended_boot_record](http://en.wikipedia.org/wiki/Extended_boot_record)

gpt is the new partitioning scheme that replaces MBR(msdos). UEFI needs gpt, but Ubuntu will boot in BIOS mode from gpt drives.
Windows only boots from gpt drives with UEFI.
Both Windows and Ubuntu only boot from MBR partitioned drives with BIOS.

---

