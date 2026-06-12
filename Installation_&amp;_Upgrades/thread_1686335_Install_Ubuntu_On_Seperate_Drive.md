---
title: "Install Ubuntu On Seperate Drive"
date: 2011-02-12
forum: Installation &amp; Upgrades
---

### Post by kevsim on 2011-02-12
I have Windows XP on one drive "C" drive, Windows 7 on another "E" drive and want to install Ubuntu on another drive "G" drive.

How do I when installing Ubuntu select the "G" drive to install to?

Then how to select the operating system required from a cold boot?

I would appreciate some advise.
kevsim

---

### Post by YesWeCan on 2011-02-12
Hi. Installing Ubuntu on its own disk is a good idea. An easy and safe way is simply to disconnect the all the other drives before you install Ubuntu.

After Ubuntu is installed, rebooted and updated, shut it down and reattach your other drives. Then set the bios boot order to boot the Ubntu disk first. Then boot Ubuntu and open a terminal and type 'sudo update-grub'. This will add your Windows OSs to the boot menu from where you can try selecting them when you reboot.

There is a possibility that XP may not boot. Windows 7 will be fine. if so come back for a work-around.

---

### Post by YesWeCan on 2011-02-12
BTW the first time you boot Ubuntu, before the update-grub, you wont get a boot menu at all. Dont be concerned. Unfortunately, the nice Ubuntu people seem to now disable the grub menu when grub only has one OS to select. I think this is a mistake and does cause confusion for the unititiated.

Also, you will always be able to boot either XP or W7 directly by choosing their disks from the bios.

---

### Post by oldfred on 2011-02-12
Disconnecting drives as YesWeCan is definitely the safest way to prevent grub2 from installing to the MBR of your windows boot drive. But if you use manual partitioning you also get a combo box on which drive's MBR to install grub's bootloader into.

Windows usually combines all its boots into only one windows boot partition that has the boot flag. Depending on how you installed it, grub may be only able to boot one windows and then you get the choice of the other windows. If installed on two drives separately then you may be able to boot both directly. Windows actually moves the boot files from the second install to the first.

Vista but applies to all versions and MBR(msdos) systems
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up.

---

### Post by gordintoronto on 2011-02-12
One other small note: C:, D: etc are DOS/Windows ideas. Linux calls hard drives names such as sda, sdb, etc (or maybe hda, hdb). Partitions on a drive get a number, so my hard drive contains sda1, sda2, sda3, sda5, etc. CD-ROM drives get a different set of names, unlike DOS/Windows.

---

### Post by kevsim on 2011-02-14
I thank you all for the replies.

Without disconnecting any drives, is there any way to install Ubuntu to a particular drive, in my case Drive "G"?

Do I need a particular version of Ubuntu to do this?

I do not know what happened but I had all drives disconnected except for "G" drive, inserted Ubuntu 10.04 and it was supposed to be installing on this drive.

All drives were then reconnected and a search of "G' drive showed it was not installed.

This is why I am asking the first part of the question in my reply.

I would appreciate more advise.

kevsim

---

### Post by oldfred on 2011-02-14
Did you go thru the full install on drive 'G'? Were you installing wubi which is inside the NTFS partition or creating Linux partitions and installing to those partitions you created. Or auto install using full drive?

If you manually partition and use manual install you can choose which drive to install to and which drive to install grub the boot loader into. Otherwise it uses defaults for everything and some do not like the results.

Issues on dual boot on same drive:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
From kansasnoob:
[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)
Trust me here! If you choose either "Use entire partition" or "Use entire disc" you are not likely to end up with "Alongside" anything! You will most likely lose the OS and any data contained therein!

---

### Post by kevsim on 2011-02-15
[oldfred,]("http://ubuntuforums.org/member.php?u=852711")
Thanks for the advise.
As this is my friends computer and he lives some distance from me, I will not be back until Saturday to assist him with the Ubuntu installation on his "G" drive.

