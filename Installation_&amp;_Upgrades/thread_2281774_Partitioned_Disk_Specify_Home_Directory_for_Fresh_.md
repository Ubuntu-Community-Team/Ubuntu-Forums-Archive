---
title: "Partitioned Disk: Specify Home Directory for Fresh Intall: Ubuntu Gnome 14.04.02"
date: 2015-06-09
forum: Installation &amp; Upgrades
---

### Post by webmanoffesto on 2015-06-09
I ran into serious problems with my previous Ubuntu installation. I'm now doing a fresh install (Ubuntu Gnome 14.04.02) on an already partitioned disk.   

I go to "Installation Type: Something Else" Then I see my partitioned disk. I know that: 
"/dev/sda5 ... ext4 ... 34999MB" will be the Ubuntu Gnome OS - Does that mean that it will be "Device for bootloader installation"?  
"/dev/sda2 ... swap ... 4099MB" will be the swap   
"/dev/sda3 ... ext4 ... 461006MB" is what I want to be my home directory.  This has all my data. It's backed up, but I still don't want to format it.

I think that I need to set 
"/dev/sda5" to be root "/" and 
"/dev/sda3" to be home "/home"  

How do I do that?
Gallery of screenshots: [http://imgur.com/a/ID7VZ](http://imgur.com/a/ID7VZ)
[INDENT]
[/INDENT]

---

### Post by oldfred on 2015-06-09
You click on the change button.
You  probably want to reformat / (root), it will find swap automatically, so you do not have to do anything with it. But with /home you also select it and choose partition, but DO NOT tick the format or else it will be overwritten.
Boot loader is always installed to a drive like sda which should be default. Do not choose partition unless you have another grub as main boot. With MBR  only one system can be in charge of booting and it must be in MBR or first sector of hard drive.

       Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)


 Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by ajgreeny on 2015-06-09
Highlight sda5 and click the Change button.  There you can choose to "Use as ext4", set mountpoint as / (ie root), select the Format tick-box to format that partition.
Now highlight the sda2 partition and click Change again, then choose to use as Linux swap.  No need to do any more on that; I'm not even sure if that is really needed as I think swap is found and used automatically by the nerw OS.
Now highlight sda3, click Change again and choose to use as ext4 partition, mountpoint /home, but for this one make sure that the Format tick-box is **NOT SELECTED**.

You should **always have a backup of important files** in your /home as it is not impossible for things to go wrong; it shouldn't happen, but you can bet your boots that the time it does is the time you don't have a backup available.

The bootloader should go to the root of a disk, never normally to a partition.  So probably put it on /dev/sda in your case, not to the root partition /dev/sda5; that will never boot the machine.

---

### Post by webmanoffesto on 2015-06-09
> **oldfred said:**
> You click on the change button.
You  probably want to reformat / (root), it will find swap automatically, so you do not have to do anything with it. But with /home you also select it and choose partition, but DO NOT tick the format or else it will be overwritten.
Boot loader is always installed to a drive like sda which should be default. Do not choose partition unless you have another grub as main boot. With MBR  only one system can be in charge of booting and it must be in MBR or first sector of hard drive.
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

That worked great. And thanks for the links too.

---

### Post by webmanoffesto on 2015-06-09
Thanks for the help.

---

