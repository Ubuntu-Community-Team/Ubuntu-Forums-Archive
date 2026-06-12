---
title: "Trouble installing ubuntu on lenovo thinkpad edge e330 3354"
date: 2012-12-03
forum: Installation &amp; Upgrades
---

### Post by Saphyy on 2012-12-03
Hi there

I have trouble installing ubuntu, it freezes on boot. I have windows 8 64 bit and ubuntu 64bit 12.10 dual boot in grub2.

This is the result of dmesg | grep fail:
```

[    3.548436]  pci0000:00: >ACPI _OSC request failed (AE_ERROR), returned control mask: 0x1d
[    3.631789] ACPI Error: Method parse/execution failed [\_TZ_.MDEC] (Node f342fc48), AE_NOT_EXIST (20120320/psparse-536)
[    3.631908] ACPI Error: Method parse/execution failed [\_TZ_.TZS0._SCP] (Node f342fca8), AE_NOT_EXIST (20120320/psparse-536)
[    5.614368] video: probe of LNXVIDEO:00 failed with error 5
[    5.773461] [drm] nouveau 0000:01:00.0: 0x76E7: i2c wr fail: -6
[    5.775522] [drm] nouveau 0000:01:00.0: 0x7737: i2c wr fail: -6
[   32.469612] init: failsafe main process (3351) killed by TERM signal

```my fstab:
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb6 during installation
UUID=0b554b13-4449-4bf9-a43b-c1071f318a49 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=dc5746d7-c1bf-46a1-b952-90b05b99b99c none            swap    sw              0       0

```Thanks for your time!

---

### Post by offgridguy on 2012-12-03
Try here

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by oldfred on 2012-12-03
Hopefully you do not have the same UEFI/BIOS as this model or that maybe by now they have fixed it.

       Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)


I also wonder above system could change name to Redhat for ubuntu's grub file location in efi menu and if it would then work?

---

### Post by Saphyy on 2012-12-03
Hi

What madde it like this was in fact boot-repair. I got an error during installation saying grub couldn't be installed so i went ahead and ran boot-repair.

@oldfred
Lenovo says it's linux certified so i really hope that is not the case. Also i think this is weird, seeing as it does somewhat boot ubuntu, but it won't go through with it...

---

### Post by oldfred on 2012-12-03
Run the BootInfo report from Boot-Repair and post link it creates.

---

### Post by Saphyy on 2012-12-04
> **oldfred said:**
> Run the BootInfo report from Boot-Repair and post link it creates.

i actually ended up running another boot repair by mistake, here is the link:
[http://paste.ubuntu.com/1410556/]("http://paste.ubuntu.com/1410556/")

here is the bootinfo summary
[http://paste.ubuntu.com/1410566/]("http://paste.ubuntu.com/1410566/")

Thanks

---

### Post by oldfred on 2012-12-04
Are you booting from sdb? And what is sda with the gpt partitioning?

Where does it fail? BootInfo does not show any error that I can see. So you get grub menu and does Windows boot from grub menu?

Perhaps a video issue or other boot parameter is required if after grub menu?

       How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

This is a different model, but is it similar?
[http://www.linlap.com/lenovo_thinkpad_edge_e430](http://www.linlap.com/lenovo_thinkpad_edge_e430)

---

### Post by Saphyy on 2012-12-05
> **oldfred said:**
> Are you booting from sdb? And what is sda with the gpt partitioning?

Where does it fail? BootInfo does not show any error that I can see. So you get grub menu and does Windows boot from grub menu?

Perhaps a video issue or other boot parameter is required if after grub menu?

       How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

This is a different model, but is it similar?
[http://www.linlap.com/lenovo_thinkpad_edge_e430](http://www.linlap.com/lenovo_thinkpad_edge_e430)
Yes i am booting from sdb. sda is my unallocated SSD with 16gb.

I tried the following boot parameters: noapic, nolapic, acpi=off, nomodeset. Nothing worked

I'm not sure what you mean by similar, but mine has quite different hardware. 

I tried disabling quiet splash, this is the last line:
> adding 3623932k Swap on /dev/sdb5 Priority;-1 extents:1 across: 32623932k

---

### Post by oldfred on 2012-12-05
You are booting, but some driver is not loading or failing.

The last line often is not the issue, but it should be in the lines above.

The log files have the same info that you saw on the screen.

From liveCD/DVD/Flash drive mount your Linux partition and drill down to the log files. I think dmesg is the one we want. If you post the entire thing be sure to use code tags, but you should look for outright errors or failures, long times  between tasks, or repeated tries and then a failure of an entry.

And then do you get different errors in dmesg with different boot parameters? A few new systems have needed multiple parameters and unless someone has posted before it is difficult to know what to use. Or an awful lot of trial & error.

---

### Post by Saphyy on 2012-12-08
Hi again and thanks for the help

I found out that windows 8 had some quick launch feature which kept ubuntu from touching the partition with windows (dev/sdb1) which resulted in my problems. I turned this feature off and reinstalled ubuntu 12.10 and now everything works.

Saphyy

---

