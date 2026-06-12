---
title: "Ubuntu bootloader vaporizes after installing alongside Windows 10 RS2"
date: 2017-04-05
forum: Installation &amp; Upgrades
---

### Post by jykang41 on 2017-04-05
[FONT=Verdana]Hi all,

I installed Ubuntu 16.04.2 alongside Windows 10 RS2(clean installed) by using GPT-formatted USB.

My system configuration is like this:
1) UEFI turned on and Secureboot turned off.
2) Bootloader has been installed in "sda", "swap" mounted in "sda".
3) In "sdb", Windows has been installed and after that Ubuntu was installed "sdb5" with "/" mounted.
4) "sda" is HDD and "sdb" is SSD.(Not that important IMO..)

[/FONT]After installation, Ubuntu boots sucessfully with grub.
However, after *first booting Windows 10 RS2 via grub*, grub vanishes and my computer boots automatically through Windows Loader.

Since there is no "ubuntu" boot option in BIOS configuration, It looks like Windows 10 overwrites Ubuntu bootloader..!

How can I solve this problem? Any possible solutions? :/

I tried boot-repair, every time I boot in to windows, I should run boot-repair over-and-over to boot my ubuntu :/

boot-repair result:
[http://paste2.org/PfO9KDD4](http://paste2.org/PfO9KDD4)

---

### Post by ajgreeny on 2017-04-05
Rub **Boot-Repair** again and follow the instructions there to run the Boot-Info-Script.	 
**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system.

---

### Post by jykang41 on 2017-04-05
Added boot-repair results!

---

### Post by oldfred on 2017-04-05
What brand/model system?

They must have fixed grub. You show /EFI/ubuntu in ESP  on sdb.

Up until now, every install to sdb has had to have the ESP - efi system partition on sda. When I do a full install on sdb, it overwrites my /EFI/ubuntu folder on sda, even though I specify sdb for grub boot loader install. I have not installed 16.04.2, but had same issues with early installs of 17.04.
Some users had to add an ESP to sda to get UEFI install on sdb work or allow grub to install at all.

Can you boot Ubuntu from UEFI one time boot key, often f10 or f12, but depends on brand, check manual.

---

### Post by jykang41 on 2017-04-08
Fixed problem, Simply turning of hibernation in windows solved problem. :/

---

