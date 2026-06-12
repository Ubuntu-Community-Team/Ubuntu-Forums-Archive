---
title: "Live Ubuntu on Exteral HDD"
date: 2010-06-17
forum: Installation &amp; Upgrades
---

### Post by pawantahiliani on 2010-06-17
I keep "revisiting" Ubuntu because of my fascination with it. I have installed it several times in my internal drives but I just don't like the dual boot everytime.

I wish to create an external hard drive that is specifically for linux. A live drive if you will. But is it possible to full install ubuntu on a separate disk as opposed to always opting for a "live" option? The performance is compromised that way isnt it? Can someone guide me to the best forum thread, or the best instructions or help me achieve this?

I don't want a dual boot menu unless I plug the external hard drive in and allow the BIOS to know that ubuntu is waiting to boot...

---

### Post by darkod on 2010-06-17
Just plug in the ext hdd, boot with your ubuntu cd and start the installer. In step 4 tell it to use the ext hdd as destination, and note down the name of the disk, for example /dev/sdb.

In the last screen of the installer, before clicking Install, click on Advanced and select grub2 to be installed on the same disk, like /dev/sdb. There should not be a number, just /dev/sdb.

If your ext hdd is /dev/sdc, /dev/sdd, etc, just use that.

That way grub2 will be on the ext hdd and you will not have grub2 menu show up unless you tell the computer to boot from the ext hdd. But for that to work your computer must be able to boot from usb.

---

### Post by pawantahiliani on 2010-06-17
Awesome! I shall get on that right away!:)

---

### Post by pawantahiliani on 2010-06-17
Okay another question..how about installing it on a usb stick as opposed to a hard drive? I realised I wont be storing much so A 4gb usb stick should be fine..will the same stuff work?

---

### Post by darkod on 2010-06-17
> **pawantahiliani said:**
> Okay another question..how about installing it on a usb stick as opposed to a hard drive? I realised I wont be storing much so A 4gb usb stick should be fine..will the same stuff work?

4GB will be very low on space. The live usb, the ISO unpacked is only 700MB but making a full install on a stick as destination takes more. The default install is approx 3.5GB so it will be very tight on 4GB stick.

You don't need to give ubuntu the whole ext hdd. Just make unpartitioned space on it (not belonging to any partition) of 25-30GB, and install there with the option Use Largest Available Free space. That will install it into the unallocated space you left.

The rest of the ext hdd can be with ntfs partitions and you can use it for both windows and ubuntu. Ubuntu reads/writes ntfs so it will be able to use it too.

---

### Post by bumanie on 2010-06-17
If you want it on a usb stick, use the Startup Disk Creator - System --> Administration --> Startup Disk Creator. It will work much better off an external hard drive as usb sticks are approximately 3x slower than a hard drive.

---

### Post by darkod on 2010-06-17
> **bumanie said:**
> If you want it on a usb stick, use the Startup Disk Creator - System --> Administration --> Startup Disk Creator. It will work much better off an external hard drive as usb sticks are approximately 3x slower than a hard drive.

That procedure will only create bootable live usb stick.

We are discussing full installation onto ext hdd / usb stick.

---

### Post by pawantahiliani on 2010-06-17
Okay..this helps a bit...I can partition my hard drive, but I have one question...is it possible to destroy the partition at any time? the ubuntu partition, without harming the other stuff? how easy is this. I pretty much have my life on this hdd so i was considering buying a new hdd but that seems futile to spend so much

How easy is it to destroy a partition and restore to hard drive to ntfs with my personal files sitting safely? This is just incase I have issues with ubuntu and I want out..I hate reformatting or doing drastic stuff

Also, will this partition bleed into the rest of the harddrive for disk space? I have a 1TB..so asume i save 200 gb for ubuntu...will the files i work on from ubuntu use the other 800 or does it faithfully sit within it's boundary?

---

### Post by vickystylton on 2010-06-17
When you destroy a partition, you'll lose all the data in that partition. However, while merging two partitions, you wont lose any data (atleast, that was the case for me when I merged two partitions using paragon). The partition manager creates a temporary directory in the new merged partition for storing the data.

---

### Post by darkod on 2010-06-17
1. You can delete the ubuntu partition(s) at any time. The data on the other partitions will not be affected, as long as you delete the correct one. That's the point of partitioning a hdd, the other partitions are safe.

2. The ubuntu system will remain on the 200GB you create for it. It will not touch other partitions by itself. You can read files or write files to the other partitions but only if you do it yourself. Ubuntu won't touch the other partitions otherwise.

---

### Post by pawantahiliani on 2010-06-17
yes but how exactly do I delete the partition? can I just go to hard disk manager in windows and destroy itt here? or do I need something awesome like partition magic? the procedure for installation remains the same i assume, excluding the option of choosing to partition...

---

### Post by darkod on 2010-06-17
> **pawantahiliani said:**
> yes but how exactly do I delete the partition? can I just go to hard disk manager in windows and destroy itt here? or do I need something awesome like partition magic? the procedure for installation remains the same i assume, excluding the option of choosing to partition...

Yes, you can delete it from windows Disk Management, from Gparted on ubuntu cd, etc.

---

