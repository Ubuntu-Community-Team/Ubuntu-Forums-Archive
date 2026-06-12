---
title: "Server 18.04 install"
date: 2018-06-02
forum: Installation &amp; Upgrades
---

### Post by novass.net on 2018-06-02
I have a system that was formerly used by my mother for Ubuntu desktop (Linux family ftw!) But was having issues with its graphics card. I want to reuse it as a server. I removed the flaky graphics card as I'm going to ultimately be headless anyway and the onboard VGA is sufficient for installation and the rare console login. The hardware is all the same except for the hard drive (she has her old drive as secondary in her new desktop box now). I purchased a 3TB SATA drive off Amazon, and it seems to be recognized just fine. I can manually edit the position table with fdisk, and it is recognized as 2.7TB (who needs that falsely advertised 300gb anyway). 

The problem arises during the install. I pick my language and network just fine. When it asks about partitioning, I tell it to use an entire drive and select my new blank drive. Then a bunch of Python errors fly by faster than I can capture on video, and I'm returned to the welcome screen. I was a long time red hat guy. My old server that I'm replacing is a Pentium 4 running an ancient version of Fedora. So this is my first personal experience installing Ubuntu. My installation media is a DVD which I burned from a Windows laptop using imgburn and was verified to have burned correctly. As far as I can think, the only differences between this box and the one my mom ran desktop on is the lack of fancy gpu (irrelevant when not running a gui, right?), The new hard drive (but it's recognized just fine), and the installation media (but that passed a verification). Can anyone point me in the right direction? I tried searching for "Ubuntu installation returns to welcome" and similar queries to no avail. 

Sorry I'm so long-winded. I hope someone can help. Thanks!

---

### Post by sudodus on 2018-06-02
Which version of Ubuntu Server are you trying to install?

- Please tell us the whole name of the iso file,

- and check the md5sum to verify that it was correctly downloaded.

What computer is it?

- Brand name and model of the computer or motherboard.

What partition table is there?

- With more than 2 TB you should have a GUID partition table, GPT, and I suspect that you want to boot in BIOS mode. This means that you need a small bios_grub partiiton. See this link

[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by novass.net on 2018-06-02
As calculated locally:
e35f45caf1d26ed5b1217d67f6ee86e8 ubuntu-18.04-live-server-amd64.iso

MD5 was a match.  I'm not sure what kind of partition table it has as it was a new drive.  In the instructions, it "just works"... No mention of any limitations on size or other considerations, so I was hoping it would not require much research.  I will post what I can find out about the hardware when I get a chance to open it up.  Like I said, this machine was purchased specifically to run Ubuntu.  I'm not sure what version was on it, but it was not current, and it was the desktop distro, not server as I intend to use.  I will look into the BIOS vs EFI.  I believe it is new enough to be EFI.  I assume I should be able to figure this out by looking in the BIOS setup?  I used to build systems back in the days of K6 and Athlon, but I'm out of the loop with the past 10-15 years of desktop tech as I've used "recycled" desktops as servers and laptops as workstations.

I see some talk of swap partitions, but it seems to say they are no longer needed?  I've always had them in the past, but I was using kernel 2.6 on a machine with 2GB RAM, so it was a different beast entirely.  So, should I create a swap partition?  This is for a personal server, BTW.  It need not support more than a few users.

---

### Post by sudodus on 2018-06-02
OK, this is the new Ubuntu Live Server

There is also the old style Ubuntu Server iso with the classical Debian text mode installer, that you can find at

[cdimages.ubuntu.com/ubuntu/releases/bionic/release](http://cdimages.ubuntu.com/ubuntu/releases/bionic/release/)

```
$ md5sum ubuntu-18.04-server-amd64.iso
1413c9797dbfa1e57fabfb5c91cfb96f  ubuntu-18.04-server-amd64.iso

```

This one might behave more like you are used to during installation, and you should get very similar servers (anyway supported Ubuntu Servers after the installation from both iso files).

When booted into Ubuntu or some other linux (installed or live from USB/CD/DVD), you can run the following commands to find out

- about the partition table:
```

sudo parted -ls
sudo lsblk -f
sudo lsblk -m

```

- about the current boot mode:
```

test -d /sys/firmware/efi && echo efi || echo bios

```

- about the computer hardware
```

sudo lshw|less

```

Swap is not as important as it used to be, now that there is more RAM in the computers. But I think you should have swap, either a swap partition or a swap file and the installers may select this in different ways. The size need not be twice the RAM, but I would suggest at least the same size as that of the RAM (in gibibytes), for example with '4 GB RAM' there is actually 4GiB RAM, 4*2^30 bytes = 4294967296 bytes, approx. = 4.3 GB.

---

### Post by novass.net on 2018-06-03
The machine is a phenom ii box built by zareason BTW. I don't see a model number on it anywhere. I looked through the CMOS settings to see if I saw any mention of hd booting bios vs efi but didn't see anything obvious. I'm not even at the point where I care about booting yet though. If it refused to boot off this drive I'd just put in another drive for booting, like we used to be able to use a boot floppy in the old days to start a machine with a hard drive not supported by bios. Is there any reason I should download the not live install media? I only get to spend a few minutes a day messing with this thing. My plan was to get it installed, get SSH working, and slowly migrate to it. Right now I'm using the TV as its display, which is watched entirely too much for me to figure this out quickly. It's like the old days of trying to use the phone line to dial up with too many females trying to compete for the same phone line to talk about whatever pointless things they talk about... lol

---

### Post by novass.net on 2018-06-03
Motherboard is an MSI 760GM-E51. I'm researching that more right now.

---

### Post by sudodus on 2018-06-04
> **novass.net said:**
> The machine is a phenom ii box built by zareason BTW.
...
Is there any reason I should download the not live install media? I only get to spend a few minutes a day messing with this thing. My plan was to get it installed, get SSH working, and slowly migrate to it.

I think the iso file with the 'old style Debian installer' is much more debugged, polished and reliable, and I think you will have less problems with it. And if there is some problem, you should get a notice about it and a chance to fix it.

> **novass.net said:**
> Motherboard is an MSI 760GM-E51. I'm researching that more right now.

It should work to install Ubuntu Server into your computer with that motherboard.

[hr][/hr]
**Edit:** But you need a suitable partition table on the hard disk drive. Please run the commands that I suggested in my previous post and edit the output into a reply. This will tell me, if you have a good partition table, or if you should modify it.

Please post the output between code tags like this
 
[noparse]```

output

```[/noparse]
 
to get output like this
 
```

output

```

---

