---
title: "After installing Ubuntu 14.04 using a USB stick, I cannot boot from my computer."
date: 2014-08-09
forum: Installation &amp; Upgrades
---

### Post by quics1 on 2014-08-09
I installed Ubuntu as explained in several forums and get the same error. During installation everythings seems to be installing fine in /dev/sda (I have a mSATA SSD) but, for some reason it cannot boot. It is using EFI

I tried running Boot-Repair and got this log: [[COLOR=#1155CC][FONT=Arial]_[http://paste.ubuntu.com/8003713/](http://paste.ubuntu.com/8003713/)_[/FONT][/COLOR]]("http://paste.ubuntu.com/8003713/")

Any idea what could be going on?

Thanks in advance!

---

### Post by SuperFreak on 2014-08-09
You installed an EFI partition in addition to Root or Root and Home right? EFI partition should be 250 MB and formatted FAT32

---

### Post by MoebusNet on 2014-08-10
This may or may not be your problem, but unetbootin does not seem to work well with newer than 12.04. I had to use Startup Disk Creator to make the USB. The netbootin USB image tested successfuly but would never boot after installation. Startup Disk Creator USB image worked.

---

### Post by quics1 on 2014-08-10
I used the Startup Disk Creator from an old computer to create the USB installer. The installer worked just fine but when removing the stick my new computer would just not boot. I wonder if the problem is that I created the installer with 14.04 and, as you mentioned, it's not quite working. Maybe if I used a previous version of linux to create it?

---

### Post by quics1 on 2014-08-10
The first time I installed ubuntu I used their default partition scheme. I noticed they had an EFI (I think 500MB long) but they did not have a /root. I added one manually by running the installation again but choosing the "do something else" option but it didn't work either. 

Just in case it's useful, I'm trying to install Ubuntu into one of these new Intel NUC (D54250wykh) machines which in theory are compatible. Looks like the problem is the GRUB is not getting installed in the NUC drive but I'm not positive about this and even if I was I'm not sure how to fix it.

---

### Post by sammiev on 2014-08-10
I use UNetbootin and have two versions of 14.04 and one version of 14.10 and never had any trouble.

---

### Post by quics1 on 2014-08-10
I found this article: [http://arstechnica.com/gadgets/2014/02/linux-on-the-nuc-using-ubuntu-mint-fedora-and-the-steamos-beta/](http://arstechnica.com/gadgets/2014/02/linux-on-the-nuc-using-ubuntu-mint-fedora-and-the-steamos-beta/) so I checked if there was a BIOS with a fix for this and it seemed to work just fine. 

This is the download center.

[https://downloadcenter.intel.com/Detail_Desc.aspx?DwnldID=24103&lang=eng&ProdId=3744](https://downloadcenter.intel.com/Detail_Desc.aspx?DwnldID=24103&lang=eng&ProdId=3744)


Thanks all for your help! (:

---

### Post by MoebusNet on 2014-08-10
@quics1 - Glad you found a solution! If your problem is fixed, please mark the thread 'Solved' with Thread Tools.

@sammiev - Netbootin worked perfectly for me from Ubuntu 12.04.4 64-bit to make Lubuntu 14.04.1 32-bit, but absolutely would not work from Ubuntu 12.04.5 64-bit (same machine) to make Ubuntu 14.04.1 64-bit. The netbootin Live-USB image would self-test good, woud run a Live-boot, but when repeatedly installing from it would throw a kernel panic: missing init message after install. Startup Disk Creator run from a Lubuntu 14.04.1 32-bit install did not. In addition, Startup Disk Creator run from the unetbootin Live-USB would fail to find a source file to use. YMMV.

---

