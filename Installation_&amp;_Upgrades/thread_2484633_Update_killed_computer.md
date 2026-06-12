---
title: "Update killed computer"
date: 2023-03-04
forum: Installation &amp; Upgrades
---

### Post by dkolars on 2023-03-04
Just did automatic update, Ubuntu 22.04... Now system will not boot.  Here's display::

scsi 10:0:0:1:Failed to get diagnostic page 0x1
scsi 10:0:0:1: Failed to bind enclosure - 19
usb 8-1.2.1: 3:1: cannot get freq at ep0x84

Going to command prompt (startx) yields::
unable to connect to X server: Connection refused

I've tried turning off external camera, mic, HDD's, etc.  No difference.

24 pkgs held back from upgrade, but it appears that the Nvidia & Xorg pkgs are broken... Nvidia-driver-525 has the wrong version... Can't see all the programs that are held back (more than a screen full), but lots of Nvidia there.

Of course, the repository for Nvidia is not a Linux repository...

I leave tomorrow for 9 days out of state, so any suggestions/fixes /etc can't be tried until mid-March!

---

### Post by dkolars on 2023-03-04
Added info... Can NOT boot from USB... Trying takes me to error screen, same messages. Can NOT enter BIOS set-up...

Ran Disk-Repair... Now says "Missing operating system".

Now, very dead!

---

### Post by Bashing-om on 2023-03-04
Hello dkolars

Please see:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1990750](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1990750)

Does this work-around work for you; or just a matter of waiting for phased updates to catch up ?

[INDENT]Maybe[/INDENT]

---

### Post by MAFoElffen on 2023-03-05
Can you get to a Grub2 Menu Screen at boot?

If so, then press the <E> key to get into an edit mode... . <Arrow-Down> to get to the line starting with 'linux'... <Arrow-Right> to remove 'quiet splash' and add '3'. Press <Cntrl><X> to boot with those run level options.

That will boot you to a text console (without trying to load the graphics layer) where you will have to log in with your credentials.
```

sudo apt install --reinstall nvidia-driver-525 nvidia-dkms
sudo reboot

```

---

### Post by dkolars on 2023-03-14
Back home after travels...  Situation is:  Computer will attempt to boot, but hangs up, black screen.  I got newest version of Boot-Repair-Disk, and it fixed many things (so it said).  Still not able to boot.  OK, got Xubuntu 22.04.2.iso file.  Put on CD.  System will not boot from CD.  Have file on USB stick.  System can't even see USB drives (Boot-Repair could see them all)...  So, thought perhaps existing, broken system was messing something up, pulled the 500Gb SSD, and put in a new one...  CD should open on start-up then, right?  Right?  Nope..."error: unknown filesystem"  Now at the grub rescue> prompt.  

Running Grub rescue commands... only "ls" & "set" work.  All other commands are "unknown".

So, is Ubuntu broken?  iso file should open on restart, but not doing it.  Like I said, Boot-Repair could see all the USB drives and read their contents!!  Gonna be hard to run the system when system can't see the .iso file to install Xubuntu...  Something weird here...

Attempted to start laptop from CD... failure again.  Bad .iso file, perhaps?  Will have to get via torrent and see if that changes anything.  Sigh

OK, d/l torrent .iso file, burned to DVD disk...  NOT recognized on start-up.
------------------------------------------------------------------------------  
error: no such device: 9e5db633-d119-45c8-9429-e921d63-e8d2
error: unknown filesystem.
Entering rescue mode...
grub rescue>
------------------------------------------------------------------------------

NO idea what device it's looking for!!  How does one install 22.04 to a HDD these days?  Used to be a very simple process.

---

