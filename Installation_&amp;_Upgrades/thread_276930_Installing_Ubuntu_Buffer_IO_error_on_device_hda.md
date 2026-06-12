---
title: "Installing Ubuntu: Buffer I/O error on device hda"
date: 2006-10-13
forum: Installation &amp; Upgrades
---

### Post by efikkan on 2006-10-13
Hi!

I'm trying to install Ubuntu on one computer in my home. (I've already installed it on three other computers :) ) But it wouldn't even boot on this computer. I've tried Ubuntu 6.06 and 6.10 beta both 32bit(only 6.06) and 64bit(both). I still get the error message after booting the kernel:
> hda: ide_intr: huh? expected NULL handler on exit
hda: ide_intr: huh? expected NULL handler on exit
Buffer I/O error on device hda, logical block 344502
This message loops. I let it run for about 10 minutes. It seems like it's always the same block.

Hardware:
AMD X2 4200+
2GB RAM
WD 320GB SATA

Though the BIOS displays the HDD as "IDE 100" at bootup. :-k 

Could anyone please help me?

Greetings,
efikkan.

---

### Post by efikkan on 2006-10-14
During bootup the BIOS displays: "IDE Channel 2: Master Disk: LBA, ATA 100, 320GB". So expects null handler on exit on "hda", which does not exist, because it's really "sda".

How can I fix this?

---

### Post by T.Louis on 2006-10-22
Stuck on the same problem. :-k

---

### Post by nadamsieee on 2006-10-23
I believe this message is being printed from the [FONT="Arial Black"]end_buffer_async_read()[/FONT] function in [FONT="Arial Black"]linux/fs/buffer.c[/FONT]. I don't know why the error is occuring though. :(

You might want to double/triple-check that your hard drives connectors are plugged in securely (this includes CD/DVD-ROM drives).

---

### Post by nadamsieee on 2006-10-23
You may need to turn off RAID arrays; here are the instructions:

[http://www.ubuntu.com/download/releasenotes/606#head-f0fc50174e566788f02aa164fb6e80aa9c65ee24](http://www.ubuntu.com/download/releasenotes/606#head-f0fc50174e566788f02aa164fb6e80aa9c65ee24)

---

### Post by nadamsieee on 2006-10-23
Another person solved this by adding '**irqpoll**' to his boot parameters.

---

### Post by jamaas on 2006-10-25
Thanks for this, could you please tell me exactly how to do this?

Thanks

Jim

---

### Post by oilyrag on 2006-10-26
I have the same error and it's the 2nd time it has occured.  Last time i reformatted the drive and started again, but i'd rather not have to go through all that again.  Can someone please provide some noob level help?

---

### Post by michux on 2006-10-26
> **jamaas said:**
> Thanks for this, could you please tell me exactly how to do this?

Just type:

```
linux irqpoll
```

in your lilo/grub command line before running the installer.

---

### Post by efikkan on 2006-11-07
Just to let you know, the final version of Ubuntu 6.10 works fine.:-D

---

### Post by rpradeep on 2006-11-28
I am using a HP visualize X Class 1GHz workstation and Samsung SH-D162C DVDROM.

Firstly My computer halt at mounting root filesystem and refused to go further. Then I changed the Firmware of DVDROM from TS04 to TS01 then it worked after several Buffer I/O error (ie only delayed the booting)

This also make delays in openning the DVD drive when new CD is inserted on Ubuntu desktop (after installation).

Recently I changed back my Firmware and changed the BIOS settings as follows.

In that i changed the IDE for my cdrom setting from AUTO to CDROM
and disabled UDMA.

Now it's working fine for me.

---

### Post by altonbr on 2006-12-12
> **michux said:**
> Just type:

```
linux irqpoll
```

in your lilo/grub command line before running the installer.

And how do you do this on a LiveCD? F6 gives you the boot options/flags but how do I add irqpoll?

I'm getting the same error as everyone else:
> Buffer I/O Error on device hdc, logical block ...

I think it has to do with "hdc" since the computer only has one hard drive, so should it not be "hda"? How do I change the installer to look for "hda"?

---

### Post by altonbr on 2006-12-12
For the LiveCD, I hit F6 to change the boot options and changed the flags from:
> /casper/vmlinuz boot=casper initrd=/casper/initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash
to:
> /casper/vmlinuz boot=casper initrd=/casper/initrd.gz ramdisk_size=1048576 root=/dev/ram rw splash irqpoll

And it seemed to be able to make it to the GUI. Thanks for the help nadamsieee & michux. In hindsight, I should have used the alternative CD.:-k

---

### Post by okipatrick on 2006-12-22
> **efikkan said:**
> Hi!

I'm trying to install Ubuntu on one computer in my home. (I've already installed it on three other computers :) ) But it wouldn't even boot on this computer. I've tried Ubuntu 6.06 and 6.10 beta both 32bit(only 6.06) and 64bit(both). I still get the error message after booting the kernel:

This message loops. I let it run for about 10 minutes. It seems like it's always the same block.

Hardware:
AMD X2 4200+
2GB RAM
WD 320GB SATA

Though the BIOS displays the HDD as "IDE 100" at bootup. :-k 

