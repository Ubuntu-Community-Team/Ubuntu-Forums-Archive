---
title: "Help with Hard Drive problems"
date: 2015-12-30
forum: Installation &amp; Upgrades
---

### Post by bknauss on 2015-12-30
It seemed like my computer got hung up when I tried to encrypt a 1TB external harddrive. After I shutdown, my computer started giving me a "No bootable device -- Please restart system"

I'd like to recover my files or just fix whatever went wrong and get back to work. I tried using boot-repair, but did not have any option other than to generate a diagnosis report, which can be found at [http://paste.ubuntu.com/14279833/](http://paste.ubuntu.com/14279833/).

The drive is fully encrypted and uses LVM, I'm not sure if that matters.

---

### Post by chathamdavid1970 on 2015-12-30
In your diagnostics, I don't see your EXTERNAL drive, I see an internal drive and a USB stick. And the reason you can't boot is because you encrypted your internal drive and now there is no Operating System to boot to...

---

### Post by bknauss on 2015-12-30
The external drive was no longer connected when I ran the diagnostics. I'm pretty sure that I was encrypting the external drive and not writing over my internal drive. The thumb drive was boot-repair bootable drive.

---

### Post by bknauss on 2015-12-30
But I may have deleted the partitions of the internal drive, thinking that I was working with the external drive.

---

### Post by Elishasmantle on 2015-12-31
Hello,

Just a thought.

I'm a bit new to being a linux user and I am not very familiar with LUKS or whatever type of drive encryption you are using but from the years I do have in pc support hdd encryption can be very pain-staking. It takes a few hours to encrypt a drive, then the hdd seem temperamental to any changes to the drive, power surges, hard power-offs, changes to kernel or system files they deem not to like, etc... and then if a user needs the data it takes bootable media, decryption keys or other methods to get access to the data on the drive. 
Unless really needed I wouldn't use it.
If you only have smaller, more personal files you could always use something like 7zip and use password protection and their encryption they offer? Just a thought to avoid a possible headaches for yourself.

elishasmantle

---

