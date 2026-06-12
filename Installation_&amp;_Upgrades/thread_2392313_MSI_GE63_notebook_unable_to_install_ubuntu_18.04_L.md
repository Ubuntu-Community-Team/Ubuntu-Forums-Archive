---
title: "MSI GE63 notebook unable to install ubuntu 18.04 LTS"
date: 2018-05-19
forum: Installation &amp; Upgrades
---

### Post by gaurav348 on 2018-05-19
Hi,

I have tried replacing quiet splash with nomodeset, adding nomodeset to quiet splash but I am unable to go beyond the black screen.

In BIOS I don't see any to use integrated graphics instead of GTX 1070.

Is there anything else I can try?

---

### Post by oldfred on 2018-05-19
These are now older threads, but may still apply. MSI seems to need various boot parameters. Not sure which may apply to which model.
I would think you also need nomodeset.
Setting in UEFI may be under another CPU setting or just IGFX setting, not clearly video setting.

       MSi GT72VR-6RE Dominator Pro - some settings required
[https://ubuntuforums.org/showthread.php?t=2365997](https://ubuntuforums.org/showthread.php?t=2365997)
Failing to Boot Ubuntu 16.10 in MSI GP72
[http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72](http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72)
[SOLVED] MSI GT72S 6QE - Freezes on boot unless acpi=off is used
[http://ubuntuforums.org/showthread.php?t=2303544](http://ubuntuforums.org/showthread.php?t=2303544)
MSI GS60 2QE 2xSSD RAID 0 + 1TB HDD dual boot w8.1/w10 problem 
[http://ubuntuforums.org/showthread.php?t=2297815](http://ubuntuforums.org/showthread.php?t=2297815)
MSI PX60 2qd 034us Haswell & Optimus libata.force=noncq for SSD hangup
[http://ubuntuforums.org/showthread.php?t=2296878](http://ubuntuforums.org/showthread.php?t=2296878)
MSI gaming laptop [SOLVED] Dual Boot Ubuntu 14.04 & Windows 8, Ubuntu won't boot
[http://ubuntuforums.org/showthread.php?t=2218742](http://ubuntuforums.org/showthread.php?t=2218742)
[http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387](http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387)
Recommended "libata.force=noncq"
[http://ubuntuforums.org/showthread.php?t=2298912](http://ubuntuforums.org/showthread.php?t=2298912)

       
 [https://ubuntuforums.org/showthread.php?t=2385770&p=13742959#post13742959](https://ubuntuforums.org/showthread.php?t=2385770&p=13742959#post13742959) by 1fallen
> EDIT: This seems to work for my card here, instead of using "nomodeset" I am using this "nogpumanager"
And I have to watch carefully any changes made to "/etc/X11/xorg.conf"

---

### Post by gaurav348 on 2018-05-20
Thanks for the reply, trying the things posted in the different threads...nothing  works so far. Would trying to install 17.10 be helpful?

---

### Post by oldfred on 2018-05-20
Are drives in RAID mode?
That often causes issues with desktop installer.
But some of the high performance laptops use RAID 0 just for speed. But then half of data is on one drive and half on other drive. With hard drives it was alternative tracks, not sure how SSDs do it.
You would have to fully back up and then could break the RAID and have Windows on one drive and Ubuntu on the other.

       Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

---

### Post by sarekstar on 2018-07-28
I am facing exactly the same problem. I cannot get past the blank screen which come just after clicking enter on "install Ubuntu x....". Have you solved the problem? Please let me know.

---

### Post by sarekstar on 2018-07-28
I am facing exactly the same problem. I cannot get past the blank screen which come just after clicking enter on "install Ubuntu x....". Have you solved the problem? Please let me know if you tried anything new.

---

### Post by bicounet18 on 2018-08-29
Same problem.
I  am trying to install Xubuntu 18.04.1 LTS on a "MSI GP72 6QE-254XFR  Leopard Pro" using a Live-USB that works properly on other PCs.
I managed to install Xubuntu version 16.04 on this machine without any problem.
I have respect the config Bios laptop.

     Fast boot: Disaled

     Boot mode select: Legacy

     Intel SpeedStep: Disaled

     Super Charger [...]: Disabled

     ERP: Disabled

     Intel Virtualization: Enabled

     VT-d: Enabled

     CPU C-States: Disabled

By starting on the USB key, I arrive at the boot menu, on which I choose the language and I understand:
new.blacklist=1 acpi=off
Then I choose, "Try Xubuntu".
The screen turns black, then after 5 seconds, the notebook reboots to return to the boot menu of the key.

---

### Post by oldfred on 2018-08-29
You do not want legacy with a new UEFI system.
Have you updated UEFI from MSI?
And remember settings you changed, most will go back to defaults with UEFI update.

Newer threads.
       MSI GS65  Boot parameter: modprobe.blacklist=nouveau 
[https://askubuntu.com/questions/1061109/dual-boot-windows-10-cannot-boot-latest-ubuntu-but-only-older-versions](https://askubuntu.com/questions/1061109/dual-boot-windows-10-cannot-boot-latest-ubuntu-but-only-older-versions)
MSI GE63 Update UEFI then acpi=off not required
[https://askubuntu.com/questions/1059029/18-04lts-msi-ge63-boot-issues](https://askubuntu.com/questions/1059029/18-04lts-msi-ge63-boot-issues)
[https://askubuntu.com/questions/1038637/how-to-install-ubuntu-on-msi-ge63-without-acpi-off](https://askubuntu.com/questions/1038637/how-to-install-ubuntu-on-msi-ge63-without-acpi-off)

---

