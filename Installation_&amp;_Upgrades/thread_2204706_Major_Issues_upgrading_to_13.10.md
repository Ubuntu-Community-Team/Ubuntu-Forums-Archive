---
title: "Major Issues upgrading to 13.10"
date: 2014-02-09
forum: Installation &amp; Upgrades
---

### Post by The_Autonomist on 2014-02-09
Firstly, I own an HP dv6 that I've been smoothly dual booting win7 and Ubuntu for years without issue. Until now.

Okay, I decided to do a clean install of 13.10 (coming from 13.04) and do so via USB stick. I copied the iso to my USB stick, booted from it, and the install was going smoothly. 

The thing is, I fell asleep during the install proces. When I woke up, there was a black screen. My laptop had been sitting for hours while I was asleep, so I have no idea at which point the install ran into problems. I just know that it did, somehow. 

So, I had to do a hard reboot. I tried to boot from the USB stick and redo the installation, but get this error after the Ubuntu loading screen: 

```
[ 13.070634] Kernel panic - not syncing: Attempted to kill init! exitcode=0x00000007

[ 13.070634]

[13.070776] DRM_kms_helper: panic occurred, switching back to text console
```

I've tried Ctrl+alt+f1, and have tried all of the options listed but every time this same message pops up after the Ubuntu loading screen. 

Well you say, just boot into Win7, redownload the iso, and try again. I can't, because I can't get into Win7 either. 

After the HP loading screen, I immediately get taken to a black screen that says: 

```
error: unknown filesystem.
Entering rescue mode...
grub rescue>_
```

I've been googling  all day and all of the responses I can find have to do with either booting into a different Ubuntu kernel/booting from an Ubuntu disk OR doing a system restore/recovery via a Win7 disk. I do not have a Win7 disk as Win7 came installed on my laptop. I do not have an Ubuntu disk, as i've always done installs via upgrade or a usb stick. I also no longer have a grub screen when I boot up, allowing me to boot into various Ubuntu kernels or Win7. 

Any help?

---

### Post by Bucky Ball on 2014-02-09
But you do have a grub terminal. Try:

grub-install /dev/sda

---

### Post by The_Autonomist on 2014-02-09
Thanks for your response! 

I tried what you said and It keeps telling me "Unknown command." :/

---

### Post by Bashing-om on 2014-02-10
The_Autonomist; Hi !

Panic not. Just proceed in a calm and orderly fashion.

Let's first look and see that the file system(s) are intact.
We will do all things from the liveUSB:
Set bios priority to boot the USB, and to have a looksee:
Activate a terminal:
```

sudo fdisk -lu
sudo parted -l
sudo parted /dev/sda unit s print

```

We have partitions ? .. ok look in the output of "fdisk" see the '*' AND ID = 83 AND system = "linux";  line and note what partition it is in.
Mount that partition, and let's get an indication that the file system is whole.
```

sudo mkdir /mnt/work
sudo mount /dev/sda6 /mnt/work ##substitute 'sda6' for the appropriate partition
##let's look ! ##
ls -la /mnt/work/home/<your_user_name>

```
##all looks good at this point, we can "assume" the file system is intact ##

The following is assuming (!!) that UEFI and GPT are not factors in the installation of ubuntu !
Else going to have to do something else . Make sure that we are working with the legacy partitioning scheme ! 

Let's (RE-)install grub (ubuntu's boot loader)
```

sudo grub-install /dev/sdx # where 'sdx' is the drive in operation that ubuntu is installed to, not the partition.
sudo update-grub ##to also pick up the windows' operating system

```

All done ? -> UNMOUNT the partition that we mounted !
```

sudo umount /mnt/work

```

OK, ready to see what the result of out handy work is ?
Let's do this !
Reboot at this time, and boot into the ubuntu install .

All hunky dory ?

YEAH !

[INDENT][INDENT]we do good work
[/INDENT][/INDENT]

---

### Post by The_Autonomist on 2014-02-10
Hi, Bashing-om!! I appreciate your help and patience. 

That's the thing, i can't figure out how to activate a terminal. I have tried all of the options on this screen: 

[IMG]https://lh3.googleusercontent.com/-DxvdhWJnb9Q/UvltcsH-LYI/AAAAAAAAHtY/sTxgfuOGKZ0/w756-h567-no/IMG_20140210_182221.jpg[/IMG]

All of them result in the same "kernel panic" error. I can't figure out how to get a terminal running. 

If i alt-ctrl fast enough after the UBuntu loading screen, i get the screen above. But i tried alt-ctrl-t instead, and all it did was take me directly to a kernel panic screen.

---

