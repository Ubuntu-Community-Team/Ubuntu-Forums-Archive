---
title: "installer kinda freezes at 'Booting kernel'"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by Patrick-Ruff on 2006-06-02
hey all, this is kinda frustrating, especially since I can't easeally download another disc. the bloody installer froze at 'Uncompressing Linux, OK. Booting the kernel' and then it sits there, forever....

---

### Post by Fr@nKy on 2006-06-03
I have exactly the same problem!

And alternate mode doesn't work either I get a Release File error or something like that! I think that's my SATA drive fault but don't know how to get around it!

---

### Post by curuxz on 2006-06-03
Patric can you post your pc's details and tell us which of the 3 install disk types your using :)

---

### Post by wood on 2006-06-03
Hi together,

I have the same problem too. I just wanted to install Ubuntu 6.06 and then the following problems occur (I tried different things ...)

1) Put in the install disc of unbuntu 6.06 and pressing "Enter" when the start dialog appears 
-> then it shows:
**Uncompressing Linux ... Ok, booting the kernel**
and nothing else happens

2) after the start dialog, I press F6 and enter:
**install acpi=off**
-> then it shows:
[B][  59.289922]..MP-BIOS bug: 8254 timer not connected to IO-APIC
[  59.523417]PnBIOS: Unknown tag '0x0', length '0'.
[  59.523447]PnBIOS: Unknown tag '0x0', length '1'.[/B]
and nothing else happens

3) after the start dialog, I press F6 and enter:
**install noapic**
-> then it shows:
**Uncompressing Linux ... Ok, booting the kernel**
and nothing else happens

4) after the start dialog, I press F6 and enter:
**install noapic nolapic**
-> then it shows:
**[4294669.603000]BIOS bug, local APIC #0 not detected!...**
and nothing else happens

5)after the start dialog, I press F6 and enter:
**install noapic nolapic acpi=off**
-> then it shows:
[B][  47.306531]BIOS bug, local APIC #0 not detected!...
[  47.307995]PnBIOS: Unknown tag '0x0', length '0'.
[  47.308024]PnBIOS: Unknown tag '0x0', length '1'.[/B]
and nothing else happens

So it's not possible to install ubuntu 6.06 at all for me :( .
Before I tried to do a complete new install, I also tried to upgrade breezy, but after the install the system don't load after grub (just a black screen).

Can anyone help me - please.
Jan (still a Linux-Newbie)

P.S.: my system is as following: (Windows XP installed parallel)

[B]AMD Athlon 64 3200+ tray Sockel 939 Venice
Motherboard MSI K8NGM2-FID (GeForce 6150 + nForce 430) [Gigabit LAN, IEEE1394, DVI] -> [/B]maybe the problem, because it's a quite new model (November 05)[B]
1024MB DDRRAM Corsair VS Kit PC400 CL2.5
hard disk 250GB Samsung SpinPoint P120 SP2504C NCQ SATAII
DVD LG GSA-4167B schwarz
inLine 3,5" Card-Reader 16 in 1
Seasonic S12-330W ATX2.0[/B]

---

### Post by wildem on 2006-06-03
Hey,

I've got the same problem on one of me machines. Here's whats happening:

Installation went ok on a P4 3.0GHz, ASUS p8S800, IDE 120, Desktop. This installed (LAMP Server) flawlessly and runs fine.

Laptop Installation(LAMP Server, Or Normal Install) on Centrino 1.4, hangs for either choice of installation , after ejecting the cd, rebooting, uncompressing the kernel, says BOOTING Kernel, and then nothing ! Just Hangs. 

Im going to try to iron the wrinkles over the weekend and get to the bottom of this.

---

### Post by Fr@nKy on 2006-06-03
Yeah! I have a similar system!!

Check it:
AMD Athlon 64 3800+ @ 2.4GHz (OCed to 2.6GHz)
2GB DDR400 Dual Channel @ 434 MHz
HD Seagate SATA 200GB 7200RPM 8MB CACHE
Motherboard ASUS A8N-SLI Deluxe
XFX Geforce 6600GT 256MB DDR3 Edition
DVD Player: Plextor PX-130A
DVD Recorder: NEC ND-3540A

Primary Master: None
Primary Slave: None
Secondary Master: Plextor PX-130A
Secondary Slave: NEC ND-3540A
1st SATA: Seagate 200GB
2nd SATA: None
3rd SATA: None
4th SATA: None

And I'm using the x86 Desktop CD!!

I have this problem with all previous releases from Flight 6 to Final (I have also tried some of the x64 versions and the same problem happened)


Sorry for invading your Thread but maybe this can solve both our problems since they look to be caused by the same reason!

---

### Post by Fr@nKy on 2006-06-03
[QUOTE=wildem]Hey,

I've got the same problem on one of me machines. Here's whats happening:

Installation went ok on a P4 3.0GHz, ASUS p8S800, IDE 120, Desktop. This installed (LAMP Server) flawlessly and runs fine.

Laptop Installation(LAMP Server, Or Normal Install) on Centrino 1.4, hangs for either choice of installation , after ejecting the cd, rebooting, uncompressing the kernel, says BOOTING Kernel, and then nothing ! Just Hangs. 

Im going to try to iron the wrinkles over the weekend and get to the bottom of this.[/QUOTE]

I hope this can be fixed! For the first time on my life I really want to leave Windows and I'm stuck! Cause this issue is present also on Mandriva for Example!

---

### Post by Patrick-Ruff on 2006-06-03
aye to that, well, I DID manage to get it installed, I hit F6 in the regular install, it showed its regular boot options already typed in, but besides the -- I put 'boot=' and for some odd reason, it actually installed, booted up the live cd and everything :). now the problem remains, it gets stuck at Mounting Root File system at reboot. but, I can boot up in recovery mode, so perhaps I could make some crucial changes there.

---

### Post by Patrick-Ruff on 2006-06-03
also, I'm on a laptop, specs are...
Pentium M 1.6GHz 2MB L2 Cache
Radeon Mobility X300 64MB (dedicated) PCI-E 
512MB o' Ram
40GB HD
no extra devices connected atm.

