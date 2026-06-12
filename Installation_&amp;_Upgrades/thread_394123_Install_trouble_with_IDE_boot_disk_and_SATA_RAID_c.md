---
title: "Install trouble with IDE boot disk and SATA RAID card"
date: 2007-03-26
forum: Installation &amp; Upgrades
---

### Post by blackmesaU on 2007-03-26
Ubuntu installs fine, but after reboot will fail to boot, with the message boot failed. A bit of background, i have a SATA raid card with ( at the moment ) one SATA drive attached, not configured or partitioned. I can see the disk in the card BIOS. If i disconnect the drive the system boots fine. 

I can only assume the loader is trying to boot from the SATA disk. All i did during the install is partition the IDE drive, tried doing auto partition and manual partition.

Any ideas? Its driving me mad. I am very experienced in UNIX and windows and Linux, but not SATA RAID cards.

---

### Post by blackmesaU on 2007-03-27
surely someone can give me a few pointers? this must be something someone here has come across before.

---

### Post by blackmesaU on 2007-03-29
This is a really friendly and informative forum. Cheers. :popcorn:

---

### Post by yabbadabbadont on 2007-03-29
Posts like that practically guarantee that no one will try to help you.  :p  :)

Post your /boot/grub/menu.lst and /boot/grub/device.map files.

---

### Post by blackmesaU on 2007-03-29
Apologies, just frustration rearing its head. After 3 days i was losing the will to live waiting for any answer. Thanks for your reply and when i get home i will post the details.

Thanks again.

---

### Post by blackmesaU on 2007-03-29
menu.lst

root (hd0,0)

Do you want all of it? as i would have to type it as i have no access to the box over the network yet.

device.map

(hd0)  /dev/hda
(hd1)  /dev/sda


Hope that helps you and me....

:)

---

### Post by bpsg119 on 2007-03-31
I'm of no help here except to breath some life into the thread possibly. I just installed a new sil3114 sata card with two new sata drives into my edgy install(desktop) which is on an ide drive. I appear to have the exact same symptoms as the blackmesaU.

The card bios detects the new drives, but just as grub us about to load the computer reboots itself, endlessly until I turn it off. If sata cables are removed, the boot is just fine. I also popped in the edgy install cd and at the prompt told it to boot off the first hard drive and everything went fine. I was able to login and see all drives (ide and sata). 

I too, think that ubuntu is trying to boot off the sata drives first, and I would hope there is a simple fix so that I do not need to boot using the cd each time I restart the computer.

I will post device.map when I get a chance.

Any help is appreciated!! thanks.

Bryan

---

### Post by bpsg119 on 2007-03-31
Hope this helps some. Here is a portion of my menu.lst

title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.17-11-generic
boot

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet
boot

-----------------------------
cat /boot/grub/device.map 
(hd0)   /dev/hda
(hd1)   /dev/hdc
(hd2)   /dev/hdd

---

### Post by iceman_ii on 2007-04-02
Not sure if this is any help here, but I am in the process of building a new machine, with a 3ware raid card... I had windows running on the raid, and installed edgy on a stand alone drive NOT on the raid card, and grub installed fine... it seems that grub likes to install on the FIRST drive, and because it recognizes the SATA drives before raid controller drives, GRUB loaded on the stand alone drive.... even though I had edgy loaded on the drive, it still did me no good with the raid card, because the drivers were comming out in the feisty kernel...

Last week a beta version of feisty came out, and wonder of wonders, the darn thing installed fine on the raid!  ANd grub, still being on the stand alone, mother board mounted drive recognized not only fiesty but edgey as well - everythings good, right... WRONG!

I rebuilt the array using the heretofore standalone drive as part of the array (5 drive raid 5 - woowhoo), after all feisty not only sees the array, but it installed fine... well, this is what I thought, unfortunately, this was not the case....

After installing a very SMALL partition of winXP (a necessary evil) I installed the beta version of feisty... and that is when everything started to go bad... it went down horribly when grub supposedly loaded, but it wouldn't reboot... when I tried to use the repair function of the disk, it got all kinds of pissy...  The only conclusion I can come to after reading about your problem, and living through mine, is that for some reason or other, GRUB does NOT like to load on the MBR of a raid array...  I think I will be attaching a very small drive to my motherboards IDE bus, just for a stable place to put a MBR... at least I know that will work.

---

