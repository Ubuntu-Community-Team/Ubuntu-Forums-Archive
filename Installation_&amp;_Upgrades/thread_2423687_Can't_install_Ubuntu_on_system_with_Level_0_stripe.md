---
title: "Can't install Ubuntu on system with Level 0 striped RAID"
date: 2019-07-27
forum: Installation &amp; Upgrades
---

### Post by mnealbarrett on 2019-07-27
My system consists of a Dell Precision T5500 with 2 Xeon processors, 24GB of RAM, and an Nvidia Geforce 760 graphics card.  I recently decided to replace my hard drive with 2 identical 512GB SSD drives running as a Level 0 striped RAID.  I have been encountering major problems getting Ubuntu to install on my system. I have been trying to install Ubuntu with LUKS full-disk encryption and LVM.  Basically, every single time I run the installation, near the end I get an error which basically says that the installer can't install grub to /dev/sda, and a message that says "This is a fatal error". I get a drop-down menu that wants me to choose where to put the MBR, but NONE of the options work. 

I have tried various recent versions of Ubuntu (18.04, 18.10, Ubuntu proper, Ubuntu Mate), and even tried the most recent version of Debian, all with the same results. To try to pin down the problem, I stripped by system down to just the core hardware -- just the graphics card and the two hard drives plugged into SATA0 and SATA1.  I am setting up the RAID volume with the RAID setup utility built-into the BIOS.  The utility is very simple to use.

BTW, to prove that there is NOTHING wrong with me or my hardware, and I am doing NOTHING wrong, Fedora 30 with full-disk encryption installs totally fine with no problems whatsoever, on the *very same hardware*.

I did find a VERY annoying work-around. I disconnected my RAID drives, and plugged a small (120GB) drive into SATA0.  I installed Ubuntu on the small drive (without encryption). Then I connected my RAID drives to SATA1 and SATA2, set up the RAID volume, and install Ubuntu with LUKS and LVM to the RAID volume. At the end, the installer puts the MBR on the small drive.  This is FAR from ideal, because if I ever boot into the Ubuntu install on the small drive and either run "update-grub" or update the OS (which will basically do the equivalent of an "update-grub" at the end), I will likely lose EVERYTHING. This is because the Ubuntu installation on the small drive will fail to see the installation on the RAID volume (since there is no MBR on the RAID volume), and I will lose the ability to boot into the RAID volume.

I plan to edit or add to this message soon with pictures of what is going on.

---

### Post by oldfred on 2019-07-27
Do not know RAID nor LVM.

But issue is the install of grub to RAID. Desktop installer now will install, but grub will not. They removed that capability back after 12.04 with the alternative installer being eliminated which was for desktop with LVM or RAID. They said they would add it to desktop but use server installer until added. They then added LVM, and now RAID almost works except grub install.

You can use server installer or install grub separately. Or use separate boot drive as you have configured.
Difference if UEFI or BIOS installs. And if drive is MBR or gpt.
With UEFI, you should be using gpt. And then must have an ESP - efi system partition. Or if BIOS and gpt you need a bios_grub partition. Best not to use the now very old MBR partitioning but can.

       May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by mnealbarrett on 2019-07-27
Thanks for the reply. My desktop system is BIOS, which is likely the reason I am having problems. I am familiar enough with UEFI, from installing Ubuntu on a couple of new laptops. If my desktop was UEFI, I might not have problems, since UEFI systems have a dedicated partition.

I do not know how to set up a bios_grub partition.

One other thing: what is Fedora doing? They use grub, and like I said, Fedora installs flawlessly on my desktop.

---

### Post by oldfred on 2019-07-27
I do not think it is grub, but Ubiquity installer.
Debian just installed grub for me to sdb's ESP. Ubiquity only installs grub to ESP on first drive.

If using gpt but BIOS, you need a 1 or 2MB unformatted partition with the bios_grub flag for grub to install. Then manual install of grub or Boot-Repair should correctly install grub.
I started using gpt in 2010/2011 on my BIOS only system before UEFI became standard with Windows 8 in 2012. Apple also used EFI which is now first version of UEFI.

Did you try the server installer which supports RAID? And then you can add desktop of choice or other software.

---

### Post by mnealbarrett on 2019-07-28
> **oldfred said:**
> 
Did you try the server installer which supports RAID? And then you can add desktop of choice or other software.

