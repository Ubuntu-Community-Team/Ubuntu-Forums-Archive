---
title: "Istalling kubuntu 7.04 on Intel Desktop Board DG33TL"
date: 2007-07-20
forum: Installation &amp; Upgrades
---

### Post by dumas33 on 2007-07-20
I changed my pc platform to Intel Desktop Board DG33TL with core duo. 

Infortunately I can not isntall kubuntu 7.04 even live CD does not start. It returns tty error. 

It seems that there is some problems with ide/sata controllers. 
WinXp installation returns blue screen whitout adding third party drivers from floppy. 

But intel does not provide drivers for linux. 
I want to install ubuntu in ata drive (sata just for media storage)
this is link to motherboard description.
[http://www.intel.com/products/motherboard/DG33TL/index.htm]("http://www.intel.com/products/motherboard/DG33TL/index.htm")

Please help me.

---

### Post by dumas33 on 2007-07-24
I found that it this mainboard is chipped with   Intel G33 Express Chipset

Any Ideas how to make disks work?

---

### Post by wpshooter on 2007-07-24
Do you have anything else already on the drive that you are wanting to install Ubuntu on that you want/need to save ?

If not, why don't you get Killdisk from [www.killdisk.com](www.killdisk.com) and WIPE the drive completely clean and then give the installation another try.

Good luck.

---

### Post by Pumalite on 2007-07-24
Check your hardware for loose connections, etc. If you did it yourself, start reviewing your steps. Graphics? Memory?

---

### Post by dumas33 on 2007-07-24
I think it is problem with i/o controller support.

I can istall winxp with adding driver floppy during setup. Without it it returns blue screen, 'no boot device' 
Phisicaly everything is ok, connected properly etc.

So think it is problem with hardware support. 
is there any chance that in guttsy gibbon it will be solved?

---

### Post by Pumalite on 2007-07-24
Try Alternate CD. It's worth a try.

---

### Post by dumas33 on 2007-07-30
> **Pumalite said:**
> Try Alternate CD. It's worth a try.

Thanks for suggestion. I tried, unfortunately it did not work. 
After selecting task in CD start-up screen, some CD activity starts but after few seconds I have black screen with binking cursor.

Maybe this mainboard is not supported by linux kernel? How to check that?

after 2 years being in Ubuntu I'm almost month living on windows. It s*cks you can believe.

 I desperately want to go back to linux. Help me.

---

### Post by Pumalite on 2007-07-30
Try this: Hit 'Esc' or F6 on boot; add to the boot option: 'live vga=771 acpi=off'

---

### Post by dumas33 on 2007-08-01
> **Pumalite said:**
> Try this: Hit 'Esc' or F6 on boot; add to the boot option: 'live vga=771 acpi=off'
i think it's not vga problem it is problem with disk controller none CD or hdd are detected correctly.
Our option did'nt help. Any more suggestions.

---

### Post by dunno on 2007-08-09
Was there ever any resolution on this?
I'm curious because I'm running into a similar problem using a intel DG965OT and am considering switching to the board mentioned here (DG33TL).

The DG33LT doesn't support Linux, but I'm not sure what 'support' means.
[http://support.intel.com/support/motherboards/desktop/sb/CS-008326.htm]("http://support.intel.com/support/motherboards/desktop/sb/CS-008326.htm")

There might be some help here:
[http://www.intel.com/cd/channel/reseller/asmo-na/eng/products/linux/feature/index.htm]("http://www.intel.com/cd/channel/reseller/asmo-na/eng/products/linux/feature/index.htm")Intel® 

There's something called a "Intel Quick Start Kit for Linux" which contains the sata drivers for boards not directly supporting Linux.

ciao, suerte

---

### Post by dabl on 2007-08-09
I wouldn't take that Intel chart too seriously.  My D975XBX has been happily running Linux for the better part of a year.

I'm guessing there's a BIOS setup issue, or maybe a BIOS version issue going on here.

Also, you'll have a miserable time trying to install Grub to a SATA drive if you already have an IDE drive with an OS on it.  I wasted days figuring that one out.  Among other issues, my BIOS wouldn't let me put a SATA drive ahead of the IDE drive in the boot sequence.  But I fooled it -- I fdisked the IDE drive, installed Win Xp to the first SATA drive, then installed Linux and Grub on that SATA drive, THEN partitioned and installed a different Linux on the IDE drive (leaving Grub on the SATA Linux in control).

  :popcorn:

---

### Post by dumas33 on 2007-08-13
Yes that's rigth my pc 97XX family chipset worked perfectly to. But this is G33 Express Chipset it is new one and I did not found anything about working linux on it.
Even winxp did not install without adding third part ide drivers, i think tihs is the question. Is G33 chipset suported by Linux kernel or not. And how to install linux on such platform.

If it is something in bios please let my know. I will be happy to solve this problems as fast as i can..

---

### Post by grmmog on 2007-08-21
I've got the DG33TL as well and had no issues installing Ubuntu 7.04.  The only problem I've had with the G33 chipset is with the NIC.

Take a look at your BIOS settings for your hard drives.  There are settings for AHCI, IDE & RAID that can mess things up.  What processor are you running?  Have you updated your bios to the latest version?

---

### Post by ysirotkin on 2007-08-21
> **grmmog said:**
> I've got the DG33TL as well and had no issues installing Ubuntu 7.04.  The only problem I've had with the G33 chipset is with the NIC.

I am also having the same problem. Could you pleas say, what configuration you have? I am using Hitachi SATA-II drive. And what are you bios settings?

---

### Post by Pumalite on 2007-08-21
As dabl mentioned it could be the mix of IDE and SATA. Some people in some boards has has success going to BIOS>IDE Configuration>Enhanced Support for PATA+SATA (or equivalent)

---

### Post by dunno on 2007-08-21
On my DG965OT I've been able to install Xubuntu 7.04 (6.10 won't work)  but first had change the bios setting: Configure SATA as: IDE (or something like that:))

So now the issue has become even more perplexing.  Xubuntu installs, but will not boot!  XP installs and boots, so I know it's not a hardware failure or connectivity issue.  I've also tried Ubuntu 7.04 Server and Ubuntu 7.04, both install but neither boots.  I've also tried installing XP to a small partition, then Xubuntu, which would detect the XP and force GRUB to run at boot: didn't work.

Check out the 'Success Stories' [here]("https://wiki.ubuntu.com/Core_2_Duo_Support").  In particular, #3.

---

### Post by grmmog on 2007-08-23
Have you tried running install with only the ide hd installed?  If you can go through install and it just doesn't boot then maybe grub-installer is having problems with pata+sata.

My system is sata only.  I have the BIOS set for AHCI.  If I'm doing a BIOS flash it'll only work if I turn off AHCI and run in IDE mode.  Do you have the latest BIOS installed?  I needed to flash mine out of the box since it didn't support the Core 2 6x50 series.

A couple of other issues with DG33TL and I'm assuming the G33 chipset.  I couldn't get the NIC to work and had to compile the module provided by Intel.  X doesn't recognize the chipset.  I've tried a couple different drivers and no dice.  Right now it's running off of the vesa driver which works fine.

---

### Post by gotlinuxed on 2007-08-27
I installed Vista, got my dual monitors running on the two video outputs at 1680x1050, partitioned it using the onboard raid5, and the nic worked perfectly.

Reformatted, installed Ubuntu x64. Wouldn't recognize raid, 32 bit ubuntu won't even innstall. On install the video doesn't work, VESA only, second video port is unrecognized, and the NIC won't work. No idea where to get my hands on a driver, and the box has no network connectivity.

As much as I hate microsoft, wow, it's cool when stuff works.

Q6600/dg33tl

---

### Post by grmmog on 2007-08-28
The onboard raid provided by the DG33TL is software based which is why Ubuntu doesn't recognize it.

You can download the kernel module for the NIC from Intel's website.

---

### Post by gotlinuxed on 2007-08-29
FYI to DG33TL owners finding this thread via google, the magic word for the NIC is "e1000-7.6.5.tar.gz" and the magic word for the Intel Storage Matrix stuff is "fakeraid". No love yet on the video.

---

### Post by AlterEgo on 2007-08-31
I am running Gutsy Tribe 4 on my DG33tl. It already contains a working e1000 network module. 
I had lots of difficulties installing Ubuntu in a configuration with Pata and Sata drives, In a pure sata configuration, it was problem-free. 
The video is working out of the box; even compiz-fusion is performing nicely. I'll post my xorg.conf on request.
Everything is working nicely, except my sensors: coretemp spits out wrong values, and no other sensors are being detected by sensors-detect. 

Has any of you DG33TL users had any success reading the voltage and temperature senors? If yes: how?

---

### Post by gotlinuxed on 2007-09-01
Hey, glad to hear about the video support and compiz fusion! I thought since you were talking about hard drives I'd add my 50c. I'm still playing with operating systems on my DG33TL, haven't made a decision yet. I'm typing this from a FC7 install with Xen extensions, and I have a window up with Vista inside a Xen vm. It's pretty amazing stuff.

I've been able to run my three SATA drives in raid1/5 with dmraid on Ubuntu & FC7 with the BIOS set to AHCPI. 

ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
scsi 1:0:0:0: Direct-Access     ATA      WDC WD4000KD-00N 01.0 PQ: 0 ANSI: 5

EIST support in FC7 also works like a champ, I'd assume in Ubuntu too but I forgot to look for the controls. All four Q6600 cores idle at 1.6Ghz, step up on demand, and respond to manual speed upgrades. Makes for a pretty wicked taskbar.

I'm using an old Nvidia 6600 right now, I'm very interested in how to get onboard video running, though I'm not sure I'm for using the dev releases, as I'm new to Ubuntu and am not really sure how to go about installing or updating it. That said I'm wiping & going back to my Ubuntu install this week after I've gone through raid failure and recovery (manually pulling a drive and wiping it so I can learn how recovery works BEFORE a disaster...)... so I'd love to see your xorg.conf. Maybe I will feel adventurous.

This thread appears to be the DG33TL survival guide at this point, might as well keep all the info here. Good luck.

PS I can't begin to describe how CLUNKY fc7 feels after ubuntu. it still feels like linux always did.. but ubuntu feels like osx now. everything just works.
PPS I will take a crack at lm_sensors and post my results..

---

### Post by gotlinuxed on 2007-09-01
even with lm sensors from source, couldn't get anything but cpu coretemp from ISA. i'll post any further progress here.

---

### Post by AlterEgo on 2007-09-02
> **gotlinuxed said:**
> 
 That said I'm wiping & going back to my Ubuntu install this week after I've gone through raid failure and recovery (manually pulling a drive and wiping it so I can learn how recovery works BEFORE a disaster...)... 

That's a pretty clever aproach to learning by doing!

> 
so I'd love to see your xorg.conf. Maybe I will feel adventurous.
 

There's not that much adventure involved. I haven't tried, but I expect Feisty to automagically boot into a working GUI. Gutsy worked out of the box. Xorg.conf is attached.

> .
PPS I will take a crack at lm_sensors and post my results..

I appreciate the effort!

---

### Post by dumas33 on 2007-09-23
Thanks for so many posts. 
I was on vacation, so after some time will try to install ubuntu again..

> **grmmog said:**
> I've got the DG33TL as well and had no issues installing Ubuntu 7.04.  The only problem I've had with the G33 chipset is with the NIC.

Take a look at your BIOS settings for your hard drives.  There are settings for AHCI, IDE & RAID that can mess things up.  What processor are you running?  Have you updated your bios to the latest version?

I updated bios to latest version, but it did not helped. PC is runing on dualcore 1.8.

> **Pumalite said:**
> As dabl mentioned it could be the mix of IDE and SATA. Some people in some boards has has success going to BIOS>IDE Configuration>Enhanced Support for PATA+SATA (or equivalent)

It looks that bios configuration is problem for me too, but i'm not sure waht is PATA+SATA?

 My PC looks like this:
1 ide HDD 160GB Partitioned 15GB-NFS 15GB-EXT 1Gb- swat (for linux) 49Gb-NTFS, 70GB FAT32,
1 SATA HDD 80GB one partition FAT32
+IDE CD-drive

I want to install ubuntu on ide HDD using ide CD-drive. I think thats the probem.
It looks like no appropiate CD-drive drivers are found..

Any more suggestions?

---

### Post by Pumalite on 2007-09-23
PATA supports IDE and SATA, SATA
People with Intel boards do well many times setting CD to AHCI

---

### Post by dumas33 on 2007-09-24
> **Pumalite said:**
> 
People with Intel boards do well many times setting CD to AHCI

How to do that?

---

### Post by Pumalite on 2007-09-24
In your BIOS

---

### Post by dumas33 on 2007-09-24
So, I set bios configuration to 
*Advanced>Drive configuration>Configure sata as AHCI*
But CD did'nt load. It was same tty error.

Maybe I give you all bios Advanced>Drive configuration options, in case I'm missing something ovious:

[I]ATA/IDE - Native (currenly set) / Legacy
Configure sata as AHCI (currenly set)/Raid/IDE
SMART Enable/disable[/I]

Configure sata as RAID or AHCI winxp works fine, but if set IDE windows fails to boot

Please give my correct config!:confused:

---

### Post by Pumalite on 2007-09-24
I just got this tidbit that might help you:

 Re: CD/DVD writer does not mount in Ubuntu
[https://answers.launchpad.net/ubuntu/+question/10747](https://answers.launchpad.net/ubuntu/+question/10747)

adding

libata
ata_piix
piix

to the bottom of the file /etc/modules and reboot.

worked for me. (DELL Latitude D630)

Worth a try maybe.

---

### Post by rperkins on 2007-10-05
> **gotlinuxed said:**
> FYI to DG33TL owners finding this thread via google, the magic word for the NIC is "e1000-7.6.5.tar.gz" .


I installed ubuntu 7.04 and
e1000-7.6.9 worked for me. I got it from sourceforge
[http://sourceforge.net/project/showfiles.php?group_id=42302&package_id=54835](http://sourceforge.net/project/showfiles.php?group_id=42302&package_id=54835)

i was so glad everything i needed to compile this was already installed.  thanks ubuntu !
it compiled fine, although there was an error installing the manpage, but i just ignored it.
i dont expect to be doing much  manual fiddling with the ethernet controller :)

i see people mentioning video issues, but xwindows came right up for me.
I am wondering, anyone using the onboard vga and dvi simultaneously in a dual head config ?

---

### Post by nishchals on 2007-10-06
I think i have hit the same problem with this hardware - and now going back to XP. 

How did you add the floppy drive to this mobo? Did you use a USB external flopy drive?

---

### Post by dumas33 on 2007-10-08
Yes I used usb flopy drive.

Now I will try to install using USB but [URL="https://help.ubuntu.com/7.04/installation-guide/i386/boot-usb-files.html"]description how to do that is completely useless for me. 
I need flecssible way to add iso file , but how to find "ubuntu archives" whit vmlinuz (kernel binary), initrd.gz (initial ramdisk image), syslinux.cfg (SYSLINUX configuration file) files?

Maybe there is better description how to install ubuntu from usb memory stick?

---

### Post by icarusx86 on 2007-10-19
hi

second time I have posted on this forum but forgot my last username....

anyway I am also struggling with this DG33TL. I have to run linux on it but have not succeeded yet.

I do recomand upgrading the bios.

	
OS:Linux*, OS Independent, Windows Vista* 32, Windows Vista* 64, Windows* 2000, Windows* XP Home Edition, Windows* XP Media Center Edition, Windows* XP Professional, Windows* XP Professional x64 Edition

ISO Image BIOS Update [DP0293P.ISO] - Bootable ISO image BIOS update; this is the recommended method to update the BIOS on systems running Linux*. It requires a blank CD and a read/writeable CD drive.

[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=N&Inst=Yes&ProductID=2806&DwnldID=14596&strOSs=39&OSFullName=Linux*&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=N&Inst=Yes&ProductID=2806&DwnldID=14596&strOSs=39&OSFullName=Linux*&lang=eng)


this has not solved my problem I am going to try 7.10 soon I hope it works coz my head is on the line.
Please excuse my spelling.

---

### Post by dumas33 on 2007-10-21
Few days ago I was able to install Mandriva 2008.  
Easterday I was successful to boot gutsy live CD. 
But the problem remained.  In 'system settings>system administration>Disk and file systems' shows both disks correctly, but during installation only one hard disk is shown and after finishing installation kubuntu does not boot, i see Mandriva grub boot menu.

So my chaotic system looks like this:
WD160GB ide
1. Windows xp
2. Mandriva

Seagate 80 sata:
1. Kubuntu

I'm not very good in all OS stuff, so I'm maybe something obvious?

---

### Post by icarusx86 on 2007-10-22
Got my system working......
Here is my config.
 
Intel Desktop Board DG33TL

Ubuntu desktop 7.10

BIOS Update 0293
Advanced = Boot Configuration ...

ATA/IDE Mode         <Native>
Configure SATA as  <IDE> (AHCI GRUB gave a Error 15 and system would not boot)
S.M.A.R.T               <Enabled>

2 x 512M Kingston 667Mhz

PATA Seagate 120Gig (Os Drive)
SATA Seagate 500Gig
SATA WD 500Gig
SATA WD 3200Gig
SATA Seagate 200 Gig

---

### Post by dumas33 on 2007-10-22
Yesterday I booted my ubuntu to. 

Back to linux again. How good it is :)

It was really obvious mistake,  wrong primary hdd was selected in BIOS

---

### Post by icarusx86 on 2007-10-22
> **dumas33 said:**
> Yesterday I booted my ubuntu to. 

**Back to linux again. How good it is** :)

