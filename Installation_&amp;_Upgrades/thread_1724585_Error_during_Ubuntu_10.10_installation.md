---
title: "Error during Ubuntu 10.10 installation"
date: 2011-04-08
forum: Installation &amp; Upgrades
---

### Post by mmayes on 2011-04-08
I have a new laptop that I am trying to put Ubuntu 10.10 onto. I used my MacBook to burn a bootable DVD, that burned and verified successfully. On the new laptop (a Toshiba) I booted to the DVD and am making my way through the installer. I use the option "Erase and use all drive space" since I don't want to mess with manually partitioning the HD. I work through the setup screens (time zone, login info, etc) and get into the Welcome slideshow. Shortly after arriving there, however, I get an error: "Input/Output error during read on /dev/sda". I'm not sure why this is occuring. I tried hitting Retry but the error just keeps happening. Ignoring it also has the same effect. If I click cancel, then the following comes up: "Error fsyncing/closing /dev/sda: Input/Output error". I click ignore on that, and then yet another error comes up: "The ext4 file system creation in partition #1 of SCSI1 (0,0,0) (sda) failed." This then stops the installation process and I get kicked back to the screen where I choose my partitions (whether to use the entire drive or manually partition). Why is this happening? I can boot to the DVD fine and use Ubuntu that way, but that's a long process and I'd rather not have to do that. Any suggestions?

---

### Post by Rubi1200 on 2011-04-08
Hi and welcome to the forums :-)

Please post the output of the following commands (Applications > Accessories > Terminal):

```
sudo parted -l

sudo fdisk -lu
```

When posting back, highlight the text and click on # in the toolbar to wrap with code tags.

Thanks.

---

### Post by Dutch70 on 2011-04-08
Nevermind :)

---

### Post by mmayes on 2011-04-08
Here's the results of those Terminal commands (both were run while booted into Ubuntu from the DVD):

```
ubuntu@ubuntu:~$ sudo parted -l
Error: /dev/sda: unrecognised disk label

Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0 has been opened read-only.
Error: /dev/sr0: unrecognised disk label

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table
ubuntu@ubuntu:~$
```

---

### Post by Rubi1200 on 2011-04-09
What was on the Toshiba before? Did it come with Windows pre-installed?

This message is quite worrying:
> Disk /dev/sda doesn't contain a valid partition table

---