### Post by bpsg119 on 2007-04-02
iceman - thanks for the reply, I actually found it informative and interesting, but I'm not sure if it'll get me anywhere. I've got edgy installed on a drive connected to one of the MB IDE channels. Everything was fine, and when I installed the PCI sata raid card with two drives, the card bios loaded at boot and recognized the drives. The post continued normally but just before GRUB would load, or as it was trying to load the computer would reboot itself. 

I don't know for certain why its rebooting, but it has everything to do with the new sata card and especially the hard drives hooked up to it. When disconnected the computer boots fine. So I surmise that the computer, GRUB is looking to the SATA drives to boot and not finding anything.

Currently, like I said having the edgy cd in the drive allows me to boot properly, but is there a way to fix it so that I don't need the cd?

---

### Post by iceman_ii on 2007-04-03
The more I think about it, I think I will wait to install the final version of feisty, rather than the beta.  You may want to bootstrap up to feisty (I think I am using the term correctly - still kind of new) 

I am holding out till the end of the month when it is to be released because it has the 2.6.20 kernel which I KNOW has drivers for my 3ware card that 2.6.18 doesn't... and a new release with the latest kernel may fix your problem as well.

Just my $.02

---

### Post by bpsg119 on 2007-04-03
The tradeoff for using it as is...which works, but has this issue vs. trying feisty beta which may cause other problems just isn't worth time I don't have at the moment. I, like you will probably wait until it is released in a more final form before upgrading.

Thanks for the reply.

---

### Post by jamesm on 2007-04-10
Similar issue -- different config, same ending issue.

I am putting together a back up server for my work.  Config is this:

