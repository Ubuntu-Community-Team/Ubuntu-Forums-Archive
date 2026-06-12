---
title: "Taking the Plunge"
date: 2005-02-08
forum: Installation &amp; Upgrades
---

### Post by tkiesel on 2005-02-08
For about a year I've been lurking on various boards and soaking up info about GNU/Linux. I've come to the conclusion that if there's an operating system that's free (in several senses of the word) and will be less of a security worry/hassle, I'd like to give it a shot.

I've finished downloading the Warty ISO (via torrent, which performs a checksum I think) and will be installing on my home computer tonight. I'm going to aim for a dual-boot configuration so I can keep Windows XP around and wean myself off of it. :)

Ubuntu is going to hopefully reside on the primary slave drive. I'll set the BIOS to boot from that drive, and hopefully the installer will get things rockin' with GRUB.

I did an install of Debian to an old laptop about a year ago. That poor thing never handled any GUI-type stuff, but I was fairly comfy with the partitioning portion of Debian's install. 

The primary slave drive has a 74GB capacity. I'm planning on splitting it up like so:

1GB - swap
7GB -  /
12GB - /home
remainder ~54GB - fat32 partition for media, etc that I want Windows and Ubuntu both to see/use.

I just wanted to post this to see if anyone spotted a glaring danger ahead in the way I plan to handle it. Too much disk space reserved for one purpose? Too little?

Happy to be a brand new part of this community,
tkiesel

---

### Post by Wardhog on 2005-02-08
I don't see anything wrong with your partition scheme, but then again, I'm no expert.  However, I have done similar things a few times.
One thing I think you'll find is that GRUB will have to go in the MBR, ie. the Master Boot Record which is (usually?) on the primary master disk, but it can divert the boot process to wherever you want to keep the Ubuntu installation, so having the installation on a slave disk is no issue.  It's just that GRUB itself will probably have to go on to the primary master.

Like you, I have been searching for "the" Linux distro.  I've tried a few of them, Redhat, Mandrake, hell, I even gave a stage 1 install of Gentoo a go.  I thought Mandrake was the one I liked best, then I found Ubuntu.  Many people claim they like how Ubuntu "just works" with their hardware, and I agree with this, but it is this AND apt-get that has really sold me on Ubuntu.

Offtopic paragraph follows, but I'm annoyed and need to rant.
For a while now, family and friends have been hammering me for support with their Windows boxes.  Spyware, viruses and internet security make up 99% of their problems, and I am totally and utterly sick of running Adaware, etc. and downloading and installing AVG for them.  I've told them all I will no longer rebuild their Windows boxes, but I will build Linux boxes for them, and they will be getting Ubuntu live CDs Real Soon Now to try out.

---

### Post by tkiesel on 2005-02-08
I've got an issue of some kind going on with burning CDs. Burned two copies from my copy of the ISO, one with Nero, and one with [burnatonce](http://www.burnatonce.com/).  Both disks throw errors during base system install and fail the installer's CD verification check located near the bottom of the install menu. (I started doing the latter when the former failed every time) Strange thing is that I tried burning one on my wife's computer and that one had the same problem. Each copy failed on different files during CD verification.

So I've got three new drink coasters.

Is the problem with the ISO file? Well, I've checked the ISO with [MD5sums for Windows](http://www.pc-tools.net/win32/md5sums/)  and the output perfectly matched the checksum in the /releases/4.10/MD5SUMS file of my nearest Ubuntu mirror, so the ISO file I've got is good.

Uggggh.

---

### Post by anomie on 2005-02-08
tkiesel, 

That is strange. So you can boot with the burned cd, but the linux mediacheck fails? 

You might try downloading the ISO from one of the mirrors just for grins. (I know you said the checksum looked ok.)

As far as your partitions go, that should be fine. You may not even need 1 GB of space for swap depending on how much RAM you have. 

----

Wardhog, 

