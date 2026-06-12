---
title: "How do I delete 32-bit 12.10 from 32/64-bit dual boot system?"
date: 2012-11-28
forum: Installation &amp; Upgrades
---

### Post by b9k9kiwi on 2012-11-28
You might as well have the whole story :(

I usually build my own boxes but decided to treat myself to a ready-built system to replace my two-year old Ubuntu self-build.

I duly installed 20.10, restored my personals from backup, and was pleased to see the system up and running and scampering along.  Not surprising as, fully 24 hours later and with my head in my hands, I realised I had grabbed the wrong DVD and installed 32-bit Ubuntu instead of the 64-bit.

The new box is;

AMD FX-8100 6-core 3.3Ghz/3.9Ghz CPU
MSI 760GM-P23 AM3 mATX mainboard
2x Transcend Jetram 8GB DDR3 1600 (=16GB)
WDC Caviar Blue 1TB SATA3 HDD
Gigabyte nVidia GTX650 2GB PCIe video card
LG CH12LS28 12x Blu-Ray/DVD/Lightscribe combo drive

... so 32-bit is clearly not the best choice.

I installed 64-bit alongside (rather than over the top of) the 32-bit on the basis that I could suck my personals from one partition to another more quickly than from external backup.  Every thing 64-bit is now up and running, 'though it doesn't seem at all stable.  Try to run Thunderbird, for example, and the system will crash to the login prompt (I can do my email on my Windows box, so I 'fixed' that by uninstalling Thunderbird).  Firefox is decidely flakey and Compiz dies two or three times a day.

I have decided to persevere for now to see if things improve - bearing in mind that this machine is not mission critical - with the option to do a new install later if that proves to be the better option.

I do not know how to remove the 32-bit installation, however.  Perhaps all I have to do is edit Grub to remove the 32-bit dual boot option and erase its partition, but I would prefer some advice on that.

---

### Post by darkod on 2012-11-28
Since 64bit was installed second, probably grub2 on the MBR is from 64bit. But to make sure, boot the 64bit and in terminal do:
sudo grub-install /dev/sda

After that you can safely delete the 32bit root partition.

---

