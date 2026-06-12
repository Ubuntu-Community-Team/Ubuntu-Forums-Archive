---
title: "Deleting Windows and moving Ubuntu installation into its partition."
date: 2011-09-23
forum: Installation &amp; Upgrades
---

### Post by Rebelli0us on 2011-09-23
I want to move my existing Ubuntu to another partition on the same disk and get rid of Windows. Image below shows my setup.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=202783&stc=1&d=1316794543[/IMG]

Proposed steps:
1-- Boot desktop CD, start GParted  and format dev/sdb1 to ext4.
2-- Copy everything from dev/sdb5 to dev/sdb1  (**don’t know how**).
3-- Update grub to boot  dev/sdb1 as well (**don’t know how**).
4-- Boot to verify that Ubuntu on dev/sdb1 runs OK.
5-- Boot desktop CD again , delete dev/sdb5 and sdb6 and append all but 4GB of freed space to dev/sdb1 by resizing dev/sdb1 in GParted. The resulting dev/sdb1 will be 294GB. Create swap partition (named sdb5 or 6?), though swap partition is wasted space since it’s never used. Is it OK to merge swap sdb6 into sdb1 as well? Will Ubuntu in sdb1 know where its new Swap partition is?? Probably not!

The final result, Ubuntu will be the only OS in primary partition sdb1 and Windows will be gone! Did I get it right? Is there a simpler way to move my installation?

---

### Post by coffeecat on 2011-09-23
Yes it is possible, but there are complications. You would need to do everything from the live CD, and you would need to attend to partition UUIDs, reinstall grub, and edit /etc/fstab for the new UUID of your re-created swap partition. That's the outline, but the details would take longer to explain. Also, when you get to resizing your new sdb1, things will probably go OK, but there is always the potential for catastrophe when manipulating partitions. Backups are essential. 

I have a simpler suggestion:

Leave your Ubuntu installation as it is.
Reformat your sdb1 to ext4 to be used as a data partition.
Edit /etc/fstab so that it is mounted on bootup.
Run chown and chmod commands on the mounted sdb1 partition so that you don't run into permissions problems when you try to write to it.
Create symlinks from folders in sdb1 to your home folder for convenience (optional).

If you want help with any of that, post back.

---

### Post by Rebelli0us on 2011-09-23
> **coffeecat said:**
> Yes it is possible, but there are complications. You would need to do everything from the live CD, and you would need to attend to partition UUIDs, reinstall grub, and edit /etc/fstab for the new UUID of your re-created swap partition. That's the outline, but the details would take longer to explain. Also, when you get to resizing your new sdb1, things will probably go OK, but there is always the potential for catastrophe when manipulating partitions. Backups are essential. 

I have a simpler suggestion:

Leave your Ubuntu installation as it is.
Reformat your sdb1 to ext4 to be used as a data partition.
Edit /etc/fstab so that it is mounted on bootup.
Run chown and chmod commands on the mounted sdb1 partition so that you don't run into permissions problems when you try to write to it.
Create symlinks from folders in sdb1 to your home folder for convenience (optional).

If you want help with any of that, post back.

Thank you, that’s a good idea, sdb1 is already a shared data partition since Linux can use NTFS and Windows can’t read ext4. 

Until this year, all my Linux installations self-destructed within a few weeks or months. Ubuntu 10.10 has NOT self-destructed, so I think I'll take your advice and leave the partitions alone, since I don't even know what &#65279;chown and chmod are. :)

---

### Post by coffeecat on 2011-09-23
Excellent! I'd assumed your sdb1 was a Windows partition - I hadn't looked at the label closely enough - and some machines designate a single hard drive as sdb, so it could have been that was your only drive. You have Windows on sda then. That's good because it's not a good idea to have a NTFS data partition if you don't have access to Windows. You need Windows's chkdsk in case of filesystem corruption.

So - not much to do then! :)

---

### Post by Rebelli0us on 2011-09-25
> **coffeecat said:**
> Excellent! I'd assumed your sdb1 was a Windows partition - I hadn't looked at the label closely enough - and some machines designate a single hard drive as sdb, so it could have been that was your only drive. **You have Windows on sda then.** That's good because it's not a good idea to have a NTFS data partition if you don't have access to Windows. You need Windows's chkdsk in case of filesystem corruption.

So - not much to do then! :)

Yes &#65279;Windows is on sda1, and sdb1 is a bootable copy of sda1.

Windows is a 20-year habit that’s hard to break, but I need Windows to run Windows apps (including my own). Running Windows in VM VirtualBox beats dual-booting, so I want to slowly get rid of Windows partitions entirely. Hows that for a plan?

---

