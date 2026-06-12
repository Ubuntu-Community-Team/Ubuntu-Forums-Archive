---
title: "/dev/hda is now /dev/sda!"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by randysparks on 2008-04-29
I'm returning to Ubuntu with the Hardy release, after being a big fan up until around Dapper. 

When I install on an IDE system (not SATA), the Ubuntu installer identifies all my drives as SCSI —/dev/sda, rather than /dev/hda. When I install there are entries in /dev for sda and not hda.

What's the reasoning behind this? Pointers towards any tech docs would be very helpful. Cheers.

---

### Post by Pumalite on 2008-04-29
Since Feisty; hda, hdb, etc, are being recognized as sda, sdb, etc. It's normal.

---

### Post by FredB on 2008-04-29
It is normal. Since linux 2.6.19, naming changed :

[http://linux-ata.org/software-status.html](http://linux-ata.org/software-status.html)

---

### Post by randysparks on 2008-04-29
> **FredB said:**
> It is normal. Since linux 2.6.19, naming changed :

[http://linux-ata.org/software-status.html](http://linux-ata.org/software-status.html)

So it looks like MOST of the the old ATA drivers were merged into the SATA module...?

Does this mean on some rare systems that the drives might still be identified as /dev/hd* etc?

Also, does this mean that utilities like hdparm will still work?

---

### Post by wkulecz on 2008-04-29
Curious, My fresh 8.04 install shows /dev/hda4 mounted as / in the df command (as its should) and /dev/hdc and /dev/hdd for the CD/DVD drives

Mounting my 6.06 partition shows /dev/hda2 (as it should) mounted on /medial/disk

What I find more distressing, is all hard drives are now mounted via UUID which will wreek havoic if you are unfortunate enough to have to restore from backups down the road.

--wally.

---

### Post by randysparks on 2008-04-29
> **wkulecz said:**
> Curious, My fresh 8.04 install shows /dev/hda4 mounted as / in the df command (as its should) and /dev/hdc and /dev/hdd for the CD/DVD drives

Mounting my 6.06 partition shows /dev/hda2 (as it should) mounted on /medial/disk

What I find more distressing, is all hard drives are now mounted via UUID which will wreek havoic if you are unfortunate enough to have to restore from backups down the road.

--wally.

Can you find /dev/hda entries in the /dev folder? What about fstab? Does that refer in the comments to /dev/sda or /dev/hda?

Also, can you tell us what motherboard chipset you have? 

I'm not sure I can help you but I'm just curious to know how Ubuntu handles some machines.

---

### Post by bsh on 2008-04-30
> **Pumalite said:**
> Since Feisty; hda, hdb, etc, are being recognized as sda, sdb, etc. It's normal.

i have feisty onymy server with a nforce2 motherboard, and it recognizes ata drives as /hdx

---

### Post by ubnewbie2 on 2008-04-30
> **bsh said:**
> i have feisty onymy server with a nforce2 motherboard, and it recognizes ata drives as /hdx

As did gutsy.  This is new in hardy

---

### Post by randysparks on 2008-05-01
It looks like this switch to /dev/sda also breaks hdparm when it comes to optimisation settings ---the following is what I get using hdparm on an old PATA (IDE) drive connected via a ribbon cable to my nForce 2 motherboard:


```
john@john-desktop:~$ sudo hdparm /dev/sda

/dev/sda:
 IO_support = 0 (default)
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed:  Inappropriate ioctl for device
 HDIO_GET_KEEPSETTINGS failed:  Inappropriate ioctl for device
 readonly      =  0 (off)
 readahead     = 256 (on)
```

---

### Post by Patb on 2008-05-01
> **randysparks said:**
> Does this mean on some rare systems that the drives might still be identified as /dev/hd* etc?
Yes Randysparks, and on some not so rare.  I installed Debian Etch on a multi-boot setup and then  wondered why my Gutsy partition would no longer boot.  It turned out the Grub menu.lst installed by Debian referred to /dev/hdx for the Gutsy partition - all I had to do was change it back to /dev/sdx.  A small trap for the unwary I guess (not to mention reckless tinkerers like me :)).

Cheers, Pat.

---

### Post by wkulecz on 2008-05-01
Yes I have /dev/hda /dev/hda1 ... etc. entries.

Motherboard is Gigabyte GA-K8U-939 using ULi M1689 chipset & Gigabyte GV-N55 Series NVidia GeFOrce 5500 AGP video.

Two Thumbs Down to the einstien who came up with this!  Will wreek even worse havoic than UUIDs if you have to restore from backups for a failed motherboard and the new one is different!

--wally.

---

### Post by randysparks on 2008-05-01
> **Patb said:**
> Yes Randysparks, and on some not so rare.  I installed Debian Etch on a multi-boot setup and then  wondered why my Gutsy partition would no longer boot.  It turned out the Grub menu.lst installed by Debian referred to /dev/hdx for the Gutsy partition - all I had to do was change it back to /dev/sdx.  A small trap for the unwary I guess (not to mention reckless tinkerers like me :)).

Cheers, Pat.

My point was that some older IDE drivers are still included for old ribbon-cable IDE drives, but most now fall into the SATA camp. So most will be identified as /dev/sda by the kernel, and a minority as /dev/hda.

---

### Post by Kernel_Krunch on 2008-06-21
Hello, here is what is going on. _[http://kernelnewbies.org/Linux_2_6_19#head-cdcbaa9c1b476decdc064e0a75d23d1328b1ddce]("http://kernelnewbies.org/Linux_2_6_19#head-cdcbaa9c1b476decdc064e0a75d23d1328b1ddce")_

I think we are using the new "experimental" drivers.  The status report is mia... I have not looked into using the old drivers yet to benchmark, maybe someone can post a 'How To'.  I'm using Asus A8v motherboard.  It works but I'm not sure if its better or worse.  

JVR(or was it JRV...) in the kernelnewbies irc channel was kind enough to point this out and I said I would pass it along. Hope it helps.

---

### Post by LepeKaname on 2008-12-05
As someone said already, It was related to the kernel more than to an Ubuntu distribution. Am I right? I change from Ubuntu Hardy to Intrepid and I just notice it. 

Does someone could fix the "Inappropriate ioctl for device" error of hdparm?

The problem is that my hdd is so slow now... I can't even play some games and the last time I burned a DVD it tooks me 45minutes to burn a 2GB data!!!

I will search for more information about hdparm with this new kernel... if someone know it, please post it here.

Thank you

---

