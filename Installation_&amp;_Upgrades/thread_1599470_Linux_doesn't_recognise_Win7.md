---
title: "Linux doesn't recognise Win7"
date: 2010-10-17
forum: Installation &amp; Upgrades
---

### Post by siddy123 on 2010-10-17
Hi, i'm new to this forum so pardon me if this problem has risen somewhere else.
 
i have a Ubuntu version 9.10 disk which i ordered ages ago, and when i get to the disk partioner. The installer only see a blank disk... i have 100 GB worth of Win7 on my desktop and the installer just see a blank disk, i want to be able to dual boot the two together... but i seem stuck. any help

my main system specs original when bought and current

[U]Original

[/U]intel pentium D 3.4 GHz
Nvidia Geforce 7300 SE
500 HDD
1 GB 800MHz DDR2 ram
Windows XP Media edition (or something like that)

[U]Current

[/U]Intel pentium D 3,4 GHz
Nvidia Geforce 220 GT
500 HDD
3 GB Ram
Windows 7 (home premium) 32-bit

---

### Post by spcwingo on 2010-10-17
Maybe the partition was not unmounted cleanly.  Boot back to Win 7 and resize the partition from there.  If you don't know how to do that, have a look here:

[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/]("http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/")

Although this guide is for Vista, the procedure is exactly the same.

---

### Post by josephpmh on 2010-10-17
You can also open the CD from within W7, and find the wubi.exe.  That will run a dual boot install from Windows.

Welcome aboard!  I'm sure that you'll be loving linux Ubuntu in no time.

---

### Post by efflandt on 2010-10-17
Boot to a live system on the CD and from a terminal see what **sudo fdisk -l** (small L) shows.  Paste the output here, highlight it, and click the **#** in the message window to put code tags around it so it maintains its spacing between columns (easier to read).

If it show type 42 partition(s) that is a Windows proprietary type of dynamic disk volume that Linux either cannot handle or may not trust itself to handle.

BTW the GT 220 works great with nvidia proprietary drivers in 10.04 and 10.10, but I did not get this computer until after 9.10, so I have not tried it in that.

---

### Post by siddy123 on 2010-10-18
Hi, i partitioned my hard drive to make 100 GB free space and finally the installer recognized win7. so i selected "use largest continuous amount of space" and  it got to 94% installation but is now saying:

"The "grub" package failed to install into /target/. without the GRUB boot loader, the installed system will not boot."

Helpppppp D=, was there something i was meant to of done?

---

### Post by siddy123 on 2010-10-18
Well i've now sent all my desktop work to my laptop and wiped my desktops hard drive through BIOS. 
 
when i ran **Sudo fdisk -l** i got this, pretty obvious though since i've just wiped my disk...
 
> ubuntu@ubuntu:~$ sudo fdisk -l
 
disk /dev/sda:250.1 GB, 250059350016 bytes
255 heads, 63 sectors/ tracks, 30401 cylinders
units = cylinders of 16065 * 512 = 8225280 bytes
disk identifier: 0x00000000
 
disk /dev/sda doesn't contain a valid partition table
 
disk /dev/sda:250.1 GB, 250059350016 bytes
255 heads, 63 sectors/ tracks, 30401 cylinders
units = cylinders of 16065 * 512 = 8225280 bytes
disk identifier: 0x00000000
 
disk /dev/sda doesn't contain a valid partition table 
 
i tried installing again, and it just keeps getting to 94% and saying 
 
> "The "grub" package failed to install into /target/. without the GRUB boot loader, the installed system will not boot."


 
really need help, i just don't get what could be interfering with the installation of 9.10 with nothing in the way of it. i want to make my desktop a primary linux machine but linix doesn't want that D=
 
thank you

---

### Post by oldfred on 2010-10-18
Some BIOS have a setting preventing writing to the MBR to prevent issues with virus. Check BIOS settings.

Also was this drive ever in a RAID configuration?

---

### Post by siddy123 on 2010-10-18
It's always in RAID0 as far as i know

---

### Post by siddy123 on 2010-10-18
also how would i check my bios for these settings?
 
my bios only says 
 
1. create RAID volume
2. Delete RAID volume
3. Reset Disks to Non- RAID
4. Exit

---

### Post by oldfred on 2010-10-18
The question on raid is becuase raid settings get saved on the drive and interfere with the install. If you have raid and a second drive you have not mentioned then you need to use the alternative (text) installer. I think the newer desktop versions may work with raid.

---

