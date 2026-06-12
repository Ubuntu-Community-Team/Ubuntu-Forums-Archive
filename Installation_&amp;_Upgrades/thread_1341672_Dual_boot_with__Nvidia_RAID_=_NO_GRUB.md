---
title: "Dual boot with  Nvidia RAID = NO GRUB???"
date: 2009-11-30
forum: Installation &amp; Upgrades
---

### Post by dvsapp on 2009-11-30
I 'm nearly at wit's end with this... DFI NF4 Ultra-D running 2 1TB in RAID 1.
 
Installed Win 7 64-bit on 180GB partition. No problem. Loaded 9.10 64-bit LiveCD, used partitioner to setup an 80GB Ext-4 for root, 4gb for swap, and the rest as NTFS Data Share. No problem. I tell the bootloader installer to install GRUB on /dev/nvidia_mapper/heffigie. I run the install, reboot and NO grub; Win 7 loads as before... Tried repeat installs selecting different partitions for the GRUB install.
 
Same dead-end....
 
I read around the forums for awhile ,tried a few things, tried to install grub manually, I get an error telling me the drive is not found in BIOS, or something to that effect. Dmraid is installed. I tried another install run, deleting my Ext-4 partition and setting up an 8-mb partition as /boot. I then tell the bootloader installer to install there.
 
Same result. So here I am typing on a Winblows machine again....
 
Weird thing is, I have an almost identical DFI machine that was almost a text-book install. I did that one with a 9.04 alternate CD, then later installed a new copy of 9.10 in it's place. GRUB was there then and both OS'es boot fine.
 
I've got my 10lb sledgehammer ready....](*,)

---

### Post by jpichie on 2009-11-30
I am having the exact same problem with an Intel raid. I believe I tried that same post, from overclock.net, and it is still not working. When I boot with the live cd, and run os-probe, it finds the 2 installs, Windows7 x64 and Ubuntu 9.10 x64. I would really like to get this setup soon, so if anyone has some advice, please share :P
On a side note, no problem getting dual boot working on my work laptop with the same OS's (No RAID).
Thanks in advance.

---

### Post by darkod on 2009-11-30
I have never installed on raid but aren't you supposed to use the Alternate Install CD (image) and not the Desktop CD?
It clearly says for LVM and/or RAID use Alternate.
[http://releases.ubuntu.com/karmic/](http://releases.ubuntu.com/karmic/)

PS. In case you want to try that, don't be confused, the installer is text based. No GUI. The final system will have the standard gnome desktop GUI, not sure if you need to select that during install. Watch out for that not to end up with text based system. :)

---

### Post by jpichie on 2009-11-30
The Kubuntu 9.10 CD sees our RAID0 partitions fine, and installs to it. This is a GRUB issue by the looks of it. It doesn't seem to install. I tried it over my MBR, and I tried it on my Kubuntu 9.10 partition. Sadly it wouldn't even overwrite my MBR, it still boots Windows 7 all the time.I even changed my HDD boot order, and it doesn't recognize any boot loader when on the Ubuntu HDD.

---

### Post by darkod on 2009-11-30
You might be right, as I said I have not installed on raid.
However, if the instructions say to use alternate install maybe that's the link you're missing. It doesn't mean desktop version won't see the drives, maybe it just fails on grub install or whatever.
Anyway, I just wanted to point out that for raid alternate install image is recommended.

---

### Post by jpichie on 2009-11-30
Thanks Darkod, I will give it a shot on my lunch and let you know.

---

### Post by jpichie on 2009-11-30
So I tried out the alternate disk x64, it found the partitions again, no problems here. Installs fine, get to the part where it asks "install GRUB to hard drive" or "install LILO to hard drive". I chose GRUB, then chose finish installation. It goes half way through, and bounces back to the same menu screen (the setup screen - setup keyboard, bootloader, etc).
I didn't have time to try out LILO, but looks like I may need to give it a shot.

Isn't GRUB faster than LILO though?

---

### Post by dvsapp on 2009-11-30
jpichie
 
I tried the alternate CD for 9.10. Same results you have.
 
I ran gparted on my AMD machine that DOES work, and found something interesting- there is NO 100MB partition for the Win 7 loader! I remember having to install Win 7 over at least once due to a problem with NF4 legacy RAID drivers, so it must have screwed up somehow. Is it because this partition is not there the reason this machine works and my other one doesn't? I see you other folks are having issues as well, I can try to find out more from the working machine if I know what to look for.
 
I tried to redo the whole non-working machine again from total scratch in case I missed something- still no go. I'm going to try again with just ubuntu, and see if that works.:popcorn:
 
Dave

---

### Post by b0b138 on 2009-11-30
I had the same problem. Would go through the install but grub wouldn't install.  The logs made a reference to an old raid I used to have (only one disk but there was apparently raid metadata left behind) It seems like grub2 isn't playing nice with fakeraids. I had to install it manually from the cd.

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)  scroll down to recover grub2 via live cd

---

### Post by oldfred on 2009-12-01
If you have an old drive that was raid but is not,  Karmic/grub2 find that meta data.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda

New grub2 is modular and I think you have to be sure to load the raid module as part of grub. I do not know raid, but as Darko said the alt install must include that module that is not in the normal desktop.

---

### Post by dvsapp on 2009-12-01
I GOT THE THING WORKING!!!:D

