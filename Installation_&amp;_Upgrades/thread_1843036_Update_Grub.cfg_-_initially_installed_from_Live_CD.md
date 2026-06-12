---
title: "Update Grub.cfg - initially installed from Live CD"
date: 2011-09-12
forum: Installation &amp; Upgrades
---

### Post by avnd on 2011-09-12
Hello!

I wanted a situation of having a separate boot partition that is not associated with any installed OS. I wanted Grub 2. There was a beautifully detailed instruction page for Grub Legacy in one of the Ubuntuguide pages but not for Grub 2.

I have 2 hard disks. So I wanted to set it up in such a way that I can boot into either hard disk and get the Grub 2 menu.

I did the following.

On my 1st hard disk, I partitioned as 
/dev/sda1 - Grub
/dev/sda2 - Xp
/dev/sda3 - NTFS - (for unforeseen Primary Partition needs)
/dev/sda4 - Extended
    /dev/sda5 - Data

On my 2nd hard disk, I partitioned as
/dev/sdb1 - Grub
Unpartitioned Space (for unforeseen Primary Partition needs)
/dev/sdb4 - Extended
    /dev/sdb5 - Swap
    /dev/sdb6 - Lubuntu
    /dev/sdb7 - Arch
    /dev/sdb8 - DATA

(I share this computer with my family. So I had to make room for them. That's the reason for the unforeseen needs).

My computer has only 256 MB RAM. So I just did a few things from the Ubuntu Live CD.

The things in the order I did.
1. Install Xp in /dev/sda2
2. Install Lubuntu in /dev/sdb6
3. Install Arch in /dev/sdb7
(Both Lubuntu and Arch had their bootloaders in the partitions and not MBR).
4. Installed Grub 2 into both /dev/sda and /dev/sdb from Ubuntu Live CD terminal (Ubuntu was dead-slow). But grub-mkconfig did not work from Live CD.
5. Rebooted into /dev/sda. Therw was no grub.cfg yet. So booted into Lubuntu from the Grub command line. Created the grub.cfg's for both /dev/sda1 and /dev/sdb1.
6. Now when I reboot into either hard disk, I'm able to get a Grub 2 menu from which I can boot into any of the 3 OS's (Windows Xp, Lubuntu or Arch).

Now, the issue.

I wanted to make certain that the Grub 2 was totally independent of any OS (that was the whole point, so I could repartition and install new distros without worrying about messing the other OS's). And since the Lubuntu was the only one which I had associated with Grub so far (creating the grub.cfg files), I formatted the Lubuntu partition and rebooted. 

Jeez! I was getting an error message saying that a parition (mentioned with UUID) was missing. The Grub menu followed and I was able to boot into the other Operating Systems though. But is there any way I can do this neatly?

I was able to do it perfectly with Grub Legacy with the method described at [http://ubuntuguide.org/wiki/Multiple_OS_Installation]("http://ubuntuguide.org/wiki/Multiple_OS_Installation")
But I really want to move onto Grub 2. 

Can anyone help with any solutions?

Thanks!

---

### Post by Blasphemist on 2011-09-12
This is a bit complicated. If I understand your process right, it seems like you installed grub to the mbr of each disk and not the boot partitions. But that isn't the issue or hat least not the only issue. To really do what you are asking, make each disk's grub2 distro independent if I understand right, I think the only way to that is to chainload and that has its own issues.

Please start with using boot-repair to give us a boot info summary to go on. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 

This tool may help to do some work for you but I don't think it will do chainloading off the top of my head.

---

### Post by avnd on 2011-09-21
Thank you for your reply Blasphemist.

As such I've become a little busy and no longer have the time to try new things. So, I think I'll stick with Grub Legacy for now and maybe experiment and post what happened a little later when I'm free.

Thanks again for your reply, mate.

---

### Post by oldfred on 2011-09-21
I use, in effect, a grub2 partition on my USB flash drives. Herman has info on grub2 on its own partition. The disadvantage of grub installed to a partition is all maintenance to the grub.cfg has to be manually done. Then it is best to chain load old grub entries (grub2 in partition is not recommended) or use partition type boot stanzas. The hd numbers can be an issue as the BIOS boot drive is always hd0.

[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB")

[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition")

Some grub2 manual entries:
```
menuentry " " {
set root= 
}

menuentry "Reboot" {
    reboot
}

menuentry "Halt" {
    halt
}

menuentry "Memory test (memtest86+)" {
 linux /boot/memtest86+.bin
}

menuentry "Custom Menu"{
        configfile (hd2,5)/boot/grub/grub.cfg
        }

menuentry "boot to first mbr"{
set root=(hd0)
chainloader +1
}

Boot most up2date Maverick kernel on sdb2
menuentry "Maverick on sdb2 - hd1?" {
    set root=(hd1,2)
        linux /vmlinuz root=/dev/sdb2 ro quiet splash
        initrd /initrd.img
}

Boot most up2date Lucid kernel on sdc7
menuentry "Lucid on sdc7 - hd2?" {
    set root=(hd2,7)
        linux /vmlinuz root=/dev/sdc7 ro quiet splash
        initrd /initrd.img
}

menuentry "Gparted Live ISO in sdc6 " {
set isofile="/ISO/gparted-live-0.8.0-5.iso"
loopback loop (hd3,6)$isofile
linux (loop)/live/vmlinuz boot=live config union=aufs noswap noprompt ip=frommedia findiso=$isofile toram=filesystem.squashfs nomodeset
initrd (loop)/live/initrd.img
}

```

---

