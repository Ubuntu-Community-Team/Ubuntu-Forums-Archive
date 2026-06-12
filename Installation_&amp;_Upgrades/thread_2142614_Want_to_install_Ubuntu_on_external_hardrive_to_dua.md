---
title: "Want to install Ubuntu on external hardrive to dual boot windows 7 and linux"
date: 2013-05-06
forum: Installation &amp; Upgrades
---

### Post by blainej1 on 2013-05-06
I ran into some problems after trying to install linux with a live usb. After I tried to boot I would get a grub rescue error. I have tried to use boot repair 3 times now and nothing seems to work. Here is the url for my boot repair log: [http://paste.ubuntu.com/5638262/](http://paste.ubuntu.com/5638262/)

What are my best options for getting my Linux and Windows dual boot running. 

Note: the external hdd with linux also has documents and games, so I cant format it just for linux.

Need help as soon as possible please, my brain hurts

---

### Post by oldfred on 2013-05-06
First, is BIOS set to AHCI not IDE? You also may need Windows drivers first if you are not now in AHCI mode.

But with some BIOS and on USB drives, some systems will not boot from a partition with boot files beyond about 100GB on the external drive. Not sure if BIOS, USB driver or grub issue.

Only work around we have found is to have boot files in a / (root) partition fully inside the first 100GB or a separate /boot partition inside the first 100GB. If it still does not boot after changing BIOS you will have to move Windows NTFS to make a 200 to 500MB /boot partition totally inside the first 100GB. Best to use Windows tools to resize the NTFS partition and then run chkdsk on it. 
While you can move a boot files from the /boot folder to a /boot partition, edit fstab and reinstall grub, it probalby is just easier to reinstall. Use manual install - Something Else and chose new /boot partition and existing / (root) to reinstall.

---

### Post by blainej1 on 2013-05-06
I checked by BIOS and AHCI was set to auto, is set it to manual and its always enabled now. Tried rebooting to my external hard drive with no luck. It tells me to insert a bootable device so its not even being recognized any more. If I boot from the internal hard drive, I get a windows boot failure, no more grub rescue at all. It seems a little concerning.

What should be my next steps. The only way I can access my computer now is through the liveusb I have of Ubuntu 12.04 LTS. Is there a simple solution by using the liveusb?

---

### Post by oldfred on 2013-05-06
Then you did not have the AHCI drivers in Windows, change BIOS back and then in Windows install AHCI drivers. 

But I think the only way to get Ubuntu to boot is with the small /boot partition within the first 100GB of external drive.

---