### Post by Bashing-om on 2014-02-10
The_Autonomist; Uhmm;

Lemme back up and we do this in baby steps.
Boot that liveUSB, at the screen with "Try ubuntu without installing" select that option, will take a long long time to boot to the desk top.
It is possible we may have to do some fiddling around to get to the desk top.

Once you are at the desk top, key combo ctl+alt+t should result in a terminal.

Please to advise on your result to that time.

[INDENT][INDENT]we will get there
[/INDENT][/INDENT]

---

### Post by The_Autonomist on 2014-02-10
When botting from the USB stick, here's what happens: 

HP screen. > Black screen. > Purple screen. > Black screen. > Ubuntu loading screen > Black kernel panic screen

The only other screen i can get is the one i posted above, but only if i press alt-ctrl.

I've tried selecting all of the options, including the "Try ubuntu without installing" and the same cycle above happens.

---

### Post by Bashing-om on 2014-02-10
The_Autonomist; Umph !

Looks like then we got to find a boot option(s) to make the kernel happy, till the kernel can do better,
Is this the box we are looking at "HP Pavilion dv6000t" with integtated "Intel Graphics Media Accelerator 950" for graphics ?

Generally Intel has no problems, so presently I am at a loss what the kernel wants. Will do a bit of research and see what I can find.

[INDENT][INDENT]hey, we can do this
[/INDENT][/INDENT]

---

### Post by The_Autonomist on 2014-02-10
Yes, that's it! 

If this helps any, i edited the boot options in the photo above and took out the "silent splash --" bit from the end so i could get a more detailed reading of what's going on when my laptop attempts to boot from the PC. I guess it worked, because now, this just showed before the "kernel panic" error i posted in my original post. 

```
calling: test-builtin
error reading /lib/udev/hwdb.bin: No such file or directory
load module index
unload module index
calling: test-builtin
error reading /lib/udev/hwdb.bin: No such fule or directory
load module index
unload module index
Bus error
Bus error
Bus error
[16.358107] Kernel panic - not syncing: Attempted to kill init! exitcode=0x00000007
[16.358107]
[16.358249] drm_kms_helper: panic occurred, switching back to text console 
```

---

### Post by Bashing-om on 2014-02-10
The_Autonomist; well that is  a bit of progress.

Let's poke at it a bit more and see if we can isolate to a graphics driver issue.

Try this and advise results:
Boot the liveUSB to the boot options screen, f6 key for boot parameters, and replace "quiet splash" and all after with the term "text" - with out the quotes. Key combo ctl+x to continue the boot process;

Do you now boot to a terminal ?

What results with terminal command:
```

sudo service lightdm start

```

What is the kernel screaming and hollering about ?

[INDENT][INDENT]sometimes I wonder
[INDENT][INDENT][INDENT]othertimes I just do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by The_Autonomist on 2014-02-10
Okay, I did what you said and replaced everything after quiet splas with "text", sans quotes. Pressing ctrl-x did nothing, but pressing enter did. After I pressed enter, the screen went black and then an extremely lengthy wall of text appeared. It was various errors. Lots of "Unable to read..." And "__________ error:" messages. Pages and pages long. Then it ended with the same kernel panic error. It did not boot into a usable terminal. :/

---

### Post by Bashing-om on 2014-02-10
The_Autonomist;

Sorry I missed your response and a delay in mine.

OK, That to me says you have a bad copy for the install medium.
Back to square 1 ->

