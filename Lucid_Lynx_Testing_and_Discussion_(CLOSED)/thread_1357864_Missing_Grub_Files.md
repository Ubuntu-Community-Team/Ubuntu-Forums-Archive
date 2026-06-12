---
title: "Missing Grub Files ???"
date: 2009-12-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Trapper on 2009-12-17
I have a Windows 2000, U9.10 and U10.04 installs on the same box. The U9.10 bootloader is written to the MBR. I note that the U9.10 /boot/grub folder has in excess of 145 files. My U10.04 /boot/grub folder only contains a splashimages folder and these files: device.map, grub.cfg, grubenv and unicode.pf2. Is this all the U10.04 /boot/grub folder is suppose to contain? I ask because I have tried many times to set up a custom (*/etc/grub.d/40_custom*) chainload to U10.04 and it fails to find grub on the U10.04 partition. I am able to boot Windows via a chainload though.

The /etc/grub.d/30_os-prober picks up what's need to boot my U10.04 install but I was wanting a custom chainload scenario because of the frequency of kernel updates in the development package and wanted to by pass a update-grub on my U9.10 install every time I get a new kernel in U10.04.

It's hard for me to believe I have a complete, working grub on my U10.04 partition. I've even reinstalled it a couple of times. I still only have several files in /boot/grub.

---

### Post by VMC on 2009-12-17
You stated that your grub mbr was written from 9.10 and not 10.04. 9.10 is where it is getting the files to execute.

BTW- I have 147 files in my 10.04. I am also booting off of 10.04 and not 9.10.

---

### Post by ranch hand on 2009-12-17
The best thing you can do is set up a custom file with a symbolic menu entry for both your Ubuntu's and put the MS menu entry in it too.  Then you can change the permissions on 30_os-prober and have a nice clean menu that will never need updating.

The symbolic menu entry just boots to the newest kernel in the defined partition.

One of mine looks like this;
```

echo "Adding Lounge on sda7" >&2 
cat << EOF
menuentry "Lounge on sda7" {
    set root=(hd0,7)
        linux /vmlinuz root=/dev/sda7 ro quiet splash
        initrd /initrd.img
}
EOF

```
Copy that twice to your 40_custom file and edit to your needs.  The stuff between the " " is completely up to you, you can call them anything you want.

You can just copy/paste your MS entry from the /boot/grub/grub.cfg file adding the missing stuff from the other entries.

As far as your /boot/grub directory goes it sounds like it is not all there to me.  If it works I would leave it alone.

When you installed it booted to that OS did it not?

If so were you able to boot to another OS from its generated menu?

---

### Post by Trapper on 2009-12-17
> **ranch hand said:**
> 
As far as your /boot/grub directory goes it sounds like it is not all there to me.  If it works I would leave it alone.

When you installed it booted to that OS did it not?

If so were you able to boot to another OS from its generated menu?

No, I did not boot directly into U10.04 on reboot, after installation. I went into my U9.10 install first and did a update-grub and then booted into U10.04 off of that menu.

During initial install I selected to install grub to the U10.04 partition rather than the MBR. As for the lack of files in the grub folder, that has existed from initial install.

I am going to attempt to install the U10.04 bootloader to the MBR and see what I get. I'll be back.

---

### Post by Trapper on 2009-12-17
Okay. In U10.04 I did a "sudo install-grub /dev/sdb and it installed grub to the MBR and I magically ended up with a full compliment of files in my /boot/grub folder. Everything booted up okay. Now I will follow your suggestions concerning custom booting, ranch hand. I'll report back once I've successfully completed that. Thanks for the help.

Trapper

---

### Post by Trapper on 2009-12-18
ranch hand,

I tried the scheme you mentioned above but never could get either U9.10 or U10.04 to boot. I'm not positive but I believe it has something to do with the way Ubuntu is finding drives. I have an IDE drive and a SATA drive. The IDE drive is set up in the BIOS as first boot drive and all of my bootable OS's are on it. However, Ubuntu determines the SATA drive to be sda and the IDE to be sdb. I am not sure but I think I have some sort of mapping difficulty.

Here are the probed grub entries that boot successfully for each OS from /etc/grub.d/10 & /etc/grub.d/30:

```
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,9)
    search --no-floppy --fs-uuid --set 6cdb6400-7ac5-4571-9f1a-632ff5145ee4
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=6cdb6400-7ac5-4571-9f1a-632ff5145ee4 ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}

menuentry "Microsoft Windows 2000 Professional (on /dev/sdb1)" {
    insmod fat
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 404d-221d
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-8-generic (on /dev/sdb10)" {
    insmod ext2
    set root=(hd1,10)
    search --no-floppy --fs-uuid --set 249a17d5-5fd8-4c4c-84fe-06de32820af5
    linux /boot/vmlinuz-2.6.32-8-generic root=UUID=249a17d5-5fd8-4c4c-84fe-06de32820af5 ro quiet splash
    initrd /boot/initrd.img-2.6.32-8-generic
}



```Here's my /etc/grub.d/40_custom. Windows 2000 boots okay. I get "error: You need to load the kernel first" when attempting to boot either Ubuntu.

