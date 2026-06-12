---
title: "Problems installing Server AMD64 from bootable USB"
date: 2011-03-02
forum: Installation &amp; Upgrades
---

### Post by BJC_001 on 2011-03-02
Hi,

I seem to have a bit of a problem, but I expect somebody's been there before me. Unfortunately, my searches aren't finding anything useful.

I'm trying to install ubuntu 10.04 LTS Server AMD64 onto an HP Proliant N64 (Microserver). The server doesn't have an optical drive so I'm trying to create a bootable USB memory stick for the install.

I downloaded the ISO image (ubuntu-10.04.2-server-amd64.iso) and also Pendrive (Universal-USB-Installer-1.8.3.4.exe) and copied them to the same folder. I then ran PenDrive (on a Windows XP laptop) and selected "Ubuntu Server 10.04.X Installer". It automatically found the iso image and I created the USB image, with no errors reported.

However, when I boot from the USB stick on the server, the main install option doesn't do anything. If I use TAB to view the settings, I note that the menu command references an installer with i386 in the path, when I'd expected amd64. AFAICT the command is simply referencing locations that don't exist on the USB image.

*N.B. I did consider editing the option but it wasn't clear which *keys could be used to edit the command. Also, looking through the files on the Windows laptop it wasn't obvious which file stored the menu options. Unfortunately, I wouldn't know the correct option anyway, except to change the i386 path to the relevant amd64 path.

The Advanced Rescue option does get a bit further but it prompts for CD-ROM drivers which seem inappropriate (for a USB device) and so it stops before mounting the (non-existent) CD.

Any suggestions?

Thanks.

---

### Post by Old_Grey_Wolf on 2011-03-02
I don't use Pendrive. I use UNetbootin for making a bootable USB's. You could give that a try. Here is a link to UNetbootin [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by BJC_001 on 2011-03-03
Thanks for the UNetbootin suggestion. I can now get a reasonable installation menu which actually seems to do something. Unfortunately, I have stumbled upon some new woes which were hinted at in my earlier message. Specifically, the installation is still trying to detect and mount a CD-ROM.

I've tried to help myself, as listed below, but I'm still stuck.

I found some useful instructions at [http://www.revouser.com/forum/viewtopic.php?f=7&t=794](http://www.revouser.com/forum/viewtopic.php?f=7&t=794) but I can't get them to work on my system. However, I suspect this might be quite straightforward, if only I had more GNU/Linux experience.

The basic theory is to also copy the iso image to the USB drive and then use a second terminal window to mount the iso in place of the CD-ROM. Sounds reasonable, but I can't find the USB device in the file system.

*ls /dev/sd**

Reports:
[INDENT]*/dev/sda  /dev/sdb  /dev/sdc  /dev/sdd*
[/INDENT]
[I]mkdir /iso
mount -t vfat /dev/sdb1 /iso
[/I]Reports:
[INDENT]*mount: mounting /dev/sdb1 on /iso failed: No such file of directory*
[/INDENT]
I've tried the following commands to no avail:
[INDENT]*ls /dev/sda1*
*ls /dev/sdb1*
*ls /dev/sdc1*
*ls /dev/sdd1*
[/INDENT]
I then tried to, more generally, find the iso image with the following commands but they reported nothing:
[INDENT]*find -name *.iso*
*find -name ubuntu**
[/INDENT]
I then had a trawl through the file */var/log/syslog* (using the command *more /var/log/syslog*) and this seems to include references to sdb that suggest a storage device (e.g. *[sdb] 1953525168 512-byte logical blocks*) but no apparent assignment of something I can view in the file system.

I then tried the command *mount -t vfat /dev/sdb /media/usbdevice*. That failed with No such file or directory. I then created */media/usbdrive* and tried again. This failed with *Invalid argument*.

How can I find my USB drive? Alternatively, how can I overcome my installation problem?

Thanks.

---

### Post by BJC_001 on 2011-03-03
Ok, with a bit of thought I've figured out a workaround for the moment, borrowing heavily from the link I posted in the earlier message. I report here in the hope that it might help someone else.

My steps were as follows.

Copy iso image to a second USB drive.
Insert USB drive to server.
Run command *tail -f /var/log/syslog* and note that drive has been allocated *sde1*.
Create a mount directory with the command *mkdir /media/usbdrive*
Mount USB drive with command *mount -t vfat /dev/sde1 /media/usbdrive*
Link the iso image to the CD-ROM device with command *ln -sf /media/usbdrive/ubuntu-10.04.2-server-amd64.iso /dev/sr0*
Switch back to installer terminal (Alt-F1)
Select option to manually mount CD-ROM.
Set CD-ROM device to */dev/sr0*

Success - installer now continues.

Thanks.

---

### Post by Old_Grey_Wolf on 2011-03-03
Let us know if it worked. I have never tried installing the 64-bit server version from USB. It looks like our on-line schedules are offset by a few hours.

---

### Post by BJC_001 on 2011-03-05
Hi,

Yep that worked just fine. It's the first time I've installed Server but I've installed quite a few version of Desktop - always from USB. Given how easy Desktop was to install, I was rather surprised that Server seems so tied to CD-ROM. I'd have thought optical drives were getting just as uncommon in servers, so this is certainly an area that would benefit from some focus.

Anyway, hopefully my notes will help anyone else with the same problem.

Regards.

---

