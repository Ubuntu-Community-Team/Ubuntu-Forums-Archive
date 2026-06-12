---
title: "This must be a simple GRUB issue?"
date: 2017-11-06
forum: Installation &amp; Upgrades
---

### Post by clepsdyrae on 2017-11-06
Hi -- sda2 is my main booting partition is 16.10, but I installed 17.10 Server to sdc1.

For years I have used sdc1 as a second dedicated linux install that I use to run scripts to do backups of my main partition, etc. (It was previously on 15.04 or 15.10, can't recall).

This install went fine, but at the 'install grub' stage of the install, I elected not to overwrite the MBR on sda, as that generally wreaks havoc (I'm dual-booting windows and have other bootable partitions, etc, and didn't want to mess with the main MBR/grub.) So, given no option to 'do nothing' and figuring that it would be harmless, I let it install grub to the MBR of /dev/sdc.

I then booted my normal linux on sda2, ran update-grub, and it found sdc1 just fine. (This is the process I have done in the past and it worked fine, though in the past I think I just didn't install grub at all during the backup-partition install, and I wasn't given that option this time...) I rebooted, found the 17.10 entry for sdc1 and tried to boot it, but grub tells me that there is an error, and that device can not be found. It lists the UUID of the partition it's looking for, which is completely correct for the sdc1 partition, and the grub entry generally looks fine to me. The boot flag is still set for the sdc1 partition.

What am I doing wrong? Any ideas? Did installing grub to the /dev/sdc MBR somehow mess this up? Is there something special about 17.10 that an older version of grub (the one that came with my 16.10 install) can't handle?

Thanks for any ideas!

---

### Post by ubfan1 on 2017-11-07
Seems OK.  Try booting sdc directly, to invoke the grub there and see if that works.  Also when booting sda, at the grub screen, select "c" for a command line and using tab completion, see what disks it sees.  The UUID boot should be fine, but you could try the device, /dev/sdc1.

---

### Post by clepsdyrae on 2017-11-07
Thanks! From /dev/sda grub's command line, I can't seem to see anything in /dev/sdc1 (aka "hd2, msdos1"). It says "unknown filesystem", despite being ext4 and being easily mountable from my normal main /dev/sda linux install.

/dev/sdc2 is an unrelated Linux Minut install -- it boots fine and can be seen from the grub command line just fine. It is ext4 as well; grub seems to have no trouble with it.

From the grub command line:

[B]probe -f (hd2,msdos2)
  ext2
probe -f (hd2,msdos1)
error: unknown filesystem
[/B]
(Just a shot in the dark: is there any reason a recently-installed ext4 partition would not be recognized as such by an older grub version? 2.02~beta2-36ubuntu11.3 is the one in my normal 16.10 install.)

I tried going to the BIOS F12 boot menu and booting the hard drive directly, with no luck (blinking cursor and nothing happens.)

I'm tempted to go to boot repair but I'd really like to know what I'm doing wrong!

fdisk -l shows this:

```
Disk /dev/sdc: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0006343e

Device     Boot    Start       End   Sectors   Size Id Type
/dev/sdc1  *        2048  10487807  10485760     5G 83 Linux
/dev/sdc2       10487808  52430847  41943040    20G 83 Linux
/dev/sdc3       52430848 976773119 924342272 440.8G  7 HPFS/NTFS/exFAT

```

But strangely enough, parted shows unexpected difference between sdc1 and sdc2:

```
# **parted /dev/sdc print**
Model: ATA ST3500418AS (scsi)
Disk /dev/sdc: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  5370MB  5369MB  primary  ext4         boot
 2      5370MB  26.8GB  21.5GB  primary  ext4
 3      26.8GB  500GB   473GB   primary  ntfs

# **parted /dev/sdc1 print**
Model: Unknown (unknown)
Disk /dev/sdc1: 5369MB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system  Flags
 1      0.00B  5369MB  5369MB  ext4

# **parted /dev/sdc2 print**
Model: Unknown (unknown)
Disk /dev/sdc2: 21.5GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start  End  Size  Type  File system  Flags

#
```

...kinda makes me wonder if either parted is buggy or if my partition table is corrupted somehow?

Thanks for any other ideas!

---

### Post by ubfan1 on 2017-11-08
You seem to have a partition table stuck in sdc2, instead of the expected "partition table: loop" you'd get for a filesystem.

---

### Post by clepsdyrae on 2017-11-08
Huh, that's odd... but should it matter, since I'm trying to boot sdc1?

---

### Post by Impavidus on 2017-11-08
I don't think it's the direct cause of your problem, but do you realise that Ubuntu 16.10 is dead? It reached end of life last July.

---

### Post by clepsdyrae on 2017-11-11
Thank you -- I do know 16.10 is dead -- that's why I'm trying to fix this grub issue: so I can boot into my backup script and back up my main partition before upgrading it to 17.10.

Any further ideas on this are very welcome... Grub is the most impenetrable and confusing part of linux for me. :-)

As it stands:

