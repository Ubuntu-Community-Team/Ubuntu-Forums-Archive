---
title: "Annoying Dual Boot/Grub2 Problem"
date: 2012-07-13
forum: Installation &amp; Upgrades
---

### Post by gameplay on 2012-07-13
I have two hard drives.  Disk A has my Windows installation.  Half of Disk B is an NTFS partition used for storage and backups of Disk A etc.  The other half has Ubuntu 12.xx installed.  

Usually my BIOS are set to boot from Disk B which pulls up the GRUB2 menu.  If I then boot into Windows via GRUB2 everything is fine EXCEPT when windows backup runs.  Then an error occurs. (The backup backs up Disk A onto the NTFS partition on Disk B.)

If I change the BIOS and boot from Disk A directly (ie into Windows directly avoiding GRUB2) backups run fine.

The problem is something to do with the fact that booting into Disk A directly, and using Windows disk manager, Disk A is the first listed (ie as '0') while Disk B is second or '1'.  The order is reversed if I boot into Windows via GRUB.

This problem was avoided when I had GRUB rather than GRUB2, by 'swopping' the drives using something like 
map hd0 hd1 and 
map hd1 hd0 or something like that.  

This seemed to 'fool' windows into accepting Disk A as as device '0' and Disk B as device '1.

The new Drivemap command does not appear to work in the same way.  Is this an error with drivemap or what?

I know this is a minor problem but it appears to be a backward step - and is really annoying when it comes to regular backups, as I have to go into BIOS to change the boot disk back to DISK A.

Any help appreciated.

---

### Post by black veils on 2012-07-13
maybe i dont know what i am saying, but cant you just set grub to be in the first disk?

---

### Post by drs305 on 2012-07-13
You might be able to work around your issue by using Grub 2's device.map file. It is located in /boot/grub and you can create it with:
```
sudo grub-mkdevicemap
```

Normally the device.map file doesn't exist, but when I created one with the above it produced this in /boot/grub/device.map
> (fd0)	/dev/fd0
(hd0)	/dev/disk/by-id/ata-ST3320620AS_9QF3KKYY
(hd1)	/dev/disk/by-id/ata-WDC_WD6400AAKS-22A7B2_WD-WMASY7162178

You might be able to run the command, reverse the order, and update-grub. I've no idea if this will solve your Windows issue however.

---

### Post by gameplay on 2012-07-14
Thanks drs305. 

I ran the command and hd0 is showing as the Windows disk (drive A in my post) and hd1 as Drive B with Ubuntu on it. 

Bear in mind that I am not an expert, and I am not sure what you mean by 'reverse the order'.  Isn't Drivemap supposed to do that?

BlackV - I don't want to put grub on Drive A as I want my windows disk left alone, and besides that wouldn't really be solving the problem which, as I said in the original post, seems to be associated with grub2 or the drivemap command.  Everything is fine apart from this reversal of drive order in Windows, which for a reason I don't know, causes windows backups to fail.

---

### Post by drs305 on 2012-07-15
> **gameplay said:**
> Thanks drs305. 

I ran the command and hd0 is showing as the Windows disk (drive A in my post) and hd1 as Drive B with Ubuntu on it. 

Bear in mind that I am not an expert, and I am not sure what you mean by 'reverse the order'.  Isn't Drivemap supposed to do that?

I don't know exactly what "Drivemap" is regarding Grub. Grub uses the device.map file if it exists to order the drives. If you reverse them then in device.map (keep the lines the same, but change hd0 to hd1 and hd1 to hd0) Grub will treat Windows drive as hd1 and Ubuntu as hd0.

If you make the change make sure you save the device.map file and update-grub.

I don't know if this will help your situation or not.

---

### Post by gameplay on 2012-07-19
Thanks drs305.  I will try this when I get back to the dual boot machine.


In case anyone is interested - found this on drivemap 


14.3.12 drivemap
 — Command: drivemap -l|-r|[-s] from_drive to_drive

Without options, map the drive from_drive to the drive to_drive. This is necessary when you chain-load some operating systems, such as DOS, if such an OS resides at a non-first drive. For convenience, any partition suffix on the drive is ignored, so you can safely use ${root} as a drive specification. 

With the -s option, perform the reverse mapping as well, swapping the two drives. 

With the -l option, list the current mappings. 

With the -r option, reset all mappings to the default values. 

For example: 
          drivemap -s (hd0) (hd1)

---

### Post by kreemoweet on 2012-07-19
I very seriously doubt that any windows backup app is going to consult the Grub diskmap
on the linux partition!

This is a serious bug in your Windows backup software; it is well known that disk ordinals
reported by BIOS are pretty much arbitrary and should not be relied on. on my own machine, the disk numbers shown in Windows Disk Manager never change no matter
which disk is set as first in the BIOS boot order. I am sure there are
many disk backup programs that do not have this error. Some are even free.

---

