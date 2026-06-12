---
title: "Windows 7/Karmic Dual Boot Question"
date: 2009-11-16
forum: Installation &amp; Upgrades
---

### Post by svtguy88 on 2009-11-16
Well, I just installed Karmic on my laptop, but grub doesn't see my Windows 7 install.  What do I need to change to get back into Windows?

pat@toshlaptop:~$ sudo fdisk -l
[sudo] password for pat: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01fe01fe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        7012    56323858+   5  Extended
/dev/sda2   *        7013       14594    60895232    7  HPFS/NTFS
/dev/sda5               1        6720    53978337   83  Linux
/dev/sda6            6721        7012     2345458+  82  Linux swap / Solaris

I just managed to get compiz running on my ATI r600 (without fglrx), and getting Windows back is the last step to completing my install...

---

### Post by darco on 2009-11-16
did it install grub2? If so run 

```
sudo update-grub
```

it should find the win bootloader


darco

---

### Post by svtguy88 on 2009-11-17
Grub is v1.97beta4, which is the newest release in the repos.  I ran sudo update-grub, and it gave me the following:

pat@toshlaptop:~$ sudo update-grub
[sudo] password for pat: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-999-generic
Found initrd image: /boot/initrd.img-2.6.32-999-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
“Adding Windows”
Found memtest86+ image: /boot/memtest86+.bin
done

Now I have the x86 memeory test in the grub boot menu, but no Windows.  When I boot up, I have to hit ESC to bring the grub menu up, otherwise it boots directly to ubuntu (kernel 2.6.32-999).  Also, if I don't hit ESC to bring up the menu, I get a brief flash of a grub error that says something to the effect of "too many menuentry."  

It appears there is something goofed up in my grub.cfg file, but I don't know what.  Ideas?

---

### Post by darkod on 2009-11-17
In your first post, why is /dev/sda1 marked as Extended? You usually don't start a hdd with extended partition, plus in ubuntu /dev/sda4 is supposed to be reserved for extended as far as I know.

If you open Gparted what does it says about the partitions? If it really is extended I think I've seen somewhere that windows installation inside extended partition is more difficult for grub2 to pick up.

PS. You could always consider making a manual entry for windows in grub2 yourself.

---

### Post by wilee-nilee on 2009-11-17
I am not sure what is causing this problem, grub should be showing with a 10 second time out before going to the default boot. Hopefully somebody will have the answer to this for you.

---

### Post by svtguy88 on 2009-11-17
I really can't tell you why my partition table is set up as it is.  I'm assuming it's because of the way that I installed everything.  Ubuntu installed itself where my old Windows XP install was (beginning of disk), which I deleted before installing Ubuntu.

Anyway...gparted shows the following:

Partition      File Sys  Mount Point  Size

/dev/sda1     extended               53.71 gb
    /dev/sda5   ext4        /        12.48 gb
    /dev/sda6   swap                  2.24 gb

/dev/sda2       ntfs                 58.07 gb

How would I go about adding a manual entry to the config file?

---

### Post by darkod on 2009-11-17
You can read more grub2 basics here:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

In short, you need to edit /etc/grub.d/40_custom with
sudo gedit /etc/grub.d/40_custom

At the end add:
menuentry "Windows 7 (new)" {
insmod ntfs
set root=(hd0,2)
search --no-floppy --fs-uuid --set CFFCFF9EECFF7F49
chainloader +1
}

I have adjusted the partition to (hd0,2), second partition, as per your fdisk -l. You need to replace the CFFC... value with the UUID of your /dev/sda2. You can get the UUID of partitions with 
sudo blkid

After you edit 40_custom save it and close. Then run
sudo update-grub

You should have your manual win7 entry in grub.

---

### Post by svtguy88 on 2009-11-18
Thanks for all of the help.  I added Windows 7 manually to the grub menu, but then I got the "BOOTMGR Missing" error.  I was going to simply use the Windows disc to fix it, but when I tried that, the disc decided that it was not the same version of Windows as my install (which it is...I used it to install Windows...).  

Anyway, I reinstalled Windows (in the same spot, just allowed the installer to install over it), reinstalled grub, and voila.  I can now dual boot properly.

I still get the "too many menuentry" error from grub on bootup though...it just flashes for a second or two.

---

