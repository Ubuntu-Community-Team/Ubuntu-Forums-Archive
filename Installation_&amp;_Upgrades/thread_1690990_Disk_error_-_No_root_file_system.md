---
title: "Disk error - No root file system"
date: 2011-02-19
forum: Installation &amp; Upgrades
---

### Post by Gingerhouse on 2011-02-19
Hello, I was trying to install Ubuntu desktop and laptop edition on a Sony Vaio netbook from a USB drive, but after I select the entire disk to be used and hit enter I get this message
No root file system is defined. Please correct this from the partitioning menu. 
If I try to start windows I just get s black screen.

---

### Post by kansasnoob on 2011-02-19
Perhaps this:

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

or this:

[http://members.iinet.net.au/~herman546/p23.html](http://members.iinet.net.au/~herman546/p23.html)

might be helpful.

But these two highlighted comments are confusing to me:

> after I select the **[COLOR="Red"]entire disk[/COLOR]** to be used and hit enter I get this message
**[COLOR="Red"]No root file system is defined.[/COLOR]** Please correct this from the partitioning menu. 

It would probably be helpful for us to see the output of this command run from the Live USB:

```
sudo parted -l
```

---

### Post by Gingerhouse on 2011-02-19
I mean that when I try to install ubuntu I have two options, I can use the entire disk or a partition. After I check ``use the entire disk`` option and hit enter, a window appers with the message ``No root file system is defined. Please correct this from the partitioning menu``. 

I ran ubuntu from the USB drive without installing, then opened a terminal and got this 

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA TOSHIBA MK2555GS (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  22.5GB  22.5GB  primary


Model: Kingston DT 101 G2 (scsi)
Disk /dev/sdb: 8011MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      31.7kB  8005MB  8005MB  primary  fat32        boot, lba

---

### Post by kansasnoob on 2011-02-19
> **Gingerhouse said:**
> I mean that when I try to install ubuntu I have two options, I can use the entire disk or a partition. After I check ``use the entire disk`` option and hit enter, a window appers with the message ``No root file system is defined. Please correct this from the partitioning menu``. 

I ran ubuntu from the USB drive without installing, then opened a terminal and got this 

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA TOSHIBA MK2555GS (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  22.5GB  22.5GB  primary


Model: Kingston DT 101 G2 (scsi)
Disk /dev/sdb: 8011MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      31.7kB  8005MB  8005MB  primary  fat32        boot, lba

Well, I'm a bit worried :(

What version of Windows do you have?

Please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Or here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

There is a specific bug in Maverick's ubiquity I posted some about in post #15 here:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

But that should not result in "No root file system is defined. Please correct this from the partitioning menu".

Regardless the most worrisome thing is this, "If I try to start windows I just get s black screen." The info requested may help us understand what damage you've already done to Windows.

It would be unwise to proceed with any installation until we find out what's up with Windows! If you've written no changes to the disc it may be recoverable using TestDisk:

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by Gingerhouse on 2011-02-19
I have windows 7.
I can`t download Boot Info Script or TestDisk. When I try to download I get this message window
``Download error. There is no sufficient memory to complete the action you requested. Quit some applications and try again.``
I also can`t open GParted, a window opens and then it immediately disappears.

When I open a terminal and type sudo parted /dev/sdb print, I get this

buntu@ubuntu:~$ sudo parted /dev/sdb print
Model: Kingston DT 101 G2 (scsi)
Disk /dev/sdb: 8011MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      31.7kB  8005MB  8005MB  primary  fat32        boot, lba

ubuntu@ubuntu:~$

---

### Post by kansasnoob on 2011-02-19
I'm not sure why your live USB is acting up. Have you just tried rebooting?

What worries me the most is this:

> ubuntu@ubuntu:~$ sudo parted -l
Model: ATA TOSHIBA MK2555GS (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number Start End Size Type File system Flags
1 1049kB 22.5GB 22.5GB primary

You appear to have only one 22.5GB partition on that 250GB drive.

---

### Post by Rubi1200 on 2011-02-19
If you are having issues with the Ubuntu LiveCD, give Slax a try:
[http://distrowatch.com/table.php?distribution=slax](http://distrowatch.com/table.php?distribution=slax)

Unlike the Ubuntu CD, Slax does not try and auto-mount partitions and I have used this to successfully troubleshoot booting problems in the past.

I don't think Testdisk is available on it, but you can certainly run the boot script kansasnoob asked for.

By the way, the Slax terminal is a root terminal by default so no need to preface the command with sudo or su.

Hope this helps.

---

### Post by Gingerhouse on 2011-02-19
@kansasnoob: I've tried to erase the entire disk and create a new table partition with 2 partitions, an ext4 one and a swap one, format the ext4 one and install ubuntu on that partition, but I get the same error message, it's like my hdd suddenly disappeared.

@rubi1200: I've installed ubuntu on my other laptop some time ago, it works really nice, I like it and I got used to it, so it would be easier for me to have ubuntu on both laptops. But if the installation problem persists I would try installing slax, as you recommend.

---

### Post by Rubi1200 on 2011-02-19
You misunderstood my intent. Slax needs to be used as a LiveCD to troubleshoot whatever is going on with the laptop.

I assumed you were trying to follow the advice posted by kansasnoob from a LiveCD. That is why I suggested Slax as a possible alternative.

---

### Post by kansasnoob on 2011-02-20
> **Gingerhouse said:**
> @kansasnoob: I've tried to erase the entire disk and create a new table partition with 2 partitions, an ext4 one and a swap one, format the ext4 one and install ubuntu on that partition, but I get the same error message, it's like my hdd suddenly disappeared.

@rubi1200: I've installed ubuntu on my other laptop some time ago, it works really nice, I like it and I got used to it, so it would be easier for me to have ubuntu on both laptops. But if the installation problem persists I would try installing slax, as you recommend.

Well, I'm confused :confused: In your original post you said, "If I try to start windows I just get s black screen." Of course, if you've erased the entire disk, then Windows is gone!

And, if you're choosing, Erase and use entire disc from here:

[ATTACH]183990[/ATTACH]

It will erase everything and, since you have a 250GB drive, it would typically create one primary partition (about 240+GB) and one logical partition for SWAP (about double the amount of RAM), but you show only one 22.5GB primary partition :confused:

Also you mention, "when I try to install ubuntu I have two options, I can use the entire disk or a partition. After I check ``use the entire disk`` option and hit enter, a window appers with the message ``No root file system is defined. Please correct this from the partitioning menu". But the only time you should see those two options is if you've chosen "Install alongside" as I discussed here:

[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)

The only time I've seen the message "No root file system is defined" is if I've chosen the "Specify partitions manually (advanced)" option because you must set the "Mount point" as shown here:

[ATTACH]183991[/ATTACH]

So, I guess question #1 needs to be, did you want to wipe out Windows? You already did!

If you want to try and recover Windows or any of it's data then it's important to NOT write any changes to the disc!!!!!!!!!!!

Please look closely at posts #1 and #15 here:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

Then let us know what your intention was.

---

### Post by Gingerhouse on 2011-03-01
@Rubi1200: yes, I misunderstood you. You mean I can create a LiveCD with Slax on it and run it without installing?
@Kansasnoob: I've tried what you said several times and I got the same message. The instalation begins, but after a few minutes it stops and I get the same error message. 
And right now it doesn't recognize the USB memory where I downloaded Ubuntu, before I could run Ubuntu without installing it, now I can't even do that... I'm worried.

---

### Post by Rubi1200 on 2011-03-02
Hi Gingerhouse,
> You mean I can create a LiveCD with Slax on it and run it without installing?

Exactly. Once you have burned it to CD you can try and boot the computer with it. The reason I suggested Slax is because, unlike the Ubuntu CD, it does not try and auto-mount partitions.

If you can boot the computer, then we can take things further.

Good luck and let us know what happens please.

---

### Post by Gingerhouse on 2011-03-02
Ok, I got slax on an USB drive and I can boot the computer. Thx. Now what should I do next?

---

### Post by Rubi1200 on 2011-03-02
Okay, great.

Open a terminal (there should be an icon on the lower panel I think or from the main menu) and then do the following:

Boot the LiveUSB. Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Gingerhouse on 2011-03-02
Now Slax won't start. 

linuxrc: line 290: cannot open dev/console: Read-only file system.

---

### Post by Rubi1200 on 2011-03-03
At what point do you get this error?

If you were able to boot the computer previously with Slax, what changed?

---

### Post by Gingerhouse on 2011-03-03
It happens at the end of the automatic boot. It stops here:
[http://www.flickr.com/photos/imreeallen/5494411205/](http://www.flickr.com/photos/imreeallen/5494411205/)
I'm not sure, but this problem began after I connected the computer to internet.

---

### Post by Rubi1200 on 2011-03-03
And if you try without the Internet connection? Same thing?

If you boot without being connected and can get to the live desktop on Slax, would you be able to connect at that point?

I think it is at least worth trying.

Did you set BIOS to boot from the USB stick (sometimes called Removable Drives in BIOS)?

---

### Post by Gingerhouse on 2011-03-03
It doesn't matter if I am connected or not, I get the same result. 
Yes, I set BIOS to boot from USB, in my version of BIOS it appears as external drive. 
Maybe something happened to the USB memory? I remember something similar happened with ubuntu. I ran ubuntu without installing, I got to the desktop, everything went fine, and then, when I restarted the computer and tried to run ubuntu from the liveCD again, it just didn't work.

---

### Post by Rubi1200 on 2011-03-04
I don't know what to tell you :-(

I will keep looking for a solution, but this could be a hardware issue and/or damage to the drive itself.

Don't give up yet, keep trying.

---

### Post by Gingerhouse on 2011-04-19
Problem solved.  I sent the netbook to Sony to have it fix. They said the hard drive had too many errors and just got blocked. I just got it back and tried to install Ubuntu again and works just fine ;) Thank you all.

---

### Post by Rubi1200 on 2011-04-19
Excellent! I am really pleased you got this fixed in the end :-)

---

