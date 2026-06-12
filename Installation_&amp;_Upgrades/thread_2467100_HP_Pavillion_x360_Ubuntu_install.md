---
title: "HP Pavillion x360 Ubuntu install"
date: 2021-09-15
forum: Installation &amp; Upgrades
---

### Post by mrdfield63 on 2021-09-15
Hello, I bought a HP Pavillion 360 it has 128 gb hard drive Intel i3 , I cannot get past the install its not seeing my hard drive I have tried everything i have looked up disabling secure boot, disabling fast start , etc... Still no matter what i try it only sees the usb not my hard drive I have also read to disable RAID to ACHI i think , but cannot find it in the Bios I have used Ubuntu on and off since 2008 and have never had this issue with a install and please bear in mind i have very limited knowledge except for the basics thank you for any help in advance

---

### Post by tea for one on 2021-09-16
Do you have Windows 10 on this device?
Is Windows hibernating?

[https://support.microsoft.com/en-us/windows/shut-down-sleep-or-hibernate-your-pc-2941d165-7d0a-a5e8-c5ad-8c972e8e6eff](https://support.microsoft.com/en-us/windows/shut-down-sleep-or-hibernate-your-pc-2941d165-7d0a-a5e8-c5ad-8c972e8e6eff)

---

### Post by oldfred on 2021-09-16
You may have to update UEFI firmware & if SSD, SSD firmware.

You typically have to first install AHCI driver into Windows.
[https://askubuntu.com/questions/1233623/workaround-to-install-ubuntu-20-04-with-intel-rst-systems](https://askubuntu.com/questions/1233623/workaround-to-install-ubuntu-20-04-with-intel-rst-systems) & 
But if you do a safe boot first to update Windows, then boot to UEFI/BIOS and change to AHCI and finally boot normally, it works
[https://superuser.com/questions/1672500/ubuntu-installation-with-intel-rst?noredirect=1#comment2565531_1672500](https://superuser.com/questions/1672500/ubuntu-installation-with-intel-rst?noredirect=1#comment2565531_1672500)
[https://askubuntu.com/questions/1233623/workaround-to-install-ubuntu-20-04-with-intel-rst-systems](https://askubuntu.com/questions/1233623/workaround-to-install-ubuntu-20-04-with-intel-rst-systems)
[https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347](https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347) & 
[https://help.ubuntu.com/rst/](https://help.ubuntu.com/rst/)

Another HP system, may be similar.
[https://h30434.www3.hp.com/t5/Notebook-Hardware-and-Upgrade-Questions/How-to-Disable-Optane-in-Bios-and-set-Disk-Controller-to/td-p/7354483](https://h30434.www3.hp.com/t5/Notebook-Hardware-and-Upgrade-Questions/How-to-Disable-Optane-in-Bios-and-set-Disk-Controller-to/td-p/7354483)

HP X360 Update UEFI F20, probably newer now
[https://ubuntuforums.org/showthread.php?t=2439220](https://ubuntuforums.org/showthread.php?t=2439220)

There is also a Windows/Intel app to disable Optane
Asus Zenbook UX425EA w/Intel Iris Xe Graphics - turn off optane with Windows Optane app
[https://ubuntuforums.org/showthread.php?t=2458373](https://ubuntuforums.org/showthread.php?t=2458373)
Used Intel App in Windows to disable Optane, need AHCI driver in Windows.
[https://ubuntuforums.org/showthread.php?t=2458373&p=14022735#post14022735](https://ubuntuforums.org/showthread.php?t=2458373&p=14022735#post14022735) & 
[https://www.microsoft.com/en-us/p/intel-optane-memory-and-storage-management/9mzng5hzwz1t?activetab=pivot:overviewtab](https://www.microsoft.com/en-us/p/intel-optane-memory-and-storage-management/9mzng5hzwz1t?activetab=pivot:overviewtab)

---

### Post by mrdfield63 on 2021-09-16
Thank you got it installed great advice

---

