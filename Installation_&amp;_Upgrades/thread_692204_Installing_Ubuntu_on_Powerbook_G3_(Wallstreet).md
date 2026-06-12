---
title: "Installing Ubuntu on Powerbook G3 (Wallstreet)"
date: 2008-02-09
forum: Installation &amp; Upgrades
---

### Post by warder on 2008-02-09
Hi everyone, thanks in advance for any help you provide...

I'm trying to get Ubuntu Gutsy installed on my PowerBook G3:

292MHz Processor with 1MB cache (I don't know how to verify this, but that is what I was told from my friend who I bought it from)
192 MB RAM
30GB HD, 400mb alloted to the os9 install, the rest unallocated. 
DVD Drive 
No onboard usb or firewire

I've got it booting to the alternate install cd, but it keeps dropping me to BusyBox. The last set of lines looks like this:

```

Begin: Waiting for roo file system... ... 
[ 101.585101] SCSI subsystem initialized
[ numbers] mesh: configured for synchronous 5 MB/s
[ numbers] mesh: performing initial bus reset...
[ numbers] scsi0 : MESH
[ numbers] eth0: BMAC at (my hardware address)

(it stops at the eth0 line for about 5 minutes)

Done. 

	Check root= bootarg cat /proc/cmdline
	or missing modules, devices: cat /proc/modules ls dev
ALERT! does not exist. Dropping to a shell!

(busybox indentifier, etc..)

(initramfs)


```

So I've been searching around for awhile, tried "modprobe ide_core" and "modprobe ide_disk" with exit after that. It returns the same check root error. 

Just last night I've found that I should try "root=/dev/hda#" in my bootx additional commands input. I'm in the process of trying that, waiting for it to fail and running the modprobe ide_core command. 

Thanks again! Let me know if you need any other info.

-warder

---

### Post by Pumalite on 2008-02-09
[http://ubuntuforums.org/forumdisplay.php?f=133](http://ubuntuforums.org/forumdisplay.php?f=133)

---

### Post by warder on 2008-02-10
I downloaded Xubuntu 6.06 Dapper Drake and seems to be installing...it's been at Detecting hardware for a while though...so we'll see what happens. 

-warder

---

