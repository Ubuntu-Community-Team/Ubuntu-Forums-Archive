---
title: "Check out NILFS!!!!"
date: 2009-06-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by autocrosser on 2009-06-03
Just looking at NILFS---a filesystem that is setup with SSD's in mind!!!! 

Links:[http://www.linux-mag.com/cache/7345/1.html](http://www.linux-mag.com/cache/7345/1.html)

[http://www.nilfs.org/en/index.html](http://www.nilfs.org/en/index.html)

I'm going to do some more looking/checking & maybe setup a partition with it--it looks like a REALLY sweet filesystem!!!!!:D:D

---

### Post by davideotape on 2009-06-03
> **autocrosser said:**
> a filesystem that is setup with SSD's in mind!!!! 

If only I could afford an SSD.... :P

---

### Post by inportb on 2009-06-03
Flash storage is widely available these days in the form of USB keys, SD cards, and such... ;)

---

### Post by davideotape on 2009-06-03
> **inportb said:**
> Flash storage is widely available these days in the form of USB keys, SD cards, and such... ;)

But you wouldn't run an OS off them, would you? :D

---

### Post by inportb on 2009-06-03
Not me. Why do you ask?

---

### Post by Keithhed on 2009-06-03
It all should come down to data transfer rates.  I have a cheap USB 4GB that only gets about 17Mb/s.  I would not run any program off of that as it would be painfully slow.  It seems having a purpose built flash hard drive (SSD) is quite faster so that would be ideal.

---

### Post by ronacc on 2009-06-03
> **davideotape said:**
> But you wouldn't run an OS off them, would you? :D

I've got 3 versions of Ubuntu  3 of puppy 1 suse and 1 sabsyon all running off of sd cards on my eeepc 701 , just pop in a different card to change personalities :p

check out newegg they've got a 30gb OCZ ssd for US $118 after MIR right now . thinking about that one myself for one of my boxes .

---

### Post by Eestlane on 2009-06-03
> File sizes of up to 8 EiB (Exbibyte - approximately an Exabyte)
Definitely the most useful feature :P

---

### Post by autocrosser on 2009-06-03
I'm at work right now, but I will be checking into it later today & if it looks like a go---I'll do a install in my main tower to see if it is faster with SATA2 drives...will be interesting to benchmark it.......

---

### Post by davideotape on 2009-06-03
> **Eestlane said:**
> Definitely the most useful feature :P

ROFL. And I like the idea of using sd cards with different distros. Depending on card prices here in the uk I think I well look into that. I've read that flash drives have a lifecycle based on the number of write cycles, so booting and running your main distro off it isn't a great idea. I do however have a USB stick that I use as a livecd in case of disasters. And is this filesystem supported by the kernel, ubuntu or gparted yet?

---

### Post by autocrosser on 2009-06-03
That's why I'm interested in this filesystem--the read/write cycle is setup for SSD--look who is developing it---Nippon Telephone......They are positioning it for mobile devices....I'm looking at it for the lower overhead--"should" make an operating system much faster...


> **davideotape said:**
> ROFL. And I like the idea of using sd cards with different distros. Depending on card prices here in the uk I think I well look into that. I've read that flash drives have a lifecycle based on the number of write cycles, so booting and running your main distro off it isn't a great idea. I do however have a USB stick that I use as a livecd in case of disasters. And is this filesystem supported by the kernel, ubuntu or gparted yet?

---

### Post by jfernyhough on 2009-06-03
Be careful when you type this acronym into Google. N and M are common typos.

---

### Post by jmmL on 2009-06-03
> **davideotape said:**
> And is this filesystem supported by the kernel, ubuntu or gparted yet?

Support for NILFS2 was introduced in 2.6.30. I can't find any information about nilfs in gparted, although gparted is just a front-end for gnu parted. The features list for gnu parted does not mention it ([http://www.gnu.org/software/parted/features.shtml](http://www.gnu.org/software/parted/features.shtml))

---

### Post by meeples on 2009-06-03
> **jfernyhough said:**
> Be careful when you type this acronym into Google. N and M are common typos.

haha. someone should make a file system called MILFS though ;) i'd use whether it was good or not. XD

---

### Post by nyarnon on 2009-06-03
Worse if I read synaptic right the modules have to be compiled first. So a lot of work for just a bit of sniffing. Think I pass on this till more info comes available. I must say it does itches, looks like a mighty fine filesystem.

---

### Post by ronacc on 2009-06-03
it looks like 2.6.29 is the latest kernel the modules will build against , built ok in jaunty with 2.6.29 but errors out imeadiately in karmic with 2.6.30 as indicated on the nils.org website , I tried both the regular src and git, both errored at the same place .sugestions anyone ?

---

### Post by nyarnon on 2009-06-04
> **ronacc said:**
> it looks like 2.6.29 is the latest kernel the modules will build against , built ok in jaunty with 2.6.29 but errors out imeadiately in karmic with 2.6.30 as indicated on the nils.org website , I tried both the regular src and git, both errored at the same place .sugestions anyone ?

Did you try compiling on an sdd ;)

---

### Post by ronacc on 2009-06-04
the only ssd I've got right now is the 4 gig one on my eeepc and I leave the default xandros on that one and put other distros on sd cards , I'm thinking about getting one for one of my destops ( see my post on page 1 this thread) . The problem isn't what it was compiled on but the kernel , nils.org says on their download page that 2.6.9 is the latest kernel that it compiles against but I gave it a shot on 2.6.30 anyway just for grins .

---

