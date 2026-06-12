---
title: "dual os"
date: 2012-01-16
forum: Installation &amp; Upgrades
---

### Post by vishalnshekhar on 2012-01-16
can i have dual boot with window 7 and ubuntu studio 11.04

---

### Post by goofey24 on 2012-01-16
I don't see any reason why not.:P

29 Beans to go so I can edit my 'profile':(:(

---

### Post by arpanaut on 2012-01-16
This should be helpful: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Pay close attention to the back-up recommendations.
With win7 if is preferable to do your partition resizing from windows disk management.

You can get your iso here: [http://ubuntustudio.org/NattyNarwhal](http://ubuntustudio.org/NattyNarwhal)

good luck

---

### Post by JoseeAntonioR on 2012-01-16
Of course you can. You should follow the instructions given in post #3. But, I recommend 11.10, as it is the latest version. You can find it here: [http://ubuntustudio.org/downloads](http://ubuntustudio.org/downloads)

---

### Post by Mark Phelps on 2012-01-16
If you're going to dual-boot, and you're currently running Win7 on your PC, then you need to do the following: Confirm that you don't already have the 4 Primary partition limit.  To do this, open the Win7 Disk Management utility and count the number of "drives" (that's what Windows calls partitions).  If you already have 4, then you're going to be faced with a LOT of work because you will have to remove one before you can create another for Ubuntu.

Also, check the "drive" types and confirm they are NOT Dynamic Disks.  Ubuntu can't be installed when Dynamic Disks are being used.

If you decide to go ahead with dual-boot, then do the following:
1) Use only the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. Do NOT use the Ubuntu installer to do this. If you already have 4 partitions in Win7, do NOT allow the partitioner to create another partition.  This will convert your partitions into Dynamic Disks -- effectively preventing the installation of Ubuntu and causing you further problems.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

---

### Post by vishalnshekhar on 2012-01-17
can you tell me which is better option Ubuntu or Ubuntu studio .
also in April Ubuntu release it's LTS version 12.04. now if i have Ubuntu 11.04 can i upgrade it to Ubuntu 12.04 LTS. because i do not want to Upgrade it to 11.10 because it does not work in proxy.

---

### Post by nipunshakya on 2012-01-17
> **vishalnshekhar said:**
> can you tell me which is better option Ubuntu or Ubuntu studio .
also in April Ubuntu release it's LTS version 12.04. now if i have Ubuntu 11.04 can i upgrade it to Ubuntu 12.04 LTS. because i do not want to Upgrade it to 11.10 because it does not work in proxy.

I recommend using ubuntu 11.04 first rather studio thing. If u are going for dual-boot, you can see the following link :
[http://members.iinet.net/~herman546/]("http://members.iinet.net/%7Eherman546/")

When i first used linux, i wanted dual-boot and followed the above suggestions. Hope it helps.Goodluck.

one more thing :  [B]After LTS releases, its better u make a clean install rather than upgrade from current version . 

[/B]Regards,WinuxUser

---

### Post by vishalnshekhar on 2012-01-17
> **WinuxUser said:**
> I recommend using ubuntu 11.04 first rather studio thing. If u are going for dual-boot, you can see the following link :
[http://members.iinet.net/~herman546/]("http://members.iinet.net/%7Eherman546/")

When i first used linux, i wanted dual-boot and followed the above suggestions. Hope it helps.Goodluck.

one more thing :  [B]After LTS releases, its better u make a clean install rather than upgrade from current version . 

[/B]Regards,WinuxUser
thanx
but please tell me how to remove the previous ubuntu for fresh installation
if i have a dual boot.

---

### Post by oldfred on 2012-01-17
If you have a partitioned install of Ubuntu (not wubi) then you just have to use manual install and reuse and reformat the existing / (root) and it will find & use swap. If you have /home, you tell it to use it but DO NOT format it.

If unsure of partitions from liveCD post this.

```
sudo fdisk -lu
```

You are not able to upgrade more than one version except you can go from LTS to next LTS. But that is usually such a large change that a clean install is often suggested. If you have lots of room on a hard drive you can install in another 20GB / (root) to test or use (if separate /home or /data).

---

### Post by nipunshakya on 2012-01-18
> **vishalnshekhar said:**
> thanx
but please tell me how to remove the previous ubuntu for fresh installation
if i have a dual boot.

Hi. you can either go with what guru **oldfred **regarding the issue. Or, to remove the previous ubuntu, simply use Disk Management from windows 7.

Just type disk management in the startup menu in win7 and run the utility.
There, you can see all the partitions your system currently has. Though you can see your windows partitions clearly and well labeled(as C: , D: ), you can just see partitions for linux without labels. Be careful while selecting your labels, and simply delete the volume/partition on which your linux was installed. 
This will make sure that windows partitions won't be deleted, as windows partitions won't act proper with gparted (its my personal experience). 

After you delete your partitions, you can simply create new partitions, format them to your wish or simply leave them unallocated.
Note: After you format, **please reboot**. Reboot ensures that your  new partitions are placed well and functional for windows 7 too. 
Then after a 2nd reboot, you can boot from LiveCD and then carry on  with your installations at the newly partitioned spaces.
I still remember that my first question to this forum was similar to yours, and i had coped up with that using the guide i suggested you and the above steps for partitions.
Goodluck.


Regards,WinuxUser:D

---

### Post by vishalnshekhar on 2012-01-18
> **WinuxUser said:**
> Hi. you can either go with what guru **oldfred **regarding the issue. Or, to remove the previous ubuntu, simply use Disk Management from windows 7.

Just type disk management in the startup menu in win7 and run the utility.
There, you can see all the partitions your system currently has. Though you can see your windows partitions clearly and well labeled(as C: , D: ), you can just see partitions for linux without labels. Be careful while selecting your labels, and simply delete the volume/partition on which your linux was installed. 
This will make sure that windows partitions won't be deleted, as windows partitions won't act proper with gparted (its my personal experience). 

After you delete your partitions, you can simply create new partitions, format them to your wish or simply leave them unallocated.
Note: After you format, **please reboot**. Reboot ensures that your  new partitions are placed well and functional for windows 7 too. 
Then after a 2nd reboot, you can boot from LiveCD and then carry on  with your installations at the newly partitioned spaces.
I still remember that my first question to this forum was similar to yours, and i had coped up with that using the guide i suggested you and the above steps for partitions.
Goodluck.


Regards,WinuxUser:D
and what about the grub.

---

### Post by nipunshakya on 2012-01-18
> **vishalnshekhar said:**
> and what about the grub.

..........Well, thats the main advantage of [FONT=verdana][SIZE=3][installing ubuntu after windows]("http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html")[/SIZE][/FONT]  (read the content in link well but ignore the use of gparted. use disk management as suggested above)
This is because u don't have to worry about repairing your grub and all if your machine has windows 7 already installed and then ubuntu.

When i first did dual-boot installation, i didn't have any problem to repair my grub and all. So basically, i would suggest you to first install windows, and then install ubuntu. That makes the bual-boot go in perfect harmony.

Goodluck
Regards,WinuxUser.:guitar:

---

### Post by oldfred on 2012-01-18
If systems are otherwise working, it is not too difficult to reinstall a boot loader. You do need to have current versions of liveCD or Windows repairCDs in the worst case of not booting at all.

And of course with any major system change good backups are important.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

But grub2's boot loader will boot Windows, so you can easily dual boot.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