---

### Post by JsPr on 2006-06-03
I had a similar problem. Solved it by disableing USB legacy support in the BIOS. Might/might not work for you.

---

### Post by Fr@nKy on 2006-06-03
But that would not make you unable to use USB? Or you could enable it later? (However I think my problem is really the SATA HD because on other Desktop CDs from previous versions of Dapper I used to got a Busybox message saying that it can't access tty. But what the hell is tty? I believe is related to the Hard Drive! Because before it shows up the Loading Driver doesn't fill the bar and it does even starts th Mouting of root filesystem)

---

### Post by Patrick-Ruff on 2006-06-03
tty related to the hard drive? I don't think so, I'm pretty sure its a network related thing. I don't think the problem is USB in my perspective, and my situation, since I don't have ANY usb devices whatsoever connected to this laptop.

---

### Post by Fr@nKy on 2006-06-03
Ok Right! Tell me one thing you added boot= with ' or without them??

And please if you manage to boot normally (no recovery mode) please tell me how you did it!! Dapper is being a big headache on this system! On my old System I have used LiveCDs a few times with no problem but this one refuses to do so!

---

### Post by Patrick-Ruff on 2006-06-03
Believe me, if I had the answer I would gladly inform everyone on the forums, hell, I'm a linux noob, so its really unlikely I can just simply figure this out. none of the 'pros' on the forum seem to want to help. or are just too lazy to do so.

---

### Post by Fr@nKy on 2006-06-03
Yeah! I'm also a Linux noob. And I'll continue to be unless someone helps me (us).

---

### Post by Patrick-Ruff on 2006-06-03
ok I'm trying something new right now, adding root=/dev/sda1 to the install options.

---

### Post by Patrick-Ruff on 2006-06-03
ok, that didn't work....I'm gonna test out a few things.

---

### Post by Fr@nKy on 2006-06-03
Well it seems that Dapper is really being a pain in the *** of many people! I have never tried breezy but it seems that it was much easier to install it! I haven't tried the Final Alternate Mode Install CD but I believe it will not work cause filght6, beta 2 and Release Candidate Versions don't! Well I'll wait a few more days to see if everything gets fixed! And maybe 6.10 version will fix all this later this year!

---

### Post by nismoskys on 2006-06-03
i have the exact same problem and i dunno what to do.. i tried your 'boot=' after -- but it didnt even get to 'booting the kernel' with that.

---

### Post by Patrick-Ruff on 2006-06-03
yeah, you gotta hela fiddle with it. try different install options and shit. for some reason the root= worked for me. but, sometimes it doesn't I suggest you try a few different thigns.  try root=sda1 or sda hda hde etc.

---

### Post by nismoskys on 2006-06-03
cool thanks.. ill try it out.

---

### Post by Fr@nKy on 2006-06-04
No one fixed this problem yet?

---

### Post by Marcel-X on 2006-06-04
Same here! I haven't tested Knoppix, Feather or Ubuntu 5.10 on this recently build machine. An older system runs fine with 6.0.6.

Copy 'n paste from Everest:

[SIZE="1"]Motherboard	
CPU Type	AMD Athlon XP, 2000 MHz 2400+
Motherboard Name	MSI K7N2 Delta2 (MS-6570E)  (5 PCI, 1 AGP, 3 DDR DIMM, Audio, LAN)
Motherboard Chipset	nVIDIA nForce2 Ultra 400
System Memory	1536 MB
BIOS Type	Award (04/01/05)
Communication Port	Communications Port (COM1)
Communication Port	Printer Port (LPT1)
	
Display	
Video Adapter	RADEON 9800 PRO -  (128 MB)
3D Accelerator	ATI Radeon 9800 Pro (R350)
Monitor	Iiyama Vision Master 450 S901GT  [19" CRT]
	
Multimedia	
Audio Adapter	Creative SB0240 Audigy 2 Platinum Sound Card
Audio Adapter	nVIDIA MCP2-S - Audio Processing Unit (Dolby Digital)
	
Storage	
IDE Controller	NVIDIA MCP2S Parallel ATA Controller (v2.6)
Disk Drive	Maxtor 6L250R0  (250 GB, 7200 RPM, Ultra-ATA/133)
Disk Drive	IOMEGA ZIP 100
Optical Drive	PLEXTOR DVDR   PX-750A

Input	
Keyboard	HID Keyboard Device
Mouse	HID-compliant mouse
	
Network	
Network Adapter	3Com EtherLink XL 10/100 PCI For Complete PC Management NIC (3C905C-TX)
	
Peripherals	
USB1 Controller	nVIDIA MCP2-S - OHCI USB Controller
USB1 Controller	nVIDIA MCP2-S - OHCI USB Controller
USB2 Controller	nVIDIA MCP2-S - EHCI USB 2.0 Controller
USB Device	USB Composite Device
USB Device	USB Human Interface Device
USB Device	USB Human Interface Device
[/SIZE]

---

### Post by ArkanjoPT on 2006-06-04
[QUOTE=wood]
1) Put in the install disc of unbuntu 6.06 and pressing "Enter" when the start dialog appears 
-> then it shows:
**Uncompressing Linux ... Ok, booting the kernel**
and nothing else happens

2) after the start dialog, I press F6 and enter:
**install acpi=off**
-> then it shows:
[B][  59.289922]..MP-BIOS bug: 8254 timer not connected to IO-APIC
[  59.523417]PnBIOS: Unknown tag '0x0', length '0'.
[  59.523447]PnBIOS: Unknown tag '0x0', length '1'.[/B]
and nothing else happens

3) after the start dialog, I press F6 and enter:
**install noapic**
-> then it shows:
**Uncompressing Linux ... Ok, booting the kernel**
and nothing else happens

4) after the start dialog, I press F6 and enter:
**install noapic nolapic**
-> then it shows:
**[4294669.603000]BIOS bug, local APIC #0 not detected!...**
and nothing else happens

