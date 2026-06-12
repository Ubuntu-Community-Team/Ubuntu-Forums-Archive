---
title: "MBR boot error"
date: 2014-09-12
forum: Installation &amp; Upgrades
---

### Post by Chris_Brody on 2014-09-12
Hello,

Asus eee PC was stuck at MBR and flashing cursor so I started up from a live USB and ran boot-repair. Rebooting gave "error: hd0,msdos3 out of disk" and a grub rescue prompt. Here's the pastebin URL, can anyone help?

[FONT=Arial]http://paste.ubuntu.com/8326436
[/FONT]

---

### Post by oldfred on 2014-09-12
I shows you have 10.10 which expired April 2012.
"Your version of Ubuntu has reached End Of Life. It is no longer supported by Canonical and it is likely that many problems simply cannot be solved. The Staff recommends that you upgrade to a supported version. Please refer to this.
Ubuntu 10.04 (Lucid Lynx) Desktop End of Life reached on May 9, 2013
[http://fridge.ubuntu.com/2013/05/10/ubuntu-10-04-lucid-lynx-desktop-end-of-life-reached-on-may-9-2013/](http://fridge.ubuntu.com/2013/05/10/ubuntu-10-04-lucid-lynx-desktop-end-of-life-reached-on-may-9-2013/)
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Upgrading_from_Ubuntu_10.04_LTS_to_Ubuntu_12.04_LTS](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Upgrading_from_Ubuntu_10.04_LTS_to_Ubuntu_12.04_LTS)
[http://www.ubuntu.com/info/release-end-of-life](http://www.ubuntu.com/info/release-end-of-life)
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)
This command will print the exact status of your system.
ubuntu-support-status

You also have a very unusual configuration.
Grub2 is not normally installed to a partition boot sector as it does not really fit. It converts to blocklists or hard coded addresses. Then if any part of grub is moved on drive from an update or even fsck then it is broken as address is wrong and has to be reinstalled.
Normal boot is grub in MBR of drive not PBR of partition. Your boot process is actually using a Windows boot loader (syslinux) in MBR to jump to PBR of sda3 to load grub.

But since your version is obsolete it will be difficult to fix.

Your sdb drive may also have issues as it is not really shown.

---

