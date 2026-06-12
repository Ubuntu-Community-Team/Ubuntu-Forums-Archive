---
title: "Disaster - Partition table gone, can't install grub to see encrypted partition, etc"
date: 2008-02-17
forum: Installation &amp; Upgrades
---

### Post by juxtaposed on 2008-02-17
I had both windows and linux installed. Linux was an encrypted install, with /boot not encrypted. I did this with 

the debian etch install CD. However, I wanted to reinstall windows, so I did. I know it bulldozes the MBR with it's 

own boot loader, so I took my feisty fawn live CD and booted it up, doing the command "grub-install /dev/sda". It 

gave an error about the BIOS i believe, so I decided to try to restore grub with the debian install CD - by going 

through it and not installing anything, but letting it reinstall grub. However, it didn't show any partitions at all 

- just my whole 200gb hard drive as unallocated (note: gparted on the feisty live cd also gives this result). Odd 

though, did my partition table get messed up? I can still boot windows.

I have absolutely no idea what to do, I have been searching and trying things for the past three hours. I think I 

first need to fix my partition table, then find a way to reinstall grub that also works with encrypted partitions 

(without killing my partition table again).

I still have my grub config file saved on my email account

I have (had?) many many partitions - windows, linux boot, linux encrypted root, linux encrypted swap, an unallocated 

space, and a 100gb truecrypt encrypted partition.

Sorry for the bad spelling and grammar and odd words here, I am trying to type this fast to post it so I dont waste  time I could use for more searching.

I will edit this with more information as I can get it. This is a complete disaster, I really hope I can get it fixed :(

Also, I know i'm using debian and not ubuntu, but I wanted to try UF first as I am far more familiar with it than I am with the debian forums.

what fdisk gives me in the 7.04 live cd:

```

root@ubuntu:/home/ubuntu# fdisk -l
omitting empty partition (5)

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        2581      249007+  83  Linux
/dev/sda3            2582       24321   174626550    5  Extended
/dev/sda4            7049       24321   138745341   83  Linux
/dev/sda5            2582        6228    29294464+  83  Linux
/dev/sda6            6229        6350      979933+  83  Linux


```

grub-install doesn't do much important:

```

root@ubuntu:/home/ubuntu# grub-install /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.
root@ubuntu:/home/ubuntu# 

```

then i mounted /dev/sda2 (what I think was the /boot) as /boot on the livecd and did it again:

```

root@ubuntu:/home/ubuntu# grub-install /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.
root@ubuntu:/home/ubuntu# grub-install /dev/sda
Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when /boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["/boot/grub"] is not on an XFS filesystem
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)   /dev/sda


```

by the way, this is from the old grub config file (i think its still being used), it might be important:

```

title		Debian GNU/Linux, kernel 2.6.22-3-k7
root		(hd0,2)
kernel		/vmlinuz-2.6.22-3-k7 root=/dev/mapper/sda6_crypt ro 
initrd		/initrd.img-2.6.22-3-k7
savedefault

```

anyway, after doing the grub-install again (see the codebox above this one), grub came back, but gave me an error 17 when trying to boot debian, but it booted into windows fine (it said windows 2000, which is from before, its now windows xp, but works fine)

---

### Post by dstew on 2008-02-17
At the present, you get the grub menu when you boot, correct? So, the error 17 (which means partition could not be mounted because it has an unrecognized file type) is probably coming from the root line in the Debian entry. If I am not mistaken, your /boot partition must be the small /dev/sda2. If so, the correct root would be (hd0,1). By targeting (hd0,2), you are asking grub to mount your extended partition, /dev/sda3. So it gives the error.

---

### Post by juxtaposed on 2008-02-17
Thank you very much for the reply :)

Yes, I do get the grub menu when I boot up the system. I think it looks a little different than before though, I think there used to be a title at the top before and there isn't now.

I just tried that and my system started to boot up - I was very happy at that point, then as usual it asked me for my password. I put it in, but it gave me an error:

cryptsetup: unknown fstype, bad password or options?

So I thought "Fine, I just put the password in wrong, it's not unheard of, even if I don't remember that particular wording in the error". So I tried it 4 more times, and it still gave me that error. I think it might have something to do with the way it is configured (because of the "bad options" part), maybe it is trying to apply the wrong cipher options to it? I believe it is twofish cbc with a keysize of 256.

Even though it's not completely fixed, it certainly is a lot closer to being fixed - I am very thankful :)

---

### Post by dstew on 2008-02-17
Sorry, I don't know anything about encryption. I can guess that the kernel root entry root=/dev/mapper/sda6_crypt might now be in error.

---

### Post by NetOS on 2008-02-18
That's a common mistake. 
Change root=/dev/mapper/sda6_crypt to root=/dev/sda6

---

### Post by juxtaposed on 2008-02-18
> 
Sorry, I don't know anything about encryption. I can guess that the kernel root entry root=/dev/mapper/sda6_crypt might now be in error.

That could be it, as maybe it can't access the partitions through the sda# way, but only through the (hd#,#) way that grub uses (because gparted shows it all as unallocated anyway). Maybe I should try the different sda numbers though (as changing the grub number method worked for something). I do know that when it is booting right before I enter my password it says it set up sda6_crypt.

> That's a common mistake. 
Change root=/dev/mapper/sda6_crypt to root=/dev/sda6

Thanks, but I tried that and it didn't work (same cryptsetup "unknown fstype" error as before) - wouldn't that make it go straight to the encrypted information that it can't decipher, where it going through sda6_crypt would give it unencrypted information from /dev/sda6?

EDIT: All the partitions show up in Acronis Disk Director on Windows, odd.

I've read that it might be some partitions overlapping, due to some windows doing something stupid.

Someone said this:

> As someone else noticed in another thread, if you install winxp in a ntfs partition after installing ubuntu, windows will mess up with the partition limits, and you end up having an overlap in the cilinders!! (TestDisk found it, and I'm gonna correct it now)


here:[http://ubuntuforums.org/archive/index.php/t-413745.html](http://ubuntuforums.org/archive/index.php/t-413745.html)

I'm going to try testdisk on windows, but before trying it it was complicated.

Here is cfdisk output:

```

                                                                        cfdisk 2.12r

                                                                    Disk Drive: /dev/sda
                                                             Size: 200049647616 bytes, 200.0 GB
                                                    Heads: 255   Sectors per Track: 63   Cylinders: 24321

       Name                    Flags                 Part Type            FS Type                         [Label]                      Size (MB)
 -----------------------------------------------------------------------------------------------------------------------------------------------------------
       sda1                    Boot                   Primary             NTFS                            []                            20974.47             
       sda2                                           Primary             Linux ext3                                                      254.99
                                                      Logical             Free Space                                                        0.01            *
       sda5                    NC                     Logical             Linux                                                         29997.60            *
       sda6                                           Logical             Linux                                                          1003.49
                                                      Logical             Free Space                                                     5741.28            *
       sda4                                           Primary             Linux                                                        142075.23            *


```

I do have the option to write the partition table to the disk, but it says it might destroy data. Should I try that?

I tried testdisk, but as I said it is complicated and only seems to bring up three partitions - 20GB NTFS, /boot, and some really small (7000KB?) ect3. It does seem to show more partitions existing, but I don't understand it very well.

---

