---
title: "restart loop after fresh 16.04 installation"
date: 2017-01-14
forum: Installation &amp; Upgrades
---

### Post by alku1 on 2017-01-14
This morning I made a big step and migrated my homeserver from Windows 7 to Ubuntu. At least I thought its gonna be a success story after promising testing in a VM: Unfortunately, the installation from USB had already some hickups: I had to use some additional parameters to be able to run the installation (nomodeset) otherwise all options in the Ubuntu installation menu (try ubuntu, install ubuntu, install as oem, ...) would lead to a restart loop.
With the additional parameter I was able to install UBuntu in UEFI mode enjoying a good old school 640x resolution -.-

However, after the successful installation the PC would always restart after having seen 2-3sec the purple Ubuntu start-up screen (before the Ubuntu logo appears).
By google I already found some hints to start in recovery mode )incl. network) by pressing F6 which worked OK (again 640x resolution...). However as soon as I would try and start normally it would constantly restart in a loop.

According to some threads I found for the 14.04 release (I thought 16.04 might be related) the issue is with the graphic driver. Since this is my first shot at Linux Im really lost with installing a different driver. However here is what I did try to make it work in normal mode:
- apt-get update
- apt-get upgrade 
- select use AMD properitery driver for AMD device (instead of not usign device) under additional drivers
- add/edit in grub:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash noapic radeon.dpm=0" or
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash noapic"

It seems like everything works ok in recovery mode (except the graphics) since I can update the software and browse internet and get the first impression about ubuntu. But the graphic is driving me nuts!

Any idea what could be the issue?


_System:_
- 250gb 2,5" sata 
- 4x3 TB WD red Hardware RAID 5 (3ware/LSI 9650 SE)
- AMD A4-5300 
- MSI FM2 a75 
- 4gb corsair ddr3 1333mhz

---

### Post by alku1 on 2017-01-15
After investing many hours and try and error many of the useful hints in the fantastic sticky from [**[COLOR=#C61919][B]MAFoElffen**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1044547"), I was able to resolve my issue.
Here is what I needed to add to my grub file to be able to normally start my new/frist Linux installation :-)

[FONT=Calibri]GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"[/FONT]
  [FONT=Calibri]GRUB_CMDLINE_LINUX=""[/FONT]
  [FONT=Calibri]GRUB_GFXMODE=1920x1200x32
[/FONT]

---