I am still a little lost as to installing Ubunu on a  separate drive "G" that does not have an operating system installed.
I intend to install Ubuntu 10.04.

1/ Does the drive "G" require formatting with a particular file system before installation?
2/ Does it require an operating system pre installed?
3/ Can I select which drive to install Ubuntu on during the installation process?
4/ With XP Drive "C", and Windows 7 Drive "E", on which one would the boot loader for Ubuntu be installed?
5/ In the above case how would you install the boot loader?
6/ When viewing the drives from My Computer, can I see if Ubuntu is installed?

On a normal computer start the Windows 7 boot loader appears first.

Is there a step by step instruction available to do what I require as explained above?

I would appreciate any advise on this matter.
kevsim

---

### Post by grahammechanical on 2011-02-15
I got nervous when I first installed Ubuntu. So, I suggest that you start the installation and remember that at any point you can cancel and no damage will be done. The installer program does not make any changes to your disc until almost the end of the setup part of the install process. The partitioner will give you a list of the changes that you have chosen to make and will ask you to approve them. You can cancel at this point if you want to think over what you were doing. Go forward and the partitioner will start to partition your discs.

When the partitioner program examines the discs of your computer it will present you with a graphical representation of the drives and partitions in the machine. Work out which drive is the one called G: in Windows. You can choose to install Ubuntu on that disc by giving it a mount point of / 

You will also need to choose a format. For Linux it usually is ext3 or ext4. You will need to tick a box called format. The format that not happen unless you put that tick there.

The install program will install the boot loader. It will probe for other operating systems and create a boot menu from which you can chose an OS to boot from. The Ubuntu OS will be at the top of the list.

I use a utility called Grub Customizer. It is in the Ubuntu Software Centre. It allows you to change the boot order, change the menu colours, put a splash image behind the menu, change the time out, change the labels on the boot menu. And other stuff. Excellent utility.

Regards.

Here is a tutorial

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
Note the images Prepare Disc Space and the image Ready to Install. click Install at this point and there is no backing out. Click Quit and the process will quit. No harm done but no good done either because you have not installed Ubuntu.

---

### Post by oldfred on 2011-02-15
See my links to Herman's site. He has very detailed instructions with screenshots to help walk you thru the process.

Manual install is preferred so you get to choose where to install. If you disconnect all other drives then you can just use the auto install. The installer has a combo box showing drives but as posted above it will not be G: but drive sda, sdb, sdc etc. 

In windows drive G: may still be on drive sda. Windows calls both partitions & hard drives as drives. If drive G: is just really a partition on sda then you have to use manual partitioning and be aware of the cautions posted above.

If G: is really another hard drive, it is best to install grub2 boot loader to the MBR of that drive and in BIOS choose to boot that drive. Grub will give you a choice to boot windows, but only one copy of windows is normally directly bootable as windows moves the boot files from second installs to the first install. Then only the first install is bootable.

---

### Post by kevsim on 2011-02-16
I thank you for the information.
To clarify a couple of points.
1/ I do not want to disconnect any HDD's and would install with all drives connected.
2/ I want to install on "G" drive which is a [COLOR=black]separate [/COLOR]drive without any operating system.
3/ Do I have to format "G" before starting the installation?
4/ What format type do I use?
5/ Is there any minimum or maximum partition size to use, can it use the total "G" drive?
6/ Can I select the drive to install from the Ubuntu 10.4 installation disk?
7/ Upon completion of installing on "G" drive, what Boot record do I have to modify, XP or Windows 7?
8/ Is there any special programme to modify the boot record, as Windows 7 is a strange beast?
Any further information would be appreciated as some other friends also want to use Ubuntu.
kevsim

---

### Post by oldfred on 2011-02-16
I had suggestions in post #4 for sizes & formats. Ubuntu will install to the entire drive if you want. But you do have to be sure to choose correct drive. It will then install grub to the MBR of the first bootable drive usually sda. I prefer manual install and then you get the choice of which drive's MBR to install grub2 into and then reset BIOS to boot that drive.