5)after the start dialog, I press F6 and enter:
**install noapic nolapic acpi=off**
-> then it shows:
[B][  47.306531]BIOS bug, local APIC #0 not detected!...
[  47.307995]PnBIOS: Unknown tag '0x0', length '0'.
[  47.308024]PnBIOS: Unknown tag '0x0', length '1'.[/B]
and nothing else happens
[/B][/QUOTE]


Same problem here ](*,) 

My hardware Specs:

Asus A8R-MVP
Opteron 170
Sata Maxtor 160Gb

---

### Post by Fr@nKy on 2006-06-04
It looks like Ubuntu really hates SATA and/or nForce 4 Chipsets :(

---

### Post by Al_maverick on 2006-06-04
Its a problem with Dapper. I use Breezy and my SATA drives and nForce chipset work fine. But now I upgraded and I get the tty job control error.

---

### Post by rbalfour on 2006-06-04
Had the same issue. I re-burned the ISO onto a CD-RW and everything was good.

---

### Post by Fr@nKy on 2006-06-04
Yeah! It's Dapper Fault. I hope this gets fixed on 6.10. This has happened from version flight 6 to final so it's not a burn cd problem for sure!

---

### Post by wildem on 2006-06-04
Hey every1, 

In reference to my post and other ppl that had problems with ubuntu freezing after 'Booting Kernel' message. I have researched my possibilities and have found no solution that can be accomplished with the Dapper Server Iso 386 Install Disc. As I have posted before, my problem was in reference to my laptop with:

Intel Centrino 1.4, 10/100 Nic, 40GB Ide, compaq X1000 ...

My solution was:

I installed the previous 5.10 Breezy.
I edited '/etc/apt/sources.list'

1.
Changed the server to query from Breezy to Dapper in any line with any reference to an update/package mirror.

So if it says somthing like: ...::/...ubuntu.com breezy main restricted - change it to ...ubuntu.com dapper main restricted. This applies to other mirrors for security updates, universe, multiverse. 

2.
run:
apt-get update
This will update the list from the proper mirrors and will let you do the third step...

3.
run:
apt-get dist-upgrade 
Prepare for about a 100 megs worth of download, and let it do its thing. Once you reboot you can choose the new 2.6.15 kernel from the boot list, and will enable you to install any package that dapper has access to.

Caution: I do not know if some installs might behave differently from mine and wreck havoc on your system. My install contained a fresh install of breezy server. This might be one route to avoid the problem of Dapper freezing at 'Booting Kernel' after install from the Dapper 6.06 install disc.

Good Luck,

btw, i found similar steps somewhere else on this forum, so respect to whoever did that.

---

### Post by ArkanjoPT on 2006-06-05
Hi guys,

Still no solution here, does anyone post this at bugs.ubuntu.com ?
Maybe it's better if he filled a bug.

---

### Post by gt24 on 2006-06-05
Just wanted to post a "me too", I had a similar problem with the K7 kernel.  However, Windows XP freaked out when I booted into it (I run dual boot on my main rig) and it ran a checkdisk on the NTFS partition on the same drive that linux is on.  Full checkdisk and smart status check later, the drive is fine.  I disabled GRUB (fixmbr from recovery console) being that I don't want to mistakenly boot Ubuntu and potentially cause damage elsewhere!

I have multiple drives (4), all NTFS except for a small Ubuntu ext2 partition on the 2nd drive.  The 3 and 4 drives are on a Silicon Image RAID controller, but not raided.  The card is annoying but it has served well, other than having no SMART status for the 3rd and 4th drives.  As mentioned before in this thread, the older kernel boots despite being largely incompatible with Dapper and the Dapper kernel causes a root filesystem kernel panic.  ](*,)

I think there is a bug report on this already... correct me if I am wrong...  If this is an appropriate bug report, it is critical and confirmed.

[https://launchpad.net/distros/ubuntu/+source/initramfs-tools/+bug/47768](https://launchpad.net/distros/ubuntu/+source/initramfs-tools/+bug/47768)

If not, there are many on this page that fit the description as well... either being "cannot mount root filesystem" to freezing to certain scripts not being updated and causing this mess... I'm not certain what bug fits the best here.

[https://launchpad.net/distros/ubuntu/+bugs/?field.searchtext=root&search=Search&field.status%3Alist=Unconfirmed&field.status%3Alist=Confirmed&field.status%3Alist=In+Progress&field.status%3Alist=Needs+Info&field.status%3Alist=Fix+Committed&field.assignee=&field.owner=&field.omit_dupes=on&field.has_patch=&field.has_no_package=&orderby=-severity%2C-priority](https://launchpad.net/distros/ubuntu/+bugs/?field.searchtext=root&search=Search&field.status%3Alist=Unconfirmed&field.status%3Alist=Confirmed&field.status%3Alist=In+Progress&field.status%3Alist=Needs+Info&field.status%3Alist=Fix+Committed&field.assignee=&field.owner=&field.omit_dupes=on&field.has_patch=&field.has_no_package=&orderby=-severity%2C-priority)

---

### Post by ArkanjoPT on 2006-06-05
Well that bug is not exactly what i'm having. Mine is more in this line:
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/38263](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/38263)

Still i just wanted to find some kind of work-around, i really would like to try Ubuntu on my new PC ](*,)

I already tried the the sticky thread but no go here with any of that solutions.

---

### Post by rjb on 2006-06-05
FYI: For me it was disabling Legacy USB Support (in the BIOIS) that solved the problem.

---

### Post by ArkanjoPT on 2006-06-05
[QUOTE=rjb]FYI: For me it was disabling Legacy USB Support (in the BIOIS) that solved the problem.[/QUOTE]

I've tried that but the same problem persist. Whats you Mobo? and do you only have SATA discs?

My Specs by the way:
Opteron 170 (Dual Core)
Asus A8R-MVP
Maxtor 160G SATA
Sapphire ATI Radeon X800 GTO2

---

### Post by rjb on 2006-06-05
I do not have any SATA drives... It is an Asus P4S8X-MX.

---

### Post by Fr@nKy on 2006-06-06
Still no solution?

---