It was really obvious mistake,  wrong primary hdd was selected in BIOS

:mrgreen::mrgreen:

---

### Post by er_vijayv on 2007-11-08
I've been a linux user for 5yrs now. Taking a look at ubuntu, I feel like working in OS X. Great work by the ubuntu team. Congrats.

> **gotlinuxed said:**
> 
I've been able to run my three SATA drives in raid1/5 with dmraid on Ubuntu & FC7 with the BIOS set to AHCPI. 

ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
scsi 1:0:0:0: Direct-Access     ATA      WDC WD4000KD-00N 01.0 PQ: 0 ANSI: 5


Happy to hear raid is possible with dg33tl using dmraid.

I have Q6600 and dg33tl with two identical 400GB segate sata drives. But, I'm unable to put them in raid configuration. I've also upgraded the bios from the intel website.

Can someone guide me in setting up raid on this machine. dmraid says "No RAID disks found". What config should i do in the bios?. I've currently put sata in AHCI config in the bios. 

What config should i use for S.M.A.R.T?

Thanks in advance,
Vijay

---

### Post by er_vijayv on 2007-11-08
Sorry. The message got posted twice.

---

### Post by plik on 2007-11-12
i've got the same Intel Desktop Board DG33TL and am using both the DVI and VGA out for dual monitor setup. this works fine in Vista and XP, but when i boot to Ubuntu 7.10 64bit, the screens are mirrored and will not allow me to correctly configure the system for dual monitor use. 
anyone else have this same issue? 
any suggestions?

thanks in advance.

---

### Post by Pumalite on 2007-11-12
[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

---

