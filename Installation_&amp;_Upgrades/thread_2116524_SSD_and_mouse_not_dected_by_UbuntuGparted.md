---
title: "SSD and mouse not dected by Ubuntu/Gparted"
date: 2013-02-16
forum: Installation &amp; Upgrades
---

### Post by ULAMSS5 on 2013-02-16
I'm trying to install Ubuntu onto my SSD, which was pre-partitioned with a 20gb for future(now) Ubuntu installation. 

However now, neither Gparted nor Ubuntu installer can detect the SSD at all. It is a Crucial M4 256GB SSD.

My mouse also doesn't work in Gparted/Ubuntu. It is a Dare-U Compass. Don't even know how I can navigate to the terminal.

Thanks for any help!

---

### Post by dino99 on 2013-02-16
you need to isolate the different issues:

- is the bios find that ssd ?
- is the mouse issue exist without the ssd plugged ?

how has been formatted that ssd ? with which tool ?  have you read its doc ?

---

### Post by ULAMSS5 on 2013-02-16
Hi, thanks for the reply.

The bios detects the SSD no problem. It is the boot drive + installation drive of Windows. In Windows Explorer, I can still see the 20gb that I partitioned out, mounted as Drive D.

Yes, and the mouse issue seems to be independent of the SSD issue.

The SSD was first formatted with Windows 7's built-in installer's repartitioner. It is in NTFS, but that shouldn't stop GParted from detecting it entirely.

---

### Post by oldfred on 2013-02-16
Gparted will not see RAID, Windows proprietary dynamic partitions, and often NTFS that needs chkdsk or is hibernatied.

If you create more than 4 partitions with Windows it may convert to dynamic.

Post this from terminal in liveCD:
sudo parted -l

Is mouse wireless or bluetooth?
 If just USB have your turned on USB keyboard & mouse settings in BIOS? Windows & Ubuntu often use own drivers but grub does not.

---

### Post by ULAMSS5 on 2013-02-17
Hi oldfred, thanks for the reply!

I suspect it may be RAID, but I cannot figure out how to navigate to the terminal without a mouse.

The mouse is wired, USB connection. The mouse and kb works in my Bios(MSI Z77-GD65 Click bios II), but mouse stops working once I boot into linux-based operating systems/live  CDs.

---

### Post by oldfred on 2013-02-17
In your BIOS should be a USB setting to enable mouse & keyboard. Otherwise it uses ps/2 ports.

---

