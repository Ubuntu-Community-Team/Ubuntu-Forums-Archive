---
title: "Dual boot, dual HD grub update error"
date: 2012-10-23
forum: Installation &amp; Upgrades
---

### Post by christerkl on 2012-10-23
I have a dual boot (Windows7 + Ubuntu 12.04), dual harddisk system with the usual Win7 partitions on /sda1 .. 3 (FAT, Recovery, OS) and several patitions on /sdb, including Ubuntu 12.04 (on /sdb5):

Model: ATA ST9500420AS (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  231GB  231GB   primary   ntfs            boot
 2      231GB   373GB  142GB   extended
 5      231GB   360GB  129GB   logical   ext4
 6      360GB   365GB  5243MB  logical   linux-swap(v1)
 7      365GB   373GB  7867MB  logical   ext4
 3      374GB   463GB  89,2GB  primary   ntfs
 4      479GB   500GB  21,0GB  primary   ntfs

(/sdb1 is actually a standard ntfs partition, not bootable)
Everything is working OK, including several upgrades from 10.04 and upward.
Upgrading to 12.10 wrecks everything, and makes the computer unbootable, just the "grub resque" prompt is present.
Could it be that the new Grub2 fails to write to the primary HD also when upgrading to 12.10 ?
Can this be done manually ?

---

### Post by darkod on 2012-10-23
Yes, you can add grub but you have to use a cd of the same version as the OS (for example 12.10 if you already have the 12.10 installed/upgraded).

From live mode in terminal you need to mount your root partition, not sure if it's sdb5 or sdb7, use the correct number:
```
sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
```

That will install grub2 to the MBR of /dev/sdb. If your root is actually /dev/sdb7 use that in the first command instead of /dev/sdb5.

Note: This only installs the small grub2 code to the MBR and will work if the rest of the grub2 installation and config files are good. If the config is messed up you will need to run a slightly longer set of commands, but you can do that from live mode too.

---

### Post by Lythala on 2012-10-23
I have almost same problem with my dual boot system.

I have asus n53jq and theese laptopts have dual boot system with windows7 and express gate (which is a linux too)
I didn't used the express gate so i wanted to change it to UBUNTU. in the past works well but today after the upgrade cannot works. 

I can load this ubuntu with the secondary power button, no other options. The secondary power button will start a built in grub and i had to change the details inside

```
default saved
timeout 0
hiddenmenu

title minik
kernel /grub.exe
title Win_1 
```

after this the grub will try start the grub on c:\

thats config is:

```
timeout 0
default 0
hiddenmenu

title Ubuntu 11.10
root (hd0,2)
kernel /boot/grub/core.img
```

i did it on last year. So nowdays with this configuration the 2nd grub cannot start the sda3's grub with ubuntu. 
the error message is:
```
Booting Ubuntu 11.10
FIlesystem type is ext2fs, partition type 0x83 kernel /boot/grub/core.img
Error 15: File not found

Press any key to continue...
```

so how can i repair it? i installed the ubuntu 12.10 and the boot loader on sda3 too

---

### Post by darkod on 2012-10-23
@Lythala, you should have opened your own thread, your problem is not the same. Plus, you are running a different, customized setup, and posting code here can confuse the OP.

The message you are getting is clear, it can't find the core.img file. Double check that it exists.

If you want to, you can try running grub2 instead of the built-in grub but I am not sure how to do that. Alternatively, put the grub2 from ubuntu on the sda MBR and use it as main bootloader.

Also, the code you have for the ubuntu entry does not call ubuntu's grub2, it only tries to load core.img directly which is not the same. To try and call the grub2 you installed on sda3 would be like:
title Ubuntu 11.10
root (hd0,2)
chainloader +1

That will chainload the bootloader on the sda3 partition, which is the grub2.

But first double check whether core.img is really there or not, maybe this is what is missing.

---

### Post by Lythala on 2012-10-23
> **darkod said:**
> 
chainloader +1

That will chainload the bootloader on the sda3 partition, which is the grub2.

But first double check whether core.img is really there or not, maybe this is what is missing.


with that options works well, thanks!

---

### Post by christerkl on 2012-10-23
Thank's darkod. 
Just a few more questions to make me understand grub better: Is there a grub MBR record also on /sda (the primary, Win7 HD) in my system ? /sda1 or /sda3 ?
I suppose that this grub - if it exists - still is version 1.99 (?), does this also need to be updated ? If so, how ?

---

### Post by darkod on 2012-10-23
We can't tell right now if there is also grub on the MBR of /dev/sda.

Grub as bootloader usually goes to MBRs, never to partitions except special circumstances. So the device for grub installation would always be /dev/sda, /dev/sdb, etc and NOT /dev/sda1, /dev/sdb5, etc. I'm sure you know that the number means a partition #.

If you want detailed look into your bootloaders on both disks, including much more info, you can run the boot-repair to create the bootinfo summary. You can use it only to create the summary, you don't actually need to run the Recommended Repair, but you can if you want to. In many cases it repairs boot problems automatically.

You can run it from ubuntu live mode.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by christerkl on 2012-10-23
Does boot-repair work with both 12.04 and 12.10 ? (grub 1.99 / 2) ?
I think that there must be some grub code on both /sda and /sdb i my case, due to the way grub behaves after trying to (without success) change the way it is displayed at startup time.

---

### Post by darkod on 2012-10-23
> **christerkl said:**
> Does boot-repair work with both 12.04 and 12.10 ? (grub 1.99 / 2) ?
I think that there must be some grub code on both /sda and /sdb i my case, due to the way grub behaves after trying to (without success) change the way it is displayed at startup time.

As far as I know, yes, it works.

---

### Post by christerkl on 2012-10-23
End of story: boot-repair fixed the no-boot problem so that I could boot into 12.10, just to find that my graphics system/card/drivers suddenly were not supported anymore. After spending a few hours trying to correct this problem I gave up.
Back to 12.04. Maybe 13.04, but NEVER 12.10 !!!

---

### Post by YannBuntu on 2012-10-24
Hello

> **christerkl said:**
> my graphics system/card/drivers suddenly were not supported anymore.

Can you boot on a 12.10 liveCD ? if no, try to [boot on it with the 'nomodeset' option.]("https://help.ubuntu.com/community/BootOptions#Changing_the_CD.27s_Default_Boot_Options")
If the 'nomodeset' option works, you just need to install 12.10, then use Boot-Repair --> Advanced options --> GRUB options --> tick Add a kernel option: nomodeset --> Apply.

Whatever the result, you should report the bug on Launchpad ('ubuntu-bug linux' command).

---

