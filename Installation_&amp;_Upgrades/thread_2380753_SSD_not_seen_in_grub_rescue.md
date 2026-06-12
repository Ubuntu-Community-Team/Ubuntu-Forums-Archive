---
title: "SSD not seen in grub rescue"
date: 2017-12-21
forum: Installation &amp; Upgrades
---

### Post by mistuh-gainz on 2017-12-21
I have a new 60Gb SSD along with my old 280Gb HDD. I'm using a HP dv7-1133cl.  I've successfully installed ubuntu 16.04 on the new drive 3 different times with a usb .iso (trying both manual partitions and automatic), but no matter what I do, my machine won't read the new SSD. 

I know the OS is on the SSD, because the old HDD still had Ubuntu and it "sees" everything on the SSD as a removable drive (even though they're both internal drives). But after wiping the HDD and with both drives installed, I end up at grub rescue and it only lists the HDD as (hd0). No other partitions are found and grub does not list the SSD at all. 

If the HDD is taken out of the computer, I don't even get to grub rescue, the laptop just says, "No bootable device -- insert boot disk and press any key"

Maybe I shouldn't have wiped the old drive, but nothing important was on the HDD, so I could do a fresh install on just the old drive if I need to. But why is this happening and how can I get the SSD to work?

---

### Post by oldfred on 2017-12-21
May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Are you installing in UEFI or BIOS boot mode?
Looks like older UEFI, so have you updated UEFI?
And many have had to update firmware on SSDs to have them work or work well.

Boot-Repair now does copy, if UEFI boot.

 HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

---

