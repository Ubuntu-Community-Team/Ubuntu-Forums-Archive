---
title: "GRUB and FullDiskEncryption"
date: 2013-03-10
forum: Installation &amp; Upgrades
---

### Post by lorenz90 on 2013-03-10
Hello, I am Lorenzo. I am a new forum user, but I am not new to the world of Ubuntu: I have been using it for years. I have always been able to solve my issues discussing with the friends of the Italian Ubuntu forum, but during the last week I installed Ubuntu 12.10 using the Full Disk Encryption and I encountered a problem that we was not able to solve. So I registered to this international forum, hoping to find some Ubuntu-Pro who would like to assist me.

**Here is the problem:**
I have to use Ubuntu in a computer which is used also by my parents, and they does not permit me to install GRUB, since it is loaded every time they start the PC. So I decided to install Ubuntu without any boot loader, and then to install GRUB on a USB flash drive. My idea was to simply boot from the USB and to load Ubuntu whenever I wanted to use it. :)
I installed Ubuntu manually using FDE (without any boot loader), and then, from the live CD, I created a bootable USB flash drive through the procedure that is used for creating USB sticks for installing ubuntu (e.g. for computers without CD drive). When I boot from the USB GRUB starts, but I do not see any partition and I am not able to run Ubuntu (the only possibility is to start the live version of Ubuntu contained in the USB device). 

[SIZE=2][FONT=arial]**The partition scheme of my PC:**
[COLOR=#101010]sda1: windows 7[/COLOR]
[COLOR=#101010]sdb1: boot partition created during the manual installation of Ubuntu (300MB)[/COLOR]
[COLOR=#101010]sdb2: NTFS used for data storage[/COLOR]
[COLOR=#101010]sdb3: Ubuntu installed using FullDiskEncryption

I think that I should indicate to GRUB the location of the partition containing Ubuntu, but I don't know how, and I don't even know which is the correct partition (boot or the one whith FDE).
Every advice is welcomed, thank you in advance.
 
Lorenzo[/COLOR][/FONT][/SIZE]

---

### Post by oldfred on 2013-03-10
If you have installed grub, then you have a grub.cfg file in your boot partition. You should be able to mount that from liveCD and copy the grub boot stanza into a grub.cfg file in your flash drive.
Since you have encryption the boot stanza will include /mapper/... as it is in a lvm.

From liveCd you will have to add lvm2 driver to mount lvm.
 sudo apt-get install lvm2

      [https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory)
[http://ubuntuforums.org/showthread.php?t=2028865](http://ubuntuforums.org/showthread.php?t=2028865)

You may just be able to mount boot partition if not encrypted? I do not know full disk encryption, many just use /home encryption.

 mount /dev/sdb1 /mnt
#copy boot stanza from this into your grub.cfg on your flash drive.
sudo gedit /mnt/boot/grub/grub.cfg

---

### Post by lorenz90 on 2013-03-10
Thank you,
I searched in sdb1 and sdb3; they both have a GRUB folder, but there is no grub.cfg in them.

Conversely in the GRUB folder of the USB device the file grub.cfg exists and the text contained in it is the following:
```
set timeout=10
set default=0

menuentry "Run Ubuntu Live ISO" {
 loopback loop /ubuntu.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/ubuntu.iso splash --
 initrd (loop)/casper/initrd.lz
}
```

What should I do, should I add some lines indicating the correct boot partition?

---

### Post by oldfred on 2013-03-10
Another LVM post
[http://ubuntuforums.org/showthread.php?t=1984459](http://ubuntuforums.org/showthread.php?t=1984459)

Entry should look something like this but with your UUID, kernel version, drive device location, and mapper locations.
Boot drive is always hd0, so your hard drive is probably hd1 for this entry, but you may have to experiment. You can create an entry and then from grub's menu use e to try alternatives if it does not work.

> 
        menuentry 'Ubuntu, with Linux 3.2.0-36-generic' --class ubuntu --class gnu-linux --class gnu --class os {

 recordfail
gfxmode $linux_gfx_mode
insmod gzio
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 11f137f9-9f85-42f7-855c-2c4be0b79766
linux    /vmlinuz-3.2.0-36-generic root=/dev/mapper/volgroup-root ro   quiet splash $vt_handoff
initrd    /initrd.img-3.2.0-36-generic

 }    

---

### Post by lorenz90 on 2013-03-10
I think we are near the solution.

I copied the lines in my grub.cfg file and I corrected the UUID (copying it from gparted), I used my kernel version, and I substituted hd0 with hd1.

Now when I boot I see the entry, but GRUB gives me the following errors:
```
[FONT=arial]unknown command recordfile
[/FONT][FONT=arial]unknown command gfxmode
[/FONT]no such device
no such partition
```

I think the string "msdos1" is uncorrect, i tried substituting it with "boot" but it did not work.

---

### Post by oldfred on 2013-03-10
It can be msdos1, 1 or gpt1 if gpt partitioned.

I am not sure if grub on liveCD is a full install of grub in the liveCD. So it may be missing the mod files.

I install a full grub2 into my flash drives, but manually have to create a grub.cfg. I usually copy an old one and add my own entries.

       How to make a GRUB_II USB
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB]("http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB")
sudo grub-install --root-directory=/media/fred/MC4GB /dev/sdb

My flash drive was MC4GB as a label I created. (Microcenter 4GB) and was mounted as sdb. Newer version now mount in /media/$USER older versions mounted just as /media.

---

### Post by lorenz90 on 2013-03-16
I cannot belive, I have been trying for days to install grub using the procedure in the website you indicated, but it always gives me an error.

```
sudo grub-install --root-directory=/media/grubbone /dev/sdc
Path `/media/grubbone/boot/grub' is not readable by GRUB on boot. Installation is impossible. Aborting.

```
The name of the USB device is correct and the disk is also correct (I also tried sdc1).

I am very sad, I tried everything, I think it is never going to work :(

---

### Post by oldfred on 2013-03-16
sudo grub-install --root-directory=/media/grubbone /dev/sdc
sudo grub-install --root-directory=/media/[COLOR=#ff0000]fred[/COLOR]/MC4GB /dev/sdb

My post was the same as the link. It just is newer versions of Ubuntu now mount flash drive by user, so I had to add fred into path. I think that was added with 12.10 and 12.04 does not have the user in the default path.

cd /media
ls

What does above show?

---

### Post by lorenz90 on 2013-03-16
Thank you, the installation of grub finally worked!! :)

Although I get the same error I obtained with the previous version
```
[COLOR=#000000][FONT=arial]unknown command recordfile[/FONT][/COLOR]
[FONT=arial]unknown command gfxmode
[/FONT]no such device
[COLOR=#000000][FONT=Ubuntu Mono]no such partition[/FONT][/COLOR]
```

---

### Post by oldfred on 2013-03-17
When you boot from a flash drive install of just grub, you do not have the rest of grub that is in Ubuntu. 
I think these do not work.
recordfail
gfxmode $linux_gfx_mode

I use simplied entries that are like this.
>  menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}



But if you are booting from a different drive, you have to change drive. In grub the boot drive is always hd0, but in Linux sda is the first SATA port normally as BIOS has written it to drive.
So when I boot from flash drive I sometimes have to use e and manually edit drive number, depending on drive I am booting from.

---

