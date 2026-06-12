---
title: "Ubuntu install doesn't recognize Corsair SSD"
date: 2012-02-28
forum: Installation &amp; Upgrades
---

### Post by pzico on 2012-02-28
I have trouble getting my Ubuntu install to recognize my SSD HD.

I have tried following distributions: 11.10 and 12.04 (daily)

Motherboard: Gigabyte z68xp-ud3 
Processor: Intel i7-2600k 
Hard Drive: Corsair 60 GB SSD Force GT

- BIOS and firmware of SSD are the latest stable versions.
- AHCI mode has been turned on from the motherboard (if there are more than one place to modify AHCI settings on BIOS I may have missed some).
- SSD is connected to first SATA3 6Gb/s slot.

Any help is appreciated!

[edit] Solved. There were actually 2 different SATA3 controllers on motherboard and SSD works fine with the other.

---

### Post by darkod on 2012-02-28
If you have used the ssd in raid before to test it or run it, it might have raid meta data leftovers. Windows ignores them but ubuntu doesn't.

If you have used it in raid, and you ARE NOT running raid any more, boot ubuntu in live mode and in terminal try:
sudo dmraid -E -r /dev/sda

Confirm to remove the meta data and it should be fine.

Another option is to try it in another SATA port.

Also, ubuntu might not recognize the SATA3 ports on your mobo, try it in SATA2 port if it has any, although this is not really a solution because if it's a SATA3 SSD with high transfer rate, you lose out running it on SATA2.

---

### Post by oldfred on 2012-02-28
You have several potential issues since you have a cutting edge system and Linux often takes a while to work well or it requires extra settings to work.

SSD, BIOS vs. UEFI, SATA 3 GB/s or SATA 6GB/s and video modes all have been posted multiple times by users. I believer their are settings & work arounds for each but if starting from scratch and you are not familar with the issues it may seem like a lot.

Are you booting in UEFI or BIOS mode. Are you dual booting with Windows. If no Windows then gpt is suggested over MBR, whether UEFI or BIOS. Windows will only work with gpt if using UEFI.

Some have had issues with the new SATA ports, not sure if all the issues have been resolved.

What video card or are you using Intel internal video?

---

### Post by pzico on 2012-02-28
Thanks for quick reply! :D

> **darkod said:**
> If you have used the ssd in raid before to test it or run it, it might have raid meta data leftovers. Windows ignores them but ubuntu doesn't.

I haven't used RAID on this. I installed Windows 7 while SSD was still in IDE mode. Afterwards I changed from IDE to AHCI (at this point Windows 7 required one fix). 

> **darkod said:**
> If you have used it in raid, and you ARE NOT running raid any more, boot ubuntu in live mode and in terminal try:
sudo dmraid -E -r /dev/sda

Confirm to remove the meta data and it should be fine.

Another option is to try it in another SATA port.

Also, ubuntu might not recognize the SATA3 ports on your mobo, try it in SATA2 port if it has any, although this is not really a solution because if it's a SATA3 SSD with high transfer rate, you lose out running it on SATA2.

I'm a bit afraid that this might be the case. I don't want to use SATA2 for anything but diagnosis.

---

### Post by pzico on 2012-02-28
> **oldfred said:**
> Are you booting in UEFI or BIOS mode. Are you dual booting with Windows. If no Windows then gpt is suggested over MBR, whether UEFI or BIOS. Windows will only work with gpt if using UEFI.

Isn't this comment related to how system boots after install? My problem can be seen already at gparted (live environment) or the partitioner used by installer. Disc is not recognized at all and install can't proceed.
 
> **oldfred said:**
> 
What video card or are you using Intel internal video?

I've got Gigabyte HD 6770. Internal video is disabled.

---

### Post by pzico on 2012-02-28
Just noticed, that Gigabyte website says that my motherboard has 2 different controllers for SATA3 ports.
[I][B]
2 x SATA 6Gb/s connectors (SATA3_0~SATA3_1) supporting up to 2 SATA 6Gb/s devices 

1 x Marvell 88SE9172 chip:

   1. 2 x SATA 6Gb/s connectors (GSATA3_6, GSATA3_7) supporting up to 2 SATA 6Gb/s devices
   2. Support for SATA RAID 0 and RAID 1 [/B][/I]

This far I've been using SATA3_0, that doesn't have RAID support. Maybe I could give a try for GSATA3_6 port? Or is it better to stick with the first non-RAID capable SATA3 port?

---

### Post by darkod on 2012-02-28
RAID or non-RAID means nothing if the setting in BIOS is set to AHCI. For raid capable ports (controller) you would have options RAID, AHCI, IDE. Unless you set it to raid, it's not using raid.

Try the other controller too with setting AHCI.

---

### Post by oldfred on 2012-02-28
I think flash drives can also boot in UEFI. But if you installed Windows in IDE mode you probably still have MBR and then UEFI defaults to booting in BIOS mode from MBR.

You may just be having the video mode issues with flash drive. 

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Resetting an out&#8208;of&#8208;range resolution (does not include grub's set gfxmode=640x480)
[https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution](https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution)
Repair grub's video mode and other settings
[https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

These parameters may apply whether BIOS or UEFI.
[SOLVED] UEFI Boot Problems 
quiet splash vt.handoff=7 rootdelay=90 reboot=a,w
[http://ubuntuforums.org/showthread.php?t=1857639](http://ubuntuforums.org/showthread.php?t=1857639)

---

### Post by pzico on 2012-02-28
@oldfred: I think here are 3 choices (not mutually exclusive)
1: I didn't articulate my problem well
2: You misunderstood my problem
3: There is something fundamental knowledge I'm missing. This is very likely.

To get my head straight and learn something new, I would like to ask this:
Can contents of the MBR have any connection to recognition of HD by gparted?

---

### Post by darkod on 2012-02-28
oldfred, I am confused too.
We are talking here about a hdd (in this case ssd) that is not even recognized in Gparted or the installer, but it is recognized correctly in BIOS and has win7 installed without problems.
How could video issues be connected to this? Are we missing something?

OP: If win7 is installed boot it and see in Disk Management whether the disk is Basic (it should be) or Dynamic (linux doesn't install on dynamic).
Also, do let us know if you are booting with BIOS or EFI. It can help.

Also, boot ubuntu live mode and post the output of:
sudo fdisk -l (small L)

Does it detect the ssd or not?

---

### Post by pzico on 2012-02-28
I tried yesterday:
```
sudo fdisk -l
```
and
```
dmesg
```

I couldn't find any signs of my SSD. dmesg was able to show that some sata3 (maybe the marvell chipset one) got logged during boot. But not mapping it to any /dev/xxx

---

### Post by darkod on 2012-02-28
I think it's time to try a sata2 port, just to see if it shows up.

---

### Post by pzico on 2012-02-28
Ok, I found the problem. My SSD was actually in SATA3 slot controlled by Marvell chip. When I changed to other SATA port (SATA3_0), SSD was recognized by Ubuntu. So I had put by mistake my SSD on other slot than intended. Thanks for help :popcorn:

---

