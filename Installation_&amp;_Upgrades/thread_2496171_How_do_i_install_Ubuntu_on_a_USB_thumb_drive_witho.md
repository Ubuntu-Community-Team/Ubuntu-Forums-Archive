---
title: "How do i install Ubuntu on a USB thumb drive without sacrificing the boot loader?"
date: 2024-03-16
forum: Installation &amp; Upgrades
---

### Post by coppercoin123 on 2024-03-16
Hi there,

so as I already had some issues with the boot loader of Win10 I wanted to install Linux directly on my USB device. Keeping everything separated and simple.

I saw that normal USB sticks don't perform well with the persistent mode (StackExchange Advice). So i got the fastest random r/w I was able to find (Kingston Data Travel Max with 1000mb/s read900mb/s write and 100-200mb/s random r/w) which should be more than fine for a direct install (recommendation was >20mb/s random r/w)

Now i just picked the first version on LinusDistroWatch that i found which was Linux Mint. However I saw that it won't work as intended, as it its a copy of Ubuntu which shares a common and old installation bug of Ubunut. It doesn't mention which bug# exactly so i couldn't take a look at it:

[https://forums.linuxmint.com/viewtopic.php?t=415443&sid=084114f200e2e5dcf3693e7771896556](https://forums.linuxmint.com/viewtopic.php?t=415443&sid=084114f200e2e5dcf3693e7771896556)


My question:

How do I then install Ubuntu on my new USB thumb drive without touching my Windows Bootloader? The GRUB2 bootloader should go ONLY on the USB thumb drive (so i can take it anywhere i want). Like the linked post says the bug however always writes the GRUB2 on the 1st NVME killing my Win Bootloader. I am not a fan of removing my first NVME physically and i don't want to remove it with each Upgrade/Update to prevent killing my bootloader.

Hope there is a simple fix or what I need to consider during the installation interface questions =)

Thank you!

---

### Post by tea for one on 2024-03-16
The foolproof way is to isolate or physically remove the Windows disk.
Otherwise, during the live session but before starting the Ubuntu installer, you have to remove the boot flags from the Windows EFI partition.

When you install to an external device, double check that the new installation will create an ESP.

---

### Post by coppercoin123 on 2024-03-16
Thanks for the quick reply.