2 160 GB SATA cards using Motherboard to control these two cards (made for an easier install and was not really interested in setting up a RAID for my boot directory etc..etc..


Anyway..I followed this walkthrough provided by 3ware (located in the .zip file provided with their drivers) to install drivers for the 9xxxx card and it worked flawlessly.  LOOK FOR MY ADDITIONS USING USB FLOPPY DISK.



1.  Copy the module "3w-9xxx.ko" to a floppy disk 

    Copy "initrd.img-2.6.17-10-generic" to a cd-rw



2.  Boot off Ubuntu-amd64 cd, exit to console (ALT+F2) when Ubuntu found no hard drive


****NOTE:  Since Ubuntu did find my 2 sata drives plugged into the MB controller, I stopped the partition editor and proceeded to the console.  (ALT+F2)
I then plugged in the USB Floppy drive.****

3.  uname -a (verify that your kernel is 2.6.17-10-generic)



4.  mkdir /mnt2 ; mount -t vfat /dev/fd0 /mnt2
****NOTE:  The floppy in a USB environment does not mount as "fd0" it usually takes the next available  SCSI  dev line.  IE:  /dev/sdc0 ****



5.  cp /mnt2/3w-9xxx.ko /lib/modules/2.6.17-10-generic/kernel/drivers/scsi



6.  umount /mnt2



7.  Press ALT+F1 to return to Unbuntu installer screen and select "3w-9xxx" to load 3ware module





Proceed to installation




****STEP 8 IS VERY IMPORTANT -- DO NOT LET YOUR CO-WORKERS HELP YOU IF THEY HAVE NOT READ THIS WALKTHROUGH---HAHAH****

8.  DO NOT REBOOT after Ubuntu is done. Exit to console again (ALT+F2)



Check your kernel version



9.  ls -l /target/boot   (should be 2.6.17-10-generic)



10.  mount /dev/hdX /mnt2



(hdX is your cdrom drive) 



10.  cp /mnt2/initrd.img-2.6.17-10-generic  /target/boot/initrd.img-2.6.17-10-generic



11.  umount /mnt2


From here everything worked fine on the reboot, full access to teh 3 TB on the controller, all of my partitions that I setup during install were available, etc..etc..

After I did my upgrades, I rebooted and found the, I no longer have access to those drives.  

I am at the point now, where recompiling the 3ware driver source is the fix, but I think I am missing some files from my 3ware driver pack.

The steps are as follows according to 3ware walkthrough:

Instructions for recompiling 3ware driver source





1.  sudo -s (must login as root)
GOT IT!

2.  apt-get install build-essential ; apt-get install libncurses5 ; apt-get install libncurses5-dev

GOT IT!
3.  apt-get install linux-headers-<your-new-kernel>
ALREADY INSTALLED! 

4.  cd /usr/src ; ln -s  linux-headers-<your-new-kernel> linux

GOT IT!
5.  tar zxvf 3w* ; make -f Makefile (recompile 3ware source)
Hmmmm...only  3 files in the zip file that I downloaded from 3ware -- a .txt walkthrough,  the .ko driver, and  the generic  header file.   Did I miss a package somewhere?

STUMPED AT THIS POINT! -- Can not continue.
6.  cp 3w-9xxx.ko /lib/modules/<your-new-kernel>/kernel/drivers/scsi

7.  rm /boot/initrd.img-<your-new-kernel>

8.  update-initramfs -c -k <your-new-kernel>

In the interim I thought that I would be able to just boot the -10-generic kernel and continue on, but obviously some other package was updated at the same time time that has prevented this.

If anyone can shed some light on reverting to the .10 specs so I can continue to work, that would be fantastic, and I will try to help with this other issue as much as possible.

Here is my /etc/fstab  /boot/grub/menu.lst and /boot/grub/device.map
##############################################
/etc/fstab
Any partition that is on the RAID array does not load now, and is marked as unclean.  
fdisk -l does not list them either.




proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=03e69848-d141-4544-a0dc-8de30bce800c /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=d1112cdf-2ce5-472a-b180-2f345ef05547 /boot           ext3    defaults        0       2
# /dev/sdd7
UUID=8af4b3ce-fdcf-4c4d-8424-80eaf245e090 /dhead_bak      ext3    defaults        0       2
# /dev/sdd9
UUID=8117ff3b-71bc-4854-8e73-330b9bdd69e4 /hipaa_archives ext3    defaults        0       2
# /dev/sdb1
UUID=b3404624-aeaa-4f8d-bc3e-6dfb43f9649f /home           ext3    defaults        0       2
# /dev/sdb2
UUID=a7829b0e-3be1-47ec-b916-bed98b88f419 /log_bak        ext3    defaults        0       2
# /dev/sdd1

#UUID=cb676b21-438b-4725-b5b5-c18d99f766e3
/dev/sdd1                                /mc1nk_bak      ext3    defaults        0       2
# /dev/sdd8
UUID=a1e97e00-bce9-4140-8ac0-4f1d80123a7e /mcgis_bak      ext3    defaults        0       2
# /dev/sdd2
UUID=169f5047-afa4-4a2b-abef-a51b5ccfa07b /mcso_bak       ext3    defaults        0       2
# /dev/sdd5
UUID=9b0146c4-a889-434c-bd5a-b6d6ddd43b06 /mctech_bak     ext3    defaults        0       2
# /dev/sdd4
UUID=9a14f6cc-f970-43f1-9672-5d0b1b5d9474 /mtj_bak        ext3    defaults        0       2
# /dev/sdd3
UUID=c56945f8-c5e5-41e5-b58c-1bea1c188be4 /sc_bak         ext3    defaults        0       2
# /dev/sdd6
UUID=cdf1a216-88cc-41f7-b935-79a2aa1b58bc /snapuser_bak   ext3    defaults        0       2
# /dev/sda3
UUID=ea8cff95-d82f-43f0-8f8f-0b61d65c5e8d /tmp_server_conf ext3    defaults        0       2
# /dev/sda4
UUID=321469a8-a073-42e9-8255-b72b1f231c7f none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0



/boot/grub/menu.lst -- I manually edited the file.  Here is uname -r output to show .10-generic is loaded

jamesm@xxxxxxx:~$ uname -r
2.6.17-10-generic

#title          Ubuntu, kernel 2.6.17-11-generic
#root           (hd0,0)
#kernel         /vmlinuz-2.6.17-11-generic root=/dev/sda2 ro quiet splash
#initrd         /initrd.img-2.6.17-11-generic
#quiet
#boot

#title          Ubuntu, kernel 2.6.17-11-generic (recovery mode)
#root           (hd0,0)
#kernel         /vmlinuz-2.6.17-11-generic root=/dev/sda2 ro single
#initrd         /initrd.img-2.6.17-11-generic
#boot

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.17-10-generic root=/dev/sda2 ro quiet splash
initrd          /initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.17-10-generic root=/dev/sda2 ro single
initrd          /initrd.img-2.6.17-10-generic
boot


device.map
(hd0)   /dev/sda -- 1st sata
(hd1)   /dev/sdb -- 2nd sata
(hd2)   /dev/sdd -- 3TB RAID ARRAY




Any insight on this issue would be greatly appreciated.  I am guessing its a recompile of the drivers for the .11 kernel, and I am now wondering if it HAD to be done before the reboot after the updates.  (Like the actual install of the drivers)
If that is the case, and I feel like going through this install again, I will document it here, but I hope someone has a better answer before that time.  I will start the reinstall at around 2:00pm today MST.



Thanks
James

---

### Post by jamesm on 2007-04-10
bump

---

