---
title: "Install GRUB"
date: 2006-08-21
forum: Installation &amp; Upgrades
---

### Post by Hg80 on 2006-08-21
hi all i had to reinstall windows ready for a LAN event at the weekend but, doing so its put its loader on the MBR, so how do i go about installing grub?
i know that windows is on /media/sda and linux is on /media/sdb
so what do i do now?

---

### Post by moma on 2006-08-21
Hello,

Ubuntu CD is a rescue CD too.

1)  Load in your Ubuntu CD, 
Boot up and  select "Start or Install Ubuntu" from the menu.

2) When in Ubuntu LiveCD, 
start gnome-terminal program from 
Applications -> Accessories -> "Terminal" menu.

3) Become a root-user
$ [COLOR="Green"]sudo -s[/COLOR]

4)  Mount your Linux-partition (/dev/sdb) to /media directory.  
Do:
# [COLOR="Green"]mount /dev/sdb  /media[/COLOR]

Note: fdisk -l will list all harddrives and their types. (in case you need to check that)
# [COLOR="Green"]fdisk -l[/COLOR]

5) Re-install GRUB boot loader on /dev/sda (the MBR). 
I also assume that your BIOS is set to boot from /dev/sda.  
Do:
# [COLOR="Green"]grub-install --root-directory=/media/boot  /dev/sda[/COLOR]

GRUB vil output some messages on the screen. 
You should see  "No errors detected" or an equivalent message.
----------------------------------------------------------------------

6) Remove the CD and reboot to Linux OS.

When in Linux, 
edit /boot/grub/menu.lst and add Windows to the boot-menu list ( if you wish).
$ [COLOR="Green"]sudo gedit /boot/grub/menu.lst[/COLOR]

# Add these lines
title Windows aha
rootnoverify (hd0,0)
makeactive
chainloader +1
boot

---

### Post by Hg80 on 2006-08-21
thanks try it when i get home, just i hate to use windows but i need to use it for alot of games and attending lan events
However i do have cedega installed too for gaming at home

---

### Post by Hg80 on 2006-08-21
ok tried that and it didnt work says it cant sind the drives,

I have been able to access my Linux files under Windows with Expolre2fs, so is there a way af installing grub to MBR to use the infomation already in my linux install?

---

### Post by Chris Tucker on 2006-08-21
replace the mount /dev/sdb part with /dev/hdXX where XX is usually a1  (/dev/hda1), your linux partition
if your not sure, use fdisk -l (in the root terminal) to find out the device for it.
likewise, change /dev/sdb in the grub line to your booting drive, probably /dev/hda
no need for a number on that one.

---

### Post by Hg80 on 2006-08-23
using the live cd i can see the HDDs but they all have little "X"s above there icons, so i cant mount them.
I think its beacause there NTFS formated surely there is a way just to install grub to the MBR to use the current one installed on my linux partion.

---

### Post by Herman on 2006-08-23
Hg80, Of course there is, there are lots fo ways to re-install Grub, here's another way if you'd like to try it, this works for most people. Click the 'GO' link for an illustration.
Re-install Grub with a GRUB shell eg; with Live CD..........................................................[GO]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD")
            
```
sudo grub
``` The above command entered in a terminal in a Linux Live CD gives you a 'Grub shell'. It will have a prompt like this: grub>

  ```
find /boot/grub/stage1
``` You can type this (above command) after the grub> prompt and enter it. The output from that will remind you which partition numbers have grub in them, to use in the next command. In my computer I have more than one to choose from.