### Post by siddy123 on 2010-10-19
i have (2x250GB) hard drives, where would i find this "Alternative (text) installer"?

---

### Post by oldfred on 2010-10-19
Also has links to alternative install -text mode & not liveCD, CD & USB install instructions
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

Alternative install is not a liveCD. You should also have a liveCD of the version just in case you need to do repairs. Or any of the linux based rescue liveCD. I used to use a stack of CDs as I wanted several, but now I just write one CD and put many updated ISOs on a grub2 bootable USB flash drive.

---

### Post by ronparent on 2010-10-19
Looking through this thread I see some major problems that may have been overlooked. Foremost is that you apparently want to install along side Win 7. Win 7 often doesn't like other OS adjusting its partitons, especially the one Win 7 is installed to. The safer route is to shrink a Win 7 partition with the Win 7 disk manager. In this case, since win 7 already recognizes the raid it should be no problem.

The second is that a pre-installed win 7 machine probably already has two, and in some cases three partitions already. Which means that you will have to use the 9.10 live cd to create an extended partition to install to. Since the 9.10 you have does not see the raid partitions that you have to get to the bottom of that before you proceed. Important because in a raid0 you could easily wipe out the windows install by doing anything to what appears to be totally unallocated space on one disk of the raid set. 

So you should boot to your 9.10 live cd and open a terminal. In that terminal enter:
> sudo dmraid -ay
dmraid should automatically detect the raid meta data already on the disk and give you a status report. Importantly, if the raid was not activated with the boot of the live cd, you should now be able to see in in gparted. Post the output to verify that this is working. Once the raid is recognized by gparted you can create an unformatted extended partition. Once you have the extended unallocated space to install to you should be abe to proceed and instal to the larges unallocated space on the raid drive. You should read the following before you proceed: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

If you should choose to try installing a later release of Ubuntu, I would recommend 10.10 since the desktop version is installable without workarounds. I do recommend that during the partitioning step that the manual option be selected. 

If you are unsure of yourself or find the requirement too bewildering I would not recommend trying to install to a fakeraid. If you want to try people on this forum will be happy to pitch in and answer your question. Keep posting.

---

### Post by siddy123 on 2010-10-19
ok, i shrinked my HDD down, so an estimated 250GB is win7's and an estimated 250GB is unallocated, 

i ran **sudo dmraid -ay** and here are the results 
> RAID SET "isw_bhebjiefbe_Volume0" is already active
RAID SET "isw_bhebjiefbe_Volume01" is already active
RAID SET "isw_bhebjiefbe_Volume02" is already active

so what do i have to do next? i didn't exactly understand the next bit or the link given :(

oh yh, and i can't install version 10, the cd distributor says i've ordered too many CD's (version 8. something and version 9.10 ( both still do not work :( ))

i don't have any CD's to burn an ISO onto + no money to buy CD's (i'm a student y'see)

so i have two questions,

a) **what should i do next?** as mentioned above
b) i have transferred all my files from my desktop to my laptop so really i have no cause for windows to be on my desktop anymore, **would it be alot easier to just wipe my hard drive and try installing 9.10 as the primary OS only?** (even though i tried that and that also ran into problems)

i do appreciate your help a lot, this problem is really getting on my nerves now, the fact i'm running into brick walls with every suggestion.

i tried the USB option earlier... and my desktop although BIOS recognizes it in it's options... gets to the loading bit and has a ponder for a few seconds as my 1st and 2nd boot options are "removable" and 3rd is "CD-ROM" it just skips past my USB stick with the installer on it...

---

### Post by oldfred on 2010-10-19
On my desktop the flash drive is not recognized as part of the USB bootable devices but as another hard drive. Look under hard drive boot choices.

Is there some reason you have RAID? I have never been a fan of RAID on desktops as RAID is for improved performance for serving web pages or databases for multiple users. RAID will not let you type faster nor download quicker which are the two main time uses on a desktop. RAID also has nothing to do with backup as everything deleted is deleted in both sets. And the fakeraid versions often create more issues than they supposedly help.

---

### Post by siddy123 on 2010-10-19
theres no reason why i have RAID... it's just how it's set.

---

### Post by siddy123 on 2010-10-20
Nope, unfortunatly running it through USB as hard drive doesn't work either =[

any other options?

---

### Post by oldfred on 2010-10-20
Break down and buy some CDs.

If you are willing to totally reinstall everything and have good backups of all your data then you can break the RAID. You will end up with two usable 250GB HD instead of only 250GB total. Do not know enough about doing that to really help. 

