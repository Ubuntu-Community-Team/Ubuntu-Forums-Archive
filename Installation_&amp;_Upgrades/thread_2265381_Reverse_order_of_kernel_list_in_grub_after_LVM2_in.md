---
title: "Reverse order of kernel list in grub after LVM2 install."
date: 2015-02-14
forum: Installation &amp; Upgrades
---

### Post by oceola2 on 2015-02-14
Initially before an update of a kernel in Fedora21, Ubuntu 14.04 booted the current Fedora kernel properly.
After an update the changed Fedora kernel version number shows up in grub but the order is backwards, older version first, and if hitting the top one it stays at the original kernel, hitting the others causes a failure.
Fedora is set up as an LVM.
In an effort to change grub I tried both grub-mkconfig and update-grub to no avail.
Grub shows a generic Fedora on the device mapper instead of the drive designation.
Trying the advanced options and the several listed items (no values or kernel version appear) states there's an inability to get some root access to boot and leaves the system at a prompt.
Is there a way to reverse the order in grub without a manual edit, and would a manual edit work with the original lead in text before the menu item?

---

### Post by oldfred on 2015-02-14
Have you installed lvm2 and mounted LVM before running the sudo update-grub?
       sudo apt-get install lvm2
    
You should also be able to manually copy the Fedora grub entries into Ubuntu grub's 40_custom and turn off os-prober. But then you have to manually update on every new kernel in Fedora.
And you still need lvm2 driver in Ubuntu.

 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

---

### Post by oceola2 on 2015-02-15
Update Grub was tried for Ubuntu 14.04 and for Ubuntu 12.04 but neither would "see" the Fedora install on sdc until LVM2 was installed.
Running update-grub shows sequence for Linux Mint 17, Ubuntu 14.04, Ubuntu 12.04 but shows Fedora with the /dev/mapper indication and not the specific drive call.
Previously, with grub on the sda drive (Linux Mint17) it showed the drive, no dev/map and the order was as below.
Each OS is on it's own drive with Mint on sda1, Ubuntu14.04 on sdb1, Fedora on sdc and Ubuntu 12.04 on sdd.
I've tried hitting all the items in the list under the Fedora advanced options with the same no complete and the root error indication.
I can open the newer Fedora Kernel Version (not complicated) by using the Asus motherboards GUI bios boot command (this is a list of the devices; when one is picked boots that device)
I had been running the os-probe with previous installs and prior to this group of installs,copying the new output of 30_ after grub or grub2 mkconfig and the appropriate kernel for any of the collected systems would be indicated and load when selected.
grub-mkconfig does not re-align the order which is older kernel listed before newer kernel. At present only way is to boot directly from the bios for newer Fedora kernel.

---

### Post by oldfred on 2015-02-15
Best to see details. DO NOT run auto repair in Boot-Repair. That installs one grub to the MBR of every drive. You want to keep each install having its boot loader in the MBR of that drive.

 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

   Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by oceola2 on 2015-02-17
Thanks for the links.
Installed boot-info-scripts from the repos to see what it would provide. Be nice if I knew what I was looking at have the "results" text.
Tried and end run by removing older kernels and updating grub.
Dopey machine booted but when checking the kinfo center still showed 3.17 kernel instead of 3.18 and also disabled wireless.
Booting out of bios gui kinfo shows 3.18 and wireless restored??????
There also appears to be no direct update-grub command for Fedora which may be part of the issue, instead they have an intermediary package which is annoying.
As it stands I believe I will leave things alone for now as I do not know yet whether the Fedora is meant to stay on the system.
I will still run the bootinfo packages you linked to in the near future and post results.
Thanks again

---

### Post by oceola2 on 2015-02-23
A re-install of LVM2 on the boot drive and a follow up of grub-mkconfig followed by sudo update-grub seemed to resolve the root permission issue.
The latest kernel is still at the bottom of the list of "Advanced Options" (load sequence is reversed) but the proper kernel loads with all functions nominal.

---

