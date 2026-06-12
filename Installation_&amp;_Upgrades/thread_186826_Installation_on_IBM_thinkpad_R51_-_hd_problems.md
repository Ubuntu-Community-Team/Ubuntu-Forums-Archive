---
title: "Installation on IBM thinkpad R51 - hd problems?"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by Doso on 2006-06-02
I tried to install/boot into LiveDVD of Ubuntu.

It all seems to go wrong here:

```

* Starting enterprise Volume Management

[4294767.616000] IBM TrackPoint firmware: 0x06, buttons: 3/3
[4294767.879000] input: TPPS/2 IBM TrackPoint as /class/input/input6
[4294774.527000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4294774.532000] hda: dma_intr: error=0x040 { Uncorrectable Error }, LBAsect=63227
73, sector=6322751
[4294774.542000] ide: failed opcode was: inknown
[4294774.546000] end_request: I/O error, dev, hda, sector 6322751
[4294774.546000] Buffer I/O error on device dm-0, logical block 6322688

```

After 2 screens of this messages it continues to boot into Gnome. I tried to use the installer to partition my drive for the installation but it took forever just to get the partitions to show up. After I setup the partitions like I want them to (resizing a NTFS partition to make room for / and swap and creating those partitions) I get an error that there was an error accesseing /hda

To see if this is a problem with 6.06 I tested the LiveDVD of 5.10. There I got no errors in the boot process but I also couldn't re-partition my HD like i wanted to and it also took forever to see the partition table in GParted. 

I am pretty sure that the harddrive is ok as it works flawless under Windows, SMART tells me there are no errors with the drive, other LiveLinux DVD/CDs work fine and don't report an error (SuseLinux 9.1 / latest KnoppixDVD) and a chkdsk under Windows didn't report any errors.

System Configuration:

Thinkpad R51 1829 R6G, 1,5GB Ram
Fujitsu MHT2060AT 60GB internal harddrive
Partitions:

C:\  with 15 GB for Windows XP - NTFS
D:\ with 40 GB for Data - NTFS

So much for my fast and easy switch to Linux](*,) 

Any ideas how i could fix/get around this and install Ubuntu?

---

### Post by mips on 2006-06-02
Have you checked the drive for errors ? Fujitsu should have some utils on their site for this.

I recalled someone having issues with a thinkpad where windows & pqm reported invalid partition sizes or something. Can you change the LBA status in the bios to see if it makes a difference maybe.

---

### Post by Doso on 2006-06-02
Nope, there is no option to change the LBA in any way. Wouldn't make much sense anyway.

---

### Post by Doso on 2006-06-02
Ok tried the text installation - no luck either :[

---

### Post by mips on 2006-06-02
Long shot, [http://ubuntuforums.org/showthread.php?t=178444](http://ubuntuforums.org/showthread.php?t=178444)

---

### Post by Doso on 2006-06-02
Hmm, interesting, I get the "partition doesn't end on cylinder boundary" message too when I use the fdisk of a Suse LiveCD, but nothing in Ubuntu o_O

I googled around but couldn't find a solution. Guess I'll be playing around with partition magic a while now.

---

### Post by Sointense on 2006-09-04
I know this post is a liitle old, but I thought I would throw my 2 cents in.

Just loaded up Ubuntu 6.06 from the DVD (text mode) on my R-51 with a fresh Toshiba 40 gig drive.

Everything loaded and is working correctly. 

My config is
R-51 288-CTO
512 meg RAM
1.5 GHZ Centrino processor. 
Make sure your grub is the 686 not 386

I tried using the 40gig drive in an external case connected vis USB, but I had a problem with drive mapping in Grub. I also had a problem with the IBM sometimes not recognizing the drive at the BIOS level.

After two days of jerkin around with it, I decided to just run it as an internal drive and swap it with my XP drive until I get the BIOS thing straightened out. 
If anyone has anything constructive to add (no "I have the same problem" posts) please add to the thread.

---

