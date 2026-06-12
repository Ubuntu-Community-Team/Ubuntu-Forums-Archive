---
title: "Windows 10 on external drive; how to add to grub menu?"
date: 2016-07-30
forum: Installation &amp; Upgrades
---

### Post by Chris Calderon on 2016-07-30
I have Windows 10 installed on an external HDD, and I have Ubuntu installed on an internal M.2 SSD.

I can boot into the Windows drive if I go into my UEFI bios's boot menu, but for some reason the Ubuntu installer didn't add a menu option to grub.

this is what I have in /etc/grub.d/40_custom

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Windows 10" {
    insmod search_label
    search --label --set --no-floppy SYSTEM
    chainloader +1
}

```

And this is lsblk output

```
chris@chris-desktop:~$ lsblk
NAME                    MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda                       8:0    0   1.8T  0 disk
&#9500;&#9472;sda1                    8:1    0     4G  0 part  /media/chris/SYSTEM
&#9492;&#9472;sda2                    8:2    0   1.8T  0 part  /media/chris/windows
nvme0n1                 259:0    0   477G  0 disk
&#9500;&#9472;nvme0n1p1             259:1    0   512M  0 part  /boot/efi
&#9500;&#9472;nvme0n1p2             259:2    0   488M  0 part  /boot
&#9492;&#9472;nvme0n1p3             259:3    0   476G  0 part
  &#9492;&#9472;nvme0n1p3_crypt     252:0    0   476G  0 crypt
      &#9500;&#9472;ubuntu--vg-root   252:1    0 412.1G  0 lvm   /
          &#9492;&#9472;ubuntu--vg-swap_1 252:2    0  63.9G  0 lvm   [SWAP]

```

This is what I get after selecting the Windows 10 option from the grub menu

```

error: no such device: --no-floppy
error: invalid EFI file path.

Press any key to continue...

```

What do I need to change in my menuentry to help grub find the EFI file?

---

### Post by oldfred on 2016-07-30
I thought Windows would not boot from external drives, except perhaps eSATA drives.

Is Windows installed in UEFI or BIOS boot mode? You entry looks more like a BIOS type entry?

Grub only finds other installs in the same boot mode. As UEFI & BIOS are not compatible and you can only switch modes in UEFI boot menu, not after you have started booting.

---

### Post by Chris Calderon on 2016-07-30
I installed it using WintoUSB. I think it is in EFI mode, since the SYSTEM partition on the external drive contains EFI related boot stuff and it's filesystem is FAT32. Also, when I boot windows, the motherboard brand image stays up while the spinny circle windows loading thing is going, which should only happen in EFI mode.

---

### Post by yancek on 2016-07-30
Take a look at the tutorial below and compare it to what you did.  I used instructions from another site to do something similar and it also said it was necessary to format ntfs.

[http://www.moreapps.org/how-to-install-windows-7-8-and-8-1-on-external-hard-drive](http://www.moreapps.org/how-to-install-windows-7-8-and-8-1-on-external-hard-drive)

Also, I would suggest you take a look at the Ubuntu entries in grub.cfg.  The entry you posted for windows has nothing indicating which drive/partition to look for files and that is also why you get the error "no such device" error.

---

### Post by Chris Calderon on 2016-07-30
I did it! I changed my menuentry to this:

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Windows 10" {
    set root=(hd0,msdos1)
    chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}

---

### Post by dioguerra on 2017-06-06
Hello,

I am in the same situation. I have an external HDD With 3 instances of Windows in 5 partitions. I wouldnt mind to explicitly have to boot into the HDD but the last installed instance of Windows do not recognize the other ones. I would like to add all Windows partitions to the grub menu but i tried the last post and it didnt work.

This is my lsblk:

```
NAME                     MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda                        8:0    0 223,6G  0 disk  
&#9500;&#9472;sda1                     8:1    0   487M  0 part  /boot
&#9500;&#9472;sda2                     8:2    0     1K  0 part  
&#9492;&#9472;sda5                     8:5    0 223,1G  0 part  
  &#9492;&#9472;sdb5_crypt           252:0    0 223,1G  0 crypt 
    &#9500;&#9472;outcast--vg-root   252:1    0 215,2G  0 lvm   /
    &#9492;&#9472;outcast--vg-swap_1 252:2    0   7,9G  0 lvm   
      &#9492;&#9472;cryptswap1       252:3    0   7,9G  0 crypt [SWAP]
