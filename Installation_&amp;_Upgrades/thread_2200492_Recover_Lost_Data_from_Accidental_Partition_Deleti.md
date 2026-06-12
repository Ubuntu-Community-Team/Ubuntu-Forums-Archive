---
title: "Recover Lost Data from Accidental Partition Deletion"
date: 2014-01-19
forum: Installation &amp; Upgrades
---

### Post by Michael_Tu on 2014-01-19
1. I had a few small but annoying problems with Linux Mint, so decided  to give Ubuntu GNOME a try
 2. I ran the installer for Ubuntu GNOME from a live  USB, and on the step where I need to select where to install the OS,  there is an option to replace Mint Petra, so I selected that, thinking  it would leave my Windows partition intact and just replace Mint. I had  Windows 8.1 dualbooting with Mint.
 3. When the installation finished  and I restarted I realized the installer actually deleted all my  partitions and created a completely new partition table. I lost all the  data on my Windows partition. 
 4. I would like to know if there is a way to recover the data from an  old partition in an old partition table. I Googled this but seems  TestDisk can only recover partitions if the partition table wasn't  changed.

---

### Post by TheFu on 2014-01-19
Got a backup?
Sorry, it doesn't look good.

There are "possible" recovery methods out there, but for a real-world application trying to restore files without the resources of the NSA, it is not practical.  You will spend the next 10 days working on this and might get a few files back. You'll probably get another HDD or 2 and try to bit-for-bit copy everything off, you know, for safety.  In 2-4 months, you'll realize that you didn't get the data back and move on, but the original HDD will sit on a shelf for a year or two.

I'm speaking from experience here.

Get over it. *Your data is gone.*  There, I've said it.  I know you won't believe me. It is the harsh truth, unless you have $5K to ship the HDD off to a commercial data recovery expert with years of experience recovering stuff like this.  I can recommend "myharddrivedied.com". Scott knows his stuff and has a DB of file metadata to help restore commonly found files quickly ... then the manual labor begins to get all the files that cannot be restored through automatic methods.

Use this as a learning experience to **Get Backup Religion**. With a backup, this should be a trivial inconvenience only.

---

### Post by QIII on 2014-01-19
Hello!

Absolutely do NOT use the machine for now.  The more you do, the more likely that your files will be overwritten.

Please read all the way through [this]("https://help.ubuntu.com/community/DataRecovery").

Pay special attention to the sections about recovering data from NTFS partitions.

Ask questions if you have them.

Best wishes.

---

### Post by Zhivargo on 2014-01-20
Sorry to hear that

it is possible to restore partitions with mkntfs but how big is your HDD because windows allocated different cluster sizes depending on how large it is. some advanced options you would need to put in
```

Advanced options

-c, --cluster-size BYTES
Specify the size of clusters in bytes. Valid cluster size values are powers of two, with at least 256, and at most 65536 bytes per cluster. If omitted, mkntfs uses 4096 bytes as the default cluster size.
Note that the default cluster size is set to be at least equal to the sector size as a cluster cannot be smaller than a sector. Also, note that values greater than 4096 have the side effect that compression is disabled on the volume (due to limitations in the NTFS compression algorithm currently in use by Windows).

-s, --sector-size BYTES
Specify the size of sectors in bytes. Valid sector size values are 256, 512, 1024, 2048 and 4096 bytes per sector. If omitted, mkntfs attempts to determine the sector-size automatically and if that fails a default of 512 bytes per sector is used.
-p, --partition-start SECTOR
Specify the partition start sector. The maximum is 4294967295 (2^32-1). If omitted, mkntfs attempts to determine part-start-sect automatically and if that fails a default of 0 is used. Note that part-start-sect is required for Windows to be able to boot from the created volume.

```

also you probably need to tell mkntfs where to start the filesystem, and how big it was... down to the block or sector.... 

trash me if im wrong but it may be next to impossible...

---

### Post by Michael_Tu on 2014-01-20
I have a 750 GB hard disk.

I'm currently running PhotoRec. I think it runs in read only mode so it doesn't overwrite data on the hard drive. It writes to an external hard disk. It looks for known file types like .jpg, .doc[x], etc. It recovered a lot of files but it does not recover file names. It will be a lot of effort to sort through the files. I'm currently exploring other options out there.

---

### Post by Michael_Tu on 2014-01-20
I now know my original partition scheme exactly in terms of megabytes. It is based on the Default UEFI/GPT diagram found on [http://technet.microsoft.com/en-us/library/hh824839.aspx](http://technet.microsoft.com/en-us/library/hh824839.aspx), with a 128 GB exf4 at the very end. The Windows RE partition was 500 MB and the size of the MSR is 128 MB. The other partitions are the EFI System partition (100MB, not shown in diagram) and the main Windows OS partition. Can I give these parameters to a recovery program to try to recreate the partition table? Do I need to know sector size (not sure of the term exactly) and how will I find that if I need it? Thanks in advance.

---

### Post by Mark Phelps on 2014-01-20
My own experience has been that MS Windows utilities do a better job of recovering Windows filesystems -- and Linux utilities, recovering Linux filesystems.

The Minitool Partition Wizard Boot CD (which you have to burn to a CD) can sometimes restore Windows filesystem partitions.

As to data recovery, if you're willing to spend a little money to get your files back, and have access to a Windows PC, then read on ...
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from [http://getdata.com](http://getdata.com).
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to their website, you can compare versions and features.

Your data ... your money ... your choice.

---

### Post by Michael_Tu on 2014-02-06
In the end I just imaged my drive using dd. I hope to use PhotoRec to recover some files by scanning the image.

---

### Post by Votlon on 2014-02-07
The recuva software for windows actually got back most of my data when i copied over my hard drive granted some was corrupt or missing thumb nails but i got back 90% of my family photos and all of my work files :).
[URL="http://www.piriform.com/recuva/download"]

http://www.piriform.com/recuva/download[/URL]

---

