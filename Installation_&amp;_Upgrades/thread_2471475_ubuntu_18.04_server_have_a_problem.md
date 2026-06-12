---
title: "ubuntu 18.04 server have a problem"
date: 2022-01-31
forum: Installation &amp; Upgrades
---

### Post by ferdo23 on 2022-01-31
Hi all,

i have tried to install the Ubuntu 18.04 server edition with pendrive 

in the server i have single SSD only

while installing the os part the Disk Category have a problem like the **/dev/sda** is not showing at all 

the ssd showing like **/dev/sdb** only, while loading the os it's says **unable to open the /dev/sda** 

 someone help me to resolve the issue 

i need to install the os on /dev/sda only 

Regards
Praveen

---

### Post by oldfred on 2022-01-31
Many need UEFI firmware update & SSD firmware update.
Do you have latest firmware for both?

Also drives need to be set for AHCI. But if you can see one drive, you probably have that set already?

What brand/model system?
Some need extra settings.
Newer UEFI/gpt or old BIOS/MBR system?
Microsoft has required vendors to install in UEFI mode to gpt partitioned drives since 2012, so most hardware now is UEFI/gpt.

On my system a flash drive as sdf gets remounted as sda on reboot, and every other internal drive moves up a letter.

---

### Post by TheFu on 2022-01-31
Unless there is a really good reason, I wouldn't install 18.04 on any system today ... or for the last year.  20.04 is the current LTS and a new LTS, 22.04, will be ready for production use mid-June-ish. It will be released in April.

There are some Intel-Windows-only storage things that don't work with Linux. I've seen some Linux beta drivers for these, but don't know when or if they will be included in Ubuntu installers. [https://askubuntu.com/questions/1162452/problem-installing-ubuntu-in-a-laptop-with-intel-optane](https://askubuntu.com/questions/1162452/problem-installing-ubuntu-in-a-laptop-with-intel-optane) shows one and provides a solution (disable it in Windows first).

---

### Post by ferdo23 on 2022-01-31
both the firmware are updated 

it's server we are using legacy to install 

gigabyte g482-z52 

new bios

---

### Post by MAFoElffen on 2022-02-01
That is a very nice server. 

If it has HBA RAID... Which model HBA RAID Card does it have? You probably see the ROM info for it in the POST messages... What hot-key is displayed to toggle into the HBA RAID ROM setup utility? If it has HBA RAID, then the drives in the 8 bay back[plane will show up under the HBA ROM Setup. Most of these systems came ordered with HBA RAID cards...

If it does not have an HBA RAID Card, then the drives will show up under Advanced > Mass storage in the BIOS setup. That is, if the SATA Controller is turned on... Ensure that the cabling is correct for that configuration, between the Motherboard and the backplane.

The SATA Controller on that board has it's own section in BIOS Setup, under AMD CBS > FCH Common Options > SATA Controller. The SATA Controller chip itself can be turned off in BIOS, as a setting. Ensure it is set to enabled. Ensure the SATA mode is set to ACHI frefetch. 

My big question is that this is a UEFI motherboard/BIOS... Why have you decided to try to boot and install as Legacy/CSM?

---

