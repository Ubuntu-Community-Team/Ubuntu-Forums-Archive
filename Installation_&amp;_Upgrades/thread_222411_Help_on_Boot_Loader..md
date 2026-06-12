---
title: "Help on Boot Loader."
date: 2006-07-24
forum: Installation &amp; Upgrades
---

### Post by x_Miyako_x on 2006-07-24
I have Win XP Pro and Ubuntu Dapper Drake on the machine. And I know Dapper Drake is on the machine but I do not get the option to choose it whatsoever, Win XP PRo just loads and goes and I have no option to choose. Is there anyway to resolve this and if so how would I go about doing so. Would be so much appreciated for any help given in this matter. THanks in advance.

Miyako Myoung

P.S. And if any of you know xp well enough, how do you change drive letters to drives?

---

### Post by cremnob on 2006-07-25
I have the same problem. I don't have an option to choose OS's. :neutral:

---

### Post by Herman on 2006-07-25
[*Click Here*]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD") for an example of how to install GRUB to MBR from a terminal in your Ubuntu Dapper 'Desktop' Live/Install CD.
Normally, the installer will automatically install GRUB to MBR in the first sector of the first track on whichever hard disk it thinks is your first hard disk.

If you have only one hard disk, GRUB normally installs without any problems. A few BIOSs have an antivirus or an MBR or bootsector protection feature that can stop anything from writing to your MBR, including GRUB. You should check that and turn it off temporarily if you really can't install GRUB.

If you have more than one hard disk, especially if you have IDE and SATA drives combined in one machine, GRUB can get confused about which one is the first hard disk. Sometimes it installs to MBR on the second hard disk by mistake. The BIOS won't 'see' it there. It will only look at the MBR on the first hard disk, which will still be pointing to Windows. You may need to try again to install GRUB to (hd0). 

First, boot your Dapper 'Desktop' Live/Install CD. Some other Linux CDs can also be used for this just the  same, for example, Knoppix.
There are five commands in the above linked how-to. 
1) sudo grub, this command is to start a 'grub  shell', it will have a new prompt. like this: grub>_
```
sudo grub
``` 
2) find, this command is used to find things in your computer, in this example we will look for /boot/grub/stage1, which is a good trick to use to find out which partition will be our Ubuntu partition. Most people will only have one, but some people have more than one Linux partition. (hd0,1) is the most common answer, but it still pays to check and make sure. Your computer might be different from mine. You need this information for the root command which comes next.
```
         grub> find /boot/grub/stage1
           (hd0,1)
``` 3)  root (hd0,1) (where (hd0,1) was the answer grub gave you from the find command), this command is to tell grub which filesytem to consider as your 'root' filesystem where you want to install the main part of grub bootloader's files. If it recognises the partition, it will answer by identifying the filesystem for you. This helps you to confirm it is indeed a Linux partition you have chosen to write Grub's files to, and it is therefore safe to proceed. Do not install GRUB to any non-linux partition.
```
                grub> root (hd0,1)
                Filesystem type is ext2fs, partition type 0x83

``` 4) setup (hd0) this command tells GRUB to install to the first sector of the first hard disk, called (hd0) in GRUB terms.  You can also install GRUB to your first sector of your Ubuntu partition, which would often, but not always, be (hd0,1) or otherwise whatever is found with the find command shown in step 2). ```
setup (hd0)
``` 5) quit this command exits the grub shell. You can exit the terminal and reboot, and hopefully this time you will see your new Grub menu and be able to choose your operating systems.
```
quit
``` I hope this helps, Regards, Herman.

---

