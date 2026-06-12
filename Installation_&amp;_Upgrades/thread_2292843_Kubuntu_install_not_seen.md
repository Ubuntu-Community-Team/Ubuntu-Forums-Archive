---
title: "Kubuntu install not seen"
date: 2015-08-31
forum: Installation &amp; Upgrades
---

### Post by shadragon on 2015-08-31
Morning, 

Here's a quick overview on my system hardware: 

- AMD Eight core 8350 CPU
- ASUS Formula-Z Crosshair Mobo - Set for non-UEFI boot
- 32GB RAM
- OCZ PCIe 240GB SSD (Win7)
- Two 3TB HD (RAID 1) (Win7)
- One 2 TB HD (Kubuntu 14.04)

Had Win 7 installed first on the SSD. Works fine. My intention was to have a dual boot machine. I added a 2TB HD to the system for a Kubuntu install. Could not get the v15 Kubuntu to install without a black screen so I installed 14.04 from USB stick with the intention of upgrading to 15. 

On reboot the machine went straight to Windows. Did a GRUB repair and rebooted. Again it went straight to Win 7 without showing GRUB boot loader. I checked the HD using a HIRENS disk and can see the Linux install on the 2TB disk.

I suspect Linux cannot see the PCIe SSD with Win 7 and cannot install GRUB on there. I'm happy to boot to Linux using a USB key. Does anyone know how I can accomplish this or otherwise set up a proper GRUB dual boot? 

Thanks

.

---

### Post by grahammechanical on 2015-08-31
Is the motherboard (BIOS/UEFI) set to look for a bootloader/OS on the 2TB hard drive? If it is looking on the 240GB SSD then it will find Windows and load that. The BIOS/UEFI will not look any further.

Regards

---

### Post by shadragon on 2015-09-01
Went home last night and changed to boot priority to the Linux drive. On  reboot I got to the GRUB terminal prompt. Looked up some GRUB commands  and tried to boot but there were a few issues. The TAB completion did  not work and even though I could see Linux.mod via ls for example, the insmod commands could not see it. 

Nor  could GRUB see the PCIe SSD. Could not get Kubuntu to load after an  hour of terminal commands. The 2TB drive is listed through GRUB as (hd0)  with (hd0,msdos1) as the ext4 partition. I've installed 14.04 several times and never had this level of difficulty. 

If  someone could talk me through how to set up GRUB on a USB key, I can  have my system default to Win7 on regular boot and plug in the USB key  to boot to Linux.

---

### Post by SeijiSensei on 2015-09-01
When you installed Ubuntu, did you not have an option to install the boot loader on the SSD (probably /dev/sda)?

---

### Post by shadragon on 2015-09-01
I don't believe Linux sees the OCZ PCIe SSD. It does not show up on the list of available drives on the GRUB terminal and I didn't see such an option on the install. 

I used the 14.04 live DVD (Which loads fine) and installed it from there.

---

### Post by shadragon on 2015-09-02
Quick check last night. The 2TB HD shows up through ls as (hd0,msdos1). Through manual GRUB commands I was able to get it to boot to the busybox terminal (initramfs), but could not get further. 

Booted through a Live CD with 14.04 and tried to follow instructions to repair the boot by installing boot-repair. Kept getting errors on apt-get install. WHY IS THIS CRITICAL PROGRAM NOT INCLUDED IN THE DISTRO???

I'm currently downloading the boot-repair ISO image to try and fix things.

---