sda: my main booting device, sda2 running 16.10 main install

sdc1: (the partition of interest, recently installed with 17.10 server)
 * partition mounts fine from my main install
 * has "loop" as its partition table
 * grub CLI shows probe -f (hd2,msdos1) result of "error: unknown filesystem"
 * all half-educated attempts to manually boot from grub CLI result in "unknown filesystem" or similar

sdc2: (an unrelated, not recently touched, booting partition with a different linux install on it)
 * mounts fine from my main install
 * apparently has "msdos" as its partition table
 * grub CLI shows probe -f (hd2,msdos2) result of "ext2"
 * boots fine (although that install has issues of its own)

I again am wondering if grub that comes with 17.10, when I installed it to /dev/sdc, is somehow unrecognized by the older (16.10 vintage) grub that is booting from the main /sda partition on startup... or if UEFI/non-UEFI has anything to do with any of it. It's all so damn baffling and the documentation is overwhelming and just leaves me more confused...

---

### Post by oldfred on 2017-11-12
Loop is not a standard partition.
It is usually from the dd image of a live installer to a flash drive. The use of dd is from the hybrid ISO that can be used either on DVD or flash drive directly.

 sudo mount -t udf -o loop image.iso /media/DVD 



I use grub2's loopmount to directly mount ISO.

---

### Post by ubfan1 on 2017-11-12
parted gives "loop" as the partition type when it is given a partition to "print", (checked on my system), so that's the expected output.  I'd have expected the problem to occur on the second partition, which seems more like a device.  Is the sdc1 just a fresh install, no personal data?  Try a reinstall/format maybe, with a normal grub install to sdc.

---

### Post by clepsdyrae on 2017-11-12
Thanks, all --

> **ubfan1 said:**
>  Is the sdc1 just a fresh install, no personal data?  Try a reinstall/format maybe, with a normal grub install to sdc.

Yeah, that was the next move I was thinking... So, re: a "normal grub install to sdc" -- after I make a new partition table and reformat sdc, when I'm installing to sdc1 via the USB key and it comes to the grub stage, I just choose /dev/sdc? (I just confirm because that's what I did last time...)

Does grub need to even be installed on sdc, given that on startup I boot the MBR of sda and it points to sdc1? That part always confuses me... seems redundant to have two installs of grub on the system, but maybe it needs to "chain" for some reason?

And after the install to sdc, I boot my normal sda linux install and run update-grub so that it picks up the sdc1 install in the sda grub menu at boot?

---

### Post by ubfan1 on 2017-11-12
Booting off sda, you really wouldn't need a grub on sdc, but there is no option on the install to not install grub.  Anyway, putting it on sdc allows it to boot independently if necessary.  Why such a small , 5G first partition?  For a root, I'd use a min of 20G.  Maybe a boot? Those only cause problems unless you have a reason like encrypted logical volumes or raid.  Don't repartition unless nothing is in sdc3 either.

---

### Post by clepsdyrae on 2017-11-12
> **ubfan1 said:**
> Booting off sda, you really wouldn't need a grub on sdc, but there is no option on the install to not install grub.

Oh good, that makes more sense. The 'requirement' to install grub on boot is what confused me, I guess.

> Why such a small , 5G first partition?  For a root, I'd use a min of 20G.

Thanks, yeah -- 5G is the 17.10 server install whose only function is to boot and run a backup script and then shut itself down. It's for doing automated backups of my regular partitions. sdc2 is a 20G for testing distros, etc.

> Don't repartition unless nothing is in sdc3 either.

Thanks -- I backed up the sdc3 stuff. I think I needed to re-do the partition table? At least I had no apparent way to fix the irregularities. Now things look more normal (e.g. sdc1, 2, and 3 are all "loop").

Gonna try to install 17.10 server on sdc1 again... wish me luck. :-)

---

### Post by clepsdyrae on 2017-11-13
Whelp, installed again, installed grub to sdc, rebooted from sda, ran update-grub, rebooted...

Same result. The UUID is listed correctly, but the filesystem is "unknown" to grub and won't boot. From sda, the sdc partitions look OK now (all "loop" in the parted print results) and they still mount just fine in my sda install.

I note that I booted the install USB drive as non-UEFI. No idea why that should matter, but in the past I've had a million UEFI/non-UEFI related bugs that seemed unrelated, so I mention it.

Anything else to try? What could be going on? I can't seem to google anything that seems relevant to the error grub is giving me, but maybe I'm not trying hard enough.

---

### Post by oldfred on 2017-11-13
Can you boot if you choose sdc?

 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 


You need to always be consistent on UEFI or BIOS. All installs should be the same.
If system hardware is UEFI, some advantages to UEFI installs. 
And if not dual booting a BIOS install of Windows on same drive much better to always use gpt and maybe have both a bios_grub partition for BIOS and an ESP - efi system partition for future conversion to UEFI.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

