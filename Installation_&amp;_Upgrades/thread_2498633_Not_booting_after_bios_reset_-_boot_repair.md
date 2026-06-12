---
title: "Not booting after bios reset - boot repair"
date: 2024-06-22
forum: Installation &amp; Upgrades
---

### Post by russellenglandv2 on 2024-06-22
The power socket on my laptop broke, I opened it up to see if I could repair it, but it was beyond my capabilities. So took out the ssd drive and took the laptop to a local repair shop.

They've fixed the power socket but looks like they have reset the bios when they switched it on. So now it won't boot from the drive after I put it back in.

I followed these instructions from Lenovo to set the bios for Ubuntu, but still can't see my ssd driive

[https://download.lenovo.com/pccbbs/mobiles_pdf/thinkpad_p43s_p53s_ubuntu_installation_whitepaper_v1.0.pdf](https://download.lenovo.com/pccbbs/mobiles_pdf/thinkpad_p43s_p53s_ubuntu_installation_whitepaper_v1.0.pdf)

I can boot from a live USB and have installed boot-repair

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Here are the results

[https://paste.ubuntu.com/p/HTyYk7Srg9/](https://paste.ubuntu.com/p/HTyYk7Srg9/)

Note: I'm pretty sure I encrypted the ssd drive via ubuntu when I installed it about 4 years ago, I know the password but no idea what the bios settings were at the time

The laptop is a Lenovo T580 using Ubuntu 20.04

The USB live stick is Ubuntu 24.04

The ssd is a Crucial MX500 2tb

Hope you can help, Thanks, Russ

---

### Post by tea for one on 2024-06-22
Only your Sandisk USB is seen by boot-repair, the Crucial ssd is invisible at the moment.
Can you double check that the ssd is attached securely?

---

### Post by oldfred on 2024-06-22
Report only shows flash drive.
Before we often had to change UEFI settings for drive from Intel RAID to AHCI. If dual booting from Windows then had to add AHCI drivers into Windows for it to work.

But with my Dell, and only a NVMe type SSD it installed Intel® VMD drive and intially did not need AHCI setting in UEFI. It now shows both VMD and AHCI as I have also booted external drives.

Many Lenovo needed UEFI firmware updates. Is yours the most current?
Firmware versions compare to vendor's support page for your model.
sudo dmidecode -s bios-version
If drive seen:
udisksctl status

Older install, perhaps similar model?
[https://tothepoles.co.uk/2017/11/16/lenovo-t470p-ubuntu-16-04-install-notes/](https://tothepoles.co.uk/2017/11/16/lenovo-t470p-ubuntu-16-04-install-notes/)

---

