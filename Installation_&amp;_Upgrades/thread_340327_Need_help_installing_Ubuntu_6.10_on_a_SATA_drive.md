---
title: "Need help installing Ubuntu 6.10 on a SATA drive"
date: 2007-01-17
forum: Installation &amp; Upgrades
---

### Post by ExploreMN on 2007-01-17
I'm having a problem I can't figure out via these forums or google. It appears everyone else's sata drive problems are far more complex than mine as they involve RAID and other such stuff.

Basically, I got it in my brain that I want to build a PVR system. So I bought an inexpensive board, memory, yada yada. 

When I try to install Ubuntu 6.10 it doesn't detect my sata hard drive. Windows Media Center installation can detect it, but I don't want Windows MCE on it (I just used it to test if the drive was good).

The motherboard is a PC Chips A31G with the 2800 XPM processor, an nVidia 7300 PCI Express video card, and a Western Digital 250GB hard drive.

Do I need to do something special to get this thing to detect and install on this drive with this system?

---

### Post by randomnumber on 2007-01-17
Does the motherboard detect the hard drive? Look in the bios.

I had a ASUS mother board that supports sata but did not recognize the sata I got for it. I think it was a ASUS thing. The hard drive was never recognized in the bios. 

sata hard drives are sda sdb ... not hda.

My laptop has sata hard drive and I installed Ubuntu on it with no problems. It did not add any difficulty to the install.

---

### Post by ExploreMN on 2007-01-17
> **randomnumber said:**
> Does the motherboard detect the hard drive? Look in the bios.


[QUOTE=ExploreMN]Windows Media Center installation can detect it, but I don't want Windows MCE on it (I just used it to test if the drive was good).[/QUOTE]

Yes...it does.

---

### Post by ExploreMN on 2007-01-17
So no one has any idea why Ubuntu 6.10 will not install to a SATA drive???

---

### Post by edward4130 on 2007-01-17
If you are doing a clean install boot from the install CD/DVD and erase all data on the drive.. the Edgy disk should let you do this. I installed back and forth from an ide and sata drive over and over.  Just for your sake only have one drive in the machine.

-Edward

---

### Post by dabl on 2007-01-17
My Kubuntu 6.10 system is happily running on a WD SATA drive, on an Intel motherboard.  The only issues I've heard about in the forums are when you try to mix 'n match IDE and SATA drives in the same machine (like I did).  Under that circumstance, the Ubuntu installer will insist on putting Grub on the IDE drive, even if all the rest of Linux goes on the SATA drive. So, there's more than just your SATA drive involved in the problem, I think. :(

---

### Post by CowzRule on 2007-01-17
Maybe you could try and set up a partition before trying to install Ubuntu. If you bought the hard drive new, it should have come with some software on a floppy or cd to do just that. If you didn't get that software, go to [http://support.wdc.com/download/index.asp?swid=1]("http://support.wdc.com/download/index.asp?swid=1") and download their Data Lifeguard Tools 11.2 for Dos.
Also, I'm assuming you have a cdrom drive installed. If it's a standard IDE drive, maybe have it plugged into the secondary IDE channel if you don't already.
And last, if you're trying to install from the Ubuntu Desktop CD (Live CD), try the Ubuntu Alternate CD instead.
Sorry I don't have any experience with installing to a brand new, blank hard drive, but those are the things I'd try.

Just took a look at your mobo at the PCChips website. I seen there that your SATA controller is version 1 (150MB/s data transfer rate). If your hard drive is a newer SATA 2 (300MB/s data transfer rate) you may have to set some jumpers on the drive to set it to SATA 1.


P.S. Are you from Minnesota? I was born and raised in the Cities but currently living in Superior, WI.

---

### Post by dabl on 2007-01-17
This utility disk gets rave reviews:

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Although when I made one and tried it, it never got happy with a screen resolution on my system.

If you have an old bootable DOS or Windows diskette or CD ROM, you might want to try booting that and then giving it an FDISK C:, and then make sure the one partition that you have is set to "active".