```
echo "Adding Ubuntu 9.10 Karmic on /dev/sdb9" >&2 
cat << EOF
menuentry "Ubuntu 9.10 Karmic on /dev/sdb9" {
    set root=(hd1,9)
        linux vmlinuz root=/dev/sdb9 ro quiet splash
        initrd initrd.img

}
EOF

echo "Adding Ubuntu 10.04 Lucid on /dev/sdb10" >&2 
cat << EOF
menuentry "Ubuntu 10.04 Lucid on /dev/sdb10" {
    set root=(hd1,10)
        linux vmlinuz root=/dev/sdb10 ro quiet splash
        initrd initrd.img

}
EOF

echo "Adding Microsoft Windows 2000 Professional on /dev/sdb1" >&2 
cat << EOF
menuentry "Microsoft Windows 2000 Professional on /dev/sdb1" {
    insmod fat
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 404d-221d
    drivemap -s (hd0) ${root}
    chainloader +1
}
EOF
```Here's my partition layouts. Both partitions on sda are simply file storage partitions. 

```
Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xde1fde1f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       14023   112639716   83  Linux
/dev/sda2           14024       19452    43608442+  83  Linux

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x11a711a6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2677    21502971    c  W95 FAT32 (LBA)
/dev/sdb2            2678       30401   222693030    5  Extended
/dev/sdb5            2678        5354    21502971    b  W95 FAT32
/dev/sdb6            5355        8031    21502971    b  W95 FAT32
/dev/sdb7            8032       10708    21502971    b  W95 FAT32
/dev/sdb8           10709       11090     3068383+  82  Linux swap / Solaris
/dev/sdb9           11091       26577   124399296   83  Linux
/dev/sdb10  *       26578       30401    30716248+  83  Linux

```

---

### Post by ranch hand on 2009-12-18
I have heard of problems with mixed drives (and IDE) and grub2.  All I  have is SATA and I boot the drives one at a time to keep them separate.

Where is grub installed, I would guess on sdb but is that so?  I see that is where you told it to install.  If it is installed there I would think that the symbolic menu entries should work.

One thing you might check is the uuid of all your partitions.  I do not know if there could be duplicates on a IDE/SATA system or not.  You can find them by;
```

sudo blkid

```
If you want to continue messing with this I think it would be a good idea to run this script and post the results;

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

It gives about all you need to figure out boot issues.  Real neat.

---

### Post by VMC on 2009-12-18
> **ranch hand said:**
> If you want to continue messing with this I think it would be a good idea to run this script and post the results;

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

It gives about all you need to figure out boot issues.  Real neat.
That is an excellent idea! I don't know if it was Gina or not, but reading his multiple drives using the above script was very informative.

---

### Post by Trapper on 2009-12-18
Well, I was already doing other things by the time the suggestion to use [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280) came up. Uniquely, if I disconnect my SATA drive and change my info in 40_custom for hd0 rather than hd1 and sdaX rather than sdbX I can get a boot into my Ubuntu installs. If I reconnect the SATA drive I cannot get either Ubuntu install to boot from 40_custom utilizing either hd0 and sdaX or hd1 and sdbX entries.

---

### Post by ranch hand on 2009-12-18
One thing you could try is putting grub on the sata drive MBR and see if it boots from there.

I can't remember if you are aware of this or not, so if you want to experiment you should have this;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by plun on 2009-12-18
A great thread about Grub2

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)


--

---

### Post by Trapper on 2009-12-18
> **ranch hand said:**
> One thing you could try is putting grub on the sata drive MBR and see if it boots from there.

I can't remember if you are aware of this or not, so if you want to experiment you should have this;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD")

I put grub on the MBR of the SATA drive and after setting up the correct hdX & sdX info in my 40_custom I was able to boot my Ubuntu installs on sdb from there successfully. I feel as if that's more like winning a battle than the war but good sense tells me to quit while I'm ahead. :-) 

As for the LiveCD recovery routine, I am familiar with that. I experiment a lot. :-)

Thanks ranch hand and everyone else that's contributed to my resolve of this problem.

---

### Post by ranch hand on 2009-12-18
If you go to thread tools at the top of the page you can mark it "solved".  This may be of help to folks looking later.

---

### Post by Trapper on 2009-12-18
Thanks ranch hand. I was looking around for a way to mark the thread solved. I appreciate your guidance.

---

### Post by ranch hand on 2009-12-18
I really like grub2.  It has its rough spots.  It is already more flexible than grub-legacy and more adaptable.

I am glad you got it running right.

Have FUN.

---

### Post by Trapper on 2009-12-19
Grub2 is change and that takes some adjustments usually. In my case I have several boxes, some of which have a number of linux flavors on them. I had a pretty nice setup with grub so I met grub2 with the "if it ain't broke ... don't fix it" attitude and have just begun to deal with grub2 and learn it. I realize that insisting to run a 34 Ford on the interstate isn't the wisest of choices. I do my reading but I also am pretty much spatial based so learning by doing and trial and error is definitely required. I'm also a bit of a control freak when it comes to my box. I take the "I'm in charge" attitude. Then something like grub2 comes along and jambs a stick in the spokes. It takes me a bit to get my feathers unruffled. But I eventually do. Thanks again for the help and insight.

Trapper

---

### Post by ranch hand on 2009-12-19
Be sure to check out drs305's How Tos.  Start with;

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

and check his sig for the rest.  He has some great stuff for control freaks (and everybody else).

---

