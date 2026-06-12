---
title: "Install to Flash Drive"
date: 2011-06-16
forum: Installation &amp; Upgrades
---

### Post by Grenad on 2011-06-16
FIRST POST!:D :

I want to download ubuntu 11.04 to my brand new 16gig flash drive from windows vista or the ubuntu live cd. I read on [https://wiki.ubuntu.com/LiveUsbPendrivePersistent]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent") that if i just use the regular installer, I am at risk of wearing out my flash memory more quickly. I dont like the link they posted under method 2. My question is: If what i read is true, what is the best way to put the full ubuntu installation on my flash drive (I expect that it involves partitioning my flash drive)?

---

### Post by mörgæs on 2011-06-17
Hi, welcome to the fora.

If you are using Windows, I would recommend Unetbootin.

---

### Post by Grenad on 2011-06-18
Thanks ill look into that but i also need to know if the os will be to "write-intensive" and wear out the flash drive too quickly. I will not be surprised if this is true but i already got it so i just want to be certain. I should have just gotten the external hard drive, but those are such a pain to carry around;).

---

### Post by mörgæs on 2011-06-18
Sorry, I don't know of that. 

If you have a cheap 1 or 2 GB USB stick you could use that for testing. We would like to hear the results :-)

---

### Post by oldfred on 2011-06-18
If you have a 16GB flash, you want to do a full install. Persistence is limited to 4GB, I think, but you could partition and have space to store other data.

You do want to change some settings to reduce writes, just like you would with a SSD. But since it is flash and thru a USB port do not expect it to be fast. I have installed it to my 16GB flash in a 8GB partition and it is functional.

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html]("http://members.iinet.net/%7Eherman546/p19.html")
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
[http://ubuntuforums.org/showthread.php?t=1404664](http://ubuntuforums.org/showthread.php?t=1404664)

Step by Step Full install 8GB C.S.Cameron Post #7
[http://ubuntuforums.org/showthread.php?t=1719346](http://ubuntuforums.org/showthread.php?t=1719346)


Use ext2 or ext4 without journal:
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

---

### Post by Grenad on 2011-06-18
@morgaes, I will be sure to post the results. It would be great to *safely* carry around the best os around in my pocket ;)

@oldfred, thanks for those suggestions; they should help a lot.

Im going to leave this thread open so that I (and anyone else) can post experiences on this topic. So please leave any info you have!

---

