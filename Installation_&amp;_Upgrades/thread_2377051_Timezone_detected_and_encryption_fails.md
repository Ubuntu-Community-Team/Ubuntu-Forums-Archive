---
title: "Timezone detected and encryption fails"
date: 2017-11-08
forum: Installation &amp; Upgrades
---

### Post by alwayshacked on 2017-11-08
Hello, My latest version of Windows 10 Enterprise LTSB has been hacked again, so now trying Lubuntu. 

Firstly, why does the Timezone during installation think I am in the US and not the UK? When I watch Youtube video's showing the installation process from Brit's, it seems to detect the correct timezone on their system?

Secondly ticked the option to encrypt the drive during the installation and this automatically also ticks the LVM manager option as well, I click next but it always throws up an error. 

Any reason why this fails? It seems common on other distro's as well.

Any suggestions for setting it up manually as I have followed one suggested by Google in the past but it still failed.

Thanks!

---

### Post by ian-weisser on 2017-11-08
Timezone estimates are based on your IP address. If you are using a VPN or proxy...

Encryption: Exactly what error?

---

### Post by alwayshacked on 2017-11-08
There wouldnt be an ip address as it was a dd dev zero'd hard drive, with UTC time and date not plugged into a network at time of installation, so there's no NTP server directives given out over DHCP if thats one of the ways its detected? 

I'll write the error's down when I wipe this system again tomorrow, as I've got some linux distro's from some Linux magazines which wont even detect the disc in UEFI/legacy mode, so trying to establish if some firmware is being hacked at the same time. So far only one linux disc has managed to load and that was only once, every subsequent attempt its failed. Multiple optical disc drives from different manufacturers. However if the linux distro is downloaded onto a windows machine and burnt then it will work. Some strange things going on here, even the computer manufactuer's support team couldnt explain it and their diagnostics have not come up with anything either, but they were only basic tests to be fair, not forensics level.

---

### Post by alwayshacked on 2017-11-08
From memory, it was complaining about the swap partition being encrypted or not encrypted, but it was definately complaining about the swap partition.

---

### Post by alwayshacked on 2017-11-09
So the exact message is:
An unsafe swap space has been detected.
This is a fatal error since sensitive data could be written out to disk unecrypted. This would allow someone with access to the disk to recover parts of the encryption key or passphrase.
Please disable the swap space (eg by running swappoff) or configure an encrypted swap space and then run setup of encrypted volumes agains. This program will no abort.



The is when the option to encrypt the disk is selected during the gui/wizard installation process.

---

### Post by ian-weisser on 2017-11-09
Are you by chance selecting the 'encrypt home folder' box? (Quite different from whole disk encryption)
If so, the behavior is a known bug ([https://bugs.launchpad.net/ecryptfs/+bug/1670336](https://bugs.launchpad.net/ecryptfs/+bug/1670336))

Which release of Lubuntu? 16.04.3? 17.10? Something else?

---

### Post by alwayshacked on 2017-11-09
Selecting whole disk encryption which then also select the LVM manager option.

---

