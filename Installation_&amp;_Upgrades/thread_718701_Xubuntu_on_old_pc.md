---
title: "Xubuntu on old pc"
date: 2008-03-08
forum: Installation &amp; Upgrades
---

### Post by Rumel on 2008-03-08
I'm trying to install Xubuntu on an old pc. I'm using a Xubuntu 7.10 Alternate i386 install cd. When I am installing it starts out normally by asking language, detecting keyboard and yada yada. Then it asks me for where my cd drive is. I tried to use ls /dev to see but I only get the bottom half of the results I don't know how to scroll up and see the rest. I have a Mitsumi Cd-Rom FX4831T!A. Does anyone know of drivers for this or what I need to enter to access this drive? Help would be much appreciated. I would like to give some new life to this PC.

---

### Post by Pumalite on 2008-03-08
Try another small distro like Puppy to see if your burner is dead or is just Xubuntu.
Also, you could burn a new CD after doing md5sum on your iso.
Clean the lens in your burner, just in case.

---

### Post by Rumel on 2008-03-08
Nope, the burner isn't dead. It's whipped out plenty of cds. I actually just used puppy on the old computer, but I'm not going to install puppy on it. I want to use Xubuntu. Xubuntu will boot with the cd and it will start to install from the cd, but then it wants you to later specify the /dev and I dont know which one. The md5sum passed.

---

### Post by jken146 on 2008-03-08
For seeing the whole of the output in the terminal, use less.

```
ls /dev/ | less
```

Press Enter to see the next page and Q to exit.

---

### Post by Rumel on 2008-03-09
I tried ls /dev/ | less and that didn't work.

---

### Post by Pumalite on 2008-03-09
How many hard drives do you have?

---

### Post by kelean on 2008-03-09
Have you tried using the live CD of Xubuntu?

---

### Post by Rumel on 2008-03-09
Yes I have. It doesn't work.

---

### Post by kelean on 2008-03-10
Have you tried any other distros?  If so do you have any problem with those or is it just a Ubuntu problem

---

### Post by FlyDanoFly on 2008-03-11
I'm having the exact same problem, although I'm trying Ubuntu Server 7.10 rather than Xubuntu.  Since it is failing at the same point, I'll bet we're both in the same boat.

My computer has Gentoo which did some simple server stuff until an upgrade went wrong (I was getting tired of it anyway).  The CD-ROM works great on it, I can mount the Ubuntu installer CD-ROM and look through the files and dirs just fine.

Gentoo see the CD-ROM drive as /dev/hdc, it appears that maybe the Ubuntu Installer is trying at access it as /dev/sdb, but I can't tell for sure.  Under gentoo I can get all sorts of info, will any if this be helpful for getting more help?

Thanks!

---

### Post by Pumalite on 2008-03-11
Make sure you burn the iso as 'image', not as 'data'
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)

---

### Post by prshah on 2008-03-11
> **Rumel said:**
> I'm trying to install Xubuntu on an old pc. I'm using a Xubuntu 7.10 Alternate i386 install cd. When I am installing it starts out normally by asking language, detecting keyboard and yada yada. Then it asks me for where my cd drive is. I tried to use ls /dev to see but I only get the bottom half of the results I don't know how to scroll up and see the rest. I have a Mitsumi Cd-Rom FX4831T!A. Does anyone know of drivers for this or what I need to enter to access this drive? Help would be much appreciated. I would like to give some new life to this PC.

Well normally, the CD/DVD drive will be mounted at /dev/cdrom.

If you have two drives; cdrom0 and cdrom1, and cdrom will point to the last used drive.

cdrom0 and cdrom1 in turn, point to sr0 and sr1.

These are for IDE drives, but they are being handled as SCSI driver hence sr0 and sr1.

If you run the command:

```

dmesg | grep -i "cd-rom"

```

you will get details as below
> 
[   20.426257] scsi 0:0:0:0: CD-ROM            TSSTcorp CD/DVDW SH-S182D SB00 PQ: 0 ANSI: 5
[   20.427502] scsi 0:0:1:0: CD-ROM            TSSTcorp CD/DVDW SH-S182D SB00 PQ: 0 ANSI: 5
[   21.460021] Uniform CD-ROM driver Revision: 3.20
[   21.460254] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   21.469195] sr 0:0:1:0: Attached scsi CD-ROM sr1


Hope this helps

Cheers,
PRShah

---

### Post by FlyDanoFly on 2008-03-11
The downloaded image passed the md5sum check.  It appears the disc has been burned properly, it has been verified and used to install Ubuntu server on a newer machine.

I can't speak to the problem where an old machine can't read the disc if it burned "too fast", is this still an issue with modern burners?

A few other things of interest...

There are 64Megs on the computer, so it has to resort to "low memory" mode.  Could this be messing it up?  On the server download page, there is a box to click to get the "alternate" cd, but it just downloads the same one I originally got: ubuntu-7.10-server-i386.iso.

