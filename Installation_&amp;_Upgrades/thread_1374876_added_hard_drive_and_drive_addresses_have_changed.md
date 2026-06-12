---
title: "added hard drive and drive addresses have changed"
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by mick222 on 2010-01-07
My computer was overheating and after blaming everything from memory to cpu I discovered the fan on my psu was broken so fixed that and at same time cleaned everything added 512mb ram giving 1gb total and a 180 gb sata hdd from a computer with a faulty graphics card.
 so now i have 1 gig ram 3hdd two ata one 40gig with ubuntu one 80gi with suse and one 16o gig which i plan to use for lucid and Mandriva.
 
  Ok so now the problem After reconnecting everything my new sata driveis Master so my 40 gig drive is now dev/sdc formally dev/sda  . So i changed it to boot from this drive in the bios. After booting i decided to run update-grub as i was getting an error Cant mount partition which is just a swap partition so i'm not to bothered about it . i get this error


>  Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
grub-probe: error: Cannot find a GRUB drive for /dev/sdc1.  Check your device.map.


 
So how do i repair the device.map
file:///home/mick1/Desktop/system.png

---

