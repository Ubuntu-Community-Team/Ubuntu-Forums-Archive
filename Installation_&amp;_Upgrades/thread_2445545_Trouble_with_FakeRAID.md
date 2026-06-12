---
title: "Trouble with FakeRAID"
date: 2020-06-15
forum: Installation &amp; Upgrades
---

### Post by dpmccormick81 on 2020-06-15
I've had just about all I can stand of seeing news reports about Microsoft breaking Windows. They don't listen to their insiders, and they continually push their bugged updates when a little attention to their insiders would have prevented the problem. So, I'm working my way toward getting away from Windows, and installed Ubuntu 20.04 LTS on a new partition on my system drive. So far so good, but I'm having a problem with my FakeRAID array. 

Ubuntu can see the individual drives of the FakeRAID array, but isn't accessing them as a RAID 0 array. All of my drives which are not part of the array, including the 250GB system drive and the 2TB SATA, are working fine. But Ubuntu won't read the array, and wants to treat them as separate drives. If I allow this, I will lose all the information on the array. 

I have the space on the archive to back up the data on the array, and switch the array over to Ubuntu's software RAID. But if I do this, Windows will lose access to the array. I do want both Ubuntu and Windows to be able to access the array in the meantime, and my work at home job does require me to have a windows installation to work from. 

Again, I would like to clarify here: Windows and Ubuntu installation are NOT ON THE ARRAY. I do not need to boot from the array, and the system drive is not going to be involved in any RAID, and neither is the 2TB Archive. The array is for short to medium term storage of unimportant data, and if I lose the array I'm not going to be too broken up over it, as long as it doesn't take either of the important drives with it. 

Windows is reading the array normally, but Ubuntu is treating the array as separate individual disks. How do I get Ubuntu to read the FakeRaid array without breaking Windows's ability to read the array as well?

---

### Post by ActionParsnip on 2020-06-16
Are you trying to setup a dual boot system or do you want Ubuntu to be the only OS on the system?

---

### Post by dpmccormick81 on 2020-06-16
Right now I'm trying to set up dual boot because, ***as I said***, my work at home job requires me to have a windows installation to work from. Maybe one day down the road I'll be able to get rid of Windows completely, For now, I need it dual booting. 

I thought I explained in my post what I'm trying to do and why. Can we please get to the how?

---

### Post by dpmccormick81 on 2020-06-16
While I've been waiting for any kind of help or useful reply, I've been continuing to do research on my own. While searching for appropriate drivers and failing to find any for any Linux distros on my chipset (x570) from AMD's website, I found this: [https://github.com/thopiekar/rcraid-dkms](https://github.com/thopiekar/rcraid-dkms)

Following the directions given by the page, I ran the commands to get and install the driver package. Now I'm stuck on the second part of the instructions in Switching to RAID mode. I can't get write access to etc/default/grub to append the command. Can anyone help with that part at least?

---

### Post by tea for one on 2020-06-16
> **dpmccormick81 said:**
> While I've been waiting for any kind of help or useful reply, I've been continuing to do research on my own. While searching for appropriate drivers and failing to find any for any Linux distros on my chipset (x570) from AMD's website, I found this: [https://github.com/thopiekar/rcraid-dkms](https://github.com/thopiekar/rcraid-dkms)

Following the directions given by the page, I ran the commands to get and install the driver package. Now I'm stuck on the second part of the instructions in Switching to RAID mode. I can't get write access to etc/default/grub to append the command. Can anyone help with that part at least?

In order to edit the grub file, you will need admin privileges.

```
sudo nano /etc/default/grub
```

You will be prompted for your user password and when you enter the password, there will be no echo, simply hit the enter key.

---

### Post by dpmccormick81 on 2020-06-16
Ok, thank you. This has solved the issue. 

Further steps taken: 
append the appropriate command to etc/default/grub
run sudo update-grub
reboot
run sudo fdisk -l
found the array listed!
```
Disk /dev/sdc: 893.24 GiB, 959098912768 bytes, 1873240064 sectors
Disk model: Array 02        
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0794f992

Device     Boot Start        End    Sectors   Size Id Type
/dev/sdc1        2048 1873235967 1873233920 893.2G  7 HPFS/NTFS/exFAT

```
run sudo mkdir /media/1TBRaid
run sudo mount /dev/sdc1 /media/1TBRaid

I now have access to my files on the Raid.

EDIT: 

Ok, so it's a partial solution. I now have access to the files on the RAID, but I've lost access to the files on the 2TB Archive drive that's not on any RAID. When I take the line out of etc/default/grub, I get access to my Archive, but I lose access to the RAID. The system drive is not on a RAID, but doesn't seem to have any problem either way. System drive is a 250GB Kingston M.2. The Archive is a 2TB Seagate Barracuda SATA. The RAID is made of a Sandisk Ultra II 480GB SSD, and a Samsung SSD 850 - 500GB. The RAID drives show up separately in fdisk -l when the necessary line is removed from etc/default/grub, but appear properly as the RAID drive when the line is restored. I don't know why the Archive is disappearing, yet still shows up in fdisk -l when the line is in place. Trying to mount the drive when the line is in place yields an error that the special device could not be found. 

Is there any solution for being able to simultaneously access both drives?

---

### Post by dpmccormick81 on 2020-06-18
I suppose this is probably a problem with the driver itself, given the inconsistencies I'm seeing in the information about the archive drive given the line in etc/default/grub versus without it. I guess it's something I'll have to  either get the guy with the driver to fix, or get the source and fix it myself. The latter I completely lack the skills for; I wouldn't even know where to start. So I'm at the mercy of the guy with the repo to fix it for me.

Thanks for what little help has been provided here. Given what I'd been reading, I figured that there was little support for what I'm trying to do, but I'd thought I'd at least get a helping hand or a point in the right direction if I posted here. What I've managed to accomplish so far has been, for the most part, my own research, and lucking out finding a semi-working driver. Looks like, for now, there is -NO- solution for using mixed RAID/Non-RAID drives with a dual-boot system Ubuntu and Windows. Windows can do it, Ubuntu can't.

I'm probably going to get rid of my array anyway and just switch to a 2TB M.2 NVMe drive to use the other M.2 slot on my board. I'm not doing or planning a dual-GPU setup anyway, so I've still got the PCIe headroom for it. Format the RAID drives and sell them to some computer shop. No more RAID. Problem solved.

---

