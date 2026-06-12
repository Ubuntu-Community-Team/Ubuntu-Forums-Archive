---
title: "Dual boot problem Windows XP and Ubuntu 6.06"
date: 2006-09-03
forum: Installation &amp; Upgrades
---

### Post by Bunro on 2006-09-03
Dual boot problem Windows XP and Ubuntu 6.06

I installed Ubuntu 5.10 in a dual boot with Win XP. this was working. When starting to upgrade the system to the new 6.06 there started some problems.
Hardware: AMD 64 3000+ desktop.
To keep it short the status is as following Win XP is still running and I can not install Ubuntu.
I deleted all the files of Ubuntu and tried to delete the partitions of Ubuntu to make a fresh start. But still no result.

Hopefully there is someone that can help me out here??

Regards, Robert

---

### Post by mssever on 2006-09-03
What errors are you getting?

---

### Post by Bunro on 2006-09-04
Hi mssever,

I am unable to install Ubuntu 6.06 on this system again.

I think because the GRUB (the boot loader) and/or source.list that is still existing. I edit the source.list during installation but no success.

My question is how can I correct my system so that I can make a clean Ubuntu installation next to Win XP. 

Regards, Robert

---

### Post by mssever on 2006-09-04
Before I can help you, I need to know more details about the problem--specific errors, where problems occur, that kind of thing. What makes you suspect Grub and/or sources.list? Will your computer boot? Are you trying to do an upgrade or a clean install?

There are many possibilities for what could be wrong. That's why I'm asking for specifics.

---

### Post by Bunro on 2006-09-05
Mssever,

I am trying to make a clean installation because the old installation of Ubuntu 5.10 is not working any more. Sorry, I don't now way because it is my fathers computer I am not using it. 

The computer is starting en running Win XP normally.
When I install Ubuntu 6.06 from disk it seams to install correctly it gets its updates. But after restart or after a clean  start I am getting the following:

Startup getting the GNU GRUB version 0.97 “window”
Whit the following selection possibility:
-----------------------------------------------------------------------
Ubuntu, kernel 2.6.15-23-am64-generic
Ubuntu, kernel 2.6.15-23-am64-generic (recovery mode)
Ubuntu, memtest86+
Other operating systems:
Microsoft Windows XP Professional
-----------------------------------------------------------------------
The boot sequence stops after:
Starting kernel log...

After this step I am getting a black screen and the system does not do anything any more.
Only a reset will get me back to reboot.

Regards, Robert

---

### Post by mssever on 2006-09-05
Are you able to boot into recovery mode? If so, you can run dmesg and look for error messages. Also, typing startx should get you a graphical environment.

Otherwise, you can boot from the live CD, mount your hard disk and huntfor/fix errors.

Perhaps the easiest option if you can't get into recovery mode would be a clean install. When you get to the partitioning part of the installer, be sure to select "manually edit the partition table." Then tell the installer to reformat your install partitions. **Don't let it format your XP partition or your /home partition, if a separate /home partition exists!** That should take care of whatever might still be lurking around and causing problems.

---

### Post by Bunro on 2006-09-06
startx is not working -> gifts a black screen. Hangs system only a reset will work.

If you could please give me the complete command line of the dmesg and or the place where I can find some sort of explanation it would be great. Because is is filling multi pull screens and I do not now how to scroll back.

After searching I found the dmesg | tail this is giving the following info back:
[   45.362837] device-mapper: 4.4.0-ioctl (2005-01-12) initialed: [email]dm-devel@redhat.com[/email]
[   45.615626] cdrom: open failed.
[   45.834617] cdrom: open failed.
[   45.835745] cdrom: open failed.
[   45.896798] NET: Registered protocol family 17.
[   46.439785] skge eth0: link is up at 100 Mbps, full duplex, flow control none
[   54.015077] NET: Registered protocol family 10
[   54.015230] lo: Disabled Privacy Extensions
[   54.015412] Ipv6 over Ipv4 tunneling driver
[   64.953972] eth0: no Ipv6 touters present 