### Post by clepsdyrae on 2017-11-13
Thanks oldfred; here is the boot-repair output: [https://paste.ubuntu.com/25957172/](https://paste.ubuntu.com/25957172/)

(I redacted the /etc/fstab from my main sda install; let me know if any info there would be useful.)

I believe my system is booting non-UEFI. (When I configure BIOS to only show me UEFI options, nothing appears. When I configure it to show only Legacy options, the normal options appear.) When I installed from the USB thumb drive, I booted it legacy as well.

Trying to boot sdc directly from the BIOS boot choice menu does not work, as before -- just a blinking _ character at the top of a black screen.

---

### Post by oldfred on 2017-11-13
I see two strange things in sdc1.
 /boot/grub/menu.lst
sdc1/etc/mdadm/mdadm.conf 

How did you get a grub legacy menu in sdc1? Ubuntu has used grub2 since 2009.

And was sdc once part of a RAID configuration? If so the meta-data on drive may be causing issues.

 Even if raid not used BIOS may have set parameters, Also check BIOS settings should be AHCI
sudo dmraid -E -r /dev/sdc

Do not use Boot-Repair's auto fix, but only advanced options with more than one install or more than one drive.
You want the install in sdc to have its boot loader in the MBR of sdc and choose that in BIOS to boot from.
      
 [https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)
Grub from desktop installer does not install correctly if RAID meta-data on drive.

You may want to start considering converting drives to gpt. You have one gpt drive already as it exceeds the MBR limit.
But you only need MBR on one drive to boot Windows in BIOS boot mode as Windows only boots from MBR with BIOS.
You can convert all other drives eventually to gpt and boot BIOS now and UEFI in future.
I now add both ESP - efi system partition and bios_grub partition to all new gpt drives. And all drives including larger flash drives are gpt.

I make these first two partitions on every new or reformatted drive.

 Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)

---

### Post by clepsdyrae on 2017-11-13
> **oldfred said:**
> I see two strange things in sdc1.
 /boot/grub/menu.lst
sdc1/etc/mdadm/mdadm.conf 

How did you get a grub legacy menu in sdc1? Ubuntu has used grub2 since 2009.

I just made a new msdos partition table with gparted, made the three partitions (I did not set the "boot" flag on any of them, though I did do that on the previous attempt), and then installed 17.10 server by booting from the USB key, and during the install chose /dev/sdc to install grub.

Then I reboot into the sda install and run update-grub (which is version 2.02~beta2-36ubuntu11.3) so that it will appear in the sda grub menu on startup.

> And was sdc once part of a RAID configuration? If so the meta-data on drive may be causing issues.

I don't think so... but to be honest I've done a fair bit of drive swapping in the last couple years, so it's possible that this is some refurbished HD.

 > Even if raid not used BIOS may have set parameters, Also check BIOS settings should be AHCI

Ok, I'll check BIOS settings.

> sudo dmraid -E -r /dev/sdc

This yields:
> # dmraid -E -r /dev/sdc
no raid disks and with names: "/dev/sdc"


> You want the install in sdc to have its boot loader in the MBR of sdc and choose that in BIOS to boot from.

...but if I'm booting normally from grub in sda, the MBR in sdc isn't important, right? Or do I need sdc grub correctly installed to boot sda grub -> sdc1?
      
Thanks for the GPT tips -- I will look in to all that going forward.

---

### Post by ubfan1 on 2017-11-13
Your grub on sda makes grub on sdc unnecessary.  When you run update-grub on the sda install of 16.10, it should pick up the OS on sdc as an option.  However, when you install to sdc, you cannot say "none" to grub location, and if you give it sda, then the grub.cfg file controlling the grub menu at boot will be the one on sdc -- probably not what you really want.  That leaves sdc as the grub target, which will be ignored by the boot process, unless you explicitly boot off sdc instead of sda.  Chaining grubs is possible, but pointless in this case.

---

### Post by clepsdyrae on 2017-11-13
I confirmed that the BIOS settings are that the SATA controller is in AHCI mode only. Not sure if there is more to investigate there.

And thanks ubfan1 -- that lines up with my understanding.

So according to oldfred I somehow have some weird legacy grub in sdc, despite having used only the default 17.10 server installer process... but I suppose that shouldn't really matter in terms of booting from sda?

Is there anything else that could cause the sda grub to not be able to recognize sdc1 as a valid place to boot? It's just odd to me that the partition mounts totally fine from the sda OS, but grub is confused by it, despite the UUID being correct, etc etc.

---

### Post by oldfred on 2017-11-14
I just like to have each install's boot loader in the MBR of that drive. Then if main boot drive has issues or fails I can in BIOS directly boot other drive.

Can you boot install in sdc with grub from sdc? 
Even though you want and use grub in sda normally.

---

### Post by clepsdyrae on 2018-03-29
I'm resurrecting this thread just to report:

I finally manually backed up all my various partitions and installed Kubuntu 17.10. After the update-grub during the install, the system magically boots to the troubled partition without issue.

So indeed it must have been some kind of incompatibility between the old grub and the new OS install.

---

