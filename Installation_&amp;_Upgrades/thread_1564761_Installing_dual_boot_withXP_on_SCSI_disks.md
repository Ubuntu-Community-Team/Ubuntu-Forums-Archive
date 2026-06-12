---
title: "Installing dual boot withXP on SCSI disks"
date: 2010-08-31
forum: Installation &amp; Upgrades
---

### Post by m.dr on 2010-08-31
Using 9.10 in dual-boot with XP:

Dell 600SC running an Adaptec 39160 dual channel SCSI controller which has 2 disks connected to it.
The machine also has 2 IDE drives connected to it.
The boot order of the disks is set to the SCSI disks as the first in boot order (after CD).

I am trying to set it to maximize performance from the SCSI config so I have XP on the first SCSI and I set up Ub 9.1 on the second SCSI in a dual-boot configuration.

In this set up the machine when rebooting goes straight to XP (on the first SCSI) and does not even see the Ub installation. The installation went fine and no complaints.
On the same machine if I just had Ub on the first SCSI - machine boots fine (albeit after a long pause looking for the bootloader).

So with XP on the first disk (which I need to - to have XP) the Ub bootloader does not seem to set the right params to be able to boot.

I hope I have made my problem clear.

Again this is with 9.1. Not trying 10.04 as with 10.04 I don't even get to boot even with standalone Ub (with no XP). However it installs fine but does not find bootloader in 10.4, so we will keep to the 9.1 for now. I am however open to working with 10.04 if there is a solution in dual-boot with XP in my config.

So again 9.1 installs fine with XP on 1st SCSI disk, an ub 9.1 on 2nd SCSI disk, but then bootloader does not get activated and machine goes straight to XP.

Your help is highly appreciated.

Thanks.

---

### Post by oldfred on 2010-08-31
Sometimes the IDE drives get promoted and that may be why grub took longer. Older versions of grub had a delay while it did the search of other drives for boot when the install was not on the same drive as the grub.

Lets see where everything is at. From liveCd or if you can boot:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by m.dr on 2010-08-31
Thanks for your reply. Attached is the RESULTS.TXT you requested.

I understand that the IDE drives get promoted as in the manual partitioning table (during install) I see the IDE drives first. However it did not matter when I installed Ub 9.1 standalone - it would eventualy find it (+/- 4 mins) and then boot fine.

However now XP is is in the first of the 3 SCSI drives. Its a dual channel card with 2 drives on 1 channel and the 3rd on the second. In the BIOS of the DELL I have the SCSI drives as the first boot drives with the first id being the first drive. This drive on its 1st partition is where XP is - SDD1. I installed Ub 9.1 on the 1st partition of the 2nd drive in that same channel - SDE1. I am using SDD2 for /opt and SDF1 for /home (just 2 gb - as I do my main storage on the IDEs).

Hope its not too confusing and please let me know if you need more details.

As I mentioned it installs fine, but on reboot goes straight to XP w/o even boot loader activation. Again in standalone in this config Ub works fine as well but I still need XP.

Btw on a side note: I tried installing Ub 10.04 in standalone on this box and again installs fine but on reboot does not find the drives. Infact when I was running this as 9.1 standalone I updated from 9.1 to 10.04 through apt and then on reboot did not load. So then I installed 10.04 from CD and installed fine, saw all drives but did not reboot.

Anyway just thought would inform you - but that's a side note just want to get XP and 9.1 going in this config for now.

Thanks immensely for your help.

monosij

---

### Post by oldfred on 2010-08-31
Did you add swap to every drive. Some think it adds something, but memory is so much more important that having just one swap is usually best if you have more than 2GB. If you had multiple linux installs and wanted to hibernate (still not recommended) then you might want multiple swaps.

The installer has an advanced button that lets you choose which drive to install grub to. You then in bios have to set that drive as the first boot drive. The installer often just chooses sda as the default install drive for grub, but if you do not boot sda then it does not work.
Install Screens shown with advanced button
[http://members.iinet.net.au/~herman546/p24/022f.png](http://members.iinet.net.au/~herman546/p24/022f.png)
Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

I prefer to have operating systems on separate drives so each drive can have its own boot loader and then work stand alone incase one has an issue. With both systems on one drive that drive had better work. If will be slightly better if you install grub into the MBR of your system drive. It will still let you boot windows. If you ever need to directly boot windows you can reinstall the windows boot loader.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Some install an operating system on every (larger) hard drive just in case.
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)

I have three copies of versions of Ubuntu and XP across three drives plus a full install on flash that I can use to boot it or any of my other drives.

---

### Post by m.dr on 2010-08-31
hello OldFred -

Thank you for all the tips. Let me clarify a couple of things from you.

In BIOS - SDD (1st SCSI) is set as first boot drive. XP is in in 1st partition of SDD - that is SDD1.

Using the advanced button:
 ** Should I be setting the bootloader to be installed in SDD or SDD1 - where XP is located **

I noticed it defaults to HDE0 but there is no HDE0 so I assumed it just sets it internally somehow to the first boot drive.

Now my / is installed on SDE1 and I tried using the Advanced button to set it to SDE1 but no luck.

