---
title: "No disk drive detected"
date: 2008-04-21
forum: Installation &amp; Upgrades
---

### Post by jmcdowal on 2008-04-21
I'm attempting to installing Ubunto 7.10 on a Dell Dimension 4400. 
After selecting "Install in text mode", the first steps of the installation proceed as expected:

- Choose language
- Choose a country
- Detect keyboard layout
- Scanning CDROM
- Loading additional components
- Detecting network hardware
- Configuring the network with DHCP
- Hostname
- Detecting disks

Then, the installation prompts to select a driver for the disk drive with the following message:

  No disk drive was detected. If you know the name of the driver needed
  by your disk drive, you can select it from the list.

As reported in bug #80503, I tried installing with the option pci=nommconf. However, 
I experience the exact same problem as above.

Please advise

---

### Post by ikt on 2008-04-21
what kind of drive is it? ide or sata?

---

### Post by jmcdowal on 2008-04-22
Ide

---

### Post by wpshooter on 2008-04-22
Have you previously or currently had any other O/S running from this hard drive ?

Make sure that all drive related parameters in the BIOS are set correctly.

---

### Post by jmcdowal on 2008-04-22
Yes, I have had Windows XP Pro running for years from this drive in this computer.  I would like to totally reformat the drive and make this a pure unbuntu install.  At least that's what I'm trying to do. 

Since the hard drive is recognized OK by windows, I assume that the BIOS settings are OK.

Thanks.

---

### Post by raygj on 2008-04-23
hi,
I had exactly the same problem.my gutsy system used /dev/hda1 and /dev/hda2 for windowsXP and /dev/hdd1 for / (root system) and /dev/hdd5 for linux swap.

After installing heron upgrade these devices were replaced with /dev/sda1 and /dev/sda2 and /dev/sdd1 and /dev/sdd5. 
As the mountlist  did not have  these new disk device names  listed in /etc/fstab and there were no similarly named [LIST]
[/LIST] folders in /media/ for these /dev's the boot failed (same as you)

I rebooted into the install CD and created a folder /media/test (as root) then I mounted my hard disk's /dev/sdd1 ("/" partition) as /media/test then I opened /media/test (edit as root) and changed each /dev/hdxx to /dev/sdxx (xx=your partition names)   

The old /media/test/etc/fstab contents =
```
 /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/hdd1
UUID=1b80f362-2e57-4bdb-a9b1-e319ff22bab1 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/hdd5
/dev/hdc /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/fd0 /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0
/dev/hda1 /media/hda1 ntfs-3g defaults,force 0 0
/dev/hda2 /media/hda2 ntfs-3g defaults,force 0 0
usbfs /proc/bus/usb usbfs rw,devgid=14,devmode=0660 0 0
/dev/hdb1 /media/hdb1 auto nouser,atime,noauto,rw,nodev,noexec,nosuid 0 0
/dev/hdb5 none swap auto 0 0
/dev/hdd5 <mount\040point> swap auto 0 0
/dev/hda2 /media/hda2 auto nouser,atime,noauto,rw,nodev,noexec,nosuid 0 0
/dev/hda1 /media/hda1 auto nouser,atime,noauto,rw,nodev,noexec,nosuid 0 0
/dev/hdc5 <mount\040point> swap auto 0 0
```


Then AFTER EDITING /media/test/etc/fstab contents are 


 ```
/etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sdd1
UUID=1b80f362-2e57-4bdb-a9b1-e319ff22bab1 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/hdd5
/dev/hdc /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/fd0 /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0
/dev/sda1 /media/sda1 ntfs-3g defaults,force 0 0
/dev/sda2 /media/sda2 ntfs-3g defaults,force 0 0
usbfs /proc/bus/usb usbfs rw,devgid=14,devmode=0660 0 0
/dev/sdb1 /media/sdb1 auto nouser,atime,noauto,rw,nodev,noexec,nosuid 0 0
/dev/sdb5 none swap auto 0 0
/dev/sdd5 <mount\040point> swap auto 0 0
/dev/sda2 /media/sda2 auto nouser,atime,noauto,rw,nodev,noexec,nosuid 0 0
/dev/sda1 /media/sda1 auto nouser,atime,noauto,rw,nodev,noexec,nosuid 0 0
/dev/sdc5 <mount\040point> swap auto 0 0
```

now create new sd(xx) folders in /media/test/media/
matching ALL the folder names already there EG
 if /media/test/media/hda1 exists create a new folder
 named /media/test/media/sda1
etc,etc,etc

then save the edited /media/test/etc/fstab
and reboot


the boot process will now find your disks and boot up Ok
I hope this helps
regards Ray

---

### Post by raygj on 2008-04-23
Please disregard my last post!! this was my first post on this forum and Somehow I've WRONGLY REPLIED to your question by mistake.SORRY.
regards Ray

---

### Post by ikt on 2008-04-24
going over basic stuff here >.> but have you tried using another ide cable or the second ide port?

---

### Post by defex on 2008-04-30
I am having this problem with being unable to detect my hard drive as well. I'm trying to install 8.04 Server 64bit on an Asus P5KPL-VM with a Sata SeaGate 200GB hard drive. I get to a point in the installation where it tells me "No disk drive was detected" and nothing I have done seems to be working.

