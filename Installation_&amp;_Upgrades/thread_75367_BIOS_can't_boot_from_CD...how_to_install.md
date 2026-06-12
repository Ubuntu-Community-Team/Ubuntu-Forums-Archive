---
title: "BIOS can't boot from CD...how to install ?"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by Kako on 2005-10-13
Hi there,

Well, the title says it all...
I have an old Gateway G6-400 and I'd like to install Ubuntu.
And bios can't boot from a CD. It is just not supported :( 

How can install Ubuntu (5.04 or 5.10) ?

I'm thinking of using a floppy to boot a tiny linux. I could then mount the cd and then...

Thanks for you help.
Kako

---

### Post by swerner on 2005-10-13
Are you using a CD-RW?  Some older drives don't support this (even if it works in windows, you may not be able to boot from it).

Have you tried your BIOS settings, are you absolutely sure that you have the boot order correct? Such that the CDROM will boot before your hard drive.

---

### Post by HermanAB on 2005-10-13
Try to upgrade the BIOS.

Failing that, sell the machine on Ebay.  Else, it is going to be a pain in the derrier forever...

Cheers,

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)

---

### Post by preater on 2005-10-13
[QUOTE=Kako]I have an old Gateway G6-400 and I'd like to install Ubuntu.
And bios can't boot from a CD.[/QUOTE]
Network boot?  You probably have a spare network card that supports PXE, even if the card that's already in the machine doesn't.  You'd need another machine to act as a DHCP and TFTP server.

