---
title: "[SOLVED] I/O error from Live CD"
date: 2007-11-21
forum: Installation &amp; Upgrades
---

### Post by ali.gilani on 2007-11-21
i got a LiveCD of Ubuntu and started using it on my Dell Laptop, which already had XP installed on it. I decided after about three days to finally install it permanently. I clicked on the install icon and the process started. I chose to allocate 30% of my single 80 Gb harddrive of which 30Gb has been used already up by XP. The partition process however failed and i had to reboot. 

However, now when i put in the CD and boot from it, i get the ubuntu menu, but upon pressing Enter to Run Ubuntu, the text  I/O error pops up, and i must reboot the system. How do i get ubuntu to work?

Thanks

---

### Post by Pumalite on 2007-11-21
Use you XP CD to fix MBR frirst. Recovery>FIXMBR>FIXBOOT. Then get Gparted Live CD and resize XP partition. Format the new partition ext3 if you want. Then install Ubuntu to this new partition.

---

### Post by ali.gilani on 2007-11-21
i do not have the XP CD. i got the system preloaded with XP from Dell. What is MBR and how do i get it fixed?

---

### Post by Pumalite on 2007-11-21
Use Super Grub then. It can fix MBR of Windows.
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
It can do a whole lot more. Read the instructions.

---

### Post by ali.gilani on 2007-11-22
i fixed the mbr with super grub, and then used Gparted to create a 13Gb ext3 partition  from my original 80 Gb partition. I ran the install from the Live CD and used the first guided option and told it to take 100% of the 12.73 Gb. Then the install started, When i came back 5 hours later, i just saw the ubuntu desktop but on the top it said Live Use Session. 

I figured that it wanted me to restart, I did and after the Bios check the screen went blank, i used super grub to get to windows again and my computer confirmed that the partitioning had taken place as the HDD was shown as 57.54 Gb.

I rebooted with Gparted and it gave me these details"

FAT      hda1    43mb(total)   238Kb(used)
NTFS    hda2    57.54 Gb      27GB
ext3     hda4   12.73 Gb       369 mb
           
            hda3           4.21Gb          ------     [
     hda6 ext3          2Gb           2Gb
 hda7  linux-swap    164.7Mb      ----
      hda5  fat32        2.01 Gb   4 Mb

I then tried supergrub to get to load linux but no avail and i had to use it again to get Xp working. SO i decided just to install Ubuntu again. However this time when i run the install option and use the first guided option choosing 100% it only shows taking up 10.23 Gb? wheres the rest? how do i finally get it done?

---

### Post by Pumalite on 2007-11-22
Clean the partition first with Gparted, format it ext3 if you want, then install Ubuntu and go Manual:
10 GB for '/'
2x RAM up to 1 GB for /swap
The rest for /home.

---

### Post by ali.gilani on 2007-11-22
i formatted the partition again, chose manual, clicked on the 12Gb partition, on the box that popped up, i selected new size 10Gb and '/' as system. I clicked ok and a message came on screen: warning windows might not like the drive settings.

Can you provide step-by-step instructions please?

---

### Post by ali.gilani on 2007-11-23
GOT IT! ubuntu is up and running, now how do i get wireless working? 

clicking on the network manager doesnt give the option to detect wireless?

---

### Post by Pumalite on 2007-11-23
Congrats! Mark this as Solved and start a new thread.

---

