---
title: "Massive fails installing 22.04 LTS"
date: 2022-09-22
forum: Installation &amp; Upgrades
---

### Post by keepitsimpleengr on 2022-09-22
[LIST=1]
[*]Downloaded 22.04 via torrent, loaded on USB with rufus, would not install on empty, new SSD
[*]Disconnected all drives but DVD and new SSD, live-cd would not boot on computer 
[*]Downloaded 22.04 on another computer, loaded on USB with rufus, computer would not boot off USB
[*]Burned iso to DVD, the computer would not boot disc error
[*]Burned iso to another DVD, live-cd hung during install
[*]Downloaded 22.04 on Linux computer, burned iso to another DVD, live-cd hung during install running some systemd
[*]Retried with the simple graphic install. live-cd again hung, screen pix attached 
[/LIST]

[IMG]https://drive.google.com/file/d/1kFBC-ps0rpRE5JFpyayMVgZ8TQ92V2sO/view[/IMG]

Attach failed

[https://drive.google.com/file/d/1kFBC-ps0rpRE5JFpyayMVgZ8TQ92V2sO/view?usp=sharing]("https://drive.google.com/file/d/1kFBC-ps0rpRE5JFpyayMVgZ8TQ92V2sO/view?usp=sharing")

---

### Post by ne29914 on 2022-09-22
The "mtd device..." error is well-known for months, that it hasn't been fixed yet is a mystery to me. It's extremely annoying but not catastrophic.
Your install problems look more like BIOS setting issues to me.

EDIT: Yay!! Just ran an upgrade and the obnoxious "mtd device..." error is gone. Joy!

---

### Post by ubfan1 on 2022-09-22
Did you ever hashcheck the dowloaded ISO, although using a torrent I'd think that wouldn't be necessary.  For DVDs, burn as slowly as possible, then if a media check is offered, run that.  Are we talking about a UEFI install?  SSDs do have possible firmware updates, ever check you model?  Likewise motherboards/laptops get firmware updates, good to check for those.  I usually just use dd to burn the ISO to a USB stick, so can't offer any advice on Rufus.  Installing to an SSD as a second disk will run into the launchpad bug 1396379, Grub installs to the wrong device (not the SSD you select).  That's what the disconnect should fix, but I find popping up a terminal in the install window and umount wrong ESP/mount the SSD's ESP then afterwards, editing the UUID into the SSD's fstab works for me.
There's another bug which might be fixed with the 22.04.1 ISO, 384633 -- Device gets used instead of a UUID on the target's grub.cfg, and of course, without the install media, the disk enumeration changes and that grub.cfg cannot find the root.  What machine are you trying the install on?

---

### Post by keepitsimpleengr on 2022-09-25
> **ubfan1 said:**
> Did you ever hashcheck the dowloaded ISO, although using a torrent I'd think that wouldn't be necessary.  For DVDs, burn as slowly as possible, then if a media check is offered, run that.  Are we talking about a UEFI install?  SSDs do have possible firmware updates, ever check you model?  Likewise motherboards/laptops get firmware updates, good to check for those.  I usually just use dd to burn the ISO to a USB stick, so can't offer any advice on Rufus.  Installing to an SSD as a second disk will run into the launchpad bug 1396379, Grub installs to the wrong device (not the SSD you select).  That's what the disconnect should fix, but I find popping up a terminal in the install window and umount wrong ESP/mount the SSD's ESP then afterwards, editing the UUID into the SSD's fstab works for me.
There's another bug which might be fixed with the 22.04.1 ISO, 384633 -- Device gets used instead of a UUID on the target's grub.cfg, and of course, without the install media, the disk enumeration changes and that grub.cfg cannot find the root.  What machine are you trying the install on?

Multiple downloads, multiple load to USB, multiple DVD burn. Too much effort for negative results.

Latest attempt, unable to launch live-cd, see link. 

[https://drive.google.com/file/d/1ZB4V7xKryhmNiUhq2wWsajNYj7V8C0ap/view?usp=sharing](https://drive.google.com/file/d/1ZB4V7xKryhmNiUhq2wWsajNYj7V8C0ap/view?usp=sharing)

Intel(R) Core(TM) 4 core/hyper i7-2600 CPU @ 3.40GHz
ASUS P8Z77-V LX LGA 1155 Intel Z77 HDMI SATA 6Gb/s USB 3.0 ATX Intel Motherboard
MBR boot
also runs archlinux, manjaro, debian, Windows10; ubunutu to be deprecated.... ...  ..   .

---