When it tries to detect the CDROM, there is no /dev/cdrom, nor /dev/sr* devices.  There is a /dev/sdb, and some /dev/sg* devices.  The cddrive is on the secondary controller (as master).

There are some error messages (typing these by hand):
...
sd 0:0:1:0: [sda] Attached SCSI disc
sd 1:0:0:0: [sdb] 256041 2048-byte hardware sectors (524 MB)
sd 1:0:0:0: [sdb] Write Protect is off
sd 1:0:0:0: [sdb] Mode Sense:00 3a 01 00
sd 1:0:0:0: [sdb] Cache data uvavailable
sd 1:0:0:0: [sdb] Assuming drive cache: write through
...(repeats this twice)
... other stuff ...
sd 0:0:1:0: Attached scsi generic sg0 type 0
sd 1:0:0:0: Attached scsi generic sg1 type 0
... other stuff ...
end_request: I/O error, dev sdb, sector 1024160
Buffer I/O error on device sdb logical block 256040
...(these 2 repeat several times with silghtly differect sector/block numbers)
end_request: I/O error, dev sdb, sector 40
end_request: I/O error, dev sdb, sector 44
...(these 2 repeated about 5 times with the same numbers)

After entering all the language stuff and it tries to detect the CD, that's where all the difficulty is happening.  I've tried:
1. doing it more than once
2. different devices /dev/hdc, /dev/sdb, /dev/sg1
3. various options (CDROM, gscd, etc) 

I've not done all the above exhaustively for every combination.

I have never entered anything for the PCMCIA resource range options (it is a desktop, I assume there isn't any PCMCIA and don't see anything that looks like it).

Thanks!

---

### Post by prshah on 2008-03-12
> **FlyDanoFly said:**
> 
There are some error messages (typing these by hand):
...

end_request: I/O error, dev sdb, sector 1024160
Buffer I/O error on device sdb logical block 256040
...(these 2 repeat several times with silghtly differect sector/block numbers)
end_request: I/O error, dev sdb, sector 40
end_request: I/O error, dev sdb, sector 44
...(these 2 repeated about 5 times with the same numbers)



These errors are familiar. I had them too when I was using a TSSTCorp / Samsung / Toshiba combine drive.

Essentially: for some reason newer Samsung ODDs are not working with Ubuntu 6.10 7.04 and 7.10. If you google for TSSTCorp you will get a lot of links about this. Note that Damn Small Linux and PuppyLinux work just fine in the same setup.

I solved the case by simply using another drive. However, once the install is over, the TSSTCorp drive works fine. Go figure.

Note that if I am using Samsung HDDs and the system goes down improperly, I face the same problem when the system check is run... this time on the hard drives. sigh.

For more details on this issue, google "TSSTCorp linux" or see my other post : [http://ubuntuforums.org/showthread.php?t=703228&highlight=samsung+odd](http://ubuntuforums.org/showthread.php?t=703228&highlight=samsung+odd)

There are also a number of posts in Ubuntu forums with "Buffer I/O error" and they all seem to be related to this type of ODDs (Optical disk drives).

If you are NOT using a TSSTCorp / Samsung / Toshiba drive, I dont know what the problem is except faulty medium/linkage; maybe burn your live cd at a slower speed, or change the HDD cables.

Cheers,
PRShah

---

### Post by FlyDanoFly on 2008-03-13
Fascinating... my drive is a Mitsumi FX4831T, but perhaps it has the same problem too.  I'll see if I can find a different drive and post back the results.

---

### Post by FlyDanoFly on 2008-03-13
I found another older CDROM drive to use (a Toshiba of some sort).  Sure enough, the installation went along swimmingly.  Unfortunately, the server kernel image won't fit the 64 megs that this old system boasts so I can't tell if it will recognize the original drive.   So either I'm done, need to upgrade the memory, need another Ubuntu flavor, or a different distro.  I'll be putting this project on the backburner for awhile, thanks for the help.

---

### Post by FlyDanoFly on 2008-03-13
One last update, I decided to fiddle with it a little more.  I think the problem isn't the kernel image, but instead a problem with GRUB.  When I try to type anything on the GRUB command line, instead of typing out the characters I'm pressing, it just parrots back the last option from the menu file, and that doesn't work anyway.  It will allow me to press 'Enter', and then it just says 'Error 28: cannot fit image into memory' (paraphrased) again and again and again.  Ironically, it is the memtest+ program it is parroting.

I've also tried creating a GRUB boot disk, and I get the same behavior.

I'm guessing it is some weird combo of my old Gateway computer, the bios, and/or the usb keyboard (ONLY usb ports, no other options for a keyboard).  Unless there are any other interesting suggestions, I'm feeling I will let this go for now.  It's starting to get outside the realm of the kind of tinkering I find interesting on Linux.

---