Could anyone please help me?

Greetings,
efikkan.



Saw your note that 6.10 final works fine.  I had the same problem but with my secondary IDE master (hdc) being a SATA drive.  The 6.06 live CD would initially recognize the drive improperly, and then it would try to mount hdc (should be SCSI sda) then go into that buffer i/o fit.

I also had to boot into Windows, down/burn the 6.10 final version and rerun with irqpoll on (I was also using acpi=ht just to be safe), and it installed like a champ.

---

### Post by okipatrick on 2006-12-22
> **altonbr said:**
> And how do you do this on a LiveCD? F6 gives you the boot options/flags but how do I add irqpoll?

If you use F6 you should be able to edit the boot flags.  Just type it in along with the other arguments it shows

I'm getting the same error as everyone else:

> **altonbr said:**
> 
I think it has to do with "hdc" since the computer only has one hard drive, so should it not be "hda"? How do I change the installer to look for "hda"?

I had this issue with 6.06 and ended up migrating to 6.1, which didn't complain when I booted with the irqpoll option.  Once you got 6.06 installed, are you finding that you still have to boot from GRUB with irqpoll?

---

### Post by senser1080 on 2007-01-24
yeah, but when I add irqpoll to the command line it starts, loads the first part and then just randomly restarts my system :cry:

---

### Post by stevareno on 2007-03-06
I had this problem also with a dell Latitude 7500 and an optiplex GX1p.  I followed the advice of one of the posters who stated it was the cd-rom drive.  I changed the cd-rom to a newer one on the GX1p and it works fine.  I have a feeling the same issue exists with the 7500 because when I attempted to install it, the cd-rom was acting up during the install.

---

### Post by nickbuntu on 2007-04-08
I had this problem on a Toshiba Tecra S1 laptop, trying to install ubuntu-7.04-beta-desktop-i386.iso. I followed the suggestion of changing the disc burn speed to x4 (from x40) and it's currently booting up into the live desktop fine! Presumeably any drive that's not particularly great will have this problem; mine's a bit old and I do occassionally get other discs not reading properly or taking longer than usual to read.

Anyway thanks for the tips on here.

---

### Post by mulle on 2007-04-25
I am meeting this problem with Enterprise Volume Management System with xubuntu...  i know this is ubuntu but it is almost the same topic.

I tried the splash thing, but it even made more error. :D
But after about 10 mins of reapeating the buffer, it loads xbuntu. I know wonder if i try to format XP and install xubuntu will it keep coming with the errors?

---

### Post by rothman130 on 2007-05-23
Had this same problem. I got the same error messages glad someone was able to get theres working, i gave up and purchesed Visita sorry UBUNTU ill still try you as a dual OS!!

---

### Post by shearn89 on 2007-06-03
> **rothman130 said:**
> ... i gave up and purchesed Vista... 

Gasp! Traitor! (jokes)
I get the same problem with a similar message... trying irqpoll now, as before I tried "noapic nolapic noacpi irqpoll", and that kept hanging... perhaps too many boot options?

---

### Post by barmaley on 2007-10-03
Hi, ubuntu people
I have the same problem "Buffer I/O Error on device sda, logical block 0"
I have pluged a brand new WD250GB SATA II hd and ubuntu does not see it when logs in.
Actually, the hard disk is seen in the hardware, but I cannot mount it by no means.
Could someone help with this, please.
What if I format the disk on another comp, will it help?

---

### Post by bronius on 2007-10-24
On a P-III Dell Latitude LS, I experienced the same error but (or in addition to?) "sta" instead of "hda" (*Installing Ubuntu: Buffer I/O error on device sta*).  I began posting here to receive clarification: are you all experiencing this error on unsuccessful boot from LiveCD or unsuccessful boot from hd immediately following apparently successful installation from LiveCD?  In my case, it was the latter.

Having begun registering here to post this reply, I gave my system a reboot and got a new, BIOS error: something about can't read the hd in the first place!  On 2nd, cold shutdown and restart, my ubuntu gui came up right as originally expected. First subsequent proper, soft reboot (gui menu to restart) appears to have failed again (after initial ubuntu logo with loading bar).  Subsequent hardware shutdown and power up worked.

In my case, I suspect either some realtime change in config recovery between alternate .iso install (had to do text install b/c of the limits of the relic machine) between boots or, more likely, a failed or failing hd.  I didn't think an old laptop could *sound* like a clunker!  ;)

hth

[update: ubuntu consistently cold boots and consistently fails to soft boot via Shutdown>>Restart]

---

### Post by Halfling Rogue on 2007-10-24
> **barmaley said:**
> Hi, ubuntu people
I have the same problem "Buffer I/O Error on device sda, logical block 0"
I have pluged a brand new WD250GB SATA II hd and ubuntu does not see it when logs in.
Actually, the hard disk is seen in the hardware, but I cannot mount it by no means.
Could someone help with this, please.
What if I format the disk on another comp, will it help?

Exact same problem. If my external hard drive is plugged in while Ubuntu is booting, I'll get the error "buffer I/O error on device dm-2, logical block 0" a couple of times. It also shows up sometimes with pvdisplay, and I can't chmod or rename the HD.

