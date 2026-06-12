---
title: "Installing Ubuntu on a external hard drive"
date: 2008-03-23
forum: Installation &amp; Upgrades
---

### Post by Hoffmann on 2008-03-23
Hi All,

My machine is a new laptop Dell Inspiron 1520, and I intend to install Ubuntu on an external USB hardrive (which I didn't buy it yet). I check on my BIOS and I realized that I have the option for booting from a USB device. However, I am not a BIOS expert, etc.
My questions:

(1) Which USB external hard drive specification should I look for?
(2) I know that I need to format that external HD as ext3 type (this will be my Ubuntu room). Do I also need to create a small Linux swap partition on that HD? 
(3) How can I install Ubuntu on that external hard drive without screwing up my Windows OS which already "lives" on my laptop (internal HD)?
(4) I have previous experience on installing Ubuntu on the same hard drive (Windows-Linux dual boot on the same HD). In the case of installing on an external USB HD how does the booting process is carried out? Do I need to install GRUB, or that is not needed? If affirmative, what about when I were on a trip without my external HD? I mean, without using the external HD where Ubuntu will "live", how can I boot on Windows?

Could I hear from you guys?

Thanks.

---

### Post by toMeloos on 2008-03-23
> (1) Which USB external hard drive specification should I look for?

Get a 2,5" USB2 drive. Basically, about every drive you can get in a store is USB2. A 2,5" version is small and does not require an external power supply. This way you don't loose all of your laptop mobility :)

> (2) I know that I need to format that external HD as ext3 type (this will be my Ubuntu room). Do I also need to create a small Linux swap partition on that HD? 

Yes you do. Treat it like a normal linux disk. I normally choose a 10 Gb ext3 system partition with my ubuntu installation (probably never gets used for more than 50%), a swap partition equal to or double of the RAM size and the rest as a ext3 partition mounted as /home. this way you don't loose your important data if the system partition becomes corrupt (has happened to me several times already).

You might want to set swappiness to a very low value though, to reduce the amount of disk I/O's.

> 
(3) How can I install Ubuntu on that external hard drive without screwing up my Windows OS which already "lives" on my laptop (internal HD)?

See my post here: [http://ubuntuforums.org/showpost.php?p=4565720&postcount=6](http://ubuntuforums.org/showpost.php?p=4565720&postcount=6)

> (4) I have previous experience on installing Ubuntu on the same hard drive (Windows-Linux dual boot on the same HD). In the case of installing on an external USB HD how does the booting process is carried out? Do I need to install GRUB, or that is not needed? If affirmative, what about when I were on a trip without my external HD? I mean, without using the external HD where Ubuntu will "live", how can I boot on Windows?

Again, read my post here: [http://ubuntuforums.org/showpost.php?p=4565720&postcount=6](http://ubuntuforums.org/showpost.php?p=4565720&postcount=6)

First of all you need GRUB (or lilo) to start linux booting. I recommend you install it on the external disk and then place usb devices before internal hard disks in your boot sequence setting of your BIOS. This way, you get the GRUB boot menu when your external drive is plugged in. GRUB will also allow you to start Windows. If it's not plugged in, your laptop will just load Windows right away.

If you allow GRUB to install itself on the Master Boot Record of the internal disk, you can't boot into Windows without having your external disk plugged in anymore. That would be irritating given the fact that you can avoid this issue as described above.

---

### Post by Pumalite on 2008-03-23
I agree that disconnecting the internal drive is the safest way for a newbie, but in a laptop sometimes this is difficult. In that case; installing with the Live CD, you get to step 8; go to 'Advanced Tab' and change (hd0) for /dev/???
??? is your USB drive. You can find out what it is by running:
sudo fdisk -lu (at the Terminal, in Live CD) while having your USB drive plugged.
Hope it helps.

---

### Post by toMeloos on 2008-03-23
Indeed. Disabling the internal disk in the BIOS however shouldn't be too difficult.

I didn't do so when I installed my external drive and chose the wrong drive to install on (turned out to be the windows disk). Had to repair windows ntldr using the Super Grub Disk, boot the ubuntu LiveCD again to manually mount the external drive and chroot into it to re-do grub-install. That did the trick.

By the way, keeping a Super Grub Disk nearby is recommended in case you run into trouble :KS

---

### Post by Hoffmann on 2008-03-23
> **toMeloos said:**
> Get a 2,5" USB2 drive. Basically, about every drive you can get in a store is USB2. A 2,5" version is small and does not require an external power supply. This way you don't loose all of your laptop mobility :)



Yes you do. Treat it like a normal linux disk. I normally choose a 10 Gb ext3 system partition with my ubuntu installation (probably never gets used for more than 50%), a swap partition equal to or double of the RAM size and the rest as a ext3 partition mounted as /home. this way you don't loose your important data if the system partition becomes corrupt (has happened to me several times already).

You might want to set swappiness to a very low value though, to reduce the amount of disk I/O's.



See my post here: [http://ubuntuforums.org/showpost.php?p=4565720&postcount=6](http://ubuntuforums.org/showpost.php?p=4565720&postcount=6)



Again, read my post here: [http://ubuntuforums.org/showpost.php?p=4565720&postcount=6](http://ubuntuforums.org/showpost.php?p=4565720&postcount=6)

First of all you need GRUB (or lilo) to start linux booting. I recommend you install it on the external disk and then place usb devices before internal hard disks in your boot sequence setting of your BIOS. This way, you get the GRUB boot menu when your external drive is plugged in. GRUB will also allow you to start Windows. If it's not plugged in, your laptop will just load Windows right away.

If you allow GRUB to install itself on the Master Boot Record of the internal disk, you can't boot into Windows without having your external disk plugged in anymore. That would be irritating given the fact that you can avoid this issue as described above.

Thanks a lot for the excellent hints!
I will follow you, so. 
Once again, many thanks!

---

### Post by Hoffmann on 2008-03-23
toMeloos:

Just one more question. Did I also need to buy a power booster USB cable for using with that 2.5" USB external HD?

Thanks,
Hoffmann

---

### Post by toMeloos on 2008-03-24
I assume you intended to write "power booster usb cable". In my experience you won't need it. I bought a drive that had a cable with 2 regular connectors for the computer end and a mini-usb connector for the drive. I've used it on multiple computers (another advantage of booting from usb) and have never needed to connect both connectors to get sufficient power. One was always enough.

There is one exception though: do not connect it to usb hubs that don't have an independent power supply. Most 2 and 4 port usb hubs don't have their own power supply which means that the power provided by the physical computer gets divieded over several devices. Tried it and that didn't work for me. I now always connect it directly to a usb port on the computer case.

---