You can partition in advance, or as part of the install. I prefer to do it in advance with gparted either from Ubuntu liveCD or another liveCD of gparted that I also have.

---

### Post by PaulReaver on 2011-02-16
I'd pull the drives.... install ubuntu then put the windows drives back in....  better to be safe.....

when the pc comes back up.... sudo update-grub.... should add windows entries to your grub list

I do this.... works for me :)

---

### Post by kevsim on 2011-02-17
I thank you all again for the information provided.
I apologise for asking so many questions, but this computer has given me problems in the past as it has so much connected to it, so do not want any more issues.

The HDD's are as follows 
XP drive 1 "C", partitioned for  "D".
W7 drive 2 "E", partitioned for  "F".
Ubuntu drive 3 "G" no partitions.
When installing with Ubuntu 10.4  and looking for the partitions and drives, how would the drive structure read?

kevsim

---

### Post by Sean Moran on 2011-02-17
> **kevsim said:**
> I thank you all again for the information provided.
I apologise for asking so many questions, but this computer has given me problems in the past as it has so much connected to it, so do not want any more issues.

The HDD's are as follows 
XP drive 1 "C", partitioned for  "D".
W7 drive 2 "E", partitioned for  "F".
Ubuntu drive 3 "G" no partitions.
When installing with Ubuntu 10.4  and looking for the partitions and drives, how would the drive structure read?

kevsim
I'm a little confused because of my experience with two separate HDDs on Win98 systems, where I'd expect drive #1 to contain drives C: & E:, and drive #2 to contain D: and F:.  Never tried two HDDs on anything more recent than Win98 so maybe they changed things, but with Win98, the first (and only) primary partition on the second hdd gets a letter before the first (and only) secondary partition on the first drive.  Either way, it's not that important for this question if we allow D: & E: to be interchangeable.  We're not about to muck with them anyway.

/dev/sda1             C: WinXP root.
/dev/sda2 if exists  - possibly extended partition or else primary E or D::
/dev/sda5 if exists  - logical E: or D: if using extended partition on /dev/sda2.
      
/dev/sdb1 depends- D: or E: WIn7 root partiton
/dev/sdb2 if exists  - possibly extended partition or else primary F:
/dev/sdb5 if exists  - logical F: if using extended partition on /dev/sdb2.

/dev/sdc1 or 1 & 2 - ext3 or ext4 Linux root partitions: as in /  - 4GB+.
/dev/sdc2 or 3       - primary /home/ partition or extended partition.
/dev/sdc3 or 4       - SWAP - 1 or 2GB should do for starters.  Rule-of-thumb: double the RAM.
/dev/sdc5 if exists - /home/ partition on logical volume if /dev/sda2 or /dev/sda3 are extended partitions.

It's a lot simpler if you know how these drives are all partitioned, and what are primary partitions and what are logical volumes within extended partitons.  It's always nice to set /dev/sd?4 to the SWAP partition because it leaves lots of versatile room for everything else, and there's ALWAYS a need for swap.

Edit: Also, if Win7 and XP follow the Win98 nomenclature for drive lettering, wouldn't that make the first partitiom on drive #3 E:, and the rest of the partitions follow from F: onward?  Luckily, Linux doesn't bother with these things, and each drive has a letter, with each partition on each drive getting a number.  Much more clarity than the old MSDOS system.

---

### Post by oldfred on 2011-02-17
From the liveCD, you can run this from a terminal to see your existing drives & partitions. Copy & paste this into the terminal. Applications, Accessories, Terminal.

```
sudo fdisk -lu
```

---

### Post by kevsim on 2011-02-19
I thank you all for your advise, Ubuntu is now up and running on my friends computer.
It is now a triple boot system and working OK.
I will later provide another post with the procedure   I adopted for installation and some examples of drive arrangements.
This then may assist others should they have a similar arrangement.
kevsim

---