---

### Post by Lucardo Mamones on 2007-01-17
does the motherboard support RAID? 

I had a problem that when the BIOS "SATA MODE" was set to RAID the drives were not detected. I had to change that to IDE to have Dapper detect them.

---

### Post by ExploreMN on 2007-01-17
Yeah, I live in Apple Valley in Minnesota! :)

I guess I am still stuck. It must be a chipset problem that Ubuntu just can't handle.

To address other posters:
I only have the one SATA drive in the system hooked up to the first SATA controller.

I have an IDE DVD+/-RW drive plugged into the IDE controller and set as a slave even though this should not matter.

The BIOS sees all drives just dandy.

Running the installer from a Windows XP CD the drive is seen perfectly and XP wants to partition it, but I don't want XP on there, so that is the farthest I've taken it.

The drive is clean/bare.

I am trying to install off the LiveCD and I will try the alternate CD, but I am not sure why that would make a difference since my understanding is that the alternate CD is for systems that don't have the memory/processing ability to load the live interface, but the installation/initially loaded drivers or whatever should be the same.

](*,)  This is just driving me nuts...

---

### Post by Lucardo Mamones on 2007-01-17
even if the bios detects the drive but it´s on RAID mode ubuntu didn´t detect it. 

If your motherboard supports RAID you should check this setting.

---

### Post by CowzRule on 2007-01-17
Where did you get you parts? Locally or mail order?
Since you motherboards SATA controller has a 150MB/s data transfer rate and the IDE controller has a 133MB/s data transfer rate, I'd see if I could exchange or return that SATA drive and get an IDE drive. I've got both in my machine and I've booted OS's from both and didn't see any difference in speed.

---

### Post by ExploreMN on 2007-01-17
Well, I don't think exchanging drives are the issue. Also, for the people that keep questioning RAID...it is not set up as RAID and RAID is disabled.

I'm not an idiot when it comes to hardware and there is nothing on the hardware side that is configured incorrectly. Basically, if I wanted to make this a Microsoft box it would be up and running already. The problem is with Ubuntu and it's inability (at least I think) the SATA controller on this particular motherboard.

What I need to find out is what driver I need to load for it to recognize the Sis controller on this particular board.  If anyone can help with that, it would be greatly appreciated. I can't believe that such a common motherboard and such a common chipset have never run into this issue before...someone out there MUST have experience with this. :confused:

---

### Post by Lucardo Mamones on 2007-01-17
I have looked into other forums in spanish and portuguese and people are having the same issue with this motherboard and SATA drives. 

Unfortunately no one has found an answer. Things to try:

