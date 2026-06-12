---
title: "Attempting to boot from hard drive"
date: 2018-11-09
forum: Installation &amp; Upgrades
---

### Post by chunkydrew2 on 2018-11-09
My Ubuntu Server 16.04 died. I bought a refurb HP EliteDesk and installed 16.04 server  again, overwriting the Win 10 that came installed and using the entire SATA hard drive. According to the installation, it installed successfully. Unfortunately, after reboot, it says ‘attempting to boot from hard drive’, but never does. I fiddled with the setup, tried disabling UEFI or Legacy, to no avail.
Any suggestions out there?

---

### Post by mitesh.agrwl on 2018-11-09
Hi,

This might be firmware/driver issue, so please check if the hardware you bought is certified for Ubuntu. HP has a long range of hardware and all of it is not compatible with all the variants of Linux and in some cases Windows compatible only. Please provide the model number and hardware details.

Regards,
Mitesh

---

### Post by oldfred on 2018-11-09
This only runs from the desktop or live installer.
       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please attach link to the summary report, the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 
    
You can run this script with terminal & post its output to pastebin site. It is part of Boot-Repair's report, but Boot-Repair shows a lot more info.
       Updated fork  as original bootinfoscript does not seem to be maintained
[https://github.com/arvidjaar/bootinfoscript](https://github.com/arvidjaar/bootinfoscript)

---

### Post by chunkydrew2 on 2018-11-11
I resolved the issue by just installing 18.04 LTS instead. It installed with no problems.

---

### Post by mitesh.agrwl on 2018-11-11
> **chunkydrew2 said:**
> I resolved the issue by just installing 18.04 LTS instead. It installed with no problems.

Hi,

May you provide the server details and the log files from boot. I will help the developers/troubleshooters to understand what might have prevented 16.04 to boot.

---

