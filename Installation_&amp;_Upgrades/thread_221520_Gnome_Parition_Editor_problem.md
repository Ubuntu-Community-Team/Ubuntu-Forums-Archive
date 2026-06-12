---
title: "Gnome Parition Editor problem"
date: 2006-07-23
forum: Installation &amp; Upgrades
---

### Post by altonbr on 2006-07-23
140GB hard drive
20GB (10GB used) Windows XP/Programs [NTFS] -- Primary
120GB (10GB used) Data [FAT32] -- Logical

... I used Gnome Partition Editor on the Live/Install CD during the installation and took 5GB for my ext3 partition and 1GB for my swap partition. It took me a couple trys get it to work (because apparently you need to have the ext3 BEFORE the swap)... so once that was settled, the installation went smoothly, and I booted into Ubuntu off the hard drive (not the cd).

I then went around to play with some options and finally GRUB located at /boot/grun/menu.lst

I played around with it and got everything set up so it would boot to WindowsXP after 5 seconds... well it worked, except it just sat there with the grub commands sitting on screen (ie: chainloader +1, etc.) The only thing I noticed was it said it couldn't tell what type of format the hard drive was... so I thought it was a problem with GRUB... well I restored it to it's backup state, and it still didn't work when booting in WindowsXP... so I wasn't happy.

I inserted the WindowsXP Professional CD and ran in Recovery mode using 'chkdsk C:', 'chkdsk D:', 'chkdsk C: /p', 'fixboot'... in that order... it said it found something wrong on the first chkdsk C:, so I restarted and XP still wouldn't load... so I got frustrated and loaded the Ubuntu Live CD and tried to format the ext3 and swap partition.. it didn't let me.

I went BACK into the WindowsXP recovery mode and ran 'diskpart', deleted the linux partitions, then ran 'fixmbr'... then it tried to boot up but the bios or post said "disk read error, hit ctrl + alt + delete to restart"... 

So finally I plugged in my BootIt NG 1.75b CD... got that installed on it's own partition, got the unformatted space back onto D:, renamed it 'Data'... and then when I clicked on C: to rename it, it came up with an error, asking me if it was ok to fix it... in my haste and frustration, I said yes (so I'm so sooo sorry I didn't write it down)... but upon reboot, I deleted the BootIt NG partition with 'diskpart', ran 'fixmbr' again and now I'm happily back into Windows but with no Linux :(.

I'm just lucky I didn't loose any data (yes, of course, I backed up, but that's not the point).

The point is, I'm leaving back home soon, so I'll go back to my Ubuntu box then, but what the hell did Gnome Partition Editor do? Was it my fault for stealing space from the FAT32 partition? Was it my fault that I had the swap BEFORE the ext3? Was it my fault that the FAT32, ext3 and swap partitions were all in a logical, extended partition? Or was it Gnome Partition Editor being buggy?

Either way, although the instructions have improved immenseley from 5.10 to 6.06... an average power user like myself even has problems installing Ubuntu without doing a clean partition.


And don't EVEN get me started on the winsoft modem... Linux without the internet, it basically like a human without water. If I can't connect my modem, how would I be able to find out what the problem is or how to fix it? Especially if all the help is online...

---