sdb                        8:16   0 931,5G  0 disk  
&#9500;&#9472;sdb1                     8:17   0  97,7G  0 part  
&#9500;&#9472;sdb2                     8:18   0 524,3G  0 part  
&#9500;&#9472;sdb3                     8:19   0  24,4G  0 part  
&#9500;&#9472;sdb4                     8:20   0     1K  0 part  
&#9492;&#9472;sdb5                     8:21   0  24,4G  0 part  
sr0                       11:0    1  1024M  0 rom  

```

My Windows partitions are in sdb1/sdb3/sdb5

And i tried to add to [COLOR=#000000]/etc/grub.d/40_custom this **(NOTE I CHANGED THE PATH TO BOOT EFI FILE)**:

[/COLOR]```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Windows 10" {
set root=(sdb1,msdos1)
chainloader /Boot/EFI/bootmgfw.efi
}

menuentry "Windows 10 - Altium" {
set root=(sdb3,msdos1)
chainloader /Boot/EFI/bootmgfw.efi
}


menuentry "Windows 10 - SolidWorks" {
set root=(sdb5,msdos1)
chainloader /Boot/EFI/bootmgfw.efi
}


```[COLOR=#000000]

Also, maybe it is important to say i am running a ubuntu minimal distro (LTS 16) with elementary-desktop graphical interface. Also, my external drives don't mount "by them selvs"
For me, the options don't even apear on grub menu, (only ubuntu and ubuntu safemode).

What am i doing wrong and can someone help me?
[/COLOR]

---

### Post by yancek on 2017-06-06
Your 'set root' lines are all wrong.  You need: (hd1, msdos1) and change the msdos in the others to the correct partition, 3 and 5.

Is the external a usb drive?  If so, how did you get them their as the windows installer won't do that in my experience.  

Your path after the chainloader entry is very different from the OP.  You need to mount the partition and get the actual path correctly.
Additionally the OP only had one instance of windows 10 installed whereas you have three on the same drive which is going to complicate matters.  You have the entries all pointing to the same file.  I'm not sure that is correct but I don't use EFI.  Are you able to boot any of the windows?  Have you tried the windows bcd bootloader,using bcdedit to create multiple entries for your different windows?  You might be better off at a windows forum to learn booting multiple windows instances EFI.  

Finally, did you install Ubuntu UEFI?  You can check that by mounting the EFI partition and looking for Ubuntu files.
What's on your internal hard drive?

---

### Post by dioguerra on 2017-06-09
I installed it with WintoUSB, the same tool referenced above....

I managed to access the latest installed Windows after entering in command line:

```
sudo update-grub.
```

After this my system can recognise all the windows but i can only boot to one of them (the last one installed)

You say i need to mount the partition, but can i even do that on bootloader? I mean, this version i have does not mount them by default and with the update-grub i can boot to windows without any mounting required.
About the multiple windows (as i understand) the WinToUSB copies the installed Windows onto the externall HD itself and adds a boot folder. You can choose the boot partition and the windows partition (which i choose the same for all the individual Windows - like a pair boot, windows)

I can try to change the msdos1 to msdosX together with the sdbX to see if it works.

[B]This is my Partition Formating after i mounted them myself (as default)

[/B]```
df -T
Sist.fichs                   Tipo     1K-blocos      Ocup    Livres Uso% Montado em
udev                         devtmpfs   3991876         0   3991876   0% /dev
tmpfs                        tmpfs       803328      9724    793604   2% /run
/dev/mapper/outcast--vg-root ext4     221968044 163287536  47382104  78% /
tmpfs                        tmpfs      4016628    282224   3734404   8% /dev/shm
tmpfs                        tmpfs         5120         4      5116   1% /run/lock
tmpfs                        tmpfs      4016628         0   4016628   0% /sys/fs/cgroup
/dev/sda1                    ext2        482922    126351    331637  28% /boot
tmpfs                        tmpfs       803328        56    803272   1% /run/user/1000
/home/me/.Private        ecryptfs 221968044 163287536  47382104  78% /home/me
/dev/sdb2                    fuseblk  549754880  17628032 532126848   4% /mnt/part
/dev/sdb1                    fuseblk  102399996  27298088  75101908  27% /mnt/Windows
/dev/sdb3                    fuseblk   25599996  18751976   6848020  74% /mnt/Altium
/dev/sdb5                    fuseblk   25599996     67852  25532144   1% /mnt/SolidWorks
```

---

