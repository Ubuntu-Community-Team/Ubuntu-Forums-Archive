---
title: "PCI and buffer I/O error on Live boot"
date: 2006-06-10
forum: Installation &amp; Upgrades
---

### Post by Laddie on 2006-06-10
I'm attempting to install Dapper on a freshly built Pentium D 805 on an ASUS P5RD2-VM motherboard with a Maxtor DiamondMax 80GB SATA drive. Since I want to dual boot, my first attempt had Windows on one partition, with the other half of the hard drive unallocated.

At first I was having problems with ACPI, but that was fixed with the pci=noacpi boot command.

Now I get this error:
4294669.649000 PCI: Cannot allocate resource region 3 of device 0000:00:00.0

If I let it go for a while (as suggested on this forum), it will eventually repeat:
Buffer I/O error on device hda, logical block 357448.

See that block reference, I thought (and having nothing left to try) that it may be having trouble with the the way I set up the partitions, so I reformatted into one logical forum and tried again. Same thing. I am using a USB keyboard and mouse, and while I don't have access to a PS/2 set, I'm willing to go get some cheapies and give it a try.

Other things I have tried:
Enabled "Full Speed" (1.1) USB in BIOS
Manually set HD config (PTA, DMA, etc.) in BIOS instead of auto
Banging head against desk
Burning a 1X CD

I have downloaded the alternative install, but I think it may be over my head, especially since I want to dual boot.

---

### Post by az on 2006-06-10
"Buffer I/O error on device hda, logical block 357448."

Bad sector?

Run 

sudo badblocks /dev/hda

---

### Post by jon_herr on 2006-06-10
Anyone know what the nature of these type of errors are?

"4294669.649000 PCI: Cannot allocate resource region 3 of device 0000:00:00.0
"

I've seen this on three different PCs with newer chipsets.  I want to say it's a driver 'problem' although there are no symptoms - everything works.

---

### Post by Laddie on 2006-06-10
Well, I finally got it installing. I'll post an update when it's finished.

I scoured a couple IDE boot commands elsewhere in the forum. What ended up working was:

boot: live pci=noacpi ide=nodma ide=reverse

We'll see if this config issue also gives Dapper problems when it's running off of the HD. It sounds like this is the same "backwards drive scanning" everyone else is having. Funny thing is, I still got the "PCI: Cannot allocate resource region 3 of device 0000:00:00.0", but it started loading a few seconds after. I'm guessing that wasn't the real problem after all.

---

### Post by kenweill on 2006-06-12
I also have similar errors, a couple of lines similar to that below:

06/12/2006 03:39:51 PM	ubuntu	kernel	[  291.930891] Buffer I/O error on device dm-0, logical block 3153168

---

### Post by kenweill on 2006-06-12
Here's my screenshot of the error found in the system log.

---

### Post by FUSION6 on 2006-06-15
I get the buffer I/O error too, when installing Xubuntu

---

### Post by Laddie on 2006-06-15
Actually, I managed to get it installed, and have moved on to hardware issues (namely DRI not loading and a high pitched whine from the audio).

I decided I was going to blog my experiences, and of course, I'm a little behind:
[http://laddie.wordpress.com/](http://laddie.wordpress.com/)

Long story short if you don't want to read the whole thing, press F6 at the Live CD menu and use this boot command:
"boot: live pci=noacpi ide=nodma ide=reverse"

From what I've gathered on the forums, Dapper registers drives backwards for some reason. To be honest, I'm not sure where I picked up the "ide=nodma" command. The "pci=noacpi" is only if you're having trouble with ACPI and don't want to disable it in your BIOS.

Good luck. If anyone has experience getting Dapper to support the graphics and sound chips on the ASUS P5RD2-VM motherboard, please let me know. I've tried everything I could find so far. The hunt continues ;)

---

### Post by joe_lace on 2006-06-21
It isn't working for me.  There are already boot options in there when I press F6](*,) .  When add the ones listed here to the ones already in there I get the same error.  When I get rid of the options that are there and type the ones listed here I don't even get that far.

The errors I'm getting are as follows:

Buffer I/O error on device hda, logical block 318411

and directly after a string of those errors I'm getting one that says

SQUASHFS error: sb_bread failed reading block 0x9ab29
SQUASHFS error: Unable to read page, block 26ac8b28, size 1b06

---

### Post by kevinfreitas on 2006-08-14
I have the same motherboard but still can't get Dapper to install despite the line Laddie suggested using. I've also tried various combinations and even a download of Ubunto 6.10 -- still no luck.

Is this board just doomed not to run Ubuntu? If so, I'd like to RMA it right away -- can anyone recommend a good Micro ATX motherboard with SATA RAID 0/1 capabilities that does work with Dapper?

Thanks!

---

### Post by kevinfreitas on 2006-08-14
I have the same motherboard but still can't get Dapper to install despite the line Laddie suggested using. I've also tried various combinations and even a download of Ubunto 6.10 -- still no luck.

Is this board just doomed not to run Ubuntu? If so, I'd like to RMA it right away -- can anyone recommend a good Micro ATX motherboard with SATA RAID 0/1 capabilities that does work with Dapper?

Thanks!

---