### Post by tao312 on 2006-06-06
[QUOTE=Patrick-Ruff]hey all, this is kinda frustrating, especially since I can't easeally download another disc. the bloody installer froze at 'Uncompressing Linux, OK. Booting the kernel' and then it sits there, forever....[/QUOTE]
I was having the same problem.  I wasted about 5 CDs, then I finally downloaded from a different mirror.  make sure the file size is 697 or 698MB.  the bad one I had was 623MB from a US mirror.  then the installation went smooth from there.  I hope this helps.

---

### Post by nismoskys on 2006-06-06
nope... mine is 697.8 MB.

---

### Post by Greg T. on 2006-06-07
I'm getting the same problem, after updating my system (including the kernel) upon the recent Dapper release. I'd been using the beta for months without problem. I was able to do a workaround by turning off USB, but that's hardly a long-term solution. I have an attached USB Maxtor drive, but it's turned off (though not unplugged). I have Ubuntu on a SATA drive connected to a ASUS A8N32-SLI Deluxe mobo. 

(While searching for a solution, I once left it sit for about 30 minutes. It just stayed on the same screen; it never dropped to console mode.)

---

### Post by dbenhur on 2006-06-07
[QUOTE=wood]
[B]AMD Athlon 64 3200+ tray Sockel 939 Venice
Motherboard MSI K8NGM2-FID (GeForce 6150 + nForce 430) [/QUOTE]

I've been struggling with a Dapper AMD64 install on a similar system with this motherboard.  I had the same issue of freezing when booting the kernal at first.  Running memtest showed a small range of memory getting errors so I searched google for references to the hex address and discovered a post somewhere suggestiong turning off Legacy USB Support in the BIOS.  That did the trick and I could boot from the Live CD no problem.

However, I have further difficulties with actually installing after the live cd boot.  The install freezes during partition/format.  I've poked around and tried various boot options (like acpi=off noapic nolapic).  Nothing fixes the problem, but I've managed to narrow down when it occurs and make it reproducible.  I can work indefinately off the live cd, but once I run Gparted after the initial device scan by Gparted, the next time anything tries to read from the CD, I see a couple of media errors (bad sector) on /dev/hda reported via dmesg and then very shortly the system freezes (mouse moves, Alt-FX consoles switch, but nothing else works at all. Alt-SysRq-t produces no output).

I've run the CD contents verification and it ran all the way through with no errors, so this isn't bad media. Something related to that device scan causes subsequent reads to the IDE CD drive to fail.

System:
MSI K8NGM2-FID (GeForce 6150 + nForce 430)
AMD64 X2 3800+
2GB OCZ PC3200 CAS-2 memory pair.
2 x 300GB 7200.9 Seagate Barracuda SATA2 drives.
NEC IDE DVD Burner ND-3550A

I've tried both the shipping BIOS 3.20 and a beta BIOS v3.35 I found here [http://www.avsforum.com/avs-vb/showthread.php?p=7511152&&#post7511152](http://www.avsforum.com/avs-vb/showthread.php?p=7511152&&#post7511152)

---

### Post by Dillius on 2006-06-07
I was able to get past this problem using the ide=nodma method, but after that point the GUI freaks out entirely and it forces me to command line.

---

### Post by popie on 2006-06-08
I also can't get the desktop disc to boot. System gets "stuck" at "Mounting root file system..."

Tried: 
noapci nolapci - didn't help
disable legacy usb support - didn't help

Problem occurs when booting Ubuntu 6.06 desktop disc, or Xubuntu desktop disc. Same result on both. 

I can boot with these discs normally with older PCs.

I'm using an AMD64 on an Asus K8N motherboard.

<EDIT> Its working... disabling USB support seemed to help, but I wasn't waiting long enough on subsequent bootups. ;) I needed to be more patient at "Loading root file system..." prompt.

---

### Post by asp on 2006-06-08
Hi all, 

it seems I am also experiencing this issue, although I do not believe it to be ubuntu specific (as I have just tried with another distro with the same result)

The computer is a IBM Netvista 6266 EA5 (according to the lable)
 Intel Celeron 633MHz (128KB), 128MB, 10GB IDE HDD, Small Form Factor (3x3), Intel 810e, Ethernet, Win2000/NT - according to IBM's site, but this one has a 1gig celeron.

So far I have tried everything that has been suggested in these forums and hours of googling including;

- acpi=off
- noacpi
- nolacpi
- ide=nodma
- Disabled USB support (completely) in the bios
- Turned off Power Management (completely) in the bios
- No USB devices attached
- Set HDD to "compatibility" mode in the bios
- It is running the latest BIOS available for this motherboard.

The BIOS has a pretty limited selection of options, but I have tried everything that seems relevant including restoring to default to no avail.

I have tried Both ubuntu 6.06 server and 5.10 as well as Trustix 3.0

In all cases it gets to "uncompressing linux... ok Loading Kernel" and then halts. In order to get some more info I have tried using "debug" as a kernel switch, but this doesn't reveal any more info.

