---
title: "How to reinstall Ubuntu 18.04.4 on a dual-boot system"
date: 2020-03-17
forum: Installation &amp; Upgrades
---

### Post by muhamedamr on 2020-03-17
[COLOR=#242729][FONT=Arial]My laptop has two hard disks 256GB (SSD) & 1TB (HDD).[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I have Windows 10 installed on the SSD and Ubuntu (18.04.4LTS Desktop) on a 300GB partition on the HDD.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I had a lot of driver issues with Nvidia drivers and most notably Audio drivers (Dummy Output) and now WiFi drivers which it doesn't even recognize my Wireless adapter now.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I have Ubuntu partitioned on the 300GB partition of the 1TB(HDD) as followed> (50GB for / partition), (12GB for /swap partition), (512MB for /boot partition) & (the rest of the 300GB for /home partition).[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]My question is how should I reinstall Ubuntu on these partitions (Which partitions should I format which I should leave them as is) & whether should I install a different version other than (18.04.4LTS) or not because I'm having a lot of trouble with drivers.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Thanks in advance![/FONT][/COLOR]

---

### Post by ajgreeny on 2020-03-17
Firstly you can delete the swap partition as that is no longer needed for Ubuntu; all the different DE versions now create a swapfile when installed.

When reinstalling use the Something Else option which will show you all the current partitions on disk; from that you can click on the current swap and delete it, then the current / partition and choose to reuse it by clicking the Change button.

Set the mountpoint as / and select to format the partition as ext4 (assuming you will be using the ext4 default).
Now go to the current /home partition and again choose to use it with mountpoint set as /home, but this time make sure the Format click box is NOT SELECTED.

Without knowing the partition layout on disk it's difficult to know whether or not you could add the swap area to another partition, but if it's next to one of the Ubuntu partitions it might be possible to do that very easily.

---

### Post by muhamedamr on 2020-03-17
Thanks for the reply :)
Can't I just delete both /home & /swap and reassign both to be a single /home partition? 
and select / and make sure its set as ext4 and format it ? 
and format the new /home partition in the process ?
and one more thing, should I format /boot or leave it ?
Thanks !

---

### Post by oldfred on 2020-03-17
I would not use /boot nor swap partitions. 
You can reuse /home if during Something Else install, you select that partition as /home but DO NOT check the format box.
Only if you have no data or totally want to redo settings should you reformat /home.
And be sure to have good backups before reinstalling for both Windows and Ubuntu. 

Is system UEFI or old BIOS? Be sure to install Ubuntu in same boot mode as Windows.

---

### Post by muhamedamr on 2020-03-17
Thanks for the reply, I have a Dell G3 3590 laptop which when I go to boot mode in BIOS I only see two options "Audit Mode" & "Deployed Mode".
I have Secure Boot disabled and windows FastBoot & Hibernation disabled as well.

---

### Post by oldfred on 2020-03-17
If you already installed, then you must have made the typical UEFI setting changes required on Dell. Some are unique to Dell, others are required for most systems.

Do make sure UEFI is up to date and SSD firmware is up to date.
Dell now supports update from within Ubuntu.
UEFI/BIOS updates brand model list  for Dell with (uefi >= 0.6.2 & dell >= 0.7.3) 
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)

You may then have to redo some of the settings you changed in UEFI.
Make sure drives are AHCI, & fast boot is off.
Windows may turn fast start up back on with updates, so you have to regularlly check that. Grub will only boot working Windows, so if fast start turned on you have to boot Windows from UEFI one time boot key, probably f12 to turn it back off.

You may need nomodeset to boot with nVidia, but newest Ubuntu now gives you the option to install the nVidia driver as part of the install of restricted extras. While LTS versions normally recommended 20.04LTS will not be out for another month. So you can try 18.04.4 or 19.10. Only if you want to experiment and do not need to worry if system breaks, you can install 20.04 and test it.

---

### Post by muhamedamr on 2020-03-17
Thanks a lot for your time and effort, I did as instructed but driver problems still persist ... Audio, Graphics drivers are not installed properly even though audio works completely fine on the bootable Ubuntu USB...

---

### Post by oldfred on 2020-03-17
How are you installing graphic drivers.
You should only install from Ubuntu repository or add ppa if very newest driver required.
And if reinstalling or changing versions, you must purge or else you get conflicts. New install does not remove old install.

If wrong nVidia driver or upgrade, you must purge & install correct driver
[https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946](https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946)
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)
[https://ubuntuforums.org/showthread.php?t=2362351](https://ubuntuforums.org/showthread.php?t=2362351)

Do not know audio issues.
If it works with live installer, I would expect it to work in your install. Can you check driver used in live installer?

---

