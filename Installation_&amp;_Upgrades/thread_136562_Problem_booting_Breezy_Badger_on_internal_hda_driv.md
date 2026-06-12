---
title: "Problem booting Breezy Badger on internal hda drive."
date: 2006-02-26
forum: Installation &amp; Upgrades
---

### Post by Escar on 2006-02-26
Hi.

I've just spent two days googling and browsing through various forums, looking for an answer to my problem. No luck. Maybe that's because I left "linux world" something like 8 years ago and now, upon returning, I'm a total greenhorn. :|

Problem description:
I install Breezy 5.10 from the latest iso (downloaded two days ago, kernel 2.6.12 if memory serves me right). Sometimes instalation goes fine (I did a couple reinstalls since the first attempt), sometimes it sort of hangs (just the background, when I hit ctrl-alt-del it sends a sigterm and reboots), sometimes LILO or GRUB refuse to install.

However when I make a standard install (just press enter), whole instalation process goes ok. Only thing that requires some thinking is the partitioning part. Since the first attempt I've tried following HDD configurations (note: I install Ubuntu on a separate 30 GB ATA/133 HDD):
Ubuntu HDD as secondary master with DVD as primary master + 2xSATA RAID 0 (Windows)
Ubuntu HDD as primary master with DVD as secondary master + 2xSATA RAID 0 (Windows)
Ubuntu HDD as primary master with DVD as secondary master (sata's disconnected)
Ubuntu HDD as sec mast with DVD as pri master (sata's disconnected)

I've tried various instalations on the above stated configurations. Some didn't go all the way, but all standard ones did, with GRUB installed without any problem. I've tested both erease whole disc:
- everything on one partition,
- desktop computer (where you have separate /home)

and

erase whole disc and use LVM:
- everyting on one,
- desktop putter.

I also tried some other partition configurations, mainly ext3 cat / active, swap swap, ext3 /home.

Regardles of the configuration used, after reboot GRUB starts, system starts to load, I get a splash screen for ~5 s with "loading modules" line which in a blink of an eye turns status to "ok", then two other lines appear (too fast to read) and then I get dropped to shell with info:
ALERT! /dev/hda1 does not exist. Dropping to a shell! 

When drive is connected as sec master and I make a reinstall I get:
ALERT! /dev/hdc1 does not exist. Dropping to a shell! 

When I use LVM... I get all sorts of other, more verbose communicae (informing that the system can't even access the DVD).

When sometimes GRUB or LILO refuse to install during installation, after reboot I get info about GRUB error number 15.

After some reading I've tried other options available to me in GRUB. Then I tried editing the standard options to try to boot from hda0 to hda6. Every time the dev does not exist.

When I type in "mount" in the shell I get dropped to I get following info:
sysfs on /sys type sysfs (rw)
iproc on /proc type proc (rw, nudiratima)
none on /dev type ramfs (rw)

I've read some more and tried to get a newer kernel by:
sudo apt-get --reinstall install linux-image-26.15-15-686 initranfs-tools

but the shell tells me that sudo is not there.

I've tried looking at fstab. When I boot from CD in rescue mode I can use "nano" but the fstab I see then doesn't resemble anything in the posts I've read. When I try to use nano in the shell I'm being dropped after unsuccessful boot I get info that there's no "nano" and when I cd to /etc and ls contents I see only two files there.

So basically, after most typical install with ereasing whole disc and allowing the install to make two partitions there (/ and swap) I get the splash screen for a couple of seconds and then info about dropping to shell because of the hda1 missing. While trying to boot in rescue mode I also noticed some error messages regarding failed access to the SATA RAID.

I've tried reruning the install couple of times in expert mode, checking the partitions if they exist. They do. I can even verify this from under windows, although of course I can't acess the contents.

I have ubuntu-5.10-install-amd64.iso.

My system specs are as follows:
AMD Athlon 64 3200+ (Socket 939) Venice (0.09 technology) 2000 MHz 512 kb cache L2 128 bit memory controler
Asus A8N-SLI-EAYZ Socket 939 (AMD Athlon 64) nForce4 SLI DualChannel nForce RAID Realtek ALC850 8CH Gigabit Ethernet Motherboard 200&400 MHz FSB
1024 MB (2x512MB) DDR PC-400 KingMax CL 2.5 RAM 200&400 MHz DualChannel @ 128 bit
Gigabyte GV-NX66128DP nVidia GeForce 6600 DX9.0c Vertex Shader 3.0 256 bit GPU@450MHz 128MB@500MHz (128-bit) TV/DVI (PCI-E x16)
AG Neovo F-417 Black LCD @ 1280&1024 72 Hz
nForce4 RAID0 128 KB cluster (200 MB/s average throughput ) / 2x  Maxtor DiamondMax 9 Plus 120 GB (228 GB useable total) 7200 RPM SATA-150 / NTFSx1 partition (boot)
1xMaxtor DiamondMax Plus 8 30 GB 7200 RPM ATA-133 / Ubuntu (hopefully)
Mint CMI87836 6CH & Dolby Digital Creative SoundWorks SBS-560 5.1 BOX 
XPower 4944 PC case / 400 W GPS-400AA-101A ChieftecPSU


I've read a very long thread here about a similar problem, but concerning booting from USB drive. Unfortunatelly, either because of my lack of skills in the matter or because it considers a slightly diffrent topic, I wasn't able to devise a way to find a cure for my problem. Especially since, when I boot from CD in rescue mode, I can't mount any partition (I get info about the mount operation failed).

If anyone knows the solution or could point me to a how-to written in a language comprehensible by a newbie, I'd be grateful. :) Especially since the other system I'm considering for my desktop ([ftp://ftp.man.poznan.pl/pub/linux/suse/i386/10.0/iso/SUSE-10.0-EvalDVD-x86_64-GM.iso](ftp://ftp.man.poznan.pl/pub/linux/suse/i386/10.0/iso/SUSE-10.0-EvalDVD-x86_64-GM.iso)) is still 14hrs away from download completion. :|

EDIT:
I also tried turning of APIC in BIOS, because some ppl suggested that this might solve the problem, but it didn't. I have one of the latest BIOS's versions from ASUS. Mine is 013 and the newest one is 014 AFAIK. The only changes between them are the lists of supported CPU types, so I don't suppose switching to 014 will do any good.

---

### Post by DaBruGo on 2006-02-27
[QUOTE=Escar]Hi.
(note: I install Ubuntu on a separate 30 GB ATA/133 HDD):
[/QUOTE]

Escar,

I have a setup guide that you may be able to adapt to your situation (since you loaded Ubuntu on a separate drive).

Take a look at the link below in my signature lines.

Hope it helps,
DAVE

---

### Post by Escar on 2006-02-27
[QUOTE=DaBruGo]Escar,

I have a setup guide that you may be able to adapt to your situation (since you loaded Ubuntu on a separate drive).

Take a look at the link below in my signature lines.

Hope it helps,
DAVE[/QUOTE]

Hi. :) Thanks for Your reply.

I've seen your guide (seems like and awsome job. :) ). That's the guide I'm writing about in this part of my post:
> I've read a very long thread here about a similar problem, but concerning booting from USB drive. Unfortunatelly, either because of my lack of skills in the matter or because it considers a slightly diffrent topic, I wasn't able to devise a way to find a cure for my problem. Especially since, when I boot from CD in rescue mode, I can't mount any partition (I get info about the mount operation failed).


Either I'm too green and can't do it right, or my problem is too far away from that one.

When I wrote "separate" drive, I didn't mean "external drive". Just that I have a HDD which is dedicated solely to one Linux instalation. It's and internal ATA/133 drive with 30 GB space.

I tried using Your guide, but when I'm in rescue mode I can'y mount any of the partitions. I see two of them, but attempting to mount any of them brings up an error message.

At some point I even suspected that the disc may be faulty, but I formatted it under Windows to standard NTFS partition, copied stuff on it untill it was full and then copied stuff back. No errors.

Furthermore, when I type in "sudo", I get en error communicae which says that "sudo" is not there. Under shell which appears after a failed boot I can't even start nano. In rescue mode I can start nano, but the entries in the files are diffrent from the ones I saw in your thread. :(

I have no idea what's causing this problem. :| I tried Ubuntu, because a friend of mine advertised it as a distro with Debian stability, but a bit more user friendly. After three days of searching for the solution I'm thinking about giving up. My primary suspect is the mobo (nForce4 SLI). Is it possible that it's just too new for the Ubuntu to run on it??

Anyway, I downloaded latest free releases of Suse, Fedora and... Mandriva over the weekend. Hopefully one of these will work better. <fingers crossed>

---

### Post by Escar on 2006-02-28
Well, it's utterly weird. :|

I've downloaded latest Open.SuSe. It installed with just one glitch. I couldn't delete NTFS partition from the installer, so I had to go into Windows, delete the partition and run the installer again. Then it installed without a glitch. Everything was perfectly fine untill first boot attempt from hard drive. I went to detailed info and saw that system couldn't access my RAID (which is understandable, since in kernel 2.6 programable RAIDs are not supported) and had some problem with ACPI, but two bottom lines in shell stated that system couldn't find dev/hda1 and dev/hda3. I've formatted drive to 1 GB swap, 22 GB / and the rest  to FAT32 (to have a space through which I could copy files from one system to another, since this kernel can't access my RAIDed drives).

But this was all for nothing, since Suse, just like Ubuntu, can't see those partitions. And they are on a HDD connected simply as primary master ATA.

What can be the problem? :( I'm really saddened by this, because I wanted to go back to Linux over all these years and give it another try. And if both Suse and Ubuntu show the same problem, I'm fairly certain that Fedora and Mandriva (which I also downloaded), won't boot either.

Anyone, with a hardware config similar to mine... any advice? I don't even have an idea where to start looking for answers. Should I disable ACPI in BIOS and try to install with no ACPI support??

ps:
The FAT32 partition on the 30 GB HDD is visible under Windows, so it seems that formatting the HDD goes ok and partitions are there. Volume manager in Windows also reports 3 pratitions on the hard drive.

Thanks for any help, ppl. :)

---