I have checked all the BIOS settings. Even went as far as disabling enhanced sata support, enabling compatible mode for sata, compatible sata+pata combined mode, enhanced sata+pata combined mode, eveything basically but nothing effects it.

The harddrive did have Windows 2k3 installed on it before I tried installing Ubuntu, but I cannot see how this would effect Ubuntu detecting the hardware.

The BIOS has detected the hard drive just fine in the sata 1 slot, so I'm at a loss to why hardy can't see it.

---

### Post by defex on 2008-04-30
Well, speak of the devil. All this time wasted trying to figure the problem out, and I manage to figure out the solution minutes AFTER posting in the forum. :)

I added the following to the boot options before running the installation and all went well. Hardy found my HDD and I was away laughing.

```
pci=nommconf irqpoll
```

I think in my case IRQPOLL was the final push that got it running, IRQPOLL didn't do anything without pci=nommconf.

I hope this helps someone else here to keep a few more hairs on their head when dealing with this.

---

### Post by mtechpro on 2008-05-04
I had this error "No disk drive detected.." while installing 8.04 server on an old HP pavilion - WD800 80GB harddisk.
As suggested in the install manual, I had the following boot option entered:
hd=16382,16,63
(format, hd=cylinders,heads,sectors)

And it worked like a champ...
:)

---

### Post by Tidoo2001 on 2008-05-24
Anyway you could walk me through these steps you took. 
Thanks
Noob - Extraordinaire

---

### Post by flatline on 2008-08-19
Ok y'all... I am trying to install 8.04 Server on my DIY machine I mentioned in my _[last post]("http://ubuntuforums.org/showthread.php?t=894618")._

Sadly, I FAIL.  No matter what I do, Ubuntu will not detect my 80GB Western Digtal IDE drive.  ](*,)

I have tried both 386 and x64 versions of the install CD.  I tried moving the jumper (tried Cable Select, Master, and no jumper at all).  I tried using the boot option "pci=nommconf irqpoll".  NOTHING WORKS!  This is not a hardware issue, the drive currently has Windows Home Server installed and still boots up just fine.

Help?

---

### Post by flatline on 2008-08-20
Anyone?  I can't see a reason why Hardy can't detect my hard drive.  Help is appreciated!

---

### Post by serpentsilver01 on 2008-10-03
I had the same problem and all the boot code I found here didn't work for me. The way I fixed it was to open up the computer and connect my hard drive and cd drive as primary master and slave (Using ATA don't know what you would do for SATA). It worked after that. My guess is that it did look at the secondary master for any drive at all. Still working on it but it got me passed the "no hard drive..." part. Hope this helps. Side note this is on an old WD300AA 30GB hard drive on an old compaq presario.

---

### Post by wdbphoto on 2009-11-19
Hello, I am a noob and trying to install ubuntu on my PPC. I can't get past the Detect hardrive section. None of the above things are working for me. Any suggestions?

---

### Post by handyhung on 2010-02-03
Hi, I did some google for my problem and I found this page.

I am installing 8.04 Ubuntu to WD800BB which occurred the Disk can not  be detected by the install progress.

I have tried ::

defex's sugestion. 
:: pci=nommconf irqpoll
:: this won;t work for me.


mtechpro's suggestion
:: hd=16382,16,63
(format, hd=cylinders,heads,sectors)
::This is the very close to mine, but I see the spec for WD800BB are slightly different, I used 16383,16,63 for the second try on this solution..  but still won't work.


serpentsilver01's suggestion.
:: Set hdd as Pri/Master and CD as Pri/Slave.
:: It's worked! Without no other Boot option.


The disk have ever installed with Ubuntu the same version, but I not the one who installed that on first time. So I don't knew if it the first-fresh HDD from box would faced this problem or not.

But it's the company PC, The CD-ROM always at Second/Master and that's it.

Thanks everyone for your answers, also I wrote down here as a milestone.


Hope you all smoothly solve this like me.

---

### Post by AndyCT on 2011-12-08
This post is for people who are web surfing for a solution to the above mentioned problem like I was.

I had Ubuntu 11.10 running (very slowly) on my computer. I decided to do a clean install of Lubuntu 11.10. Unfortunately, I aborted mid install and, when I went back to retry, it could not detect my HDD. I tried wiping the disk clean (using DOS debug), but that did not help. Then I read serpentsilver01's and handyhung's posts . . . 

My drive configuration is 1 HDD in the master position on IDE cable 1 and 2 DVD drives (master and slave) on IDE cable 2. I ended up solving my problem by pressing <Del> at startup to enter my computer's BIOS Setup, selecting "IDE Drive Configuration" on the Boot menu and swapping the Primary Slave IDE and Secondary Master IDE drives so it looked like this:

Primary Master IDE = 1st IDE
Primary Slave IDE = 3rd IDE
Secondary Master IDE = 2nd IDE
Secondary Slave IDE = 4th IDE.

I did not physically swap any drives. This solved my problem.

---