### Post by mmayes on 2011-04-09
Actually, it had Ubuntu 10.10 on it previously. I had installed a batch of recommended updates (there were a lot as I hadn't been on that computer in a while) and then rebooted. At that point, Ubuntu wouldn't boot so I got into the GRUB menu and ran Memtest86. I only did one pass, but there were no errors there. I went back to the GRUB menu and tried booting into the kernels available (also tried safe mode) but each time I was kicked back to the shell. At this point I decided to try and reinstall Ubuntu and thus the original post. The computer is somewhat old so there is also a possibility that the hd could be giving out, but I don't know.

---

### Post by Rubi1200 on 2011-04-09
Okay, this is what I suggest:

1. go back and boot the Toshiba with the LiveCD and then go to Disk Utility and check the SMART status to see whether the drive is healthy

2. if it is, go to GParted and create a new partition table (available via Device > create partition table)

3. exit GParted and start the Ubuntu installer and try again

Let me know what happens please.

---

### Post by mmayes on 2011-04-09
SMART status isn't supported on the HD. Went into GParted and it couldn't find any devices, I tried refreshing the list and still nothing.

---

### Post by Rubi1200 on 2011-04-09
Okay, if you are still on the LiveCD please run this command:

```
sudo dmraid -r -E /dev/sda
```

If it asks you to remove metadata or other RAID settings, do so and then try the GParted step again.

---

### Post by mmayes on 2011-04-09
Here's what I got back. It doesn't look good...

```
ubuntu@ubuntu:~$ sudo dmraid -r -E /dev/sda
ERROR: asr: reading /dev/sda[Input/output error]
ERROR: ddf1: reading /dev/sda[Input/output error]
ERROR: ddf1: reading /dev/sda[Input/output error]
ERROR: hpt37x: reading /dev/sda[Input/output error]
ERROR: hpt45x: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: jmicron: reading /dev/sda[Input/output error]
ERROR: lsi: reading /dev/sda[Input/output error]
ERROR: nvidia: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: sil: reading /dev/sda[Input/output error]
ERROR: via: reading /dev/sda[Input/output error]
no raid disks and with names: "/dev/sda"
ubuntu@ubuntu:~$ 
```

---

### Post by coffeecat on 2011-04-09
@mmayes, hi, Rubi1200 asked me if I had any other thoughts.

I fear that you may be right and the HD is dying, but I have one suggestion. It's remotely possible that a corrupt partition table is confusing fdisk and confusing gparted sufficient for it not to do anything for you. You could try zeroing the partition table by zeroing the mbr - the first 512 bytes with this from a live CD session:

```
sudo dd if=/dev/zero of=/dev/sda bs=512 count=1
```And then see if you can create a partition table with Gparted the way Rubi1200 described.

This will also zero out any bootloader in the mbr, but that won't matter because that will get rewritten if this works and you can re-install.

---

### Post by mmayes on 2011-04-09
First off, I'd just like to say thanks for you guys' help. It's nice to see a welcoming community like this one.

Secondly, here's the result of that last command, I don't think it did anything:

```
ubuntu@ubuntu:~$ sudo dd if=/dev/zero of=/dev/sda bs=512 count=1
dd: writing '/dev/sda': Input/Output error
1+0 records in
0+0 records out
0 bytes (0 B) copied, 0.00182288 s, 0.0 kB/s
ubuntu@ubuntu:~$
```

Fortunately I have a few spare HDs to go through and see if they still work, and it seems replacing the HD on a Toshiba Satellite is a fairly simple procedure. I have a feeling this HD is dead so I'm probably just going to replace it and see if that works. I'll get back to you.

Edit: For kicks, I ran GParted after running that command and it still didn't show any devices, even after refreshing.

---

### Post by Rubi1200 on 2011-04-09
Unless coffeecat has some more suggestions, I think you may need to accept the fact that the drive could be finished.

However, it will be interesting to know if another drive works on the machine.

Good luck!

---

### Post by coffeecat on 2011-04-09
> **mmayes said:**
> Secondly, here's the result of that last command, I don't think it did anything:

```
ubuntu@ubuntu:~$ sudo dd if=/dev/zero of=/dev/sda bs=512 count=1
dd: writing '/dev/sda': Input/Output error
1+0 records in
0+0 records out
0 bytes (0 B) copied, 0.00182288 s, 0.0 kB/s
ubuntu@ubuntu:~$
```

Indeed, it didn't do anything. The I/O error and the "0+0 records out" suggests that there was no viable drive to write to. 

Good luck with the drive replacement.

---

### Post by mmayes on 2011-04-09
I'll have a new drive put in hopefully later tonight or tomorrow, so I'll update you guys once I get it in and see what happens. The "new" drive is another old-ish one, so we might eventually end up back where we are now, but we'll see. For now I'm just hoping it'll work.

---

### Post by mmayes on 2011-04-11
Well I'm marking this as solved, though it is certainly a less than ideal solution. Replaced the hard drive and now everything seems to be okay. Had to buy a new IDE drive but everything is going smoothly now, right now it's updating but Ubuntu installed without any problems. Thanks again for your help.

---

### Post by Rubi1200 on 2011-04-11
> **mmayes said:**
> Well I'm marking this as solved, though it is certainly a less than ideal solution. Replaced the hard drive and now everything seems to be okay. Had to buy a new IDE drive but everything is going smoothly now, right now it's updating but Ubuntu installed without any problems. Thanks again for your help.
Okay, well I am pleased you managed to get something sorted out in the end.

Good luck and enjoy :)

---

### Post by coffeecat on 2011-04-11
Good luck! :)

---

