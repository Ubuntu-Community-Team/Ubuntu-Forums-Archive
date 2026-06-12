---
title: "Tying to Install Linux on Dell Workstation wit Windows 7"
date: 2013-05-13
forum: Installation &amp; Upgrades
---

### Post by mathboy2 on 2013-05-13
I have a Perc H710p hard disk controller, running 2 1 TB drives in RAID 1.  When I try to install Ubuntu (and also same now with Red Hat) I get to the partition part of the installation, and the installer tells me that it doesn't see an operating system.  I can see various partitions--just nothing identified as a Windows 7 partition.  Which makes me nervous to go forward.  Also, for some reason, Dell configured this as a GPT drive (don't ask me why).  Any thoughts on the easiest way to get this done?  I would very much like to be able to dual boot.  

So obstacles that I see:
- Perc H710p controller (though Ubuntu sees the hard disk, just not that Windows is already installed)
- RAID
- GPT

If it would make it easier, I would probably sacrifice the RAID.  Given my luck with hard drives, I would prefer to have the RAID, though.  (It will at least be amusing to see two disks fail at the same time.....  And I know it will happen.)

Thanks in advance.  I did see that this question has been discussed, and I tried what I could from the advice there.

---

### Post by SeijiSensei on 2013-05-14
As a guess, the installation image doesn't include the PERC driver.

I suggest trying to install the server version of Ubuntu first, which might include the driver.  I'm a bit surprised that RedHat does not install, though, since it's usually quite good about drivers for Dell hardware.  If the server version installs, you can add a GUI desktop with something like "sudo apt-get install kubuntu-desktop".

If you take the "Try Ubuntu" approach from the installer, see if you can browse the hard drive and list the partitions with "fdisk -l".  If the drive looks correct, then you may be able to run the installer from the demo session.

---

### Post by mathboy2 on 2013-05-14
Thanks.  Both Ubuntu and Red Hat do recognize the Perc controller.  But I will try what you say as well and report back.

---

### Post by dooberheim on 2013-05-14
Hello.  I'm having the same issue on a Dell Inspiron 17R i7 2 GHzwith 1 TB hard drive.  Neither 10.04 LTS or 12.04 LTS seem to be able to see Windows 7 home premium (or Windows 8, which the machine originally came with).  I can run 12.04 from the DVD, and "fdisk -l" returns nothing.  The hard drive lists in Windows as an ST1000LM-02 HN-M101MBB ATA Device.  If it's a driver issue, can that be fixed?

Mark

---

### Post by mathboy2 on 2013-05-14
I did fdisk -l from a terminal window running Unbuntu from the DVD.  Nothing found.  The man files for fdisk are clear though that it does not work with GPT.  Note also that I can see my Windows files just fine from Unbuntu.  Any other ideas?

Thanks

---

### Post by SeijiSensei on 2013-05-14
> **mathboy2 said:**
> Note also that I can see my Windows files just fine from Unbuntu.Thanks

Did you try running the installer using the icon on the desktop?  If the DVD image sees the disk correctly, I suspect the installer will as well.

---

### Post by mathboy2 on 2013-05-14
> **SeijiSensei said:**
> Did you try running the installer using the icon on the desktop?  If the DVD image sees the disk correctly, I suspect the installer will as well.

Yes.  Same result...says it does not see any other operating system and gives me a choice between deleting everything and "doing something else."

---

### Post by mathboy2 on 2013-05-14
Any help would be greatly appreciated.  Thanks!

---

### Post by SeijiSensei on 2013-05-15
I've run out of ideas, I'm afraid.  You might want to consider posting a bug report at Launchpad.net.

---

