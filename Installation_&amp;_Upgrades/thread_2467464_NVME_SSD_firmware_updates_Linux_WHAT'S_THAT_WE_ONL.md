---
title: "NVME SSD firmware updates: Linux? WHAT'S THAT? WE ONLEE HAV 4 WINDOZE"
date: 2021-09-27
forum: Installation &amp; Upgrades
---

### Post by watchpocket on 2021-09-27
I've got two new 1TB Sabrent Rocket 4 Plus nvme drives installed on a new desktop workstation computer that I've just finished building.

I was about to install my OS of choice (Ubuntu-MATE) on one of them when I saw that Sabrent has a firmware upgrade for that drive available.  

***Available, that is, as a Windows driver only.* ** 

My drives have fw v1.1 on them.  Version 1.2 is now available for download from Sabrent.  One reviewer said the update increased his drive's speed dramatically.

The plan was to update the firmware using the nvme-cli command line suite of tools, but there's no driver (or image file) available for Linux.  I called their tech support to see if there might be any way they would make the actual firmware image available.  You can guess what they told me.

My question here, then (perhaps a bit of a longshot), is:  

*Is there any way one can . . .** extract*** *the actual firmware image from the files that appear after opening the windows zip file and then opening the dot-exe windows executable?  * 

If there was some way to isolate or extract a functioning firmware image, one could then use the nvme fw-commit command etc to do the update.  

My guess is that this is a bust, but thought I'd ask around to make sure.

(I do have a windows laptop lent to me by a friend, but using it for the update would mean yanking out the drive from my box and opening up his laptop to install it there -- if the laptop even has an M.2 port inside it, which it may well not.)

(I've actually got the same problem with a DAC from the RME company -- firmware drivers for Windows only.  At least in this case I can just plug the DAC into the Windows laptop and do the update from there.  *But what is with the makers of these products?!  They really believe that in the year 2021 there is only ONE computer platform in the world!*)

---

### Post by oldfred on 2021-09-27
I have a Samsung NVMe drive and it offered a downloadable ISO to boot & install update. ISO was just for my model SSD and just the one update. But it worked without issue.

I saw this, not sure if it can be used for others or not:
HP UEFI update - extract .bin from .exe file and copy into FAT32 partition.
[https://askubuntu.com/questions/539120/how-to-perform-a-hp-bios-upgrade-with-only-ubuntu/1234098#1234098](https://askubuntu.com/questions/539120/how-to-perform-a-hp-bios-upgrade-with-only-ubuntu/1234098#1234098) & 
[https://h30434.www3.hp.com/t5/Notebooks-Archive-Read-Only/How-to-update-BIOS-on-Linux/m-p/5441775#M1205498](https://h30434.www3.hp.com/t5/Notebooks-Archive-Read-Only/How-to-update-BIOS-on-Linux/m-p/5441775#M1205498)

Some UEFI/BIOS in the past offered to download a DOS bootable image, so you could run the .exe file.
Not sure then if you can create your own DOS bootable flash drive. That would not be UEFI, but may work in BIOS mode?
Some very new computers are now UEFI only, with no CSM/Legacy/BIOS mode.

Vendors that at least indirectly support Linux offer firmware updates. A few have NVMe drives on list. Did not see Sabrent on list.
Devices using LVFS for firmware updates
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)

---

### Post by watchpocket on 2021-09-27
Thanks loads.  I think the way to go for this is to get an nvme-drive enclosure, pull the nvme drive out of my box, put it in the enclosure, plug it into a Windows laptop and use the windows update-utility tool to update the drive's firmware to the new version 1.2, and then re-install in my box.  A bit of a pain, but the simplest way to do it, I think, given no Linux driver.

---

### Post by GhX6GZMB on 2021-09-27
> "One reviewer said the update increased his drive's speed dramatically."

:lolflag:

---

### Post by watchpocket on 2021-09-27
> "LOL"

So this speed increase with a fw update is unlikely?    (Maybe it's the "dramatically" part that's unlikely.)

---

### Post by rbmorse on 2021-09-27
Not all nvme devices can be updated while installed in an external enclosure...USB interfaces can be especially problematic. 

This is the main (but not only) reason I only buy Samsung SSDs. They provide an operating system independent means of updating firmware for their devices.

---

### Post by watchpocket on 2021-09-27
The way I see it there's no harm in trying.  It's my only recourse anyway unless I want to toss my 2 new Sabrent drives and buy Samsungs.

---

