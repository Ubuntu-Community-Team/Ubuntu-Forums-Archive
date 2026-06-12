---
title: "[SOLVED] USB-CF install, later to CF-IDE adapter; Grub problems"
date: 2008-06-08
forum: Installation &amp; Upgrades
---

### Post by grinningleopard on 2008-06-08
Okay, I'm relatively new to ubuntu, but not to linux. I have used mint in the past though so I'm not totally deficient. What I want to do is this:

-install a CLI Ubuntu on my very tired PIII600 192mb Thinkpad 

then 

-build desktop/programs to suit my needs and hardware ( eg openbox, abiword rather than the hefty gnome, openoffice default)

First hurdle is that the thinkpad in question doesn't have a cdrom, and is using a 2gig CF card for HDD, so I used my main laptop to install ubuntu (CLI) from the alternate install CD (CF hooked up to usb reader) Install went fine, took about 500mb of the 1.6gb partition. To avoid confusion with drive names I skipped the grub install, planning to add to my existing one from another disto (I have a seperate partition for grub, followed by my puppy linux install) Seemed sensible at the time. Probably wasn't.
So I put the card back in the laptop, booted into puppy and edited my menu.lst to include ubuntu thus: 

# Linux bootable partition config begins
  title Ubuntu Hardy (on /dev/hda6)
  root (hd0,5)
  kernel /boot/vmlinuz-2.6.24-16-generic vga=792 root=/dev/hda6 ro quiet splash
  initrd /boot/initrd.img-2.6.24-16-generic
  boot
# Linux bootable partition config ends


Which brings me to my problem. It boots the kernal and notes the apm bios, but then loops an incessant stream of data which looks like dma stuff but I might be wrong. Is there something I missed in the appends? I already tried ide=nodma and ide0=nodma to no avail. Here's a sample from the start of the loop:

[  44.885338] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[  44.886802] ata1.00: status: { DRDY }
[  75.081537] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen

what follows is all much the same for a dozen lines before this:

[  196.774765] Buffer I/O error on device sda, logical block 0
        check root= bootarg cat /proc/cmdline
        or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/hda6 does not exist. dropping to a shell!

after which it displays a busybox shell, then repeats the above ad nauseum with different (increasing) numbers at the start between the [...]s. I've booted into puppy and checked and the ubuntu files are all in hda6, so i can't quite see what it's problem is - any help is greatly appreciated!

many thanks



GL

---

### Post by grinningleopard on 2008-06-08
marked as solved, found a simpler way using Debian (not too much of a defection i hope!)


GL

---

