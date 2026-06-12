---
title: "Grub Rescue and Windows Bootloader"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by Da Janx on 2010-01-06
Alright so I thought it would be really cool to install Karmic Koala on an external drive. I read that it is very important to disconnect all internal drives beforehand, but I was unable to boot into the CD without the drive attached even tho CD-ROM has the highest boot priority. So I went ahead with installation and of course now without the external drive connected, GRUB tries to start and send me to GRUB rescue. The conclusion I was looking for was to just have XP on my laptop and boot into the USB HDD whenever I felt like it. I have tried certain GRUB commands like boot and root, but all I have been able to use with success is ls, which shows my internal drive and yadda yadda.  I have tried the XP repair, but it is asking for an admin password which my work has lost and was never given to me, ergo I am unable to run the fdisk /mbr so try and rescue the windows bootloader. I am sooo stuck!!!!!!

---

### Post by kansasnoob on 2010-01-06
Please connect the external drive and boot into Ubuntu. Then go to Terminal and post the output of:

```
sudo fdisk -l
```

We can restore the Windows MBR with an Ubuntu Live CD or from your Ubuntu external drive.

---

### Post by Da Janx on 2010-01-06
I am extremely thankful that someone responded in such a timely manner, so happy that I ended up registering for the forum. So I powered on the external drive and even set the priority in the bios to the secondary drive, and it still boots into grub rescue. Running the Live CD, I ran the command and got the response of both my hard drives, my internal being only 60GB and my external being 40GB as shown below.....

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe2a0e2a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7296    58605088+   7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4677    37567971   83  Linux
/dev/sdb2            4678        4863     1494045    5  Extended
/dev/sdb5            4678        4863     1494013+  82  Linux swap / Solaris

---

### Post by kansasnoob on 2010-01-06
> **Da Janx said:**
> I am extremely thankful that someone responded in such a timely manner, so happy that I ended up registering for the forum. So I powered on the external drive and even set the priority in the bios to the secondary drive, and it still boots into grub rescue. Running the Live CD, I ran the command and got the response of both my hard drives, my internal being only 60GB and my external being 40GB as shown below.....

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe2a0e2a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7296    58605088+   7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4677    37567971   83  Linux
/dev/sdb2            4678        4863     1494045    5  Extended
/dev/sdb5            4678        4863     1494013+  82  Linux swap / Solaris

So you're running the Live CD right now?

If so do this to try and fix the Windows MBR (please copy-n-paste commands):

```
sudo  apt-get install lilo
```

```
sudo lilo -M /dev/sda mbr
```

If you would like you can try to reboot now and see if Windows will boot, but I'd just go ahead and try to also fix grub on the external:

```
sudo mount /dev/sdb1 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo chroot /mnt
```

```
grub-install /dev/sdb
```

```
update-grub
```

```
exit
```

```
sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

I'd give that about a 90% chance of working to get Windows booting if the USB drive is unplugged, only about a 50% chance of working to boot Ubuntu with the USB drive plugged in.

You do know that the proper boot order must be set in BIOS huh?

Like mine is set to try and boot from CD first, USB second, and then hard drive.

---

### Post by Da Janx on 2010-01-06
Alright, so you are just like the best friend a guy can have right now! The story behind the story is that yes this is my work laptop, but my girl uses it for grad school, so she would not be happy if I lost everything. HA. So I had already been running the repair on the Windows partition, so after rebooting it jumped right back into finishing that, which is alright, I will just have to re install some things probably. But no files lost, so yizzzzahhhh! Since this is like two days in the making I am going to try to configure the External Drive tomorrow, need to take a break from pulling my hair out. I will update you with what happens with that. Thanks again man, this just proves that Ubuntu and other linux distributions are able to take its place with the other Operating Systems.

---

### Post by Da Janx on 2010-01-07
Update GRUB is giving me 
Unable to find partition list 

I have re installed Ubuntu on the drive, and made sure to disconnect internal drives. Set the priority and not able to boot into the external drive.

---

### Post by oldfred on 2010-01-07
Make sure everything is plugged in and run this script so we can see where everything is:

Boot Info Script 0.44 courtesy of forum member meierfra.
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Instructions:  louieb's
 [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
 
or as example if on desktop or  downloads directory from liveCD download:
sudo bash ~/Desktop/boot_info_script*.sh
or depending on where it downloaded
sudo bash ~/Downloads/boot_info_script*.sh
This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here, it can be big. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text, to make it easier to view.

---