When I try to run Ubuntu again from cd the system is also hanging.

Regards, Robert

---

### Post by Bunro on 2006-09-06
I made a BIOS upgrade on the system.
Now I am getting the same error when I am trying to run from the live CD.
The system gets stuck at the Starting kernel log...

In the BIOS I set the following settings:
Cool N'Quiet:		Disabled
ACPI 2.0 Support:	No
ACPI APIC Support:	Disabled

If any body have a solution it would be great!

Regards, Robert

---

### Post by Bunro on 2006-09-06
Sorry I had to change back these settings because win XP will otherwise not work.

Cool N'Quiet:		Disabled
ACPI 2.0 Support:	No
ACPI APIC Support:	Disabled

Regards,  Robert

---

### Post by Bunro on 2006-09-06
I find the following in the dmesg file:
$sudo pico /var/log/dmesg
I read the file and found some items that could row:

[   29.539869] Driver 'sd' needs updating – please use bus_type methods

[   35.296102] Probing IDE interface ide0 ...
[   35.887954] Probing manual resume
[   35.898839] EXT3-fs: INFO: recovery required on readonly filesystem.
[   35.898899] EXT3-fs: write access will be enabled during recovery.
[   35.018182] ieee1394: Host added: ID:BUS[0-00:1023] GUID[00e01800005d42d5]
[   36.080131] EXT3-fs: recovery complete.

[   47.069452] codec_read: codec 0 is not valid [0xfe0000]
[   47.076252] codec_read: codec 0 is not valid [0xfe0000]
[   47.083077] codec_read: codec 0 is not valid [0xfe0000]
[   47.089856] codec_read: codec 0 is not valid [0xfe0000]

[   47.408950] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[   47.409007] ieee1394: sbp2: Try serialize_io=0 for better performance

[   48.146261] cdrom: open failed
[   48.419091] cdrom: open failed

Please advice?

Regards, Robert

---

### Post by Bunro on 2006-09-06
Will searching the Internet it pointed to the Hard disk but I did not find a solution jet!

[   29.539869] Driver 'sd' needs updating – please use bus_type methods

I have the feeling the problem is with my hard disk?
The hard disk is a Maxtor 160 Gb 7200rpm 8MB SATA.
In the BIOS there are the following settings:
Main => 	Primary IDE Master :	[Not Detected] (It is set to auto detect)
		Primary IDE Slave :	[Not Detected] (It is set to auto detect)

		Secondary IDE Master :	[_NEC  DVD_RW ND-250] (DVD-RW)
		Secondary IDE Slave :	[JLMS XJ-HD166S] (DVD-Rom player)

Advanced => 	OnChip SATA BOOTROM:	[Enabled]
		Operating Mode :	[Onboard IDE Operate Mode] (The other option is RAID but because in the system there is only one HD I set this setting).
 
Please advice?

Regards, Robert

---

### Post by mssever on 2006-09-06
First, a tip or two: Whenever a command spits out too much to fit on a screen, you have two options: Alt+Page Up/Down will scroll the screen; or, the easier way is to put |less at the end of the command. For example, ```
dmesg | less
``` will show you all bootup messages and errors.

Also, when you have problems with X, you can usually kill it with Ctrl+Alt+Backspace, rather than having to reboot.

When it comes to the problem you're having, I really don't know what the problem is. Is that disk a SCSI disk or IDE? You say that the live CD won't boot anymore? What about the alternate install CD? If it does, the easiest thing might be to completely reinstall as directed above. You might also want to try a non-Ubuntu live CD--such as Knoppix.

---

### Post by Bunro on 2006-09-07
After many hour of Googling I found the solution on the following site:

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

After installing the ATI driver my Ubuntu started again!

So the problem was that with out the correct ATI video driver Ubuntu is not entering Xorg.

Thanks mssever for giving me the direction!

Best regards Robert

---

### Post by mssever on 2006-09-07
I'm glad you got it fixed. It appears that I was barking up the wrong tree...

---

