---
title: "Dual Booting Ubuntu 22.04, black screen (no clear sol from boot-repair pastebin)"
date: 2023-06-05
forum: Installation &amp; Upgrades
---

### Post by yaybeno on 2023-06-05
Hello! I've been trying to dual boot my hp spectre x360 laptop with windows 11. 

I attempted following a general solution of partitioning my drive, installing ubuntu 22.04 LTS on a pen drive (I followed a tutorial and ensured I partitioned correctly and set up the pen drive with the proper settings). Booted that up. Didnt work because of secure boot. Disabled that, tried again (it found a preexisting version of ubuntu and I reinstalled), it gave a black screen. 

A suggested solution was to use boot-repair but it seems that my issue is non-obvious, as the pastebin ends with: 
The default repair of the Boot-Repair utility would not act on the boot.

Here's the pastebin logs, I'd very much appreciate any help on this issue. Thanks!

[https://paste.ubuntu.com/p/r6gdxX5smy/](https://paste.ubuntu.com/p/r6gdxX5smy/)

---

### Post by tea for one on 2023-06-06
[COLOR="#0000FF"]Line 114[/COLOR] - nvme1n1:29.3GB:nvme:512:512:unknown:INTEL HBRPEKNX0202AHO
This looks like Intel Optane, which can cause installation difficulties for Ubuntu.

Can you access your UEFI settings and check:-

Disable Secure Boot (Some vendors require an Admin password to access the Secure Boot setting)
Disable Fast Boot (It may prevent access to one-time boot menu via dedicated keys because the device boots too fast) 
Disable Legacy mode 
Check that Legacy USB Support is enabled
Change SATA mode to AHCI where the default is RAID or Intel RST (Windows may need AHCI driver)
[https://superuser.com/questions/1672500/ubuntu-installation-with-intel-rst?noredirect=1#comment2565531_1672500](https://superuser.com/questions/1672500/ubuntu-installation-with-intel-rst?noredirect=1#comment2565531_1672500)
Disable TPM (Trusted Platform Module) or PTT (Platform Trust Technology) or FTPM (Firmware Trusted Platform Module) or TPT (Trust Platform Technology)
Disable Optane memory and storage
Remove Optane drive and reset UEFI to default (with the suggested changes above)
[https://ubuntuforums.org/showthread.php?t=2471365](https://ubuntuforums.org/showthread.php?t=2471365)

If you can still access Windows ([COLOR="#0000FF"]Line 29-31[/COLOR] shows only Ubuntu detected):-

Turn off Bitlocker (if installed)
Do not have any drives encrypted during Ubuntu installation process
Disable Fast Start Up i.e. Windows is not hibernating
Some Windows updates turn on hibernation automatically
Disable applications which manage Intel Optane memory & storage

Then try to Install Ubuntu 22.04 again.

---

### Post by yaybeno on 2023-06-06
Thank you so much! I didn't realize that intel optane had those issues with Ubuntu. There were certain specifications you mentioned that I couldn't find but the suggestion for intel optane guided me to tutorials that helped me get this issue fixed!

---

### Post by tea for one on 2023-06-07
Can you provide the link(s) to the helpful tutorials?
It would be useful for other users/searchers with similar problems.

---