---

### Post by jrtorrent on 2007-10-27
I've tried 7.04 server alone, with windows, Deleted all partitions and reformatted the whole drive with DR DOS. Cant shake this error!
Buffer I/O error on device hda, logical block 0

Second error line ldm_validate_partition_table (): disk read failed

I downloaded and burned the image at all times of the day or night, speed of 1x to 16x tried to implement every one of the solutions in this forum and other forums and "experts" guidance has not helped either. 

I have a AMD dual core on a ASUS A8N5X motherboard, 60G PATA harddisk, two of the latest SONY DVD DL burner and 4G of ram

HELP ANYONE?

---

### Post by jrtorrent on 2007-10-29
> **michux said:**
> Just type:

```
linux irqpoll
```

in your lilo/grub command line before running the installer.

_So, forgive me ... I have the hard disk formatted I run the installation AMD 64 DVD and doesn't work. How am I supposed to use lilo or grub if they are not available. After I get this errors_

[68.628889]Buffer I/O Error on device hda, logical block 0
[66.002245]ldm_validate_partition_table(): disk read failure



Kernel Alive
Kernel direct mapping tables up to 140000000 @ 8000-e000

[U]
"then it sits for a while completely irresponsive finally dropping to" [/U]

Check root = bootarg cat /proc/cmdline
or missing modules, devices: Is /dev
!ALERT /dev/mapper/ubuntuserver-root does not exist. Dropping to a shell!

BusyBox v1.1.3 (Debian v1:1.1.3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of commands.

/bin/sh/ can't access tty; job control turned off.
(initramfs)
(initramfs)

"what I find odd is that the exit command does not get me out of "initramfs" furthermore the command "ls" reveals there is no boot directory on root.


I have tried the install Ubuntu server with a maxtor 60G, a Seagate barracuda and a samsung 80G with the same lack of success. 

I have to confess that this experience feels no different that the screwups with  Microsfot's Vista. What's the difference? I didn't pay for Ubuntu the time invested tracking this issue is significant larger than I would spend with Microsoft. Time is valuable and I see lots of people with similar issues so (maybe) the free software is costlier than Microsoft Vista. With so many people (just Google the error and they are coming out of the woodwork) with this issue how can Ubuntu inner crowd make the quality and ease to install and use claims they make?

Fluster, frustrated and getting really mad ... Yeah! who wouldn't after 17 installs and applying (trying to) over 37 "solutions" without any success! 

If you have a solution ... HELP!

---

### Post by bastubis on 2007-11-14
I'm getting grub error 5 when trying to boot from a fresh install of gutsy to a Seagate Barracuda 320 gig HD. I booted into system rescue, fdisk lists the partition table but I can't mount it, error message says 'special device' doesn't exist.  

BIOS correctly identified both disks before I started but BIOS could no longer see the slave (a Maxtor MaxDiamond 250 gig SATA which was working fine before) AFTER Ubuntu had failed to boot from the HD. 

Anyone got any idea why?

---

### Post by scotlandak on 2008-02-01
I had the same problem and I fixed it by switching my my hard drive to slot 2 on the motherboard and putting my cd drive on slot 1. Now the errors still come up but it load into the live cd.  However now I can not get the installer to recognize my hard drive. 

When I installed I removed one of ram chips, I tried with the HD set to cableselect, master, and slave, I have 2 of the same hard drives and I tried the other one and no luck.  I also choose safe mode without graphics and changed the splash to nosplash.




Jetway 830cf
amd duron 1.3
wd400 40gb

---

### Post by tomiscool on 2008-03-02
ok peeple i have tried billions of times and got this prob and then had an idea so the things that are not connected to the computer should be disabled in the bios like floppy if u do not have it connected ok now if u have front panel usb 2.0 and u dont have it connected to the computer disable that as well now if there is anything else u have in the bios that is not connected make sure to disable it unless u dont know what ur doing if u dont understand what im saying just reply ok hope this helps:):):):popcorn::KS

---

### Post by tomiscool on 2008-03-02
also forgot to say my story of what happend maybe this would be interesting to read well anyway i was annoyed at the fact it aint booting from the cd it will show the first part of the screen where u see the bar going back and forth then after that a blank screen show up saying that error message "b/o buffer hda" whatever stuff ok so i heard people talking about floppy drives and how they did not have it connected so i disabled mine cuz i dont have it connected ok then tried to boot it but still oh god it didnt work but the error message was different so then i said well i did something to change it and thought there has to be something else after giving up for two days i decided to try it again. Then i got the stupid message so i went to bios and went to usb then saw it saying usb 2.0 front panel and said hey i dont have that connected either so i diabled that then saved the settings and rebooted the computer once i rebooted i tried the run from cd again and luckily it showed smoothly and fast i couldn't believe it and wanted to install it so bad so i just took a hard drive from a crappy slow 128 mb of ram computer and put it in the computer instead beside the other computer sucks of course lol and installed ubuntu on that hard drive and all went well i was so happy it worked it was beautifull lol im sure this hass to be the prob for u guys hope this helps:popcorn:

---

