---
title: "Windows partition not found? Installed on separate drive"
date: 2015-12-06
forum: Installation &amp; Upgrades
---

### Post by megawatt2 on 2015-12-06
There are three drives on my computer, the first two are in Raid 0 and have Windows 8.1 installed. In my third drive, I had openSUSE installed. Every time you started the computer it would have the Grubloader open up and you could choose an operating system, openSUSE or Windows.

I wanted to give Ubuntu a shot, since it's been years since I last used it, and when I put the install disc in, it didn't detect the Windows partitions or the two hard drives in raid 0. It only detected the openSUSE partition and the swap partitions. I thought okay, no problem, and partitioned the entire third hard drive to have Ubuntu installed.

Now this is the problem, Ubuntu installed fine, but I'm not able to boot into Windows. If I choose to boot through the Raid 0 drives, Ubuntu loads up instead. When I take out the third hard drive and restart the computer, it goes into Grub Rescue mode. I put the Windows installation CD back in, and it was able to detect the Windows partitions and it was able to detect that Windows 8 was still installed, but programs like gParted say "Unallocated" for one of the hard drives in raid 0, and "Unknown" for the other hard drive.

How to get Windows to load correctly again? Did the openSUSE grubloader somehow 'encrypt' the hard drives in a way so that only grubloader could see it?

---

### Post by oldfred on 2015-12-06
Best to see details:
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Grub did not correctly install to a RAID configuration except with server installer. Did you use Desktop? Did you use Something Else install option. Every other option installs grub to drive seen by BIOS as sda, but I do not know RAID and it may still install to that if BIOS set that as default.

Was Windows hibernated or fast start up on?

---

### Post by megawatt2 on 2015-12-06
Here's the boot-info: [http://paste.ubuntu.com/13769772/](http://paste.ubuntu.com/13769772/)

I used Xubuntu, and went to customize the partition, deleted all the previous SDC partitions, then created a 109GB OS partition, 10GB Swap partition.
SDA and SDB which have Windows installed as Raid 0, did not show up at all in the list of partitions.

I chose SDC to install the boot loader to.

It was in complete shutdown mode, no fast start up or hibernate.

---

### Post by oldfred on 2015-12-07
I do not know RAID, but thought BIOS booted the boot loader in the RAID root, not sda.
You do now have grub installed to the MBR of sda, Windows to the MBR of sdb & grub to sdc.

Best to only have grub installed to Ubuntu drive or sdc. And keep your Windows installed to sda.
But your sda & sdb are not matched, so are they RAID? 
Ubuntu sees the two RAID drives separately.

Not sure sure if you just need to reinstall Windows boot loader to sda. Script does not seem to show any RAID at all. But there are many types of RAID and that is what I do not know.

---

### Post by megawatt2 on 2015-12-07
> **oldfred said:**
> I do not know RAID, but thought BIOS booted the boot loader in the RAID root, not sda.
You do now have grub installed to the MBR of sda, Windows to the MBR of sdb & grub to sdc.

Best to only have grub installed to Ubuntu drive or sdc. And keep your Windows installed to sda.
But your sda & sdb are not matched, so are they RAID? 
Ubuntu sees the two RAID drives separately.

Not sure sure if you just need to reinstall Windows boot loader to sda. Script does not seem to show any RAID at all. But there are many types of RAID and that is what I do not know.

Hi OldFred, thank you, buI I was actually able to solve it through the Windows installation CD.

If anyone ever has this issue, please check out this article: [http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/t](http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/t)

---

### Post by oldfred on 2015-12-07
Glad you got it working.
Your link has an extra /t at end and goes to wrong place. But those repair instructions are just the standard Windows repairs posted many places.

---

