---
title: "Ubuntu UNR hangs when attempting to install"
date: 2010-12-21
forum: Installation &amp; Upgrades
---

### Post by BDot on 2010-12-21
I'm trying to upgrade an EeePC from 9.10 (I think it is) to 10.10. I've tried two different thumb drives and a CD, redownloading the UNR image each time.

What happens is it will get the the screen where it says 'Preparing to install Ubuntu-Netbook'. I hit forward, and then the little dial just spins indefinitely. I've also tried plugging the thumb drives into different USB ports, and playing around the with the hard disk compatibility mode on in the BIOS (currently set to 'compatible', but AHCI, IDE Enhanced etc made no difference).

Any ideas?

***EDIT***

It's a model 1005HAB. Thanks again.

---

### Post by sikander3786 on 2010-12-21
Check the downloaded image for any defects.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If ok, set your HDD mode to AHCI and try adding some boot options from F6 menu.

[https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options](https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options)

There are 6 of them and you might need to try all of them one-by-one. However, I feel acpi=off or noapic would work for you.

If none of the above helps, it would be handy to post your hardware specs.

> I'm trying to upgrade an EeePC from 9.10 (I think it is) to 10.10

You are going to do a clean install with 10.10, aren't you?

---

### Post by BDot on 2010-12-21
> **sikander3786 said:**
> Check the downloaded image for any defects.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If ok, set your HDD mode to AHCI and try adding some boot options from F6 menu.

[https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options](https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options)

There are 6 of them and you might need to try all of them one-by-one. However, I feel acpi=off or noapic would work for you.

If none of the above helps, it would be handy to post your hardware specs.



You are going to do a clean install with 10.10, aren't you?

How would I access the boot options with UNR?

***EDIT***

Nevermind, I got it. I'm going through the options now. I'll report back with results.

Thanks again.

---

### Post by sikander3786 on 2010-12-21
Press any key as soon as the computer starts booting from the disc and you might see the menu. It should be the same as mentioned in the screenshot I believe.

---

### Post by BDot on 2010-12-21
Tried all available options, and none worked.

Specs:

Asus EeePC 10005HAB
Processor: Intel Atom N270 @ 1.6Ghz
Ram: 1024MB
Hard drive: Seagate ST9250315AS 250GB

Not sure what wireless card it's using (Google didn't turn up much). Also, what should the ATA/IDE config in the BIOS be set to (Enhanced, Compatible, AHCI, IDE etc)? Does it matter?

And I dont mind wiping the system partition. As long as I can keep the home partition intact, I'm not complaining.

Thanks.

---

### Post by sikander3786 on 2010-12-21
Can you boot Ubuntu with Try mode from the CD/USB and post the output of these commands from Terminal.

```
lspci | grep VGA
```

```
sudo fdisk -lu
```

Regarding Bios HDD settings, AHCI and Compatible definitely work.

---

### Post by BDot on 2010-12-21
> 00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)

and

> ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x935d59dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    78125055    39061504   83  Linux
/dev/sda2        78127102   488396799   205134849    5  Extended
/dev/sda5        78127104    81125375     1499136   82  Linux swap / Solaris
/dev/sda6        81127424   488396799   203634688   83  Linux

Disk /dev/sdb: 4038 MB, 4038065664 bytes
255 heads, 63 sectors/track, 490 cylinders, total 7886847 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     7886846     3943392    c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
     phys=(489, 254, 63) logical=(490, 238, 3)

Typed from this godforsaken EeePC.

---

### Post by sikander3786 on 2010-12-21
That output seems pretty ok. So that might not be a problem with the HDD or partitions.

I'll try to find some reason behind that with that specific machine. Or refer some experienced member here. Please hang in there.

---

### Post by BDot on 2010-12-22
Alright, I defintitely appreciate all the help man. And for what it's worth, I've decided to reinstall 10.04 on this machine. 

Turns out that's what it was using before it crapped out (different story).

It's back up and running. So far so good.

---

### Post by dk412 on 2010-12-28
Same issue with Eeepc 1005pxd. This computer has been a headache from the beginning, couldn't even install Windows 7 Ultimate because of driver issues. Will try 10.04 Netbook Remix. I just want a freaking OS on this machine.

---