Or, how about some [Breezy netinstall floppies?](http://www.ubuntuforums.org/showthread.php?t=75372)

Andrew

---

### Post by greengrass on 2005-10-13
download  rawrite2.exe  and sbm.bin  off the internet  (do a search)    Once you have these files,  put them both in the same folder.   Get a blank floppy, put it in the floppy drive, and then run rawrite2.exe.   Take the floppy that this program creates, put it in the computer you are installing the OS on,  and turn it on.  Make sure your bios is booting to floppy.  A menu will come up, select  CD-rom,   hit enter,  and walla,  you will boot your CD.

---

### Post by Kako on 2005-10-14
Many thanks Greengrass. Your solution worked like a charm :D

---

### Post by justme11 on 2005-10-14
Hey guys,

Just came across this thread as I want to install Kubuntu 5.10 on my laptop, which is currently running Gentoo. The question is, since my cd burner appears to be dead, how could I go about installing without the need to burn it?

Oh, forgot to mention, I already have downloaded the Iso file and would like not having to go the netinstall route.

Kind regards,
Oliver

---

### Post by swerner on 2005-10-15
There is still the USB or Floppies option.

---

### Post by james4e on 2005-10-15
What is your current OS? 

1.If your current OS is windows, you can use grub for dos to install ubuntu. I have succeeded install ubuntu using ISO file without burning. 

2.If your already install 5.04,you want to upgrade to 5.10. You can also do that without CDROM. 
> sudo mount -t iso9660 -o loop ubuntu_install.iso /cdrom
           sudo apt-cdrom -m -d /cdrom add


Then you can upgrade your OS. I had better comment all horry sources.

>   sudo apt-get update
             sudo apt-get dist-upgarde


---

### Post by jnoreiko on 2005-10-15
[QUOTE=greengrass]download  rawrite2.exe  and sbm.bin  off the internet  [/QUOTE]

Smart Boot Manager is included on the install CD.
/install/sbm.bin

---

### Post by justme11 on 2005-10-15
[QUOTE=james4e]
1.If your current OS is windows, you can use grub for dos to install ubuntu. I have succeeded install ubuntu using ISO file without burning. 
[/QUOTE]
As I already mentioned, I am currently running Gentoo. So the way using grub to install ubuntu sounds very interesting to me. Could you please tell me how to do this?

Thanks,
Oliver

---

### Post by moopere on 2005-10-16
[QUOTE=swerner]There is still the USB or Floppies option.[/QUOTE]

What floppies option?

I've been pulling out my hair ever since Warty because I have a bunch of machines with no CD.  Coming from debian this was no problem as I could always do a netinstall via a 2 floppy boot, but Ubuntu doesn't seem to have the floppy images available.

Cheers,
Craig

---

### Post by dhigger on 2005-10-27
If people want to boot from the CD but can't, and need a boot floppy to spin up the CD and boot from it, AND Smart Boot Manager doesn't work...

see this thread

[http://ubuntuforums.org/showthread.php?t=81280](http://ubuntuforums.org/showthread.php?t=81280)

Dave

---

### Post by Sonic-NKT on 2005-10-31
just found this thread and have the same problem. 
i just have a usb drive but i cant boot of it :-/ 
got it working under dos but nothing more, i dont know how to start the ubuntu setup from dos. this grub4dos disc image emulation is intresting, can someone explain that a bit more to me

EDIT: tried loadlin with the files in the install folder of the cd.. it didnt worked :( 
ok i will download the netinstall floppies next. hope this will work atleast

---

### Post by moopere on 2005-11-02
[QUOTE=Sonic-NKT]just found this thread and have the same problem. 
i just have a usb drive but i cant boot of it :-/ 
got it working under dos but nothing more, i dont know how to start the ubuntu setup from dos. this grub4dos disc image emulation is intresting, can someone explain that a bit more to me

EDIT: tried loadlin with the files in the install folder of the cd.. it didnt worked :( 
ok i will download the netinstall floppies next. hope this will work atleast[/QUOTE]

My email is going to do nothing but give you hope and wet your apetite.

I have been able to install ubuntu by booting from a DOS floppy using either a USB CDROM or a USB memory stick.  Took me an absolute age to work out - most of the instructions out there right now are just plain wrong.

I'm going to write up a wiki page on the subject but am too overloaded right now and won't get to  it for at least 2 weeks.

My intention is to provide links to some proprietry drivers required (but freely available on the net).  You will need MSDOS too, which might be a problem, I've only had limited success with FreeDOS.  

A big tip you can use right now is that you will need to find and use linld (instead of loadlin) as the 2.6.x kernel is too large for loadlin.

For now, stick with it, it _can_ definately work.  If you can wait a couple of weeks I'll map out the exact procedure.

Cheers,
Craig

---

### Post by Sonic-NKT on 2005-11-02
nice to hear that for the next ubuntu install.
tried the netfloppys but they dident worked fore me (but those seem to be my oooold floppy disks ;) ) then i used loadlin and dos to load the netinstall system and that worked well.

---

### Post by ozone on 2006-02-19
I also had a similar problem - an old laptop with no CDROM drive. I did have an USB CDROM drive but the BIOS couldn't boot from it. Smart Boot Manager didn't help either as it doesn't support USB CDROMs.

The laptop had an existing Win98 installation that I wanted to replace with Ubuntu but I didn't want to destroy it completely in case I needed to do something with it during the installation.

So what I did was this:
 - used Win98 defrag.exe (actually the WinME version, since it's much faster - google for it) and then split off a 730MB partition (/dev/hda3) from the Win98 one using FIPS
 - used a tomsrtbt floppy, together with the add-on USB drivers I put on another floppy, to copy the Ubuntu installation CD contents from the USB CDROM to the new hda3 partition (I used dd, so in effect i put a ISO image directly on the raw partition!)
 - tried to boot the new hda3 partition using SBM - I figured that since it's able to boot from an CDROM and from any hard disk partition, it might be able to boot an El Torito ISO image if stored on a partition - alas, it didn't work
 - I created a simple GRUB boot floppy (no grub.conf) and tried to use that to boot the CDROM partition - didn't work either, I couldn't get GRUB to read the files from inside the ISO even though it should support ISO filesystems (maybe I just didn't know GRUB well enough)
 - using the tomsrtbt floppy once more, I split off yet another partition (hda4), about 10MB, created an ext2 fs on it, and copied vmlinuz and initrd.gz from the Ubuntu CD to it
 - finally, using the GRUB floppy I was able to boot the kernel and initrd.gz on the hda4 partition
 - the Ubuntu installer booted. For some reason it didn't recognize my USB CDROM (it just gave weird SCSI errors) so it asked for the CDROM device name. I pointed it to /dev/hda3 and hooray, it was able to mount the partition as if it were a CDROM. The rest of the install went normally. Phew!

Non-CDROM installs seem to be one of the few downsides of Ubuntu. Or maybe I just did it the hard way, but I couldn't figure out any easier solutions. A net install might have been easier, see here:
[http://ubuntuforums.org/showthread.php?t=29555](http://ubuntuforums.org/showthread.php?t=29555)

---

