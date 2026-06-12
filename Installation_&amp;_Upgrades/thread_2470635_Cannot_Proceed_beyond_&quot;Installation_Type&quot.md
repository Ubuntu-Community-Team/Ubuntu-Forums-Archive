---
title: "Cannot Proceed beyond &quot;Installation Type&quot; when installing Ubuntu v20.04.3 LTS"
date: 2022-01-06
forum: Installation &amp; Upgrades
---

### Post by 78xTVkaRQP£ on 2022-01-06
[Note: Auther of thread is new to Linux]

I am trying to install/dual boot "Ubuntu v20.04.3 desktop amd64" alongside "Windows 10" on an Acer laptop with these details in the image below:
(The laptop is only showing two available options for "SATA Mode" in "BIOS Manager", which are: "AHCI" and "Optane without RAID". It is set to "Optane without RAID" perhaps because it only has a Hard Disk Drive as its ROM Device. Setting the "SATA Mode" to "AHCI" does not seem to help solve the problem and Windows 10, on the laptop, has trouble booting in this mode.)
[https://i.stack.imgur.com/W2gaj.png](https://i.stack.imgur.com/W2gaj.png)




The "Disk Management" screenshot of the laptop is as follows:
(As can be seen, I have had 260.00GB already reserved as an unallocated partition on which I intend/ed to install Ubuntu.)
[https://i.stack.imgur.com/NKFRn.png](https://i.stack.imgur.com/NKFRn.png)




After successfully booting the laptop from a 16GB bootable USB stick I had prepared using "Rufus v3.17", I stumbled upon this unfamiliar screen below at "step 5" of Ubuntu's installation wizard:
(I cannot continue because a partition/memory allocation on which Ubuntu will be installed has to specified. I cannot specify because no storage device is showing/able to be detected.)
[https://i.stack.imgur.com/TgNGj.png](https://i.stack.imgur.com/TgNGj.png)



&#55357;&#56911; Really need your help on how to go about this one. Thanks!

---

### Post by tea for one on 2022-01-06
Just to supply information about your first question.

Many Acer PCs require a supervisor/admin password to access all the UEFI settings.

In essence, you need to:-

Change SATA mode to AHCI where the default is RAID or Intel RST (Windows may need AHCI driver).
Disable TPM (Trusted Platform Module) or PTT (Platform Trust Technology)
Disable Optane memory and storage

[https://askubuntu.com/questions/1233623/workaround-to-install-ubuntu-20-04-with-intel-rst-systems](https://askubuntu.com/questions/1233623/workaround-to-install-ubuntu-20-04-with-intel-rst-systems)
[https://superuser.com/questions/1672500/ubuntu-installation-with-intel-rst?noredirect=1#comment2565531_1672500](https://superuser.com/questions/1672500/ubuntu-installation-with-intel-rst?noredirect=1#comment2565531_1672500)
[https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347](https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347)
[https://softwarekeep.com/help-center/how-to-download-standard-sata-ahci-controller-driver-on-windows-10](https://softwarekeep.com/help-center/how-to-download-standard-sata-ahci-controller-driver-on-windows-10)

---

### Post by oldfred on 2022-01-06
Windows AHCI instructions - some have found safeboot method better
[https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571](https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571) & 
[https://askubuntu.com/questions/1233623/workaround-to-install-ubuntu-20-04-with-intel-rst-systems](https://askubuntu.com/questions/1233623/workaround-to-install-ubuntu-20-04-with-intel-rst-systems) & 
But if you do a safe boot first to update Windows, then boot to UEFI/BIOS and change to AHCI and finally boot normally, it works
[https://superuser.com/questions/1672500/ubuntu-installation-with-intel-rst?noredirect=1#comment2565531_1672500](https://superuser.com/questions/1672500/ubuntu-installation-with-intel-rst?noredirect=1#comment2565531_1672500)
[https://askubuntu.com/questions/1233623/workaround-to-install-ubuntu-20-04-with-intel-rst-systems](https://askubuntu.com/questions/1233623/workaround-to-install-ubuntu-20-04-with-intel-rst-systems)

What model Acer?
Newer one's need Control-S to open the extra options.
Acer Swift 5 (2019) ctrl-s  in UEFI required to be able to change to AHCI mode.
[https://askubuntu.com/questions/1217061/installation-on-acer-swift-5-freezes-no-partitions-shown](https://askubuntu.com/questions/1217061/installation-on-acer-swift-5-freezes-no-partitions-shown)
Acer Aspire 5 Model A515-54-5649  Intel Core i5-10210U Install Tutorial
[https://ubuntuforums.org/showthread.php?t=2437702](https://ubuntuforums.org/showthread.php?t=2437702)

Many Acer also need "trust" setting after install on "ubuntu" entry in UEFI. With Acer it may be "unknown" and then you have to set trust in UEFI with Secure Boot on. But if installed with Secure Boot off, have to turn it off again.
Never lose the Password you set in UEFI, or immediately reset to blank.

Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)

---