So if I set bootloader in SDD1 where XP is is there an chance of corruption of XP so it does not load again? I need to use it. However if you think it can be fixed - in ways you have mentioned in this link:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708) that will be great.

I try to put /, /usr, /var in separate SCSIs to get performance through parallelization on SCSI chains. And so I do multiple swaps as well. I don't know how much this kind of configuration helps but I have always used SCSIs - so have old habits.

Thanks again sir and wait to hear from you before I start install this evening.

Btw any ideas on why I get the issues with Ub 10.04?

monosij

---

### Post by m.dr on 2010-08-31
Btw Fred - Yes I added swap to every drive as I understand that increases performance - especially if I do virtualization from Linux and start my XP from within it? Also if I am running several apps simultaneously and such.

Btw I have 4 GB and its a Pentium HT processor 3 GHz.

Also may I ask you one other question:
I have another almost identical (small changes in HDD config) machine that I use just as a server. I have a DVD burner in it that does not seem to be recognized by Ub. What happens is:

I put in the install CD Ub 9.1 - it shows up and gives me option to install.
I choose install and then the Ub logo shows up.
But then it does not go anywhere from there.

So what is happening I don't understand since obviously the DVD is getting recognized and drivers are loaded for the Ub CD to show up and then when I choose install for the logo to show up as well? Or is it that the drivers are not getting loaded for the DVD burner? Its 7 month old dual-layer (I think) DVD burner.

I tried with Alt and Server - same situation. In fact I want to install server on it - so I am running SuSE 11.3 which works fine. But just thought I would ask as I would like to run Ub server on it actually.

Again thanks OldFred for your help.

monosij

---

### Post by oldfred on 2010-08-31
The comment on swap is because increasing performance on swap is not worth much. You want applications to run in memory and add memory if necessary. If you really want to speed up hard drives then you have to think about SSDs.

You do not want, and with all the MBRs you have do not need, to install grub to a partition. You only install grub2 to MBRs except in unusual cases. Grub2 is also considered less reliable in partition boot sectors as it has to use blocklists and if a boot file gets moved you will  not be able to boot without reinstall.


On my system with Nvidia, I was disappointed with Lucid as when I first tried to install it turned off my monitor. Karmic had worked without issue, but they updated some video things and for me at least it was a regression. I only knew system was still working since I install from USB flash drives and the flash drives light was still working. 

I had to do this:
boot from the cd, press F6 and then select the nomodeset option.
(I edited my grub.cfg as I use grub to boot ISO on USB, or in USB's syslinux.cfg or text.cfg)
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
After I installed nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
sudo nvidia-xconfig
Or it should be in System>administration>Hardware drivers.

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
    * Older Intel video card: i915.modeset=1 or i915.modeset=0
    * nVidia: nomodeset
    * Generic: xforcevesa

Also with servers RAID can cause issues. With the older versions you have to use alternate install CD. If drives were ever RAID there may be meta data on drive interfering with a desktop install.

---

### Post by m.dr on 2010-09-01
hi OldFred -

I am happy to say that Ub 9.1 worked great on the dual-boot with XP. I installed GRUB into the primary disk's MBR rather than the partition which I did before. Thank you for that pointer. Really appreciate it.

After that I updated 9.1 - changed to GRUB2 I think as it asked if I wanted to keep current version or package maintainer's. I chose the second.

After update 9.1 booted fine and then ... I chose to upgrade to 10.04.
Updated fine, GRUB loaded and showed me the various options incl XP.
However could NOT boot into 10.4. Can boot to XP however.

So from GRUB when I choose the 10.04 (default), it sits for a while and then gives the following messages:
---------------------------------------------------------------
Gave up waiting for root device. Common Problems:
- Boot args (cat/proc/cmdline)
 - Check rootdelay= (did the system wait long enough?)
 - Check root= (did the system wait for the right device?)
- Missing modules (cat/proc/modules; ls /dev)

ALERT! /dev/disk/by-uuid/7c34...... does not exist Dropping to a shell!

Busybox v1.13.3 ... built in shell (ash)
Enter 'help' for a list of commands.

(inittamfs) ..
---------------------------------------------------------------

I know the disks are good as I did a BIOS level check and XP boots fine.
I am assuming I should be able to set something in the GRUB commands to wait longer?

Like I said 9.1 works fine even after upgrade which updated GRUB. 10.04 also updated the GRB I think as it wanted to run an update script on the bootloader and had the right drive checked as well.

That's all I have. As I said if this is a big deal I am fine with 9.1 and can just work with that. However if this is something that I can fix with your help - would really appreciate it.

Thanks again.

monosij

---

### Post by oldfred on 2010-09-01
I have seen a couple of solutions to try:

See post #4 busybox exit & boot - blue screen;s post
[http://ubuntuforums.org/showthread.php?t=1531999&highlight=rootdelay](http://ubuntuforums.org/showthread.php?t=1531999&highlight=rootdelay)
See quixote post
[http://ubuntuforums.org/showthread.php?t=1561652&highlight=rootdelay](http://ubuntuforums.org/showthread.php?t=1561652&highlight=rootdelay)

---

### Post by m.dr on 2010-09-01
Thanks you sir! I got it all working. That was a valuable pointer.

I have spent endless hours on this. I should have posted earlier!

Really appreciate it.

monosij

---

