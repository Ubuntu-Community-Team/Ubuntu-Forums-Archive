---
title: "[Errno 5] Input/Output Error - SQUASHFS ??"
date: 2007-12-08
forum: Installation &amp; Upgrades
---

### Post by ghingres on 2007-12-08
I'm trying to install 7.10 desktop onto my dell latitude c600 - and i get the [Errno 5] input/output error...

Of course this makes me think CD, but running a cdcheck reveals no errors and the md5 checksums were valid for the ISO. The failure occurs at 49% and having a quick look at /var/logs shows the following: -

SQUASHFS error: zlib_inflate returned unexpected result 0xfffffffd, srclength 65536, avail _in 0, avail_out 8601
SQUASHFS error: sb_break failed reading block 0x53f4
SQUASHFS error: Unable to read fragment cache block [14fec87f]
SQUASHFS error: Unable to read page, block: 14fec87f, size 4ade

What do I do ? Keep burning CD's (and believe the error is the media) or think that there is a problem with SQUASHFS ?

Just thought i'd post what i'd found in /var/logs in case it helps...

Cheers

Gary

---

### Post by kolla on 2007-12-09
experiencing same error as Gary while installing 7.10 desktop

**[Errno 5] input/output error**
Failed to copy files; faulty CD/DVD or hard disk?

failure occurs at 51%

**GParted**
 - checked my hd
 - partitioned (deleted all data)

this is how my hd looks like after the aborted installation:
```

Partition  filesystem     Mountpoint       Size         Used      Flags
/dev/sda1    ext3        /target          35.83 GiB    1.43GiB    boot
/dev/sda2    extended                      1.43 GiB     ---       ---
/dev/sda5   linux-swap                     1.43 GiB     ---       ---

```

**/var/log/syslog** contains multiple lines like:
```
SQUASHFS error: zlib_inflate returned unexpected result 0xfffffffd, srclength 65536, 
   avail _in 1018, avail_out 57709
SQUASHFS error: sb_bread failed reading block 0x4eb89
SQUASHFS error: Unable to read fragment cache block 
SQUASHFS error: Unable to read page, block
```


no errors on cdcheck

---

### Post by Pumalite on 2007-12-09
Get a new iso.

---

### Post by kolla on 2007-12-09
Pumalite, there is nothing wrong with the iso / cdrom / cd drive
got it working without getting a new iso

I think my hard disk was the problem.
Not sure though what exactly the problem was.

Here is what I did:

[LIST=1]
[*]booted live installation
[*]partition manager (geparted) setup 1 partition ext3 and 1 swap partition
[*]ran a check disk, fix errors option in gparted
[*] right clicked on "install" icon on the desktop copied the command to install ubuntu 7.10 desktop
[*]opened a shell and run the command without any parameters. it will start the installation process in gui mode
[*]step 3(?) partitioner, selected 3rd option (no wizards) and edited mount point on first partition
 from '/dev/sda1' to '/' (root) 
[*]in one of the next screens is an 'advanced' button, clicked that button and deselected option install grub loader
[/LIST]

I guess somehow during the first failed installation attempt grub is already installed and doesn't need to be installed again?

Gary, I hope this works on your machine as well. Please let us know.

---

### Post by YoDaddeh on 2007-12-09
I had been having a problem like that too.

Nothing is wrong with the install media its the guided partitioning style. You have to manually partition your hard drive in order for it to install properly.

I've waisted at least 4 hours today trying to figure that one out myself :lolflag:

We should sticky this somewhere for people who are having problems installing on some systems.

---

### Post by Pumalite on 2007-12-10
Glad you got it working. Bookmarked.

---

### Post by fadingfastsd on 2007-12-12
I had this same problem. Turned out I used a ball point pen to label the CD and it had kind of etched its way through the top layer and was showing on the reverse data side of the CD.

I burned a new cd from the downloaded ISO and it booted fine.

Hope this helps anybody.

---

### Post by fulcrumbg on 2007-12-22
> **YoDaddeh said:**
> I had been having a problem like that too.

.......... You have to manually partition your hard drive in order for it to install properly.........

I did that , but still got the [Errno 5] message !? :(

---

