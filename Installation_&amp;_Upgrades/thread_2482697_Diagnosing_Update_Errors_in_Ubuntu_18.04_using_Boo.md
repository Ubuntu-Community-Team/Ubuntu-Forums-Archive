---
title: "Diagnosing Update Errors in Ubuntu 18.04 using Boot Repair"
date: 2023-01-08
forum: Installation &amp; Upgrades
---

### Post by noexit23 on 2023-01-08
Howdy Folks!  I must first sadly concede I'm much more of a Windows guy, but let's just say I'm learning thanks to the community's generosity!  

We have an older laptop running Ubuntu 18.04 and when trying to update using apt-get I often get an error that reads something like:  "failed to get canonical path of 'aufs' ".

I booted to a Boot Repair USB flash drive I made and per the instructions at [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) I have begun by clicking the **Create a Boot-Info Summary button. **

I've uploaded the results to [https://pastebin.ubuntu.com/p/Rb2d756QPb/](https://pastebin.ubuntu.com/p/Rb2d756QPb/)  and would love your generous review of my dilemma.  Thanks so much for the guidance!

---

### Post by oldfred on 2023-01-08
Note that 18.04 expires April 2023, so best to be planning upgrade before it expires. You can get extend support for a fee.

Is error from "ubermix" which I am not familiar with.
It looks like report dumped a lot of additional info, as it was not familiar with that distribution, so printed all the grub files.

You also have newer UEFI hardware & booted live installer in UEFI mode. But installs are using BIOS boot on gpt partitioned drive.
Repair's normally are in same boot mode as you boot live installer, but it does look like Boot-Repair does not see the ESP - efi system partition so still will install grub in BIOS boot mode. But it defaults to first install. If you want second install as default boot, you can use Boot-Repair's advanced mode.

Canonical path issues, are often where you are trying to update live installer which is not updatable. 
Is this a docker image or something similar that is using the aufs?

---

### Post by noexit23 on 2023-01-08
I think I understand now.  Ubermix is a hybrid version of Ubuntu that I had installed several years ago.  From what I remember, Ubermix loads a sort of Read Only template of the OS on one partition and saves user files on another partition.  I thought I had deleted that install when I installed Ubuntu. But apparently not completely. Given the complexity of the problem with partitions and the expendable nature of this OS install, I think I'll just harvest the user's data, delete partitions and upgrade to the next version of Ubuntu after deleting ALL partitions and starting over.  Thanks so much for the guidance!

---

