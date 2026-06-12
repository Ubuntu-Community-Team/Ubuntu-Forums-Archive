---
title: "darned!!  Install almost worked - help please"
date: 2017-02-18
forum: Installation &amp; Upgrades
---

### Post by mangurian2 on 2017-02-18
I booted from the latest dvd and selected INSTALL.
I had an external HD with two partitions (1.8T and 100Gig)
I selectedthe option to also install 3rd party items (mp3 etc).
When the part about where to install came up I chose the 100G and got a msg something like "no boot sector"?
I formatted the 100G partition as ext3 and set /boot.
I then chose the 1.8T partition (NTFS) for swap.

Off it went - chose location, chose English
The machine went chugging along happily for a while.

I went back to the computer and there was a msg saying either the DVD or the HDD was bad.

Could it be something else?  How about my options?  Is ext3 correct?  Is selecting /boot on the 100Gig right/ok ?  Can the swap be NTFS ?
I am installing from an old laptop with small amount of RAM - could that be the problem ???

 Thanks
I really want Ubuntu.

---

### Post by oldfred on 2017-02-18
You need to understand parititons.
/boot is not normally required with most desktops.
And swap is for RAM overflow if you do not have enough RAM to run a process. It must be unformatted. It is not a shared NTFS data partition.
        MBR or gpt partitions:
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) 
    
Default install is / (root) & swap. And / is normally formatted to ext4.
Some then may also want /home as a separate partition or other data partitions like your shared NTFS data partition. But you cannot create NTFS during install, just leave space or partition in advance.
If installing to a second drive, you need to use Something Else, so you have to option at the bottom of the partitioning screen to install the grub2 boot loader to the second drive. Otherwise it defaults to sda or internal drive.

       Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)

---

### Post by mangurian2 on 2017-02-18
Excellent explanation of what to do.   Thank You

---

