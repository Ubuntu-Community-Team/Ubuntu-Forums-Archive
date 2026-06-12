---
title: "Ubuntu 6.10 - &quot;hda: DMA disabled&quot; and my PC hangs"
date: 2006-11-08
forum: Installation &amp; Upgrades
---

### Post by Boneless on 2006-11-08
I have downloaded the Desktop CD of the latest Ubuntu release, burned it, and soon after that I tried booting it. OK, I get to the first screen (where it lets you choose between the various choices), I choose the default choice (after changing the language to Italian), but the computer hangs soon after. I tried the graphics safe mode (I have an ATI Radeon something - can't remember the exact model - so I assumed there must be some driver problems), just the same. I tried then to start Ubuntu in verbose mode (from the boot options, I deleted "quiet" and "splash"), and it seems the PC hangs as soon as the CD tries to access my HDs. I have WinXP installed, with NTFS filesystems on both HDs. Now, it incurs in a few errors for each HD (something that's got to do with IDs o something similar), then, after trying two or three times (it's all very fast, it doesn't stop) the PC hangs after displaying "hda: DMA disabled". What's the problem?

P.S.

My PC is an IBM Netvista.
CPU: Intel Pentium III 863 MHz
RAM: 256MB PC133 (used to be 128MB)
GPU: ATI Radeon 9250 (has been added lately)

HDs: 2 Seagates, 20GB and 15GB.

And here's what comes on screen before crashing...

```
hda: dma_intr: status=0x51 {DriveReady SeekComplete Error}
hda: dma_intr: error=0x10 {SectorID NotFound} LBAsect=39876480, sector=39876480
ide: failed opcode was : unknown

hdb: dma_intr: status=0x51 {DriveReady SeekComplete Error}
hdb: dma_intr: error=0x84 {DriveStatus Error BadCRC}
ide: failed opcode was : unknown

hda: dma_intr: status=0x51 {DriveReady SeekComplete Error}
hda: dma_intr: error=0x10 {SectorID NotFound} LBAsect=39876480, sector=39876480
ide: failed opcode was : unknown

hda: dma_intr: status=0x51 {DriveReady SeekComplete Error}
hda: dma_intr: error=0x10 {SectorID NotFound} LBAsect=39876480, sector=39876480
ide: failed opcode was : unknown

hda: dma_intr: status=0x51 {DriveReady SeekComplete Error}
hda: dma_intr: error=0x10 {SectorID NotFound} LBAsect=39876480, sector=39876480
ide: failed opcode was : unknown

hda: DMA disabled
```

---

### Post by Boneless on 2006-11-08
Sorry for the double post... the main problem is that it's a serious issue, for my PC... 1 single HD (15GB, as well) is not enough for me, I'm a musician, and I record a lot... and I need the most space I can get, and I can't afford to "lose" a hard disk this way.

I'm sorry if I sounded bad mannered and insolent, but it's urgent for me to fix this problem...

---

### Post by foxmulder on 2006-11-08
Ok: you never got so far as to install anything right?

I'm no expert, but somehow it might be that your PC lost it's BIOS settings and maybe doesn't know the HD sizes anymore?

Try to go into the bios and see if it sees your HD's correclty and if the size reported is right.

If possible change it to autodetect and see if that works booting again.

If that is not the cause then it looks like your HD might be failing. Given the fact they are 15 and 20gb they sound rather old...

Good luck!

---

### Post by Boneless on 2006-11-08
I solved the problem (temporarily) by telling the kernel not to probe hda. The thing is: if I tell the kernel not to probe ANY hard disk (meaning, either one or the other, there is no difference), the system boots all right... I tried not to probe hda, and it worked. I tried not to probe hdb, and it worked just the same. Thing is, I needed to install Ubuntu on hdb, so I decided to boot the Ubuntu CD with hda=noprobe, and I installed Ubuntu on the second hard disk. After that, I set GRUB not to probe hda (again) and it works all right. I tried telling the kernel the HD's geometry, but it hangs just the same as before. My suspect is that there must be a problem in probing BOTH hard disks at the same time, probing only one at a time doesn't make any problems... I might try to change the connections between the HDs, maybe I can solve the problem making this HD Primary Master (or Secondary master).

---

### Post by foxmulder on 2006-11-08
Actually when you search Google for IBM Netvista and hda DMA disabled you will find many posts about a bug in the Netvista architecture and many other Linux distro's have a problem with that PC...

From your post I did not see if you even got to install it or not...

---

### Post by loclei on 2006-11-09
i have a problem too
when i put the cd and run install - first option in the menu- after a while i get this message:
[1719705.296000]hdd:timeout waiting for DMA
[1719705.300000]hdd:drive not ready for command
and after that i get something like  hdd can't access sector number *******

---

### Post by Boneless on 2006-11-09
Yes, I did install it... but, as I said, without probing hda at all. So now Ubuntu recognizes hdb (well, it's installed on it :D ), but not hda. No problem though with the DVD burner.

---

### Post by tedrogers on 2006-11-11
Are you sure you have your master / slave set-up right? And the DVD/CD on a different and separate IDE from the the HD's? If you're not too hot with master / slave's you can put both drives on cable select and it will figure it out for you when booting.

Go into the BIOS and set everything for HD's to auto if possible. You may also be able to force to turn off DMA in the BIOS. Get the latest firmware for your BIOS as well...this could be a known issue that is addressed by IBM/Lenovo.

Failing all of that, bearing in mind that there were many other people who have your machine having problems with lots of linux distros (as suggested by Googling)...then I would pop onto a popular auction site and get a different motherboard for as cheap as possible.

It sounds like a very old machine and as such the parts won't cost much. It doesn't even have to be an IBM motherboard, you can just build a hybrid PC and it should work in theory, as long as you match the specs as closely as possible, i.e. mainly FSB speed for your CPU and RAM. I recommend ASUS, Gigabit or MSI boards....though Intel ones are good too.

Hope some of this helps.

---

### Post by Cloaked on 2007-11-26
> **loclei said:**
> i have a problem too
when i put the cd and run install - first option in the menu- after a while i get this message:
[1719705.296000]hdd:timeout waiting for DMA
[1719705.300000]hdd:drive not ready for command
and after that i get something like  hdd can't access sector number *******

I have a similar problem.

"[  183.239166] hda: timeout waiting for DMA
 [  188.233102] hda: drive not ready for command
 [  249.400922] hda: timeout waiting for DMA"

It just keeps on repeating like that. The numbers change but it looks like they do so randomly.


Hardware:
CPU: Intel Core 2 Duo 2.4ghz
Mobo: ASUS P5N32-SLI SE Deluxe
Optical: HP|dvd840i
HDD: Two SATA (3gbs) 7200rpm 250gb Seagate Barracudas

One Hdd is ready to be formatted and have Ubuntu installed while the other has my XP Pro 64bit edition install on it as well as my data.


P.S.

I haven't been able to get any linux install to work yet on my 64bit intel >_<

---

