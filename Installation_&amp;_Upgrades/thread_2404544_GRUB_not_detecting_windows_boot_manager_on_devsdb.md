---
title: "GRUB not detecting windows boot manager on /dev/sdb"
date: 2018-10-25
forum: Installation &amp; Upgrades
---

### Post by michalmdc on 2018-10-25
[http://paste.ubuntu.com/p/hv5FNp6DX9/](http://paste.ubuntu.com/p/hv5FNp6DX9/)

After Windows 10 crash i restarted my laptop and grub boot menu shown, but this time without windows boot manager, or any other partition on ssd disc. I tried boot-repair, os-probe, changing settings in uefi, even manually adding win 10 to /etc/grub.d/40_custom, but nothing improved. I have dual boot with Win 10 on ssd and ubuntu on hdd drive, but fdisc -l is not detecting anything except sda partitions. I cannot choose any other options than "grub' after clicking F12 while system starts. Also my laptop is acer, but i don't know if it is really important.

---

### Post by yancek on 2018-10-25
You have an EFI install of Ubuntu on the larger (465GB) drive which also has one windows partition.  Is that the drive you had windows on or was it on the other drive?  There should be windows boot files in the EFI partition and there are none so it won't boot and you can't fix that from Ubuntu/Linux.  Do you have a windows install/repair DVD?  You need to somehow get the windows EFI files on the system.

---

### Post by michalmdc on 2018-10-25
On this drive(hdd) i have Ubuntu and Windows user files, the Windows OS is on ssd drive, which is not detected. I don't have windows repair dvd, but I got Win key, so i think that i can use windows repair from pendrive or something. Repair is last thing i can do, because I'm afraid of losing files, so firstly I'm trying to repair it from Ubuntu.

---

### Post by oldfred on 2018-10-25
Grub only boots working Windows.
So if Windows crashed you have to use your Windows repair disk and Windows tools to fix it.
Only a few minor Windows fixes can be done from Linux.

But if drive is not now shown, that is more of a major issue. Could be just drive corruption or complete drive failure. 
In Ubuntu Disks application and icon in upper right corner is Smart Status. Is your SSD shown there and what is its status?

---

### Post by michalmdc on 2018-10-25
Well everything tell me that my ssd disc is OK and with not detected  data, but after running Smart Test it returned me some error, I'm  including it in printscreen. I don't know if i done it right with this attachments tool. I also including prtsc from fdisk.

---

### Post by oldfred on 2018-10-25
Its sdb, the SSD that seems to have issues. 
Cannot translate Smart Status output.

Does this tell anything about SSD, if sdb?
sudo gdisk -l /dev/sdb

---

### Post by michalmdc on 2018-10-26
Seems that gdisc and Ubuntu Discs Tool are detecting it as OK, but empty. I'm attaching screen shot.

---

### Post by oldfred on 2018-10-26
Does testdisk find old partitions. 
Not sure with SSD what info may still be there. With trim, most old data is trimmed out, so only current data still on drive.

       Testdisk Instructions, new versions use sectors, old ones were CHS
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by michalmdc on 2018-10-28
It didn't detected any partition on ssd, and i did few other things and tests and it seems that disc is damaged, last thing i will try is to use windows repair, then i'm going to go to service with laptop. So thanks for help and i don't know if I should change thread to 'solved'?

---

