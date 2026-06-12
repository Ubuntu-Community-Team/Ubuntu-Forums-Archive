---
title: "Problem with GRUB when upgrading an external USB HD from 18.04 to 20.04"
date: 2021-03-14
forum: Installation &amp; Upgrades
---

### Post by Don_Phillips on 2021-03-14
Hi all,

I had a laptop that was running Ubuntu 18.04 that finally refused to power up.

I replaced it with an HP Pavillion.

I removed the HD from the dead laptop and purchased an external USB case for the drive.

With the drive installed and plugged in, I've successfully booted to Ubuntu 18.04.

Then, I decided to 'do-release-upgrade', having successfully done this on two other systems (that weren't running on an external USB HD).

I'm pretty sure that I foobar'd the GRUB installation, as it offered me options when installing grub that I hadn't seen before.

In any event, after completing the upgrade, when booting, I escape to the point that I can choose the external USB HD as the boot device.

At that point, I get "error: symbol 'grub_file_filters' not found" and end up entering grub rescue mode.

I booted the device from a Ubuntu 20.04 LTS USB flash drive, downloaded and installed boot-repair. Ran boot repair with the external USB HD plugged in. Selected the "Recommended Repair" button and generated the following pastebin:

        [https://paste.ubuntu.com/p/cbFPZMzHzr/]("https://past.ubuntu.com/p/cbFPZMzHzr/")

The system boots with the same error mentioned above.

Any help or suggestions would be appreciated.

---

### Post by oldfred on 2021-03-14
You are missing the e in paste, so link does not work unless you manually add it.

You show Windows hibernated. You need that off for updates to work to dual boot or access NTFS partitions.

Your installs & configurations are very confused.
Your system is UEFI and has Windows installed in UEFI boot mode which required gpt partitioning.
You show sdb as MBR(msdos) and have grub installed in the MBR for BIOS boot. 
You also have grub installed to the PBR - partition boot record/sector which grub does not recommend and if that is the updated version, will not boot.
If you change system to boot in BIOS/Legacy/CSM boot mode, can you boot sdb?

You cannot dual boot from grub if one install is UEFI and one is BIOS.
Since two drives, you may be able to get it to boot, but have to change UEFI to BIOS or vice-versa. Many systems now do boot, but you have to select from UEFI boot menu every time.

Your install in sdb is LVM with encryption.
I do not know encryption, but everyone highly recommends really good backups as if issues with encryption, you often have to reinstall & restore from backup.

---

### Post by tea for one on 2021-03-15
> **Don_Phillips said:**
> Any help or suggestions would be appreciated.

Dual boot Windows and Ubuntu with mixed mode installations is fraught with difficulty
Line [COLOR="#0000FF"]196 -197[/COLOR] of the report is the clue

Your best choice is to backup your Ubuntu data and re-install in UEFI mode with GPT.

Windows 10  and Ubuntu on separate disks is ideal for the future but there are some details to consider.

Before any more progress, can you confirm that you can still boot into Windows 10 successfully?

---