1. Upgrade BIOS: [http://www.pcchips.com.tw/PCCWeb/Products/ProductsDetail.aspx?MenuID=16&LanID=0&DetailID=367&DetailName=BIOS](http://www.pcchips.com.tw/PCCWeb/Products/ProductsDetail.aspx?MenuID=16&LanID=0&DetailID=367&DetailName=BIOS)

My apologies for insisting on RAID, I installed Dapper on a SIS motherboard and until I set the SATA mode to IDE it would not see the freakin´drive. no shape or form. I was however able to see it with windows just like you can.

can you see the drive when you go into the rescue mode? doubtfull but it´s worth a try.

---

### Post by Sponge34 on 2007-01-17
Hi,

Just a hint from the old PC Chips MLR810 days - PC CHIPs make the most rubbish motherboards in history... we had no end of trouble with them; too many different things to go in to here.
One of the issues was with the HDD controllers which either didn't detect all the drives or a particular drive or provided throughput that was only marginally quicker than a floppy disk (seriously). The AGP port only supported certain cards as well.... so much for 'standard'.

I am not convinced that windows would work entirely as expected on the PC Chips board (unless they have improved vastly)

I would try another MoBo which will probably solve your problems (except the one of what to do with the PC Chips crock)

S.

---

### Post by ExploreMN on 2007-01-17
Listen, I really appreciate the replies and efforts to help a complete stranger, but I don't think people fully understand the situation.

It's great to say things like "try another motherboard" or "try this other piece of hardware" as possible solutions. If you are going to pay for it, then great, I'll try it without hesitation! However, the point of software is that it should be made to work with hardware...you don't make hardware to work with software as that is counter-productive. ](*,) 

Yes, I knew PC Chips was cheap going into it and that is why I bought it. $66 for the motherboard with an AMD XPM 2800+ processor.  I don't have tons of money for this "project" and I am not willing to invest in more hardware as it would defeat the purpose to begin with. If I wanted a cutting edge, state of the art powerhouse system I would not have bought something like this to begin with. I would have something like a high end Asus motherboard running a Intel Core Duo Extreme processor with a couple GB of ram, etc etc. :???: 

So, back to the topic at hand... :-D 

It is NOT a hardware problem. The hardware is configured perfectly and works fine. The problem is with the Ubuntu installer or whatever. It can't "see" this particular controller that the drive is plugged into. Does anyone know where I can get a driver that works with this particular board's controller? If not, then fine...but please, no more recommendations on changing the hardware, buying new/different hardware, etc. That is not productive and does not help in any way, shape, or form.

Thank you again for anyone who can help.

---

### Post by richbl on 2007-01-17
> **ExploreMN said:**
> 

So, back to the topic at hand... :-D 

It is NOT a hardware problem. The hardware is configured perfectly and works fine. The problem is with the Ubuntu installer or whatever. It can't "see" this particular controller that the drive is plugged into. Does anyone know where I can get a driver that works with this particular board's controller? If not, then fine...but please, no more recommendations on changing the hardware, buying new/different hardware, etc. That is not productive and does not help in any way, shape, or form.

Thank you again for anyone who can help.

ExploreMN, I'm with you here. Same problem.

I've been a happy Ubuntu user for a couple of years and just today revved my hardware to... a single Seagate SATA HD with IDE CD/DVD drive... and Edgy fails on install.

Furthermore, I can tell you that other Linux distros appear to fail to detect the SATA HD as well. Windows XP SP2 happily sees the SATA drive and can format accordingly.

So, evidently there is something natively lacking wrt SATA detection here. I have no problem with calling it "user error," but it would be a "very good thing" if Ubuntu (of all distros) would provide some direction when it fails to detect a HD (any HD).

I'll continue to troubleshoot this from my end. 

Best of luck.

---

### Post by ExploreMN on 2007-01-18
Well, I found that the controller is a Sis 965L chip and sis.com has a linux download for it. I tried all 3 versions and can't get them to compile or whatever.  Each one comes up with different errors, but the one that looks like the "latest" version gives this response:
ubuntu@ubuntu:~/Desktop/sis18x_2.6.10_1.00.00$ make
cp /usr/src/linux-2.6.17-10-generic/drivers/scsi/scsi.h /usr/src/linux-2.6.17-10-generic/drivers/scsi/scsi_obsolete.h /usr/src/linux-2.6.17-10-generic/drivers/scsi/scsi_typedefs.h .
cp: cannot stat `/usr/src/linux-2.6.17-10-generic/drivers/scsi/scsi.h': No such file or directory
cp: cannot stat `/usr/src/linux-2.6.17-10-generic/drivers/scsi/scsi_obsolete.h': No such file or directory
cp: cannot stat `/usr/src/linux-2.6.17-10-generic/drivers/scsi/scsi_typedefs.h': No such file or directory
make: *** [default] Error 1
ubuntu@ubuntu:~/Desktop/sis18x_2.6.10_1.00.00$ 

I have no idea what to do from here...

---

### Post by richbl on 2007-01-18
> **ExploreMN said:**
> 
I have no idea what to do from here...

Here's a quick update that may help.

After doing a text install (press F6 and delete the quiet or silent command line switch), I noticed that the installation was hanging on the following:

PNP: no ps/2 controller found

which suggested to me that the immediate issue may not be SATA related, but USB / PS/2 controller related.

So, I plugged in a real (non-USB keyboard) and tried again. 

The install got a little further, but failed again.

So, thinking this was a keyboard-related issue, in BIOS I disabled the setting which mentioned something like "allow USB keyboard."

After rebooting, I have... so far... gotten past the hang and made it to the live desktop. As I type this, I am attempting a full install.

At the moment, I'm at 72% of a REAL install on a SATA DRIVE!

Why this is the way that it is? I have no idea, but... it's worth a try...

---

### Post by ExploreMN on 2007-01-18
No, its nothing like that. The LiveCD loads just fine and everything except the hard drive is seen and configured correctly.

I've identified the problem and I am 100% certain it is that Ubuntu does not have the right drivers available to it in order to utilize this controller (the SiS965L) and I just don't know where I can get a working driver and...if I could get it...how to install it.

---

### Post by agracey on 2007-01-18
I am having the same issue with my drive. I found two sata controllers on my motherboard? and am currently trying to install with one disabled and then will try with the other. Also I know it is not a hardware problem because suse installed fine in safe mode. With the amount of people having trouble with this same thing somebody with more expertise than me should be able to show us how to fix it. And for the record I am not running a raid.

---

### Post by CowzRule on 2007-01-18
I don't know if you can, but you may need to compile your own kernel. Just a thought :-k

---

### Post by ExploreMN on 2007-01-18
Unfortunately, compiling my own kernel goes far beyond my abilities...especially since I can't even compile the SiS drivers I need.

So, I've basically given up on Ubuntu even though I have grown comfortable with it. I am trying some of the other big names now. Mandriva failed to detect or install drivers for it...so as I type this I am downloading Suse 10.2 which I read somewhere can handle this hardware. If Suse fails, then I will just go with Windows Fricken Media Center and deal with it until the linux community matures another generation. :mad: 

I hope the Ubuntu development team gets on the ball and starts incorporating more drivers in their next distribution.

---

### Post by ExploreMN on 2007-01-21
Just an update. I've come to the conclusion that there isn't a single distro out there that supports the SiS 965L chipset. I tried Mandriva 2007, Fedora 6, GenToo, Suse 10.2, and a few more.

So if you plan to buy a board with this chipset...be warned that you will need to somehow figure this problem out on your own.

So, as unfortunate as it is, I had to install Windows XP since Microsoft does support this chipset without problems. Luckily there is a nice Windows port/comparible product that works like MythTV (Media Portal in case you are interested) so I still have a working PVR. I just feel bad that I had to give Microsoft another $85 for a license. :mad: (I'm not a pirate, I just play one on TV)

Anyway, thanks to those who attempted to help me resolve this issue. I hope the next version of Ubuntu adds support for this chipset. The current beta doesn't even install on this board (locks up after keyboard selection) so I'm guessing that it won't. It's a shame though...there are a LOT of boards out there using this chipset from what I can see. :frown:

---

### Post by FrankVdb on 2007-01-26
Not sure if I can contribute anything to this thread as a new Ubuntu user migrating from Windows, but could it be that Ubuntu and the other distros don't come with a SATA controller natively? I.e. not included in the kernel? Personally, I'm trying to add an SATA drive to an existing IDE RAID configuration but the SATA drive (naturally) goes undetected...

---

### Post by triode on 2007-01-26
I am having the same issue also... e.g. under ubuntu it loads the kernel and goes to
install, but then hangs. On the alternative disc, it loads the kernel then starts the 
install, but when it gets to the point when it needs to mount the CD, it can no longer
find the CD drive. 

This same problem is going on under Gentoo, Fedora and a few other distros I have
tried. Like the other poster, if I drop a win disc in there it comes up fine, no problems. 

This is a new Gigabyte board (GA-965P-DS3), 2GB OCZ 800mhz ram, 2.66ghz core
2 duo, Nvidia PCI-X16 video, 250GB WD SATA3.0 drive. I have two of them, both
exhibit this behavior under a linux install, both work fine under a winbloz install.

However, I note that when looking carefully at the gentoo output, it really seems to 
be the following: The sata is setup as an IDE drive, as others have mentioned, and
the CDrom drive is also on the IDE chain, but it gets kicked closer to the end of
the chain (logically) under the bios... i.e. looking under the bios I see the CDrom drive
is at logical IDE5 master (probably as I have 4 sata ports). I think gentoo and the others
are setup without that many /dev/hdX devices and miss it... or something like that. 
Looking at output from gentoo and output from Ubuntu and seeing what others are
saying here (and at a ton of other forums) I think the problem is drive naming and
that it can not find the install media...

As someone else pointed out, however, I have a (%$^%^) hard time believing that 
so many people are having this problem (I have been reading forums looking for the
solution for about 4 hours now) and no one has a solution/guide/tip/FAQ/RTFMpointer/etc
on this. I mean, no bashing/flaming, but hardware like this is not bleeding edge. 
These boards have been out for some time, and I see posts on other forums from mid 
2006 on this very subject (in fact, the Gentoo guys say go grab the ubuntu advanced CD
and use that to kickstart the gentoo install! Funny, I couldn't get the ubuntu working in 
the fist place which led me to see the gentoo problem, as I thought they would have
solved it)...

Again, as others have asked... anyone have any ideas other than solutions for people
with RAID or bad hardware? (I am not doing raid, I only have one hard disk)...

---

### Post by tnseditor on 2007-01-26
I was having problems installing Ubuntu 6.10 on my new system (SATA hard drive, Core 2 Duo, Intel board).   I could not get anything to work until I downloaded and tried to install Feisty Herd 2 ([http://www.ubuntu.com/testing)](http://www.ubuntu.com/testing)).  The install went flawlessly and easily.  You may want to try it.

---

### Post by triode on 2007-01-26
Well, I think I have found the problem... according to this:

[http://www.sabayonlinux.org/forum/viewtopic.php?t=3264](http://www.sabayonlinux.org/forum/viewtopic.php?t=3264)

If the ata_piix driver is loaded before the ide module, it crams it. 

I rebooted my ubunto-advanced CD, got to where it could not find the
drive, then went to the second VT and did a dmesg... there it is!! Linux
sees both of them, but the CD is being loaded after the ata_piix and it
is getting wasted. Note, these guys have spotted the same thing:

[http://www.thinkwiki.org/wiki/Problems_with_SATA_and_Linux#DVD_drive_not_recognized](http://www.thinkwiki.org/wiki/Problems_with_SATA_and_Linux#DVD_drive_not_recognized)

I think (again, from what I see here and on my terminal) that this
is the problem. The real problem I face is that I do not have another
ubuntu machine to compile a new kernel on (my other box is a mini-itx
gentoo system)... and then you would need to rework the init so that 
ata_piix gets done after ide. 

Bueller? Anyone? Bueller?

---

### Post by S.V. on 2007-01-27
Hi ExploreMN,
You have almost similar pc configuration and almost similar problem like mine!

Mine is an AMD Sempron(s754) 2800+ASUS mobo+256MB DDR400 system. 120GB Seagate SerialATA disk on fisrt SATA controller and a DVD writer on first IDE controller.

When I tried to install Ubuntu 5.10 and 6.06LTS they didnot even recognize my Seagate SerialATA disk. Then I got 6.10, which recognises the SATA disk goes till the disk partitioner stage when I select the manual partitioning option, it starts 'gparted' and then just hangs?!

Is it memory related problem? its just 256MB.

I have installed Dreamlinux 2.2 and Vectorlinux 5.8 on the same disk without any problem. Had also installed FC6 and openSUSE though they complained about lack of memory to run their graphical installer. They asked me to immediately activate the swap and after that there was no problem. Whats with Ubuntu?

Will be following your thread...

---

### Post by RickBos on 2008-04-21
Hi.

Was this issue resolved ?

I am having problems installing Ubuntu Linux on a PCChips A13G+ motherboard and a SATA drive.

---

