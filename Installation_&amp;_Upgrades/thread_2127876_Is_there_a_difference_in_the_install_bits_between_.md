---
title: "Is there a difference in the install bits between 12.04.1 and 12.04.2?"
date: 2013-03-21
forum: Installation &amp; Upgrades
---

### Post by petrocc on 2013-03-21
I have a USB stick that I use to install various Linux flavors. Well, for values of "various" that mean Scientific Linux 6.3 and Ubuntu at this point, but that *could* change. 

Anyway, it's a 16 GiB stick and has 3 top level directories:

/grub
/iso
/SL3
(well, and lost+found, but that's not relevant here) 

/iso contains ubuntu-12.04.1-desktop-i386.iso  ubuntu-12.04.2-server-i386.iso  ubuntu-12.10-desktop-amd64.iso 

and /grub/grub.conf contains: 
menuentry "SL EL" {
	insmod loopback
 	insmod iso9660
 	set isofile="/SL3/SL-63-x86_64-2012-08-02-Install-DVD.iso"
 	loopback loop (hd0,1)$isofile
	# loopback loop /iso/SL-63-x86_64-2012-08-02-Install-DVD.iso
	linux (loop)/isolinux/vmlinuz  rootfstype=auto  root=live:/dev/loop 
	initrd (loop)/isolinux/initrd.img
}

menuentry "Ubuntu 12.10 64bit Desktop ISO" {
	set isofile="/iso/ubuntu-12.10-desktop-amd64.iso"
	loopback loop (hd0,1)$isofile
	linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}


menuentry "Ubuntu 12.04 32bit Desktop  ISO" {
	set isofile="/iso/ubuntu-12.04.1-desktop-i386.iso"
	loopback loop (hd0,1)$isofile
	linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
	initrd (loop)/casper/initrd.lz
}


menuentry "Ubuntu 12.04.2 32bit SERVER ISO" {
	set isofile="/iso/ubuntu-12.04.2-server-i386.iso"
	loopback loop (hd0,1)$isofile
	linux (loop)/install/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
	initrd (loop)/install/initrd.gz
}


My problem is that the first three work, but the last does not. 

Initially it couldn't find vmlinuz, which moved (for some reason) from /casper to /install on the ISO (or it's always been in install but was also in /casper and is now gone). 

But now the device boots off the USB stick does a few things (sets up the language and the keyboard) then goes to mount the ISO and can't find it. 

What am I missing here? 

I'm sorry if this has been covered before, but I can't find anything in the change log, or in the forums. Probably because I can't think of good search terms.

Anyway, thanks for your help.

---

### Post by petrocc on 2013-03-21
To be more exact, the error I'm getting is: 
"Your installation CD-ROM couldn't be mounted. This probably means that the CD-ROM was not in the drive. If so you can insert it and try again.

Retry mounting the CD-ROM?"

I should note that this machine currently has 12.04.1 Desktop on it, installed from the entry directly prior, and I created the Server entry by cutting and pasting, and when that didn't work I s/casper/install/ on the linux and initrd lines and changed initrd.lz to initrd.gz. 

Thanks.

---

### Post by darkod on 2013-03-21
The server installer wants to "see" a cd-rom in the machine. It can only install from usb stick with a work around. You can use something like this since the iso file is already on the stick:
[http://ubuntuforums.org/showthread.php?t=1550317&p=9705738#post9705738](http://ubuntuforums.org/showthread.php?t=1550317&p=9705738#post9705738)

---

### Post by schragge on 2013-03-21
Cannot comment on your problem, but the following strikes me as unusual:
> **petrocc said:**
> 
menuentry "Ubuntu 12.04.2 32bit SERVER ISO" {
    set isofile="/iso/ubuntu-12.04.2-server-i386.iso"
    loopback loop (hd0,1)$isofile
    linux (loop)/[COLOR=red]install[/COLOR]/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
    initrd (loop)/[COLOR=red]install[/COLOR]/initrd.[COLOR=red]g[/COLOR]z
} The other two entries for Ubuntu use directory */casper* and lzma-compressed initrd.

---

### Post by petrocc on 2013-03-21
@darkod, thanks for the quick response.

Apparently Things Have Changed, and the instructions in that post describe a sequence that no longer exists. 

The documentation here: [https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot) should probably reflect the differences and note that the server variant is significantly different. 

i will echo what Shakma said 2 and a half years ago " P.S. Canonical - I love you, but you must realize people will be installing from usb drives more than CDs from this point forward. Please update the server installer! " 

Well, except the "I love you" part. I'm more of a "let's be friends".

---

### Post by petrocc on 2013-03-21
> **schragge said:**
> Cannot comment on your problem, but the following strikes me as unusual:
 The other two entries for Ubuntu use directory */casper* and lzma-compressed initrd.

Yup.

But if you look on the ISO there is no /casper and the initrd is gzipped.

---

### Post by darkod on 2013-03-21
That sequence should work but I just remembered that I was doing it with the extracted ISO onto a stick, not the ISO file on it like you are. So, that might be the difference, sorry.

---