### Post by ssam on 2009-06-04
my jukebox/backup machine boots off a 4GB compact flash (SanDisk extreme IV) card (using a IDE to CF adapter)
```

sam@flute:~$ sudo hdparm -tT /dev/sda
/dev/sda:
 Timing cached reads:   110 MB in  2.02 seconds =  54.55 MB/sec
 Timing buffered disk reads:   34 MB in  3.01 seconds =  11.28 MB/sec

```
not supper fast, but does the job. i think the speed is limited by the motherboard (via epia MII6000E) seen as a 400GB PATA drive (SAMSUNG SpinPoint T133 series) does about the same. 
```

/dev/sdb:
 Timing cached reads:   116 MB in  2.02 seconds =  57.54 MB/sec
 Timing buffered disk reads:   44 MB in  3.02 seconds =  14.58 MB/sec
```

it used to be a 1GB CF card, but i upgraded. overall i have been using CF cards in it for about 4 years, and never had any trouble. good cards have a very long warranty, so just make sure you have a back up.

---

### Post by durand on 2009-06-04
> **ssam said:**
> my jukebox/backup machine boots off a 4GB compact flash (SanDisk extreme IV) card (using a IDE to CF adapter)
```

sam@flute:~$ sudo hdparm -tT /dev/sda
/dev/sda:
 Timing cached reads:   110 MB in  2.02 seconds =  54.55 MB/sec
 Timing buffered disk reads:   34 MB in  3.01 seconds =  11.28 MB/sec

```
not supper fast, but does the job. i think the speed is limited by the motherboard (via epia MII6000E) seen as a 400GB PATA drive (SAMSUNG SpinPoint T133 series) does about the same. 
```

/dev/sdb:
 Timing cached reads:   116 MB in  2.02 seconds =  57.54 MB/sec
 Timing buffered disk reads:   44 MB in  3.02 seconds =  14.58 MB/sec
```

it used to be a 1GB CF card, but i upgraded. overall i have been using CF cards in it for about 4 years, and never had any trouble. good cards have a very long warranty, so just make sure you have a back up.

That is strange...
```
/dev/sda:
 Timing cached reads:   2680 MB in  2.00 seconds = 1341.25 MB/sec
 Timing buffered disk reads:  188 MB in  3.02 seconds =  62.26 MB/sec
durand@Deuterium ~> sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   2996 MB in  2.00 seconds = 1498.98 MB/sec
 Timing buffered disk reads:  186 MB in  3.00 seconds =  61.91 MB/sec
```
...on a laptop with a 5400rpm HD..

---

### Post by jfernyhough on 2009-06-04
OK, random crappy benchmark. I've no idea if this is actually any good as I don't know exactly which part of the drive hdparm is testing. :D

1GB generic USB pen drive (USB2)

VFAT:
/dev/sdb:
 Timing cached reads:   3008 MB in  2.00 seconds = 1504.26 MB/sec
 Timing buffered disk reads:   64 MB in  3.08 seconds =  20.77 MB/sec

Ext4:
dev/sdb:
 Timing cached reads:   2706 MB in  2.00 seconds = 1353.71 MB/sec
 Timing buffered disk reads:   64 MB in  3.09 seconds =  20.73 MB/sec

NILFS2:
/dev/sdb:
 Timing cached reads:   2940 MB in  2.00 seconds = 1470.85 MB/sec
 Timing buffered disk reads:   64 MB in  3.06 seconds =  20.90 MB/sec


All within the same range, so I'd say this metric is meaningless. :D Woot for meaningless statistics! :D

---

### Post by durand on 2009-06-04
My benchmark sounds too high...

---

### Post by jfernyhough on 2009-06-04
Naw, I think hdparm is testing raw device speed and has nothing at all to do with the partition type - note how it's run on /dev/sdb (the drive) and not sdb1 (the partition). Hence my test runs were all on the same drive, regardless of filesystem (so pretty pointless :D).

My internal drive is:
/dev/sda:
 Timing cached reads:   3146 MB in  2.00 seconds = 1573.23 MB/sec
 Timing buffered disk reads:  206 MB in  3.02 seconds =  68.20 MB/sec

(and I'm sure it was 1700MB/sec when I tested it before...)

A quick file-copy test (that lacked any rigour) had NILFS2 at 1m20 and EXT4 at 1m30 when copying a 320MB file.

---

### Post by jfernyhough on 2009-06-04
Uh... the bit in bold is kind of crucial to the news item, isn't it? The next point isn't particularly encouraging, either. :)
[quote=http://www.nilfs.org/en/current_status.html]TODO List

    * Checkpoint rollback
    * Checkpoint based remote replication
    * Performance improvement (Better Block I/O submission)
    * atime support
    *** Optimization for silicon disks (e.g. SSD)**
    ** fsck*
    * Faster inode allocation
    * Extended attribute
    * POSIX ACLs
    * Online resizing
    * Online defrag
    * filesystem freeze support
    * Variety of Garbage Collection policies
    * Design document and better developer support
    * Better support of fsync, mmap, and direct I/O.
    * Filesystem label support
    * More backup copies of the super block
    * Unified user command ``nilfs'' (rather than separate commands like lscp, rmcp, mkcp, etc).
    * "Time-based" tools (e.g. tls, tdiff, tgrep, tfind, ttar and so on. They come from the Elephant file system)
    * Time-machine like browser.
    * Time slider [/quote]

---

### Post by ssam on 2009-06-05
> **jfernyhough said:**
> All within the same range, so I'd say this metric is meaningless. :D Woot for meaningless statistics! :D

hdparm does not measure the filesystem speed, only the raw read speed of the device.

---

### Post by Starks on 2009-08-18
Hopefully in a year or two, this and Butter will be everything Reiser4 was supposed to be.

---

### Post by xebian on 2009-08-18
> **davideotape said:**
> ROFL. ... I've read that flash drives have a lifecycle based on the number of write cycles, so booting and running your main distro off it isn't a great idea....

That's why I have mine saved in the drawer still in the plastic wrap.  :P

---

