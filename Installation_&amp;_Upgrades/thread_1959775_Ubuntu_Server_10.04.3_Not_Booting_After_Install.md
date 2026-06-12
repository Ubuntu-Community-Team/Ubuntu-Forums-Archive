---
title: "Ubuntu Server 10.04.3 Not Booting After Install"
date: 2012-04-16
forum: Installation &amp; Upgrades
---

### Post by mjbardel on 2012-04-16
I’m installing Ubuntu server 10.04.3 on a PC which uses an Intel dual-core atom based processor.  This PC also has a 2TB drive in it. After which appears to be a successfully install the server will not boot. I get the following message when it try’s and boots up, “No Bootable Device—insert boot disk and press any key”. After getting this message I can boot off of the CD and choose “Boot from first hard disk” from the menu and successfully login to the server. Below is the output from running the “sudo fisk –l” command when I’m able to login.

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.
Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      243202  1953514583+  ee  GPT
Partition 1 does not start on physical sector boundary.

I’ve tried the installation (partitioning) using both guided and manual and get the same results. I get the impression that GRUB is not writing to the MBR of the hard drive. Any help would be appreciated.

Thanks

---

### Post by nothingspecial on 2012-04-17
*Thread moved to **Installation & Upgrades**.*

---

### Post by mjbardel on 2012-04-17
So, I went back to my old 9.10 (64 bit) server CD and the installation was successfully in that I could boot after the install. I then redownloaded and reburned the 10.04.3 server (64 bit) and reinstalled but with no success. I tried the same process again using 11.10 (64 bit) and once again I couldn't boot after the install.

I get the feeling Grub is the issue. Should Grub be installed on the MBR for this disk?

---

### Post by darkod on 2012-04-17
Yes, grub should be installed on the MBR. Otherwise, which bootloader will boot the OS?

So, what is the current situation, Server 11.10 installed?

Boot with a live cd in live mode and post the output of:
sudo parted /dev/sda unit s print

---

### Post by mjbardel on 2012-04-17
"So, what is the current situation, Server 11.10 installed?
"
I got the same results with 10.04.3. I can get through the install but the server will not boot. I've attached the output from the command you suggested to run.

---

### Post by darkod on 2012-04-17
Hmmm, maybe just the grub2 installation to the MBR failed. If you have a live cd with the same version (11.10 or 10.04 depending what is installed right now), you can try to add grub2 to the MBR.
Boot into live mode and in terminal try:
sudo mount /dev/sda2 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

If that doesn't fix it, try running the boot info script from the link in my signature. You can do that from live mode. Post the results, they will show more details.

---

### Post by mjbardel on 2012-04-18
sudo mount /dev/sda2 /mnt
When I ran the above command the prompt came back with no error messages.

sudo grub-install --root-directory=/mnt /dev/sda
After running the above command it came back with:
Installation finished. No error reported.

I then rebooted the PC and the same error came up. I will now try boot info script.

---

### Post by mjbardel on 2012-04-18
Output from boot info script is attached.

---

### Post by darkod on 2012-04-18
I can't see absolutely anything wrong, except one small thing which might be creating this error.

Because ubuntu doesn't need a boot flag as windows does, when you have only ubuntu it never sets the boot flag on any partition.
Some motherboards don't like this and think there is no bootable disk because they are used to expect the boot flag to exist on some partition.

Try setting it on /dev/sda2 with parted, like:
sudo parted /dev/sda
set 2 boot on
quit

Better do it from live mode, not sure if you can set the flag when the server has booted from sda2.

Check if the flag has been set with:
sudo parted /dev/sda print

---

### Post by oldfred on 2012-04-18
There was a bug in grub2 which may still be there, that on very large  (root) partitions it would just get lost and not boot. Boot script for some reason did not show locations of files on drive. Often an issue when some of grub is near front and some near end.

About half the users I have suggested just to shrink / to a much smaller size had then been able to boot. Not sure with a server if you want separate /home or separate /data and smaller system partition, as some server software may default to writing into root.

For Desktops  with separate /home a / (root) partition only needs to be 20 to 25GB but again for a sever that may be different.

---

### Post by mjbardel on 2012-04-18
I'll try using smaller partitions and see what happens. In the mean time I went back to my 9.10 server CD and installed it successfully and booted. I then ran boot info script with this version and attached the output to this reply.

Maybe you can take a look and see if you see anything different between the two outputs for a clue. Thanks for your help on this.

I guess I can always just upgrade from 9.10 to 10.04.3 (LTS) since the 9.10 install is working.

---

### Post by oldfred on 2012-04-18
Both your first and current boot scripts look normal to me.

You could add these so it shows the locations on the drive of the kernels & grub files it needs to boot. Often the issue is just they are not all near the beginning of the drive. 

Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

It is somewhat like the issue of booting with old BIOS that could only boot from the first 137GB and maybe some settings like IDE which should be LBA or large or AHCI. If you really want a large system partition, you could create a separate /boot partition.

---

### Post by darkod on 2012-04-18
Did you try my suggestion from post #9 about the boot flag?

Or is that same with the bios_grub flag oldfred? The message No Bootable device might mean the motherboard complains about not detecting the boot flag that linux doesn't use anyway.

---

### Post by oldfred on 2012-04-18
Grub does not use boot flag. Gpt has no specification for a boot flag. When gparted sets boot flag on gpt it really is saying it is the efi partition.

But you still may be correct as we have seen Intel motherboard's BIOS that will not boot without a boot flag whether msdos or gpt. So a boot flag with gpt may be the solution.

In libparted-based tools, you'd give it a "boot" flag (which is entirely unrelated to the MBR boot/active flag, although libparted makes them look the same). In gdisk, you'd give it a type code of EF00.

Add boot flag (even though not required with gpt) - see post by srs5694
[http://ubuntuforums.org/showthread.php?t=1563699](http://ubuntuforums.org/showthread.php?t=1563699)
Gparted did not add flag correctly but converted partition to efi???
[http://ubuntuforums.org/showthread.php?t=1686929](http://ubuntuforums.org/showthread.php?t=1686929)

---

### Post by mjbardel on 2012-04-19
Success!! The boot flag not being set for the bios_grub partition was the culprit. I don’t think I previously set this flag properly before. Using the links you provide in your reply I used fdisk to set the flag for /dev/sda1.

So, now the question is why does the CD install process work for v9.10 and not 10.04.3 or 11.10? I noticed from my previous replies (v9.10 boot script info) that the boot flag wasn’t set for that install either but it worked (would boot). Is grub2 the difference? I’m just curious and I can pose this question in a new thread if necessary. Thanks again for your help.

---

### Post by oldfred on 2012-04-19
Not sure of the difference with older grub2 vs. newer.

Separate Issue:
I do see your older install has the gpt partitions starting at sector 34. My older install 10.10 used that version of gparted and also started at 34, but that is ok with my old 160GB drive. With your new 4K 2TB drive you need to start on a sector divisible by 8.

First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)

---