Ubuntu Server is a total no-go.  The installer in Ubuntu Server did not see my RAID volume, it just detected the two individual drives. (Which is odd, you'd think a *server* OS would have support for hardware RAID volumes)  There also was no support in the installer for LUKS.

---

### Post by oldfred on 2019-07-28
The first version of the new Subiquity, gui based server installer did not support LVM & RAID. 
Did you use an older version? And the gui based installer?

The older text based server has always supported RAID & LVM.

[https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes](https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes)
> The next generation [Subiquity]("https://github.com/CanonicalLtd/subiquity") server installer, brings the comfortable live session and speedy install of Ubuntu Desktop to server users at last. 


Also new in 18.04.3 is support for encrypted LVM volume groups and  reusing existing partitions, as well as LVM, RAID, vlans, and bonds  which were added in 18.04.1. 

---

### Post by mnealbarrett on 2019-07-28
> **oldfred said:**
> The first version of the new Subiquity, gui based server installer did not support LVM & RAID. 
Did you use an older version? And the gui based installer?

The older text based server has always supported RAID & LVM.

[https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes](https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes)

I grabbed an ISO for Ubuntu server 19.04 live, and put it on a flash drive. When I booted it, the installer asked if I wanted to upgrade to version 19.06 of the installer, so I went ahead and let it do that. I used the text version of the installer.

---

### Post by TheFu on 2019-07-28
Is it HW-RAID or Fake-RAID?

---

### Post by mnealbarrett on 2019-07-28
> **TheFu said:**
> Is it HW-RAID or Fake-RAID?

Hardware RAID.  I set up the RAID volume using the utility built-into the BIOS.

---

### Post by oldfred on 2019-07-28
If from UEFI/BIOS that is FakeRAID.
Hardware RAID is a separate controller card.

       Ubuntu Software RAID vs FakeRaid vs Hardware RAID. Home user
[URL="https://ubuntuforums.org/showthread.php?t=2422516&p=13873154#post13873154"]https://ubuntuforums.org/showthread.php?t=2422516&p=13873154#post13873154

      [/URL]Not updated since 2017, so may not be totally correct. But explains differences.
 [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
dmraid was replaced by mdadm for handling FakeRAID in Ubuntu 14.04 and later. 
    [URL="https://ubuntuforums.org/showthread.php?t=2422516&p=13873154#post13873154"]
[/URL]

---

### Post by mnealbarrett on 2019-07-30
> **oldfred said:**
> If from UEFI/BIOS that is FakeRAID.
Hardware RAID is a separate controller card.

       Ubuntu Software RAID vs FakeRaid vs Hardware RAID. Home user
[URL="https://ubuntuforums.org/showthread.php?t=2422516&p=13873154#post13873154"]https://ubuntuforums.org/showthread.php?t=2422516&p=13873154#post13873154

      [/URL]Not updated since 2017, so may not be totally correct. But explains differences.
 [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
dmraid was replaced by mdadm for handling FakeRAID in Ubuntu 14.04 and later. 
    [URL="https://ubuntuforums.org/showthread.php?t=2422516&p=13873154#post13873154"]
[/URL]

All of this has been an adventure down a rabbit hole.  My system is a Dell Precision T5500, which is called a "mini server".  I thought a "mini server" would have a real hardware RAID, but turns out it does not. It uses an Intel software RAID.  Probably why Ubuntu Server didn't detect the RAID volume, just as two individual drives.

Anyway, this system has a PCI-X slot in addition to the 4 normal PCI Express slots. Can anyone recommend a cheap PCI-X SATA (*not* SAS) RAID card?

---

### Post by TheFu on 2019-07-30
In a home environment, where you can't have hot-spares to replace a failed HW-RAID, almost everyone uses SW-RAID at this point. It is much more flexible, just as fast, and doesn't tie you to specific hardware.  Very few people use Fake-RAID anymore, since it has all the negatives of using HW-RAID, and none of the positives of using SW-RAID.

If you **Must** have HW-RAID, then you don't want a cheap card.  Get an LSI. Sorry, buy 2 LSI cards, identical, test both, and use one. If the data is THAT important that only HW-RAID will work, then having a spare is only prudent.

But .... you're only doing RAID0?   No need for HW-RAID in that config. Use LVM in a striped config. Use NVMe SSD storage and you won't be able to touch that performance with any normal SATA RAID.

---

