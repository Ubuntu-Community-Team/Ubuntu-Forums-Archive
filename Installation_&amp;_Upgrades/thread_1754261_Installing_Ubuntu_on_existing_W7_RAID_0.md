---
title: "Installing Ubuntu on existing W7 RAID 0"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by khardbored on 2011-05-09
I have an existing W7 install on two 500g drives in RAID 0 and would like to, if at all possible, install Linux and dual-boot W7 and Ubuntu with no data loss on the current raid.

From what I have read this is next to impossible if not extremely difficult and involved.

This would be the latest version of Ubuntu and it's already on a 4GB flash drive ready for install.

Any tips, thoughts, links, howtos would be greatly appreciated!

Thank you so much!

---

### Post by collisionystm on 2011-05-09
> **khardbored said:**
> I have an existing W7 install on two 500g drives in RAID 0 and would like to, if at all possible, install Linux and dual-boot W7 and Ubuntu with no data loss on the current raid.

From what I have read this is next to impossible if not extremely difficult and involved.

This would be the latest version of Ubuntu and it's already on a 4GB flash drive ready for install.

Any tips, thoughts, links, howtos would be greatly appreciated!

Thank you so much!

Aren't you just a wee bit scared running raid 0? If one drive fails you lose it all. 

I don't think installing side by side should even present itself as an issue. The raid is handled at the hardware level. As far as ubuntu is concerned, or windows for that matter, its just a 1tb drive. Ubuntu will recognize the raid config, but I can't see how it will cause an issue. Best thing to do is.... give it a try! That's the fun part of computers....breaking them =)

---

### Post by khardbored on 2011-05-09
> **collisionystm said:**
> Aren't you just a wee bit scared running raid 0? If one drive fails you lose it all. 

I don't think installing side by side should even present itself as an issue. The raid is handled at the hardware level. As far as ubuntu is concerned, or windows for that matter, its just a 1tb drive. Ubuntu will recognize the raid config, but I can't see how it will cause an issue. Best thing to do is.... give it a try! That's the fun part of computers....breaking them =)

Well, when I boot up from the flash drive it presents the option to install along side W7 but only shows my external USB HD. It doesn't show the raid array. Also, when I go back and choose the "do something else" installation option it does show my raid as raid-name1 and raid-name2...maybe I am missing something here...lol.

And I am not too worried about losing anything as I tend to backup onto my external HD often and am buying a second, 1TB external for redundancy.

---

### Post by collisionystm on 2011-05-09
Hmmm....

Its probably the raid filesystem. If you run the live cd and go to disk utility, you will see its not marked as a normal filesystem. Maybe try doing a search for installing ubuntu nameoffilesystem on google? Im not to good with formatting drives in linux. I couldn't get 10.04 to install on a 4tb raid10. I had to use server 10.04 to do it because desktop did the same thing yours does lol. You could try the desktop alternative cd and see if it presents a side by side option.....I figure its worth a shot

---

### Post by khardbored on 2011-05-09
Odd.
I disconnected my external drive and fired up the installation again. This time it did not even give me the option to install side by side with W7. The only options were destroy the W7 installation and other options. Other options shows my raid array, one is simply the name of the array and then two more, one for each drive in the array.

I would really like to have both installed but it's not looking too feasible at the moment.

---

### Post by Quackers on 2011-05-09
The only way I got 11.04 to install properly with a Bios-raid setup (Intel) was to boot the live cd/usb and select "try ubuntu". From the loaded live desktop, if you run gparted you will see that the raid array is not "seen" by 11.04 (it would be with 10.10). I was advised (correctly) to install kpartx at this stage and I did (with synaptic). After that gparted did recognise the raid array - and so will the installer. Make a note of the raid set's name (dev/mapper/ whatever)

The installer though, may not be able to format the partitions created (mine wouldn't) so the ext4 partition(s) and swap space need to be created before commencing installation.
Then at the partitioning stage select the 3rd or 4th item (can't remember which) called "something else" which is like the older manual partitioning part.
Select the partiton(s) you have created and use the proper mount points ( "/" for root and /home for home) BUT DO NOT  check the box for formatting them! Leave that box empty or it will fail. You will get a pop-up saying that the boxes are not going to be formatted - just accept that.
When the partitions are sorted out, at the bottom of the partitioning page there is a long field entitled "device for bootloader installation" which will default to /dev/sda - you need to change this to your raid0 hard drive. It will be listed in the drop-down box (something like /dev/mapper/isw_bfcjfheyegu or /dev/mapper/nvidia something).
You need to choose the drive NOT a partition on the raid setup (no number at the end)
Good luck :-)

ADDED  For some reason the installation also had problems if the boxes for updating during installation and the 3rd party addon boxes were ticked. When unticked the installation ran perfectly.

---

### Post by CyberNerdz on 2011-05-09
I have a RAID 0 (4 striped drives) running Windows 7 Ultimate 64. Aparrently WUBI does not support RAID arrays. I did attempt to install it still but I got the "Can not define Root Path.." error which brought me to this Wiki mentioning the none-RAID support:

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
> Although installing Wubi to RAID is not officially supported there have  been reports of users who have done so successfully. This has not been  thoroughly tested and users who experience problems with installing to  RAID should address their concerns on the Ubuntu Forums. Additionally,  users who have computers with software RAID metadata, where the RAID has  not enabled, may need to delete the RAID metadata before installing  Wubi. 

Here is my drive configuration:

C: OS Drive (SATA-RAID 0 / 160GBx4)
D: Data/Program  Drive (Single SATA 1.5 TB drive)
E: Back-up drive (Single SATA 3TB drive)

Regardless which drive I try to install Ubuntu (10.10 or 11.04), I still get the root path error. I think it has something to do with the Windows 7 MBR on a RAID arrays. It should work if your OS or MBR was not on your RAID array.

---