Here's what I did. Start with clean drives, set up the RAID set. Install Win7, set the size of your windows partition with the partitioner in windows setup. When you format the partition, Win 7 wants to create a 100mb partition for system files. Format the partition, in my  case, 180GB. 
Then, DELETE the 100MB PARTITION. leave it as free space. Finish your windows install.

Load up the live CD, set up your /  and swap partitions, install ubuntu. At step 7, click advanced and install grub2 on the mapped drive, in my case, /dev/mapper/nvidia_hfewhatever, let it install. Reboot, and you should have the grub screen.

I used gparted to format the remainder of the RAID set as an NTFS data share.
After a little tweaking with fstab, I should be set.

Hope this helps.

Dave

---

### Post by Tolerpro on 2009-12-01
I have found a similar problem attempting to install a single-boot 9.10 Server on an ASUS RS120-E5/PA4 server with two 80G seagate SATA drives in an Intel MSM RAID 0 configuration. Attempting the same with the LSI Logic RAID 0 option was worse - the partition setup got confused as though it couldn't identify the logical volume.
 
With the MSM, the install proceeded properly but I got the same trouble at the GRUB step that jpichie mentioned.
 
Definitely looks as though there is a problem with GRUB and "fakeraids". Will try the advanced tip and see how that works.

---

### Post by jpichie on 2009-12-01
I'll give these tips a try at lunch. Also, just to mention, I do not have that 100mb partition that Win7 wants, as I did all my partition with Acronis from a Hiren's disk (I did not like Win7 taking 100mb for nothing). So I do not have that extra partition. Hopefully this time it works out.

---

### Post by Tolerpro on 2009-12-03
OK - being something of a newbie when it comes to RAIDS, I was starting off on the wrong foot using a fakeraid in the first place. It seems the only reason one would do such a thing is to coexist with Windows. Since this is not on my agenda, the solution was to disable the silly RAID in the BIOS and learn how to use the partitioner.
 
In the hope that this might save someone else in my position some headaches, here is what I did to get my server running with two SATA drives in a simple RAID0 configuration (note that this works best when drives are new or cleared to zero before configuring. Also, I used EXT3 to maintain compatibility with my disk image backup utility - you can use EXT4 if this is not an issue):
 

[SIZE=2][LIST=1]
[*]When partitioner starts - select 'Manual'.
[*]Select first hard drive (sda). Select 'Yes'.
[*]Select second hard drive (sdb). Select 'Yes'.
[*]Select FREE SPACE on sda. Select 'Create a new partition'. Enter "100 MB". Select 'Continue'.
[*]Select 'Primary'. Select 'Beginning'.
[*]Change 'Use as:' to 'EXT3 journaling file system'.
[*]Change 'Mount point:' to '/boot'.
[*]Set 'Bootable flag:' 'on'.
[*]Select 'Done setting up the partition'.
[*]Select FREE SPACE on sda. Select 'Create a new partition'. Accept default partition size. Select 'Continue'.
[*]Select 'Logical'.
[*]Change 'Use as:' to 'Physical volume for RAID'.
[*]Select 'Done setting up the partition'.
[*]Select FREE SPACE on sdb. Select 'Create a new partition'. Enter "100 MB". Select 'Continue'.
[*]Select 'Primary'. Select 'Beginning'.
[*]Change 'Use as:' to 'do not use the partiton'.
[*]Select 'Done setting up the partition'.
[*]Select FREE SPACE on sdb. Select 'Create a new partition'. Accept default partition size. Select 'Continue'.
[*]Select 'Logical'.
[*]Change 'Use as:' to 'Physical volume for RAID'.
[*]Select 'Done setting up the partition'.
[*]Select 'Configure software RAID'. Select 'Yes'.
[*]Select 'Create MD device'. Select 'RAID0'.
[*]Use spacebar to select the two defined RAID partitions.
[*]Select 'Continue'. Select 'Finish'.
[*]Select 'Configure the Logical Volume Manager'.
[*]Select 'Create volume group'. Enter "UBUV0". Select 'Continue'.
[*]Use spacebar to select '/dev/md0'. Select 'Continue'.
[*]Select 'Create logical volume'. Select 'UBUV0'. Enter "ROOT". Select 'Continue'.
[*]Subtract "3300" from displayed volume size and enter result. Select 'Continue'.
[*]Select 'Create logical volume'. Select 'UBUV0'. Enter "SWAP". Select 'Continue'.
[*]Accept '3300MB' and select 'Continue'. Select 'Finish'.
[*]Select the '#1' partition in 'LV ROOT'.
[*]Change 'Use as:' to 'EXT3 journaling file system'.
[*]Change 'Mount point:' to '/'.
[*]Select 'Done setting up the partiton'.
[*]Select the '#1' partition in 'LV SWAP'.
[*]Change 'Use as:' to 'swap area'.
[*]Select 'Done setting up the partiton'.
[*]Select 'Finish partitioning and write changes to disk' (you may need to scroll the display to see the option).
[*]Select 'Yes'.
[/LIST][/SIZE]Note that GRUB installs fine with this arrangement and Ubuntu provides the RAID0 functionality in software.

---

### Post by gilson585 on 2009-12-20
try installing grub1 after the install completes. also with 9.10 you can install onto fakeraid just fine using the livecd. instructions here [http://ubuntuforums.org/showthread.php?t=1360445](http://ubuntuforums.org/showthread.php?t=1360445)

---