Verify the .iso file:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Burn the .iso file to image:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[http://ubuntuforums.org/showthread.php?t=1958073](http://ubuntuforums.org/showthread.php?t=1958073)
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Once reburned, check the mediums integrity:
Boot option screen from the liveUSB -> "check disk for defects"

Then:
Boot to "try ubuntu" and see what happens.

[INDENT][INDENT]got to put out feet
[INDENT][INDENT][INDENT]on firm ground
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by The_Autonomist on 2014-02-13
Okay!! i'm back. after trying other methods, without avail, to recreate the bootable disk via my chromebook, i finally decided to just dd the file. voila, worked like a charm. i should have done that at first. 

Anyway, i finally have the Ubuntu installer up and am currently in "Try Ubuntu" mode. I ran the fdisk command like said in your first response. Everything looked good, EXCEPT this Warning that is listed in the terminal readout: 

```
WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU parted.
```

In your first response you said > The following is assuming (!!) that UEFI and GPT are not factors in the installation of ubuntu! Else going to have to do something else...

Apparently, this IS an issue. So, where do i go from here?

EDIT****

I just followed your instructions in[ this]("http://ubuntuforums.org/showthread.php?t=2204271") thread, and installed gdisk. so, now can i proceed with the rest of your instructions in your first response to my thread?

---

### Post by frank18 on 2014-02-13
> **The_Autonomist said:**
> Okay!! i'm back. after trying other methods, without avail, to recreate the bootable disk via my chromebook, i finally decided to just dd the file. voila, worked like a charm. i should have done that at first. 

Anyway, i finally have the Ubuntu installer up and am currently in "Try Ubuntu" mode. I ran the fdisk command like said in your first response. Everything looked good, EXCEPT this Warning that is listed in the terminal readout: 

```
WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU parted.
```

In your first response you said 

Apparently, this IS an issue. So, where do i go from here?

EDIT****

I just followed your instructions in[ this]("http://ubuntuforums.org/showthread.php?t=2204271") thread, and installed gdisk. so, now can i proceed with the rest of your instructions in your first response to my thread?


When i first installed Ubuntu 13.10 also had same problem which i solved by using the <Try Ubuntu> then when in the Desktop you have the Usb drive files just click  Install Ubuntu

---

### Post by Bashing-om on 2014-02-13
The_Autonomist; You do good work .

OK, we got tools to work with,
so let's see what we are working on.

From the liveUSB -> "try ubuntu" -> Terminal :
Post the output of terminal commands:
```

sudo parted -l
sudo gdisk -l /dev/sda

```

And then we can have a looksee, Hopefully all we have to do is (re-)install grub to the EFI partition (??).

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by The_Autonomist on 2014-02-13
sudo parted -l yields this: 
```
Model: ATA SAMSUNG HM641JI (scsi)
Disk /dev/sda: 640GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  210MB  209MB   primary   ntfs            boot
 2      210MB   311GB  311GB   primary   ntfs
 3      311GB   640GB  329GB   extended                  lba
 6      311GB   631GB  320GB   logical   ext4
 5      631GB   640GB  8651MB  logical   linux-swap(v1)
 4      640GB   640GB  108MB   primary   fat32           lba


Warning: The driver descriptor says the physical block size is 2048 bytes, but
Linux says it is 512 bytes.
Ignore/Cancel? ignore                                                     
Error: No valid partition map found.
```

sudo gdisk -l /dev/sda yields this: 
```
GPT fdisk (gdisk) version 0.8.7

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. 
***************************************************************

Disk /dev/sda: 1250263728 sectors, 596.2 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 8FCDD581-7F01-4D37-BFF6-C90ACD571DBB
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1250263694
Partitions will be aligned on 2048-sector boundaries
Total free space is 6077 sectors (3.0 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          409599   199.0 MiB   0700  Microsoft basic data
   2          409600       607651839   289.6 GiB   0700  Microsoft basic data
   4      1250050048      1250261679   103.3 MiB   0700  Microsoft basic data
   5      1233154048      1250050047   8.1 GiB     8200  Linux swap
   6       607653888      1233154047   298.3 GiB   8300  Linux filesystem
```

---

### Post by Bashing-om on 2014-02-13
The_Autonomist;

Sorta floundering right now, I did not expect to see a boot partition sda4 "4      640GB   640GB  108MB   primary   fat32           lba"
As well as sda1 -> " 1      1049kB  210MB  209MB   primary   ntfs            boot"

But in the meantime while I am pondering.

Is the file system intact ?
Let's look:
```

sudo mkdir /mnt/work
sudo mount /dev/sda6 /mnt/work

```
That should mount the ubuntu partition; -> ;look around ->
```

ls -la /mnt/work/home/<your_user_name>
ls -la /mnt/work/home/<your_user_name>/Downloads
##or where ever you want to look##

```

All done looking around ? ReMeMbeR, one must unmount that partition that we mounted !
```

sudo umount /mnt/work

```


OK, file system is intact ?

(RE-)install grub, and I gotta find out about the doubled up boot partition.. This may not happen in this session !

[INDENT][INDENT]if I knew everything,
[INDENT][INDENT][INDENT]I would not be me
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by The_Autonomist on 2014-02-13
hmm...that is odd. i never realized it before. all i remember is when i first unstalled ubuntu alongside win7 a few years back i split the harddrive into 2. one half for linux and one half for win7. i recall that windows partitioning system required me to keep a separate partition for "SYSTEM" and another for HP_TOOLS but that's it.

but, onto re-installing grub. when i typed the command "grub-install /dev/sda" it yielded this:

```
rm: cannot remove &#8216;/boot/grub/i386-pc/915resolution.mod&#8217;: Permission denied


```

when i added "sudo" in front, it yielded this: 

```
Path `/boot/grub' is not readable by GRUB on boot. Installation is impossible. Aborting.
```

---

### Post by Bashing-om on 2014-02-13
The_Autonomist; Hold everything !

EFI puts a different perspective on things such that  "grub-install /dev/sda" is inappropriate.
That is to install grub onto the legacy partitioning scheme, we need to install to the EFI partition.
I am not Windows literate but I still do not follow that there are the 2 EFI partitions. I am going to have to do some homework on that prior to advising where/how to install grub.

Along that line of thought. Is your system AMD 64 architecture ?

We are going to chroot into the install from the liveUSB, mount some stuff, "modprobe efivars" and install grub; then back out of the chroot.
If you want a shot in the dark, well we can do that, but, I am not certain of the EFI partition sda1.

Ask yourself, is the risk worth the gain ? I can take a shot at it !

[INDENT][INDENT]I like my ducks in a row
[/INDENT][/INDENT]

---

### Post by The_Autonomist on 2014-02-13
hmm, EFI rang a bell. i remember why. when i entered the command "sudo fdisk -lu" it yielded this: 

```
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x99fd87a4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS/exFAT
/dev/sda2          409600   607651839   303621120    7  HPFS/NTFS/exFAT
/dev/sda3       607653886  1250050047   321198081    f  W95 Ext'd (LBA)
/dev/sda4      1250050048  1250261679      105816    c  W95 FAT32 (LBA)
/dev/sda5      1233154048  1250050047     8448000   82  Linux swap / Solaris
/dev/sda6       607653888  1233154047   312750080   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 2003 MB, 2003828736 bytes
255 heads, 63 sectors/track, 243 cylinders, total 3913728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5017c91c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           0     1808383      904192    0  Empty
/dev/sdb2         1791448     1795991        2272   ef  EFI (FAT-12/16/32)

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb1'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb1: 925 MB, 925892608 bytes
255 heads, 63 sectors/track, 112 cylinders, total 1808384 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5017c91c

     Device Boot      Start         End      Blocks   Id  System
/dev/sdb1p1   *           0     1808383      904192    0  Empty
/dev/sdb1p2         1791448     1795991        2272   ef  EFI (FAT-12/16/32)


```

It's odd, none of my /dev/sda drives are EFI. but, this drive /dev/sdb has the EFI partition. sda is my interna; harddrive, and i do not presently have my external HD plugged into my notebook. the only other drive i have on my notebook right now, is my USB drive. could this be the /dev/sdb? what else could it be? and yes, my notebook is AMD64.

---

### Post by Bashing-om on 2014-02-13
The_Autonomist;

Yeah, I am out in left field, not paying close enough attention to what we are doing !

Let's install grub !

From the liveUSB -> terminal:
```

sudo mount /dev/sda6 /mnt
sudo grub-install --boot-directory=/mnt /dev/sda
sudo umount /mnt

```

Reboot into the install and to pick up Windows:
terminal command:
```

sudo update-grub

```

[INDENT][INDENT]should workie great 
[INDENT][INDENT]last long time
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by The_Autonomist on 2014-02-13
okay! the first part went smoothly, without error. 

then, i restarted back into the ubuntu install > try ubuntu and typed 

sudo update-grub

i got this: 

```
/usr/sbin/grub-probe: error: failed to get canonical path of /cow.
```

HUH???

---

### Post by Bashing-om on 2014-02-13
The_Autonomist;

We want to do that "update-grub" from the real actual install.

So Boot the hard drive install and activate a terminal. In the installed system's terminal:
```

sudo update-grub

```

to chainload Windows to grub.

Advise now on results.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by The_Autonomist on 2014-02-13
YES!!!!!!!

```
Generating grub.cfg ...Found linux image: /boot/vmlinuz-3.11.0-12-generic
Found initrd image: /boot/initrd.img-3.11.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows Recovery Environment (loader) on /dev/sda2
done



```

THANK YOU, extremely kind and patient sir or madam!! If you are ever in the Houston area, i will buy you a beer/coffee/drink of your choice!

Thank you! My notebook is now fully functioning after 5 days, and everything is in tact and running like a charm. THANK YOU!!!!

---

### Post by Bashing-om on 2014-02-13
The_Autonomist; Outstandingly great !

You are quite welcome, just pass it along.

Last - as this was an unattended update, and things went west.
Let's make sure the system is all happy:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade ##apt get's smart mode to deal with any "held back" components##

```

If/when all comes back good, then ->
[INDENT] happy trails to you[/INDENT]

---

### Post by The_Autonomist on 2014-02-14
the updates and upgrades went flawlessly!
(call me crazy, but i think my computer runs better now after all the tinkering than it did previously lol)

thank you again, and i'll be sure to pass it on!!

---