Also for installing on fakeraid (motherboard raid), this might help you:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) remove dmraid

If you remove RAID you have to remove metadata on the drives:
Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discussion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

### Post by ronparent on 2010-10-20
oldfred is right. Can you do it without throwing away Win 7 - in other words, do you have the distribution dvd for it? The loss of read write speeds by breaking the raid 0 won't be significant unless you are reading/writing very large files.

---

### Post by siddy123 on 2010-10-20
I have the Windows installation CD and Ubuntu 9.10 CD. 

so if anything does go seriously wrong with windows, i can repair or reinstall.

---

### Post by siddy123 on 2010-10-20
WOAH, FINALLY... i broke the raid settings and separated my 2 hard drives into two separate physical disk and installed windows on 1 and ubuntu on the other.

now, as a new ubuntu user i have three questions

1) when loading through BIOS, it's gone straight to linux. what do i do when i want the bios to ask me which OS i want to boot into?

2) does linux have automatic updates like windows 7? does it download drivers, updates such and such. i do i have to manually install all of my drivers

3) can i upgrade to version 10 from 9, or do i have to download the ISO and put it onto a disc then wipe 9.10 and install 10?

thank you so much for all your help, i would never of guessed what to do D=

---

### Post by siddy123 on 2010-10-20
actually don't worry about 2 and 3, i think i just killed 2 birds with one stone when i found "update manager" :L

Thank you once again

---

### Post by oldfred on 2010-10-20
When you installed, grub probably installed to sda where you have windows. But maybe grub did not see the windows install?

Try this from terminal:
```

sudo update-grub
```

Since you now have two drives, I suggest you install the windows boot loader to the windows drive in case you ever want or need to directly boot windows. Install grub to the Ubuntu drive and set BIOS to boot the Ubuntu drive.

Run this so we can see what is where:
```

sudo fdisk -l
```

---

### Post by siddy123 on 2010-10-20
when i installed it, i installed it to a partition that was empty,  the other partition was full up with a NTFS (Windows) so i used the  empty one, 

ran **sudo update-grub** and here's the results:

> user@user-desktop:~$ sudo update-grub
[sudo] password for user: 
head: cannot open `/boot/grub/video.lst' for reading: No such file or directory
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
doneran [B]sudo fdisk -1 :
[/B]
> user@user-desktop:~$ sudo fdisk -1
fdisk: invalid option -- '1'

Usage:
 fdisk [options] <disk>    change partition table
 fdisk [options] -l <disk> list partition table(s)
 fdisk -s <partition>      give partition size(s) in blocks

Options:
 -b <size>                 sector size (512, 1024, 2048 or 4096)
 -c                        switch off DOS-compatible mode
 -h                        print help
 -u <size>                 give sizes in sectors instead of cylinders
 -v                        print version
 -C <number>               specify the number of cylinders
 -H <number>               specify the number of heads
 -S <number>               specify the number of sectors per track


---

### Post by spcwingo on 2010-10-20
> **siddy123 said:**
> ran sudo fdisk -1

It didn't work because it's a lower-case "L", not a "one".

---

### Post by siddy123 on 2010-10-20
ah, silly me. i should get my eyes checked... sorry

> user@user-desktop:~$ sudo fdisk -l
[sudo] password for user: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xeb346cfb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29367   235890396   83  Linux
/dev/sda2           29368       30401     8305605    5  Extended
/dev/sda5           29368       30401     8305573+  82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9b0c7d3b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30402   244196352    7  HPFS/NTFS


---

### Post by oldfred on 2010-10-20
If grub's osprober is not finding windows there must be a problem. The boot info script should show use what may be wrong. Did windows boot ok before you installed Ubuntu? You show windows in sdb, was it sdb when you installed it or did you switch drives? Windows install should have put boot flag on sdb1. If you want to repair or directly boot windows sdb1 will have to have a boot flag. You can use gparted or Disk Utility to set boot flag. Grub does not use a boot flag, just windows.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by siddy123 on 2010-10-21
i sorted it out, i just installed windows and linux, for some reason windows used up an entire disk then puts its boot loader onto the second disk.... when installing linux it detected windows but not its boot loader so i thought the other disc was empty. and it deleted boot loader. 
 
i resolved it by simply wiping, and reinstalling more carefully.
 
i would like to thank all contributers to this =D
 
hopefully there shouldn't be many problems for the forseeable future

---

