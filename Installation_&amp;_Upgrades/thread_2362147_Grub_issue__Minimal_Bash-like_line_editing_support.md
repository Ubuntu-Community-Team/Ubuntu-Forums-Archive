---
title: "Grub issue:  Minimal Bash-like line editing supported...(16.10)"
date: 2017-05-24
forum: Installation &amp; Upgrades
---

### Post by joseph123321123 on 2017-05-24
[COLOR=#111111][FONT=Ubuntu]So I recently created a small partition on my HDD and installed Windows 10 on it.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Once I restarted it would only boot into Windows, I expected that though. I then booted Boot-Repair-Disk and went through the steps so as to repair and get a boot menu when I start my laptop.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]HOWEVER, once rebooted it goes to a black screen which says:[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]'GNU GRUB version 2.02~beta2-36ubuntu11.2'[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]'Minimal Bash-like line editing is supported'.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I have tried a few things from that screen though nothing seems to have repaired it yet. I was thinking it might be a good idea to boot the live/trail CD (USB) and then try to repair/reinstall GRUB, however I wouldn't know what commands to run in terminal.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I have a paste.ubuntu link which was given by Boot-Repair-Disk:[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu][http://paste.ubuntu.com/24647205/](http://paste.ubuntu.com/24647205/)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I think, although i'm not sure, the grub was on sda1 When I went through the process it seemed to be making changes to sda6 (my main ubuntu partition, about 400gb). Windows is installed on sda2.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Any ideas as to how I can get it to boot to GRUB and then select Ubuntu or Windows, or if that isn't possible just to boot Ubuntu, would be greatly appreciated.[/FONT][/COLOR]

---

### Post by QIII on 2017-05-24
Moved to its own thread from [https://ubuntuforums.org/showthread.php?t=2355722](https://ubuntuforums.org/showthread.php?t=2355722).

Please do not hijack the threads of other users.  Your problem might present with similar symptoms and yet be completely different.  If others try to answer both your question and the OP's, the thread can be confounded and confusing for everyone.

Please allow other users to get their full measure of support without interruption and start your own thread so you can expect the same.

Thanks.

---

### Post by oldfred on 2017-05-24
Windows is actually on sda1 as boot partition and sda2 as main working partition. That is Windows standard partition structure with BIOS/MBR configuration.

Even with BIOS install you must have Windows 10's fast start up or hibernation off.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

You now show a gap in partition table from 920.. to 968...?
Did you have another Linux partition, perhaps a /boot?
Script did not show grub nor kernels that would be in a /boot.

You can use Boot-Repair to uninstall/reinstall all of grub & install latest kernel in advanced options. That would use the /boot folder, not a /boot partition.
Most desktops do not need, nor should use a /boot partition. Some servers, LVM & encrypted configurations may need a /boot partition.

Or you can try to recover a missing partition with testdisk or parted rescue.

       
 Used parted rescue
[http://ubuntuforums.org/showthread.php?t=2315405](http://ubuntuforums.org/showthread.php?t=2315405)
backup partition table before any changes, so you can get back to current if changes not correct
sudo sfdisk -d /dev/sda > PT_sda.txt
So you know sectors:
sudo parted /dev/sda unit s print 

 Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462](http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462) 
      
 [URL="https://help.ubuntu.com/community/DataRecovery#Lost_Partition"]https://help.ubuntu.com/community/DataRecovery#Lost_Partition
[/URL]
 Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step) 

Windows installs or major upgrades rewrite partition table. And usually "forget" to include all the Linux partitions. 
This has been a "bug" or perhaps Windows considers it a feature since Windows 7 came out with partitioning tools.

[URL="https://help.ubuntu.com/community/DataRecovery#Lost_Partition"]
[/URL]

---

### Post by joseph123321123 on 2017-05-24
Hi

Thanks very much for your reply, seems to be really useful so far although I've only read first few paragraphs and links.
So are you saying that once/if I can boot windows it is essential to have fast start up off?

---

### Post by joseph123321123 on 2017-05-24
Since posting I tried to run the live cd and repair GRUB and I also installed 17.04 on unallocated space as I thought that doing so might repair the bootloader. I also did this to make sure that I could still access the files in the sda6 partition. I can also some say that I don't have permission to access.

This was what I tried:

[http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd)

Still the same issue though.

The picture in the link is my HDD in GParted in live CD/USB:

[https://ibb.co/dU38xa](https://ibb.co/dU38xa)

Those are all of the partitions. The 23.08GB (sda7) is new since I posted the paste.ubuntu link, all the other partitions are as they were though.

I'm going to read the section about boot-repair now.

Thanks

---

### Post by joseph123321123 on 2017-05-24
> **oldfred said:**
> 
You can use Boot-Repair to uninstall/reinstall all of grub & install latest kernel in advanced options. [URL="https://help.ubuntu.com/community/DataRecovery#Lost_Partition"]
[/URL]

I cant see an option for uninstall GRUB, although I have ticked the options for reinstall and upgrade GRUB to it's most recent version.
There is an option to restore MBR and also an option to purge kernels then reinstall last kernel. Those are the only other options there that seemed as though they might be relevant, should I try either of those??

I'm fairly sure that there isn't a missing boot partition :(

---

### Post by joseph123321123 on 2017-05-24
I've solved it!!!!

This link was very useful:

[https://askubuntu.com/questions/88384/how-can-i-repair-grub-how-to-get-ubuntu-back-after-installing-windows](https://askubuntu.com/questions/88384/how-can-i-repair-grub-how-to-get-ubuntu-back-after-installing-windows)

Whilst boot repair didn't work when I tried with a USB and the terminal commands didn't work also. I booted the live USB and installed boot-repair then ran it and told it to install to the new partition sda7 (the one with 17.04). I rebooted and the GRUB menu appeared!! I can now choose the 16.10 from the menu and it boots fine... although it does take longer now and when booting there is a lot of messages like.... 'starting...such and such'. Windows boots fine and 17.04 boots fine also. I might try to start using 17.04 as I can access all my files on the 400gb 16.10 partition from there.

It's kinda messy now but I'm really pleased to be able to boot 16.10 again and also to be able to boot windows for the one specific task that I was trying to boot it for... lol.

I should mention that before doing all that I restored the MBR with the Boot-Repair Lubuntu tool. I've never seen Lubuntu before so that was cool! :P

---

