---
title: "No Bootloader after Ubuntu 9.10-installation"
date: 2009-12-25
forum: Installation &amp; Upgrades
---

### Post by Klingan on 2009-12-25
Greetings!

I just installed Ubuntu 9.10 to initiate my converting-progress from Windows to Linux.

I have two 250 GB drives set up in a RAID 0-array.
I have a few partitions.
[LIST]
[*]**1 PRIMARY x 100 MB** - Automatically created by Windows 7
[*]**1 PRIMARY x 100 GB** - System OS for Windows 7 (NTFS)
[*]**1 PRIMARY x 100 GB** - System OS for Ubuntu (EXT4)
[*]**1 LOGICAL x 4   GB** - SWAP-partition for Ubuntu
[*]**1 LOGICAL x 296 GB** - Unallocated Area - Intended for DATA-partition shared between the two OS's
[/LIST]

I have had **Windows 7** installed for a while.
I did not want to install Ubuntu through **WUBI** (Windows Installer) but wanted a separate, dedicated partition for this with the EXT4-file system.

During setup, I chose "**Advanced Setup**" with manual setting on partitions. I flagged the OS-partition with "/" and added a SWAP-partition right after.

After the setup was complete - It rebooted the computer.

Neither one of the Windows 7 nor GRUB2-bootloader showed up, instead the only message displayed was that Windows 7 bootinfo(?) was damaged and I got two alternatives. One was to repair Windows 7, the other one was to boot normally.

- How do I get a working Boot Loader so I can boot either Operating System? The only one working at the moment is Windows 7, and the error display message with the repair-alternative only showed up once.

Thank you in advance!

---

### Post by Klingan on 2009-12-26
Anyone?

---

### Post by darkod on 2009-12-26
I haven't tried raid myself but see if this can help:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Scroll down a bit for bootloader installation.

---

### Post by Klingan on 2009-12-27
But I'm not using a software RAID but a Hardware RAID? Is it really supposed to be that tricky? The reason I retried Linux was that it was supposed to be easy to setup nowadays. :-/

---

### Post by darkod on 2009-12-27
Do you use a dedicated raid card or just the onboard function of the motherboard? If you use the mobo raid that is the fakeraid mentioned in the article. That's how it's called.
Software raid is something else, although the fakeraid is a software raid in a way.
Because the fakeraid is sort of a raid simulation, installing the bootloader can be tricky sometimes but people have reported it's working fine sometimes even without needing to set it up additionally.
I wouldn't say it's complicated, read the article if you're using fakeraid and it's few commands basically.

---

### Post by Klingan on 2009-12-27
I don't want to put too much effort into it, since that was the reason I decided to retry Linux. :-)

It's an onboard function on the MB. But is it certain this is the cause of the problem?

Thank you for your engagement!

Kind Regards,
Tommy

---

### Post by presence1960 on 2009-12-27
Try installing with the alternate text based installer for RAID support. Get it [here]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate").

---

### Post by Klingan on 2009-12-27
> **presence1960 said:**
> Try installing with the alternate text based installer for RAID support. Get it [here]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate").

Alright. I might just try that. But I couldn't notice any specifications about supporting RAID? It just seemed to be an alternative for those who could not use the graphical enironment on their PC during install?

---

### Post by darkod on 2009-12-27
**Alternate install CD**

  The alternate install CD allows you to perform certain specialist installations of Ubuntu. It provides for the following situations:
  
[LIST]
[*]setting up automated deployments;
[*]upgrading from older installations without network access;
[*][COLOR=Red]LVM and/or RAID partitioning; [/COLOR]
[*]installs on systems with less than about 256MB of RAM (although note that low-memory systems may not be able to run a full desktop environment reasonably). 


[http://releases.ubuntu.com/karmic/](http://releases.ubuntu.com/karmic/)
[/LIST]

---

### Post by presence1960 on 2009-12-27
> **darkod said:**
> **Alternate install CD**

  The alternate install CD allows you to perform certain specialist installations of Ubuntu. It provides for the following situations:
  
[LIST]
[*]setting up automated deployments;
[*]upgrading from older installations without network access;
[*][COLOR=Red]LVM and/or RAID partitioning; [/COLOR]
[*]installs on systems with less than about 256MB of RAM (although note that low-memory systems may not be able to run a full desktop environment reasonably). 


[http://releases.ubuntu.com/karmic/](http://releases.ubuntu.com/karmic/)
[/LIST]

+1
Thanks Darko

---

### Post by Klingan on 2009-12-27
Okay, I simply searched for RAID on the current page but there was nothing, I'm assuming you found that on some kind of Wiki?

It supports RAID-partitioning. But I could repartition my remaining space on the current drive with the installer I used - which should mean it supported my RAID aswell (since it could find & edit the drives) ?

I just don't want initiate a big action unless the problem is obvious.

Thank you. :)

---

### Post by presence1960 on 2009-12-27
> **Klingan said:**
> Okay, I simply searched for RAID on the current page but there was nothing, I'm assuming you found that on some kind of Wiki?

It supports RAID-partitioning. But I could repartition my remaining space on the current drive with the installer I used - which should mean it supported my RAID aswell (since it could find & edit the drives) ?

I just don't want initiate a big action unless the problem is obvious.

Thank you. :)

[https://help.ubuntu.com/9.10/installation-guide/amd64/module-details.html](https://help.ubuntu.com/9.10/installation-guide/amd64/module-details.html)

scroll down to configuring multi disk devices

---

### Post by gilson585 on 2010-01-23
Your issue is GRUB2 does not support booting fakeraid. Use this guide [http://ubuntuforums.org/showthread.php?t=1360445](http://ubuntuforums.org/showthread.php?t=1360445) This is supposed to be fixed in 10.04 when it is released.

---

