---
title: "Python Editor install results in failed grub2: virus/Trojan? Recovery?"
date: 2019-11-06
forum: Installation &amp; Upgrades
---

### Post by arclite7 on 2019-11-06
I have downloaded a couple of Python editors/IDEs for Python3. Immediately, I lost the ability to add bookmarks to my Firefox browser-I keep records here of all my additions, hw/sw/knowledge refs/testing YT refs vs YT bookmarks. This caused me to reboot... I have successfully installed an ssd on acpi/uefi before replacing it with a similar 2TB by the same manufacturer, Goldenfir who use the same controller hw as Kingston/ or Micron? Although now using Linux Mint Cinnamon 19v1, I have installed all partitions with over provisioning, this is now considered unnecessary. "Swappiness" is still set to 60, I read 1-5 is more appropriate, my RAM is 8GB? I intend to code, compile, design electronics, 3D design, print via OctoPrint, edit audio and video. I have installed Time stamp, the system is updated and upgraded before each new software install. The system is then rebooted and observed. The uefi partition was backed up initially with Timestamp. The base applications were also backed up to speed recovery to a vanilla install. Re-threading software installs to the required toolbase successfully if instabilities should appear first time.

The system now refuses to boot. Error: no boot drive found!

What would be the best approach here please? I am still a newbie! I am not sure if a spurious broken grub2 signals a virus attack? I am not working on a duel boot (SiC) system, choosing virtual box approach instead. I cannot say if I have bitten myself yet!

It can be very difficult to get experienced Linux users to spend time with mere mortals. I am discouraged by this repeated observation. The whole of Linux is damaged by this attitude! With genuine gratitude in advance!

Thank you
Alexandra

---

### Post by ubfan1 on 2019-11-06
Assuming you're not using any LVM/encryption, ust try booting off the install media and run an fsck on the root filesytem of the SSD.  Next install the smartmontools package and run the smartctl on the  ssd to see if any problems are seen.  I like to wait until I have a specific problem before changing system parameters like swappiness. For instance, if you find copying big files several times your memory size is unacceptably slow, try adjusting swappiness and/or the scheduler.

---

### Post by oldfred on 2019-11-06
No boot device is often UEFI/BIOS boot mode setting is wrong.
The mode you install, does not have to match default boot mode in UEFI/BIOS.
If correctly installed in UEFI boot mode, check that default boot mode of install is UEFI in UEFI settings. Or maybe UEFI Secure boot is turned on?
Also some brands like Acer require additional "trust" settings in UEFI to allow anything other than Windows to boot.

What brand/model system?

---