```
root (hd0,1)
``` (Where (hd0,1) is my Ubuntu partition. This means I want to install Grub from my first Ubuntu partition, (as opposed to some other Linux partition which may have been in the list from the previous command's output).

```
setup (hd0)
``` The above command will write Grub to MBR. If you want, you can also install Grub to the first sector of you Ubuntu partition by typing 'setup (hd0,1) if that is the partition number for your Ubuntu partition. 

```
quit
``` That just brings you back to your regular BASH shell (terminal). From there you can exit, reboot and remove the Linux CD and see if it worked.

Regards, Herman  :D

---

### Post by Hg80 on 2006-08-23
got grub working, using the super grub disc and telling my bios to boot from that HDD, but grub wouldn't find the right partitions so i edited the grub command and hay all but the boot to windows feature works now need to find out the hdd which im doing now
i just dont get the grub hdd feature i think it goes up like hd0,1 hdd 1,1 etc it i think

---

### Post by Herman on 2006-08-24
>  i just dont get the grub hdd feature i think it goes up like hd0,1 hdd 1,1 etc it i thinkHg80, Well, hard disks and partition names are known by different names and numbers according to what operating system or bootloader or disk partitioning software we are using at the time.

The best way to find out what partition numbers you have at the moment is to take a look with your favorite partitioning software. There are some third party (commercial) disk partitioners that give nonsense partition numbers which are useless and even misleading if you are trying to use that information in Linux. Most Linux compatible disk partitioning software will give you meaningful partition numbers. Any 'Parted based partitioner, GParted, QTParted, or fdisk or cfdisk should be good.

The disk partitioners's partition numbers, or Linux partition numbers, for example /dev/hda1, or /dev/hda2, /dev/hda3, and so on, need to be converted to Grub's numbering system when you want to use them for purposes associated with Grub.

Grub calls the first hard disk (hd0) and the second hard disk (hd1), the third hard disk (hd2), and so on.
Grub calls the first partition on the first hard disk (hd0,0), the second partition on the first hard disk (hd0,1), and the third partition of the first hard disk (hd0,2) , and so on.
As you will have noticed, grub always begins counting from zero.
An IDE hard disk is called by Linux /dev/hda or /dev/hdb or /dev/hdc, and so on. If the disk is SCSI or Sata, Linux calls it /dev/sda, /dev/sdb, or /dev/sdc, and so on.
Grub has a different system for identifying hard disk drives. Grub does not differentiate between IDE or SCSI/Sata drives. All types of hard disk is called 'hd' by grub. As for numbers, Grub always starts counting from 0 . That means our first hard drive is called (hd0) by Grub.

Another useful fact to keep in mind with partition numbers is that there are four entries in the partition table, so any primary partition can have a number between 1 and 4. There can be one special primary partition called an 'extended' (Primary) partition, it can also be number 1,2,3 or 4.
The 'extended' partition can contian a great number of 'logical' partitions. These 'Logical' partitions always begin numbering at 5 and upwards. So if you see a partition with the number 5 or greater, you always know it is a 'Logical' partition.
Numbers between 1 and 4 are always either 'Primary' or 'Extended' partition numbers. Very often the hard disk will only have one or two primary partitions and an extended partition, so a number will be skipped. For example, Windows is often the first primary partition (hd0,0), and Linux might be on the second primary partition (hd0,1). When Linux was installed, the installer usually makes the swap area 'logical', and in doing so, also makes the 'extended' partition which houses the logical swap area. So the extended partition is given the number 3, and the swap area will be number 5. 
What happened to number 4? The number 4 is reserved for primary partitions, so it wil be skipped until some day when we decide to make another primary partition.

If you find all that confusing, don't worry, we all find it a little confusing at first.

Super Grub Disk has a very useful collection of tools for working with Grub and other bootloaders, and it is educational as well.
There are menus for selecting which disk you want to select and they show you that hard disk 1 is also called hda, sda, or (hd0), hard disk 2 can be called hdb, sdb, or (hd1). If you use Super Grub disk you can't really go wrong, because all the equivalent disk designations are arranged in rows, you just need to select the appropriate row.
Next, you will be offered a list of partitions, and these too are arranged in rows. You will see that if you pick partition 1, it will be also called hda1, sda1, or (hd0,0) Those are all ways of referring to partition number 1.

I'll bet all this is far more than you ever really wanted to know, but I still feel like posting it anyway, verbose as it is, because hopefully someone will find at least part of it useful, and they'll think  'aha', (I hope).

Regards, Herman :D

---

