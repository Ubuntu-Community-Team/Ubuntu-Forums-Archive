---
title: "Inaccessible Boot Device"
date: 2017-12-02
forum: Installation &amp; Upgrades
---

### Post by HDTimeshifter on 2017-12-02
I restarted to boot to my Windows 7 drive and the GRUB came up with a Windows 10 loader in place of the old Windows 7 loader. I had not upgraded to Windows 10, so this was unusual. I selected the Windows 10 loader (on /dev/sdb1), and the Windows 10 logo and circle started swirling. A screen then came up with "Inaccessible Boot Device" error. The computer then rebooted with the same result.

How do I get the GRUB back with the Windows 7 loader so that I can boot to Windows (7)?

---

### Post by yancek on 2017-12-02
Where does Grub fit into this as you only mention windows 7 and windows 10, neither of which has anything to do with Ubuntu/Linux.  Do you have Ubuntu installed and if so, which version.

I you have not upgraded to windows 10, that would be very surprising behavior.  There isnt enough information in your post for anyone to actually give any useful advice so I would suggest that if you have an Ubuntu install or Live DVD/flash drive, you go to the site below and get the boot repair software.  Once downloaded, you can run it by selecting the Creat BootInfo Summary option and do NOT try to make any repairs.  It will give you a link you can post here. 

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by HDTimeshifter on 2017-12-05
I have Ubuntu 16.04 LTS installed as listed in my profile here.

I figured I could boot directly to my Windows drive by selecting it in the BIOS, but it no longer show up in the Boot Drive Priority list. However, it does show up in the Hard Drives list as well as the AHCI Settings SATA port. The strange thing is I am able to see the drive in the Files window and copy files from my Ubuntu drive to it.

I booted form my Ubuntu 16.04 LTS DVD and installed and ran boot-repair with default settings and the paste file is at [http://paste.ubuntu.com/26116749]("http://paste.ubuntu.com/26116749")
I rebooted, but the Windows drive is still missing from the Boot Drive Priority list, so I ran boot-repair again, this time selecting advanced options and repaired the MBR on sdb1 (the Windows drive) and the past file is at [http://paste.ubuntu.com/26116799]("http://paste.ubuntu.com/26116799") After rebooting, it still doesn't show up in the Boot Drive Priority list and when I tried selecting the Windows 10 loader, Windows 10 runs "Preparing Automatic Repair", then "Diagnosing your PC", but does not boot.

---

### Post by HDTimeshifter on 2017-12-07
I was able to move around the drives in the BIOS drives list so that the Windows drive shows up as the first drive and was then able to select it so that it boots to it first, but it still won't boot to Windows.

---

