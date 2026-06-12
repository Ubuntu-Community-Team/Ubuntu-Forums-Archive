---
title: "dd  old hard drive, problems"
date: 2012-03-14
forum: Installation &amp; Upgrades
---

### Post by linuxkid3 on 2012-03-14
I have been struggling with this and don't seem to find any info to help.
I have an old working! hd from about 1991, fat16 81mb!

with dos fdisk giving this:
cyl = 980, hd = 10, pre -1, lz 980, sec 17, size 81mb
I have a usb to pata cable but when I plug it in I get the drive detected as 2.19TB!!!. 
I would like to dd the drive, but I need to get access the right sectors I imagin, otherwise I make a 2TB image! 

I found that ddrescue looks like it maybe able to directly access the drive, but when I try   
```
sudo ddrescue -s 104857600  -db 17 /dev/sdc sdc.dd logfile
```
It does not seem to be accessing it correctly! or I did not understand the man page?

```
od  sdc.ddrescue 
0000000

```


My feeling is I need to get the usb driver or kernel to recognice the disk, would that seem right? Or is the a way to manualy enter the correct data for the disk?

Or get ddrescue to 

If anyone has any ideas?

dmesg gives
```
[ 3596.344053] usb 2-3: new high speed USB device number 2 using ehci_hcd 
[ 3596.484042] scsi7 : usb-storage 2-3:1.0
[ 3597.488695] scsi 7:0:0:0: Direct-Access     QUANTUM  GO80A            1    PQ: 0 ANSI: 2 CCS
[ 3597.636301] sd 7:0:0:0: Attached scsi generic sg3 type 0
[ 3597.642173] sd 7:0:0:0: [sdc] Very big device. Trying to use READ CAPACITY(16).
[ 3597.643801] sd 7:0:0:0: [sdc] Using 0xffffffff as device size
[ 3597.643811] sd 7:0:0:0: [sdc] 4294967296 512-byte logical blocks: (2.19 TB/2.00 TiB)
[ 3597.644547] sd 7:0:0:0: [sdc] Write Protect is off
[ 3597.644551] sd 7:0:0:0: [sdc] Mode Sense: 00 38 00 00
[ 3597.645298] sd 7:0:0:0: [sdc] Asking for cache data failed
[ 3597.645302] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[ 3597.646543] sd 7:0:0:0: [sdc] Very big device. Trying to use READ CAPACITY(16).
[ 3597.647419] sd 7:0:0:0: [sdc] Using 0xffffffff as device size
[ 3597.649044] sd 7:0:0:0: [sdc] Asking for cache data failed
[ 3597.649048] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[ 3597.686727]  sdc: unknown partition table
[ 3597.689297] sd 7:0:0:0: [sdc] Very big device. Trying to use READ CAPACITY(16).
[ 3597.690169] sd 7:0:0:0: [sdc] Using 0xffffffff as device size
[ 3597.696069] sd 7:0:0:0: [sdc] Asking for cache data failed
[ 3597.696076] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[ 3597.696080] sd 7:0:0:0: [sdc] Attached SCSI disk

```

---

### Post by sudodus on 2012-03-14
I would look for an old PC with IDE interface and try directly in that computer. If that computer is old, but not too old, it should be possible to boot a live session from a CD drive. And maybe you can read the drive.

It might be even better if you find an old computer which can run booted from an internal drive and where you can connect another IDE drive and maybe use some tool of that operating system or some old version of Ghost, booted from the floppy drive.

About ddrescue:

The info pages are excellent (more complete than the man page)
```
info ddrescue
``` I have used ddrescue, but not direct disk access. Anyway, I cannot spot the error. Have you tried to run it (with a size limit) in normal mode? What happens?

---

### Post by lkraemer on 2012-03-14
You haven't said if you also have the working computer that can boot that
old IDE Hard Drive.  If so, here are a few suggestions I'd try.

Download Slitaz, or Tiny Core and burn the ISO's to a CDR.  These Distro's
can boot an old I486 type system.  (Debian 6 can also be used, but you will
have to build a Minimum Install and select the I486 Kernel, for your Minimum system.)
Then boot one of those Distro's from CDR on your OLD Computer, and have a look
at your old IDE Drive.  You should be able to access your files.  Then copy what
you want to access to a NFS Server, or use Filezilla to FTP then where you want them.
Or copy them to another IDE Drive.

If you are wanting to clone the drive, you can use a Floppy with Ghost (Windows Software)
or boot a LiveCD of Clonezilla to Duplicate the drive to another IDE Drive of the same
or different size on your OLD system.

If this doesn't meet your needs, exactly what are you trying to access
from the OLD Drive?  And is the OLD Drive Windows 3.1, Win 98SE, Win2K,
Win ME, or what OS?

There is software for Windows named xxclone that is free and works well to duplicate Drives
with Windows installed.

[http://www.xxclone.com/](http://www.xxclone.com/)


lk

---

### Post by linuxkid3 on 2012-03-14
Yes I have the computer it comes from it's an old laptop with only space for one ide! one floppy and serial and parallel, NO cdrom, usb etc...

I dont have any other computers with internal ide connectors, and it sort of bugs me that I can't access it under linux, as I said the drive is ms-dos 5.0 and I have in the past used serial plip but I don't have a computer that has serial! so I am stuck with direct access, it's not such a problem what's on the computer, as I was thinking of getting rid of it, but I would like a digital image of the drive for my backup! and it seems like a good chalange! but I am stuck... 

yes I have read the ddresuce manual and it would look like -b is block size so I thought that might do something but I just get zero.

I think (but may be wrong) that it may be a kerenl config setting, or something in the usb system, but I would have thought that ide usb stuff is in a kerenl module? but it is years since I had to manual install the usb modules and I may be missing something easyer???

---

### Post by sudodus on 2012-03-14
Do you think it would work to connect the computers via a usb-to-serial adapter, according to the following link?

[[COLOR="Red"]_http://www.usb-serial-adapter.org/_[/COLOR]]("http://www.usb-serial-adapter.org/")

It suggests to get a 'PRO USB to Serial adapter', and describes what it means. I have no idea of the price level compared to standard adapters. I suggest that you check at some internet store in your country.

[I]Edit: Have you tried to run ddrescue (with a size limit)
- in normal mode (without -db 17)? What happens?
- with only -d (and let it find the sectors itself)? What happens[/I]

---

### Post by linuxkid3 on 2012-03-14
Yes I tried a ddresucue with just the -d and it looks great, but the file size I think would be 2TB in size and looking at the image with od you see:

```
0000000 177400 177400 177400 177400 177400 177400 177400 177400
*
1076600000
```
and I know the drive should look a bit more intrresting than that!

I don't have a usb to serial, might be a long term other distraction to play with, good idea...

For the moment I do wonder if my problems are with linux or in the chip of the usb to pata ide cable?

---

### Post by sudodus on 2012-03-14
> **linuxkid3 said:**
> Yes I tried a ddresucue with just the -d and it looks great, but the file size I think would be 2TB in size and looking at the image with od you see:

```
0000000 177400 177400 177400 177400 177400 177400 177400 177400
*
1076600000
```
and I know the drive should look a bit more intrresting than that!

I don't have a usb to serial, might be a long term other distraction to play with, good idea...

For the moment I do wonder if my problems are with linux or in the chip of the usb to pata ide cable?

I wonder too ... might be the chip of the usb to pata ide cable. An alternative to test that would be to attach the usb to pata ide cable to a computer with Windows. Or even test on a small partition to install Windows 98 (based on MSDOS and managing USB).

---