### Post by ubfan1 on 2023-03-14
md5sum check the downloaded iso:
  See [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
  Check the number against the listing in the link for your release listed at
  [http://releases.ubuntu.com](http://releases.ubuntu.com) under the MD5SUMS link.
  For other releases' hashes, like lubuntu, see:
  [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
 
 If using a CD/DVD, did you burn the disc as slowly as possible?
  See [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
  If using USB install media, use a  tool like unetbootin or rufus. 
  Don't just copy files to the USB.  
  See [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)  

 Did you select the media check before trying to install?  
  See [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

How did you put the iso on the CD/USB?  What program? Even dd should work, but other programs may offer additional capabilities like persistence.

---

### Post by dkolars on 2023-03-15
Well, I'll investigate all the above... seems a lot more complicated than it used to be?  I d/l the .iso, burned it to DVD using Xfburn, as I've done for years when needing an .iso.  

There are 3 directories on the DVD:
El Torito Boot
El Torito BootJoliet level 3
ISO9660

This looks like what I'm familiar seeing on previous DVD discs.  Only this time it doesn't work!!

---

### Post by dkolars on 2023-03-16
Well, after much putzing, I now have NO error messages, but the system hangs after finding the OS:
/dev/sda6:  clean, 999/999 files, 999/999 blocks.
Flashing cursor, and there it sits.  DVD still not working...  Boot-Rescue working fine, but can't connect to internet from it, even tho' it wants me to...

---

### Post by TheFu on 2023-03-16
Sounds like there's some hardware issues that are getting in the way.
I'm not convinced that the optical drive isn't starting to fail too.

With USB-flash drives, just copying the ISO file over into an existing file system doesn't work. You have to copy it over in a specific way.

Here's what a USB flash drive looks like after mounting the 3 partitions and running 
```
$ lsblk -e 7 -o name,size,type,fstype,mountpoint
...
sdc                               7.5G disk iso9660     
&#9500;&#9472;sdc1                            1.3G part iso9660     /mnt/1
&#9500;&#9472;sdc2                            3.9M part vfat        /mnt/2
&#9492;&#9472;sdc3                            6.2G part ext4        /mnt/3
```

That's a 20.04 (focal) server x86-64 installation.  I don't have any desktop releases handy. Sorry.

---

### Post by dkolars on 2023-03-16
> **TheFu said:**
> Sounds like there's some hardware issues that are getting in the way.
I'm not convinced that the optical drive isn't starting to fail too.

With USB-flash drives, just copying the ISO file over into an existing file system doesn't work. You have to copy it over in a specific way.

Here's what a USB flash drive looks like after mounting the 3 partitions and running 
```
$ lsblk -e 7 -o name,size,type,fstype,mountpoint
... like 
sdc                               7.5G disk iso9660     
&#9500;&#9472;sdc1                            1.3G part iso9660     /mnt/1
&#9500;&#9472;sdc2                            3.9M part vfat        /mnt/2
&#9492;&#9472;sdc3                            6.2G part ext4        /mnt/3
```

That's a 20.04 (focal) server x86-64 installation.  I don't have any desktop releases handy. Sorry.



OK, as stated before, the system will NOT recognize the USB when plugged in, just like it will not recognize the DVD when in tray.  IF the optical drive is the problem, putting in the new one should have fixed that, yeah?  Error message with that as well...  I burned the DVD with Xfburn, not copied, so it should be a valid disc.

---

### Post by MAFoElffen on 2023-03-16
> **dkolars said:**
> Flashing cursor, and there it sits. [COLOR=#ff0000]** DVD still not working...**[/COLOR]  Boot-Rescue working fine, but can't connect to internet from it, even tho' it wants me to...

[QUOTE=dkolars]There are 3 directories [COLOR=#ff0000]on the DVD[/COLOR]: [/QUOTE]
What is this computer? Make, model, CPU, GPU?

RE: [https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1930880](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1930880)

At Ubuntu Version 21.04 and later, the size of the ISO and the fsck process that was added, the Live Image is meant to boot from a USB device. The problem that occurs is that many systems trying to read from a DVD Optical Drive, because of the read speeds, will get timeout errors and fail... Especially during the fsck process at the start. Some machines take over 30 minutes to boot from DVD with 22.04. Sometimes adding a ""fsck.mode=skip"" as a boot parameter will help with this...

Does it not boot from a USB Thumb drive?

But before that, do you not want to try to see if you can fix your computer without having to reinstall the whole system first? For example, when it boots and goes to a blank screen, can you hold down the <Cntrl><Alt><F4> keys and toggle over to VTTY session? Do you ver see the Grub2 menu like I asked you in Post #4? You have NVidia, with NVidia drivers installed on your system... That is an easy fix if you can get to either of those...

---