I am installing via PXE (I need to do it this way as for some reason this PC doesn't want to boot from CD) but I know this works fine as I have done the same on my laptop and it progresses past "loading kernel" and into the installer, so there are no "corrupted files".

It must be related to some hardware incompatibility on the Netvista, but I am at a loss as to figure out what.

Is anyone here able to offer any further advice or suggestions?

---

### Post by asp on 2006-06-08
[QUOTE=asp]
Is anyone here able to offer any further advice or suggestions?[/QUOTE]

Nothing? :(

---

### Post by asp on 2006-06-09
As a last roll of the dice i tried an older distro using kernel 2.4. Results in the same thing. "uncompressing linux...ok, booting kernel" then hangs. I guess it just wasn't ment to be. The shame of it all is windows XP installs and loads perfectly on the machine.

---

### Post by Fr@nKy on 2006-06-10
Well I give up on Linux! All betas from flight 6 to RC failed on both Desktop and Alternate CD and the final I have only tested the Desktop CD also with no success! I'd love to leave MS but at least their OS works!

---

### Post by edgecrusher on 2006-06-12
I have to confirm what asp said about this not being a Ubuntu problem. I have been tackling this problem for more than 6 months now. It looks to be a kernel problem. The last kernel I could successfully boot was 2.6.13.5. Anything after that gives me the "Uncompressing linux...Booting the kernel" line, then freeze.

So hang in there guys, and if I can work it out I'll let you know.

FYI, my specs:
AMD K7 950 MHz, 384Mb RAM, PCChips (SIS chipset) motherboard.

---

### Post by korinel on 2006-06-12
Just a quick "me too".  Have only tried AMD64 live disks so far (2 of them), but similar kernel opts methods to the rest of you.  System rock solid under Windows XP and Vista Beta 2 (barring some missing drivers). 

Specs are:

MSI K8NGM2-FID Motherboard
AMD Venice 3000+ E6 Processor
Corsair TWINX2048-3200 paired DDR (2*1GB)
1*Samsung 250GB SATA II drive
1*Asus DRW-1608P2 IDE DVD Writer

Not good. :(

---

### Post by thedguy on 2006-06-12
deleted: bad info...:-x

---

### Post by N!zzo on 2006-06-12
Im having the same problem.

Is there a way to install ubuntu with an earlier version of the kernel? and would my problem be because of a SATA hdd on my computer, with this current kernel?

specs:
ASUS P5LD2 mobo
Intel Pentium D 3GHz
DDRII RAM 2G
WD 160G SATAII
Sony DVD drive
BenQ DVD burner

---

### Post by mayostard on 2006-06-12
[QUOTE=edgecrusher]I have to confirm what asp said about this not being a Ubuntu problem. I have been tackling this problem for more than 6 months now. It looks to be a kernel problem.[/QUOTE]

Just to add more data...

I concur with this.  However, the fix seems to be different for different hardware combos.  My gut feeling is that there is something the bios is leaving in memory that the newer 2.6.x kernels are not expecting.

I have seen this problem on a Proliant DL380 G2 (P3 1.2GHz) and a Proliant DL580 G1 (4x Xeon 700MHz) and a Proliant 6400R (2x Xeon 500MHz).  All of them exhibited the problem with both Server and Desktop 6.06.

On the DL380, I got around it by adding acpi=off to the boot command line, and adding that into the grub menu file.

This did not work on the DL580.  I haven't had enough time to try anything else yet.  I haven't tried anything on the 6400R.

---

### Post by ember on 2006-06-13
I have an additional suggestion for those experiencing that problem (read: I had it, too ;)):

Try setting your USB ports to "1.1 only" and see whether it boots. For me that helped (though its not really useful to have an external harddisk connected via USB 1.1, but it's a workaround) - I use a Asus K8N-E (Nforce 3 250 GB) that used to work up to breezy. 

I'll try building a custom kernel 2.6.16 and see whether it works the next days.

---

### Post by edgecrusher on 2006-06-13
For N!zzo,
To install Ubuntu with an older kernel you would have to install Breezy (5.10). And then you could either use synaptic (or apt) to upgrade to the last kernel supported in that release, you get down and dirty and roll your own.

---

### Post by krazyd on 2006-06-13
Have to add to this thread, just to say 'me too!'
This was on an ASUS A6000KT notebook. Got it past the freeze by disabling usb in bios, but now I have no usb mouse in Ubuntu :/

It's a shame cos I was really looking forward to trying linux and Dapper seemed the perfect opportunity. Noticed a couple of other problems (running live), just in case someone with the same hardware is thinking about Ubuntu..
[list]
[*]Couldn't get wireless working, so no internet.
[*]Screen resolution set at 1024x768 - widescreen not recognised, and 61Hz for some reason.
[/list]

---

### Post by Healey on 2006-06-14
Hi

I dont know if it will help any one but I solved the stuck at "Mounting Root file system" by changing the CD rom drive for a different one !!

I had an old one that had been inside a cupboard for a while and I thought I would give it a try and it worked - Loaded Dapper no problem !!

I cant explain why this is the case as the orginal CD Rom drive was fine for Breezy !!!

To make it even more interesting I tested loading breezy with the "new drive and breezy did not like it very much !!

So it seems that it could be a cd rom hardware related problem

I am no expert - but it worked for me 

Hope it helps

Healey

---

### Post by B0rsuk on 2006-06-22
This is NOT exclusive to dapper ! Here's my unanswered post from another topic a while ago:

> 
Hi

I got Kubuntu 5.10 Breezy Badger installed on my friend's machine. I got it to work and even configured ADSL connection, and upgraded some packages.

I rebooted it a few times and went home.

Several days later my friend says Kubuntu doesn't boot.
I checked his computer today (posting this from his machine, in fact) and it always freezes at 'booting up kernel'. I enabled debug in grub but it shows no additional information.
The most frustrating part is that it doesn't even boot from install CD anymore ! It immediately freezes at 'booting up kernel', too !

The 3 partitions look fine if you check them via explore2fs utility (windows). What could it be ?

Even before I arrived to his home I asked him about suspicious actions like messing with partitioning software, checking disks, etc, installing strange software, changing BIOS settings, etc. Nothing, except that he admitted to ocassionaly turning off his machine by cutting off power (!!). And I was certain this is the problem until I arrived here; as I said it doesn't even boot from Kubuntu 5.10 Breezy install cd. Grub works and winxp loads fine. My friend says he checked disks with some kind of software and no errors were found.
What could it be ? It's most probably not broken partition, if it doesn't even boot from CD. How to debug it ? What BIOS settings/windows software could affect it ?
Please help, it's quite urgent.
--------------

Hardware:
radeon 9000
athlon xp around 1400+
asus mainboard
512 + 128 RAM

HDDs:
?western digital
Samsung something


In other words, bump.

---

### Post by B0rsuk on 2006-06-23
**IT WORKS.**

As one of you above suggested, I booted it with extra
acpi=off apm=off
options. If you're unsure how to do it, press c for grub commandline, then type boot.
It will freeze, but you'll get more messages this way. Write down all the commands.
Then next time it boots, I had to rewrite all several lines (and then type boot), BUT add acpi=off apm=off to the line containing the line
kernel /boot/vmlinuz (blah blah)
------------

Alternatively, if you can access your linux filesystem, edit grub configuration file menu.lst, (I think it's located in /boot/grub/ ) and add
acpi=off apm=off  
to the end of the line which starts with kernel /boot/vmlinuz blah blah. Make sure you edit the menu choice you normally use, so or select the one you edited.
-----------------

One last thing. The problem started to appear once my friend sold cd-rom drive and replaced it with dvd drive. So far, I don't know what's the model, but I soon will.

---

### Post by Dadgumit on 2006-07-12
I don't think these are all the same problem. I have the same motherboard as the original poster and similar issues.

I have not ever been able to install dapper. 

I have tried all of the mentioned commands (noacpi etc...) except for the apm=off (what does that one do?).  I also have not tried disabling USB in any regard, but will try both tonight.

I read somewhere that going back to breezy and upgrade worked for some people so I tried that. It worked _partially_. I can boot dapper if I use an older kernel (15 I think), but then I can't get 3D rendering online (I believe the drivers depend on the kernel). 

The error I get when trying to boot with the most recent kernel (as well as the error I get when installing noacpi) is something to the effect of:

PNPBios Error: Resource structure does not contain an end tag.

I have been lookin for a fix for this error, but haven't found a thing yet.

---

### Post by tjansson on 2006-08-02
I'm trying to install ubuntu server i386 on my acient latop (233MHz, 128 Mb ram, 4 Gb HD - Acer extensa 501T) and I'm having the same problems. After booting the machine I have the options to install in example the LAMP server and if choose to do so it start loading the kernel and after writing "*Ok, booting the kernel*" it restart. 

I've tried noapic, nolapic, apci=off, apm=off and nodma none of the worked.

---

### Post by tjansson on 2006-08-02
I'm trying to install ubuntu server i386 on my acient latop (233MHz, 128 Mb ram, 4 Gb HD - Acer extensa 501T) and I'm having the same problems. After booting the machine I have the options to install in example the LAMP server and if choose to do so it start loading the kernel and after writing "*Ok, booting the kernel*" it restart. 

I've tried noapic, nolapic, apci=off, apm=off and nodma none of the worked.

---

### Post by caffine_fizz on 2006-08-07
Hey tried the changing out of the CD ROM and it worked for me, in the middle of installing now, no problems as of yet touch wood.
:p

---

### Post by caffine_fizz on 2006-08-07
**NO............**, now hangs copying files across. think i'l throw in the towel shortly!

---

### Post by nwgray on 2006-08-07
I had the same problem. Went in to BIOS and enabled USB Keyboard support (D'oh!) and turned off ACPI. It is working fine now on a ZBoard USB keyboard.

---

### Post by tjansson on 2006-08-08
I think it is kernel problem. I tried to isntall Debian Sarge instead and had servere problems with the 2.6 kernel but trying to install the 2.4 kernel everything went fine. 

I tried to turn USB on and off and it didn't make a difference in my case.

---

### Post by pjwigan on 2006-08-09
> I think it is kernel problem.

Looks that way.

I'm having similar issues with a new self-build box:

  Intel Core 2 Duo E6600
  Gigabyte GA-965P-DQ6
  2Gb Corsair TwinX DDR2 PC6400
  2 x 250GB Seagate Barracuda SATA300 disks

All the Linux distro's I've tried have failed as described in this thread, but PC-BSD installs smoothly.

[For the record, I tried Ubuntu 6.06, Kubuntu 6.06, Debian 3.1, Suse 10.1, Suse 9.3, and DSL 3.0.1.]

---

### Post by pjwigan on 2006-08-10
Fixed.

I swapped the original IDE DVD drive for a SATA one, and presto, Ubuntu installs :-)

Losing the IDE devices after the kernel has loaded appears to be a common problem with Intel P965 based motherboards.  There is no IDE support in the P965, so motherboard makers are rolling their own.

---

### Post by Forko on 2006-08-10
I had the same problem with my HP PC and it worked for me by typing;

live acpi=off

it can't hurt to try it.

---

### Post by Robbyx on 2006-08-14
> **Forko said:**
> I had the same problem with my HP PC and it worked for me by typing;

live acpi=off

it can't hurt to try it.

Having not bought a SATA cd/ dvd I am unable to install Ubuntu. My two SATA HD are unformatted and there are no other drives in the machine. It is new and I am installing from the CD on bootup. Where do I type "live acpi=off" ?

Since this thread seems to have dried up is it because there is now a solution to the problem other than buying another CD reader?

---

### Post by bearyj on 2006-08-14
I am attempting to install Dapper Drake on a EMachines T3140 (Sempron 3400+) and am experiencing the same issue.

I get to the booting kernel screen and it hangs.

Any resolution yet?

---

### Post by chakra_dude on 2006-08-15
I also have the same problem. i'm reading more maybe somewhere there's a solution

---

### Post by jac1d on 2006-08-16
I experience the problems outlined in other posts when attempting to install to an HP Proliant DL-380 server with RAID.

I disabled USB completely in the BIOS (I'm going to go turn it on again now that the OS is installed on the HD and see what happens).  I also added:

acpi=off apm=off

To the kernel boot options using F6 from the boot menu.  The system then booted fine from the live CD and performed the install using the icon on the desktop.  I'm using the desktop install CD on purpose as I wanted an X console in my rack.

Once I made those changes the system installed and booted with no problems.  I'm now downloading the 161 updates (I must not have the 6.06.1 CD).  I'll reboot, reenable USB and make sure things are ok.

-Jeff

---

### Post by djsamsel on 2006-08-24
hi guys, a little more info on the subject. i think there are multiple systems causing the same error. i have the asus a8n32-sli motherboard and could install .13 kernel as soon as i upgraded the kernel i'd get the same problem you're describing. tracking it through safe boot the system would stop on an ohci driver, which is for firewire. i disabled firewire on my mthrbrd and still no luck. i have a firewire port on my audigy sound card, but have not had time to remove the sound card and try. i suspect it won't do anything. it is ubuntu's build though. i have installed both sled and opensuse on the machine and both run very well. i hope ubuntu gets this bug worked out, because i love the community here, but until then, at least there is an option. plz contact me if anyone finds a workaround.

---

### Post by djsamsel on 2006-08-26
bump

---

### Post by Ray901 on 2006-08-27
Same problem here.

Have been using linux on and off for the best part of 10 years now and have spent the last three days trying to get Ubuntu to install. I have tried everything suggested on this forum (and more), have tried disabling every module possible in boot options - to no avail. It just does not like my shiny new PC.

Linux for everyone - easier said than done, back to windows for me I guess :( - see you in a years time when linux can install (maybe) on a machine with modern hardware.

---

### Post by djsamsel on 2006-08-27
> **Ray901 said:**
> Same problem here.

Have been using linux on and off for the best part of 10 years now and have spent the last three days trying to get Ubuntu to install. I have tried everything suggested on this forum (and more), have tried disabling every module possible in boot options - to no avail. It just does not like my shiny new PC.

Linux for everyone - easier said than done, back to windows for me I guess :( - see you in a years time when linux can install (maybe) on a machine with modern hardware.

hey ray, don't give up on linux just because of ubuntu. sled10 and opensuse have both installed on my desktop and laptop perfectly. give them a shot. i love the ubuntu community, but sled and opensuse gave me a far better oob experience. and for a free distro, ubuntu was costing me a ton of time.

---

### Post by Ray901 on 2006-08-27
djsamsel,

I will take your advice and give another distro a try. I was thinking of Suse as that is what I have used a few years back (Red Hat more recently on my old PC). Though someone did mention that this might be a kernel issue...

Holding down two jobs I just don't have the time to spend on the install anymore. For me, Ubuntu==](*,) at his time.

cheers

---

### Post by missingxtension on 2006-08-27
tried everything on this thread but doesnt work 
well i expected this from some other distro but not ubuntu it seems hopeless
i guess ill just go back to BSD it moght be more dificult but it has not let me down yet

---

### Post by Philote on 2006-08-28
Disabling The USB legacy support in my BIOS did the trick for me. So, if your having this issue try that 1st then move on to other solutions.

---

### Post by randell6564 on 2006-08-29
I'm tellin' ya folks.,Google some stuff regarding your Bios!

Play with your Bios.  If ya got a system that works, and ur just trying to test ubuntu, then start eliminating possibilities from your Bios!

You all seem to have up to date hardware, so Linux should work!  

I ran into some problems with dual-booting on a P4 msi board, and went into the Bios, changed from 'Auto' to 'LBA' and fell in Love! It all worked just doing that!

So play a little.  It won't hurt anything, and it just might work!

PEACE!

---

### Post by Tableleg on 2006-08-30
I am proud to say that I'm typing this in Dapper! I origionally downloaded the 6.06.1 cd version and was getting the freezing thing. So I thought I'd try the DVD version to see if there was anything different about it. Well (3.2 gigs latter... :D ) the first install option did the same thing to me! But the DVD version has different install options. 

So I tried the text-only install and it worked! Too bad I was doing other stuff while it installed and I forgot what my user name and/or password was... ](*,) 

So I install it again. And this time it didn't want to install right (I ended up trying about 5 times)... and it seemed that every other try, something else didn't want to work...  but finally, success!

This might be due to the old hardware I'm using as my test bed but the fact that the DVD version has the different install options (text and OEM are the other two that I can remember) it's worth a try downloading. It only took me 2.5 hours, but the rest of you might not be so lucky to have the fastest interenet available in your area.;)

---

### Post by fireboxtester on 2006-09-02
> **pjwigan said:**
> Fixed.

I swapped the original IDE DVD drive for a SATA one, and presto, Ubuntu installs :-)

Losing the IDE devices after the kernel has loaded appears to be a common problem with Intel P965 based motherboards.  There is no IDE support in the P965, so motherboard makers are rolling their own.

I made a wiki page to put all of the information about this issue in one place:
[https://wiki.ubuntu.com/Core_2_Duo_Support](https://wiki.ubuntu.com/Core_2_Duo_Support)

As you can see it's a pretty major issue.  There are already 3 bugs and at least 9 forum threads regarding this.  Hopefully we can get this fixed for Edgy.  (I'm going to test Knot 2 later tonight)

---

### Post by fortytwo on 2006-09-02
> **pjwigan said:**
> Fixed.

I swapped the original IDE DVD drive for a SATA one, and presto, Ubuntu installs :-)

Losing the IDE devices after the kernel has loaded appears to be a common problem with Intel P965 based motherboards.  There is no IDE support in the P965, so motherboard makers are rolling their own.

This seems to be the exact problem I'm having.  Has anyone had something similar to this?  Fixed by using a different kernel?  Different distro?  Curious if anyone has had success using only IDE harddrives/cd-roms with a P-965 board.

Thanks

---

### Post by onioneater36 on 2006-09-04
Put me down as someone who had the same problem.

Disable Legacy USB in the BIOS worked for me.  This is the 2nd time I have had to do this.  When I first got my rig (see sig), I ran MemTest86 and it bombed on tests 6 thru 10.  Disable Legacy USB fixed that problem too.  Having learned that was FALSE ERRROR reports on MemTest86, I re-enabled Legacy USB after MemTest tested OK.  I will NOT re-enable this &!@#^$(*& feature again as this is the 2nd large headache it has caused me.  Either ASUS needs to fix this in the BIOS, or programmers have to figure out what libraries have incompatibilites with this issue and tackle it.

---

### Post by Beomagi on 2006-09-06
Add me to the list - msi s271 laptop
tried disabling legacy usb through bios - didn't help.

s271 is based on turion x2, ati IGP 1150 northbridge/gpu, ddr2 - newer socket s1 for ddr2 mem.

any other hardware info needed?

I'm gonna try other distros to see if my pc can run linux at all. was hoping for dapper cause i've heard of it's xgl installation being "easier" than most.

---

### Post by Beomagi on 2006-09-07
suse had the same problem, but had the option of installing with acpi turned off - THAT worked.

---

### Post by lsoderman on 2006-09-10
Was having same issue. I reburned the CD at a much lower speed (4x) and it got past the freeze-up location without a hitch. 

Now I'm installing, and it looks like it's doing the partitions.

**UPDATE** I may have jumped the gun. Got to the partitioning/formatting, and it seems to have locked up. Grr.

---

### Post by blx_286 on 2006-09-15
Guess I need to add myself to this list. I have tried everything listed in this thread and my box still dies during the install.

Uncompressing Linux ... Ok, booting the kernel

[179571-432000] .. MP-BIOS bug : 8254 Timer no connected to IO-APIC

Here are the specs on the box:

Compaq Proliant ML750
PIII 700Mhtz Zeon (has 4 of 8 CPU's installed)
2GB RAM
18.0GB Drives x 10 drives setup RAID 5
These are SCSI drives on a Compaq Smart Array 4250ES Controller

The only BIOS options this box has that refer to APIC are in the MPS Table Mode section. Here are the options to set:

Full Table APIC
Full Table Mapped
Disabled
Auto Set Table

The only option I have not tried is the Auto set Table.

Anyway, thought I would throw this out here. I sure did want to make use of this older hardware. ](*,)

---

### Post by jrjazzman on 2006-09-15
I had this problem when instaling from a CD-RW.  I burned to a plain ol' CD-R and everything booted and installed fine.

---

### Post by The Aa of Ron on 2006-09-15
I guess I should join the party.  Same problem: "Kernel Loading" is where it seems to stop.

Equipment:
Brand new Intel DG965SS Motherboard with 2 gigs of Crucial RAM.
Intel Core 2 Duo 6300
Seagate 160gig SATA
NEC 16x DVD burner (ATA)

Motherboard bios updated.

I've now attempted to load Ubuntu 64-bit desktop, Ubuntu 32-bit desktop, Suse 64-bit, Fedora Core 5 64-bit, Debian of many flavors, and Gentoo (and maybe one or two others that I forgot).  NONE OF THEM WOULD LOAD.  This indicates to me that this is not Ubuntu, but a Linux kernel problem.  

Interestingly, the different flavors of Linux gave different levels of feedback on the problem.  One of them continually claimed that there was no bootable device which resonates with the claim in this thread that some Intel boards have the ATA control fall off after kernel load.  I _may_ try a SATA DVD burner.  I'll report back on any success that I may have with that.  Other versions stopped with a message that seemed to indicate it was probing the PCI bus.  But none of them worked which really bums me out.  I just bought all this equipment with the intent of having a fast Linux-only box.  ](*,) 

Incidentally, I have verified the proper operation of my machine by loading Win2k.  And it worked.  But I don't want to run Windows!  _I want to run Linux!_


I'll post more to let you know how my personal battle with this mystery works out.

---

### Post by ramdisk on 2006-09-16
I found a solution to the problem... I upgraded my kernel to 2.6.17 and it solved the problem on my Proliant ML-310  ( ML310 )

step by step kernel upgrade procedure here:: 

[http://ubuntuforums.org/showthread.php?t=217657](http://ubuntuforums.org/showthread.php?t=217657)

---

### Post by The Aa of Ron on 2006-09-16
This may be a solution for an upgrade problem, but I (and others who have posted in this thread) are having trouble getting it to install at all.

Please correct me if I'm wrong, but you have to at least have a kernel up and running to perform the steps outlined.

On the other hand, it does give more credence to the idea that this is not an Ubuntu problem, but a linux kernel problem.#-o 

Will the next ubuntu release have an upgraded kernel?

---

### Post by Dr. Dweebis on 2006-09-19
I have just about the same system/same problem - have you gotten it resolved?

Thanks 


> **N!zzo said:**
> Im having the same problem.

Is there a way to install ubuntu with an earlier version of the kernel? and would my problem be because of a SATA hdd on my computer, with this current kernel?

specs:
ASUS P5LD2 mobo
Intel Pentium D 3GHz
DDRII RAM 2G
WD 160G SATAII
Sony DVD drive
BenQ DVD burner

---

### Post by The Aa of Ron on 2006-09-24
Okay.  Update on my progress.  I tried installing a SATA DVD drive.  That appears to have solved some of my trouble, but now it stops at the step where it tries to start X.  It seems that so much is new on this latest Intel board that Linux just doesn't have the drivers yet.  (this board, the DG965SS, has Intel's latest video driver, the graphics accelerator X3000 or something like that.)

I may just wait for a while and play with the installed Windows Vista.  I'm tired of fighting with this install.

---

### Post by Robbyx on 2006-09-26
What  I do not understand is why it is not possible to put the installation disk onto the HD and install from a partition.

I happen to have a second HD which I hope to use as a raid disk.  I could use it to install if  I knew how. Does anyone know how to install other than from the DVD?

Robin

---

### Post by jetty on 2006-10-01
I had the same problem and got the CD to boot and run by disabling USB Legacy support in the BIOS. I'm using an ASUS A8N32SLI Deluxe motherboard with SATA RAID drives--works fine in Windows XP.

---

### Post by Robbyx on 2006-10-01
Unfortunately it did not work for me.

Robin

---

### Post by Patrick-Ruff on 2006-10-07
wow I never thought this thread would become soo popular.

ok well first off, the main basis of such problems is the Unable to mount root, most often.  the problem is caused by your hard drives name and your boot file directing it to mount to a hard drive that doesn't exist...so with such information, play around with it and get the right hard drive and it should mount ok, but for other problems not relative to this one, I don't know the solution.


good luck

---

### Post by soyamilk on 2007-09-25
Hi,

I have the same problem. Can't install Ubuntu on my laptop. Tried everything suggested here, but nothing worked. 

Is it an Ubuntu version bug, or should I try something else to do with my machine config?

---

### Post by nyomplong on 2007-10-07
The same issue come to my machine, "freeze at booting kernel". Still have to find the easy way to solve. 

But, i tried to install Ubuntu 6.0 Desktop the problem can be solved with adding acpi=off. 
Try to install Ubuntu 6.06 Server the problem still the same. 
Maybe have to download another installation. But still want to know where exactly the problem.

---