I can sympathize. Constantly running spyware / virus checks (and updating definition files) for various relatives gets old quickly.

---

### Post by anomie on 2005-02-08
In fact, when my brother and I got my folks a new PC for xmas this past year we gave it to them with SuSE 9.1 installed. It is impossible to get them to understand how to operate a Windows pc safely, so we said "why bother?". They don't have the root password, so they're going to have a difficult time breaking anything (something they're quite good at under Windows).

---

### Post by Wardhog on 2005-02-08
[QUOTE=anomie]

Wardhog, 

I can sympathize. Constantly running spyware / virus checks (and updating definition files) for various relatives gets old quickly.[/QUOTE]

Heh.  I just recently rebuilt their Win2k box and took it back around to them.  In the time it took for them to connect to the web, download AVG and ZoneAlarm, and get set up, the Doom32 virus had got in.  That's why I give up on Windows.

They're clueless Windows users, they might as well be clueless Ubuntu users (who have no idea how to install software under Linux but insist on installing every piece of crap available on the web for Windows).

---

### Post by tkiesel on 2005-02-08
anomie,

The mediacheck fails if I run it. If I don't interrupt install to use the CD check near the bottom of the menu, then "install base system" fails. It's a different message there on each CD.  The first one I got was amusing:

```
No installable kernel was found in the defined APT sources.

The current default kernel package is 'linux-386'.

You may try to continue though this rather strange error is probably fatal.
```

That one made me laugh out loud.

I'll download again if that seems like it'll help. The checksum match seems like fairly airtight evidence on that end of the mystery.

Oh, and re: the swap partition.

Quick system hardware specs, in case it'll reveal anything for anyone.
AMD Athlon XP 2400+
EPoX mobo - VIA KT266A chipset
512MB RAM
40 GB Primary Master HDD (Windows)
74 GB Primary Slave HDD [currently empty] (Media, misc files, Ubuntu?!)
TDK CD burner
Realtek NIC
Aopen graphics card - Nvidia Geforce FX5900XT 128MB

I'm looking forward to getting Ubuntu going. Still excited, just not sure how to proceed!

take care,
tkiesel

---

### Post by anomie on 2005-02-09
tkiesel, 

Your swap size will be fine - 2 X RAM is pretty standard. 

The reason I suggest trying to get the ISO from one of the mirrors is perhaps a bogus ISO is circulating on bitorrent (if that sounds impossible, it's probably because I am not very familiar with bitorrent). 

You said you burned the image with Nero, and I have never had a problem with that. Also, it seems a lot more likely that if Nero was at fault you wouldn't even have a bootable cd. 

I can't think of any other variables to isolate with the symptoms you're seeing.

---

### Post by tkiesel on 2005-02-09
Update:

I got some new CDR media and burned even slower than before. Ripped image from the burn and checked the md5, and it matched the original ISO. So, with renewed confidence I plunged on.  :grin: 

I'm writing this from Windows XP, so things didn't proceed perfectly, but nearly so. 

Networking isn't working.

Got this on Gnome startup:

Could not look up internet address for gecko.
This will prevent GNOME from operating correctly.
It may be possible to correct the problem by adding gecko
to the file /etc/hosts.

I played around with the Network configuration on the desktop, but there was no network device listed. The device manager does show the card though (or what I think is the card).

The computer should be getting its IP from DHCP.. a server at 192.168.2.1, but is not, apparantly.  ](*,) 

I'll keep playing around, and post my questions in a new thread with a nice informative title. Cursory use of the search on this forum and Google hasn't shown me much that seems to match my experience here. 

Any help at all is much appreciated, and I can attempt to gather any info that might be needed to diagnose things, but for now I'll just play around with getting used to things.

Happily running Ubuntu (as much as possible),
tkiesel

edit: One thing I wasn't certain about during partitioning was the choice beween primary/logical for swap.  I chose logical. Not sure if that's a problem.

---

