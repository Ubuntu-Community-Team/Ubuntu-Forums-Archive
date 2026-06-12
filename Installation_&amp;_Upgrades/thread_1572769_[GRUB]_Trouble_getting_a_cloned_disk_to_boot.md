---
title: "[GRUB] Trouble getting a cloned disk to boot"
date: 2010-09-11
forum: Installation &amp; Upgrades
---

### Post by pspkiller91 on 2010-09-11
I'm having trouble getting an installation of Ubuntu 10.04 to boot. Originally I had it installed on a 2.5" 60GB SATA drive but due to the need for this drive elsewhere I replaced it with an 3.5" 80GB model. Also the fact that I was using a 2.5" drive in a desktop meant that it couldn't be properly attached to the chassis as well as the obvious performance issues.

So, I decided to do a bit for bit clone of the 60GB drive onto the new 80GB drive. Obviously it didn't work. 

The UUID of the new drive is different to that of the old drive meaning GRUB didn't know what to boot from. Fine. Stick the old drive back in with the new drive, boot up from the old drive, use blkid to get the UUID of the new drive, reboot holding shift to get to the GRUB menu and edit the boot commands to the new UUID. Sounds simple.

Except that didn't work either. GRUB editor doesn't save my changes when I hit ESC to exit or CTRL+X to boot. 

Does anyone know a solution to my problem?

---

### Post by presence1960 on 2010-09-11
> **pspkiller91 said:**
> I'm having trouble getting an installation of Ubuntu 10.04 to boot. Originally I had it installed on a 2.5" 60GB SATA drive but due to the need for this drive elsewhere I replaced it with an 3.5" 80GB model. Also the fact that I was using a 2.5" drive in a desktop meant that it couldn't be properly attached to the chassis as well as the obvious performance issues.

So, I decided to do a bit for bit clone of the 60GB drive onto the new 80GB drive. Obviously it didn't work. 

The UUID of the new drive is different to that of the old drive meaning GRUB didn't know what to boot from. Fine. Stick the old drive back in with the new drive, boot up from the old drive, use blkid to get the UUID of the new drive, reboot holding shift to get to the GRUB menu and edit the boot commands to the new UUID. Sounds simple.

Except that didn't work either. GRUB editor doesn't save my changes when I hit ESC to exit or CTRL+X to boot. 

Does anyone know a solution to my problem?

Boot off the Live CD/USB. Go to the desktop. Open a File browser (Places > Computer). Mount your partition that has ubuntu installed on the cloned drive by highlighting the partition on the left pane of the file browser.

Next open a terminal and run ```
gksu nautilus
``` You will now have nautilus as root user. In the left pane of the root nautilus window navigate to your cloned ubuntu partition, then go to /etc/fstab

Open the fstab file and edit your UUIDs to what they are on the cloned partition. Be careful- you are now root.

When UUIDs are changed click Save on the top tool bar & close the file. Reboot without the Live CD.

Make sure you edit all UUIDs in fstab including swap if you have a swap partition.

---