[COLOR=#000000]> you have to remove the boot flags from the Windows EFI partition

I am only aware of one boot flag. I think its also the "active" flag. Are there more than i need to remove?

Do I need to change the attribute ([/COLOR]Globally unique identifier [https://en.wikipedia.org/wiki/GUID_Partition_Table](https://en.wikipedia.org/wiki/GUID_Partition_Table) [COLOR=#000000]) as well? Like from [/COLOR][COLOR=#202122][FONT=monospace]C12A7328-F81F-11D2-BA4B-00A0C93EC93B (EFI) to Windows Basic Data Partition [/FONT][/COLOR][COLOR=#202122][FONT=monospace]EBD0A0A2-B9E5-4433-87C0-68B6B72699C7 ?


[/FONT][/COLOR][COLOR=#000000]> When you install to an external device, double check that the new installation will create an ESP.

[/COLOR][COLOR=#4D5156][FONT=arial]ESP = EFI system partition?

[/FONT][/COLOR][COLOR=#000000]How do I do that during installation? I assume before installation is too early and afterwards is too late, so is there a keyword i should be looking in the installation menu?


[/COLOR][COLOR=#000000]> The foolproof way is to isolate or physically remove the Windows disk.

[/COLOR][COLOR=#000000]When exactly would I have to remove it? Only exactly once forever with installation or with major upgrades/updates or version changes as well?

The idea is to use it as mobile linux, so I can use it anywhere also at friends where i might not be able to remove their harddrive.

[/COLOR]

---

### Post by tea for one on 2024-03-16
When you remove the boot and esp flags from your Windows disk, the Ubuntu installer will not interfere with your Windows Boot Manager.

The installer will automatically create an ESP for your external USB but it will tell you the partitions being created.
If it doesn't offer to create an ESP, then stop the installation.

Boot into a "Try Ubuntu" live session, open Gparted and explore your Windows Efi partition.

---

### Post by tea for one on 2024-03-16
By the way, back up all your Windows data before embarking on this project.

---

### Post by ubfan1 on 2024-03-16
Launchpad Bug 1396379 - Grub installs to wrong disk, is a "feature" of the ubiquity installer used in Ubuntu 22.04.  A different installer is used for 23.10, and actually installs grub to the disk you specify.  With the LTS 24.04 due out next month, might be easier to use 23.10 and upgrade next month.

---

### Post by oldfred on 2024-03-16
I have installed to multiple flash drives and now external SSDs.
And have had to work around the bug. My work around is more complicated, but is in bug report.
Posted work around to manually unmount & mount correct ESP during install #55 or( #23 & #26)
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Remove esp flag from Windows before install to second or external drive - Tim Richardson
[https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator) & 

Issue is with any official version of Ubuntu or unofficial version of Ubuntu that uses the Ubiquity installer.
Ubuntu is converting to the Subiquity installer with does let you choose drive for ESP.
And Lubuntu uses Calamares installer and Kubuntu will use Calamares with 24.04. Kubuntu 24.04 has a bug in a python script that causes it to crash, but workaround exists.
Once I edited the python script, Calamares installed Kubuntu 24.04 to my sdb drive without issue.

If using flash drive, often better to use a lightweight flavor which then uses less resources. I found Kubuntu which is not really a lightweight flavor also works well.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, Xubuntu, Ubuntu MATE, Budgie

I also now highly recommend external SSD. 
I got into external SSD  more by accident. Built system in 2017 that had M.2 that could use SSD or NVMe drive. NVMe drives were very expensive then so used a smaller SSD. Wanted to upgrade to larger drive, so purchased new NVMe drive as now only a bit more expensive than SSD, but faster. And then used M.2 SSD in a USB3/USB-c to M.2 adapter.
Found external SSD worked so well I will not buy anymore flash drives, but I have a lot of flash drives already, almost all with full installs, some now obsolete & most with data.

---

### Post by erastus11 on 2024-05-09
@OldFred
Thank you for your info on the issue described in this thread. I'm hoping you will see this and answer my additional questions and concerns. I am posting here because it follows with the original question.

It's been a while since I was bit by the bug that made my windows system unbootable when I tried to install Ubuntu to an external SSD. I'm getting ready to try this again, with the knowledge gained. (Last time it happened, I restored my Windows and then installed a different distro to the external drive without any issues.) This time I'm going to be installing Mint Debian. But I'm asking here since Mint is based on Ubuntu.

I am able to selectively turn off the drives in my UEFI bios settings. Is that enough to be safe, or is removing the flags a better precaution?  I could also physically remove the Windows NVMe drive from the laptop. I'm wondering if turning off the drive in BIOS, and/or turning off the partition flags is enough. Which is the preferred/best option?

Then my concern is what happens later on, when grub gets reconfigured after an update or upgrade? Will the updater know NOT to write to the Windows EFI? 


Thanks.



> **oldfred said:**
> I have installed to multiple flash drives and now external SSDs.
And have had to work around the bug. My work around is more complicated, but is in bug report.
Posted work around to manually unmount & mount correct ESP during install #55 or( #23 & #26)
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Remove esp flag from Windows before install to second or external drive - Tim Richardson
[https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator) & 

Issue is with any official version of Ubuntu or unofficial version of Ubuntu that uses the Ubiquity installer.
Ubuntu is converting to the Subiquity installer with does let you choose drive for ESP.
And Lubuntu uses Calamares installer and Kubuntu will use Calamares with 24.04. Kubuntu 24.04 has a bug in a python script that causes it to crash, but workaround exists.
Once I edited the python script, Calamares installed Kubuntu 24.04 to my sdb drive without issue.

If using flash drive, often better to use a lightweight flavor which then uses less resources. I found Kubuntu which is not really a lightweight flavor also works well.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, Xubuntu, Ubuntu MATE, Budgie

I also now highly recommend external SSD. 
I got into external SSD  more by accident. Built system in 2017 that had M.2 that could use SSD or NVMe drive. NVMe drives were very expensive then so used a smaller SSD. Wanted to upgrade to larger drive, so purchased new NVMe drive as now only a bit more expensive than SSD, but faster. And then used M.2 SSD in a USB3/USB-c to M.2 adapter.
Found external SSD worked so well I will not buy anymore flash drives, but I have a lot of flash drives already, almost all with full installs, some now obsolete & most with data.

---

### Post by oldfred on 2024-05-09
Do not know Mint and what installer it now uses. If still the Ubiquity installer you have to use one of the work arounds. But gpt partitioning in advance and making sure you have an ESP on external drive is most critical as then it can be easily fixed if not correct.

New versions of Ubuntu use the Subiquity installer that supposed has fix for where to install grub. And the Calmares installer works to let you choose drive to install grub. 

I really like a lighter weight install for external devices. Not sure if Mint is a lighter weight flavor or not.

I do like Kubutu and the 24.04 version  now has the Calamares installer that Lubuntu has used.
I also did a test install of KDE Neon which also used the Calamares installer and looked a lot like Kubuntu even though also not an official flavor.

Major updates to grub reinstall to the ESP you mount in fstab. As long as it is the ESP on the external drive it should be ok.

But good backups are always required for any major system change.

---

