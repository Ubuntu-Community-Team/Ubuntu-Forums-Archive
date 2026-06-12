---
title: "grub in root part"
date: 2011-08-19
forum: Installation &amp; Upgrades
---

### Post by ottosykora on 2011-08-19
I have just one question to grub gurus:

I need to have the grub in the root partition, as I either use third party boot manager (mostly) or separate grub partition and then all linux roots have to have something boot with.

When I did some recent installs, the grub2 displayed messages that it should definitely not be installed into root partition.
I dont recall where from I got the info (probably also from some grub2 readme or those warnings displayed by it) to use grub legacy instead.

Does anyone know the background to it and what make the problem for grub2 to live in root partition?

Are there any background infos to this?



I just think if the devs themselves put such warning into the grub installer, they know about some particular problems with it.

I found one time a serious problem with it, it did not survive some upgrade procedure.
From there on, I keep replacing in such situations the grub2 with grub legacy and this works stable and never had any problems.

---

### Post by dino99 on 2011-08-19
so which installed grub it is ? which ubuntu ?

using grub2 (grub-pc): remove menu.lst & grub legacy (grub) then:

sudo dpkg-reconfigure grub-pc
should be installed in root (/dev/sdx, x=a->z) (not sdxx)

uptodate grub link below

---

### Post by YesWeCan on 2011-08-19
> Does anyone know the background to it and what make the problem for grub2 to live in root partition?
I would not call myself a Grub guru but I know a thing or two about it.

Windows can be chain-loaded from a partition boot record so why can't Ubuntu/Grub?

Technically, I assume that in the Windows partition the boot program can be kept at a fixed location so the PBR (partition boot record) boot code, which is very primitive, can always find it in the same place. I can only assume this is not possible with the current design of the linux file system OR the Grub designers chose not implement it. The upshot is that if you install Grub's boot code to a PBR it will work at first but eventually the file system manager will move and/or change the block fragmentation of the boot program thus rendering the boot program unloadable.

I imagine the original Grub developers could have:
1) Worked with the linux filesystem developers to fix the problem.
2) Avoided the problem by installing Grub's PBR code and its boot program to a dedicated partition without a file system.
3) Avoided the problem by installing Grub's PBR code and its boot program to the only location on disk without any partitions or filesystems: the MBR area.

They chose 3. Of course, the trouble is that this trashes the BIOS/MBR system and causes serious conflicts with Windows which is MBR compliant, and other programs that nefariously use the "unused" area between the MBR and 1st partition start.

So why didn't they implement 2? Ironically, they now have but only for GPT disks! Grub can be installed to a special "BIOS boot" partition and chain-loaded. Why did they do this...out of necessity: there is no "unused" area at the start of a GPT formatted disk. So the PBR boot has been implemented for GPT (which is not really supposed to be BIOS booted anyway) and not for MBR where it is really needed.

An MBR disk can have Ubuntu and Grub installed in a reliable, PBR chain-loadable arrangement. I have implemented this. But it is not supported by the existing installation tools.

> Are there any background infos to this?
Almost nothing that I have found.

---

### Post by ottosykora on 2011-08-19
Ok, fine, I was just curious if some knows any reason. The reason given by you sound plausible, as yes, things may go moved in files system. But after all most of the files making grub are stored in the actual files system, except the initial MBR sequence anyway. So this would particularly be concern for the 512b of the boot record itself.
But any way, even in this case,  could make sense.

But on the other hand, this does concern the legacy grub too, so if I install the legacy grub to PBR, simply just to be able to boot linux at all, this seemed to me to be no problem to lave there the currently standard grub2, but the build in warnings coming from the devs of the grub2, make me to replace that one after each installation with legacy grub.

As I said I need some boot loader in the partition. Sure is grub an overkill for just that. Could use Lilo as well, but this gets complicated if one forgets to update it after a kernel update.
 
So I am keeping to have legacy grub in the PBR for the time being to avoid any problems , but I have so far not much idea as of what problems are to be expected.

---

### Post by ottosykora on 2011-08-19
>so which installed grub it is ? which ubuntu ?
<

well it is concerning any linux and it is the Q why the devs of grub2 have build in the warning that grub2 should *not* be installed in PRB.

---

### Post by YesWeCan on 2011-08-19
I don't know how Grub legacy differs from Grub2 with regard to PBR booting. I'm inclined to think it will have exactly the same problem but I don't know.

---

### Post by dino99 on 2011-08-19
> **ottosykora said:**
> >so which installed grub it is ? which ubuntu ?
<

well it is concerning any linux and it is the Q why the devs of grub2 have build in the warning that grub2 should *not* be installed in PRB.

might be some red hairing left behind while versioning upgrades

---

### Post by YesWeCan on 2011-08-19
> **ottosykora said:**
> I need to have the grub in the root partition, as I either use third party boot manager (mostly) or separate grub partition and then all linux roots have to have something boot with.
What you can do is to install Grub to the MBR area as usual. But then copy the Grub MBR boot code (bytes 0 to 445 in sector 0) to a PBR, leaving the Grub boot program in the 50 or so sectors after the MBR. When you chain-load the PBR it will load the Grub program at sector 1. Then you can put back standard MBR boot code in sector 0.
Not advisable unless you know what you are doing; an error in copying could trash a partition.

---

### Post by YesWeCan on 2011-08-19
> **ottosykora said:**
> Ok, fine, I was just curious if some knows any reason. The reason given by you sound plausible, as yes, things may go moved in files system. But after all most of the files making grub are stored in the actual files system, except the initial MBR sequence anyway. So this would particularly be concern for the 512b of the boot record itself.
But any way, even in this case,  could make sense.

Not quite. Two files are installed to the MBR area. One is boot.img, the tiny 440 or so bytes of boot code, and this goes in the MBR sector just before the partition table. The other file is core.img which is about 50 sectors and is the main boot program and this is put just after the MBR. Core.img has enough code to be able to read a linux file system so it can find other Grub files in /boot/grub even if they move.


So you might ask...why don't they do the same thing in a PBR area? Well, the ext file system format only leaves 1 unused sector of space after the PBR sector. There isn't room for core.img. So they leave core.img in the main file system and put boot.img in the PBR with a pointer to it. But the core.img file will get moved and the pointer will be wrong. This is why the grub-install command refuses to istall to PBR unless forced.

Presumably, the ext file format does not support "immovable" files otherwise there wouldn't be a problem.

---

### Post by ottosykora on 2011-08-19
hmm, yes true , so what would be the proper thing to load linux? Lilo? Or otherwise what?

---

### Post by oldfred on 2011-08-19
So what boot loader are you usinig?

I originally chain booted everything and had a grub legacy partition just for booting. I installed the first grub2 into a partition and it worked fine for the time I had it there. But the grub2 code is larger and has to convert to using blocklists or hard coded addresses to link to files. If files get moved on a grub update then the blocklist address will be wrong & you have to reinstall grub to the partition to fix it. 

But you can boot several different ways from grub2 or grub legacy.

I boot many of my test Ubuntu installs by partition (the links in / that Ubuntu updates on kernel changes), so I get the newest kernel with out having to reboot into my main install to update it when the test install needs a reboot after a kernel update.

---

### Post by srs5694 on 2011-08-19
I have a few comments:


[list]
[*]From a practical perspective, oldfred's question of what boot loader you're using in the MBR is quite relevant, as is the question of why you want to use it. It could be that there's a better way to accomplish your goals than whatever you're doing now, so understanding what it is you're doing now and what you want to accomplish is necessary to move beyond a theoretical discussion or discussion of hypothetical scenarios that might or might not be relevant to you specifically.
[*]Several other Linux boot loaders for BIOS-based computers are available and might suit your needs better than GRUB 2. These include:

[list]
[*][LILO](http://freshmeat.net/projects/lilo/) -- One of the oldest and simplest Linux boot loaders. Still usable, but not very popular any more.
[*][GRUB Legacy](http://www.gnu.org/software/grub/) -- Simpler than GRUB 2 and used by many distributions other than Ubuntu.
[*][Syslinux](http://syslinux.zytor.com) -- This is actually a family of boot loaders that are installed in various places (MBR, FAT boot sector, ext2/3/4 boot sector, etc.).
[*][LOADLIN.EXE](http://youpibouh.thefreecat.org/loadlin/) -- This is a DOS program that loads Linux. Today it's a bit of a relic, but it's still useful in some situations.
[/list]

[*]Computers based on [UEFI](http://en.wikipedia.org/wiki/Uefi) rather than a traditional BIOS can boot in an entirely different way that requires entirely different boot loaders. UEFI booting does away with the code that's resident in the MBR, and normally code in partitions' boot sectors, too. Instead, boot loaders exist as EFI applications in a special partition, the EFI System Partition (ESP), so you can install, uninstall, and manipulate your boot loaders the way you do other programs. Many of the newest computers today use UEFI, so it's conceivable you can use it already. Whether this would be beneficial to you specifically depends on your specific needs and priorities.
[/list]

---

### Post by ottosykora on 2011-08-20
well so far I still use the traditional computer with MBR and what ever comes with it.

As I have more then one computer , I have also some different boot managers in use.
The MBR poits to a boot manager which is in some cases bootmagic, some cases acronis boot manger and in some cases legacy grub.

In the case where I have legacy grub in MBR, it is then having its rest in a own partition and then every os has its own bootloader in PBR. This mainly because on this particular system 6 os are on one hard disk, so this makes more managable .

So we can say , that in any case, I have not a grub system which does start in MBR and ends up in one of the actual / of any of the os.

So all os (not only linux) have their own loaders, in case of linux I try to keep them all legacy grub due to the warning included in the grub2 itself. It is some work with it to replace the grub2 by legacy grub, but I try to do it because of this warning in grub2.

The reason, that if some files of grub get moved, then the whole thing may stop work is plausible and it may well be, that the warning inside the grub installer is placed exactly because of this.

But then again, replacing it with legacy grub is not so much better, apart from the fact that legacy grub is smaller in size, thus chances something gets move are less.
This may be only key fact why it may be preferred in such set up.
(had never any drop out myself in fact)  
So far I also installed all linux, even the latest 11.04 into a ext3. Due to absence of any defrag , files are not moved unless the disk ist somehow full or so, therefore it probably works so far.

As far as I can see it , there is very little alternative to boot linux from its partition (PBR) as Lilo is also tricky in some way and needs to be reconfigured after every kernel update.


I have no idea how to employ syslinux in such scenario, but could this be really an alternative?

Is it worth to experiment with it? Will it reside inside some ext partition or does it need an extra vfat place to live in?

Has someone done this?

---

### Post by ottosykora on 2011-08-20
OK have seen on the syslinux website, they have something called extlinux , so will try to read what it is about and if this is a solution to this not so urgent problem.

---

### Post by Quackers on 2011-08-20
You can install grub2 to the root partition of your system although it is not recommended and it warns you of this at the time of installation.
There are several forum members here who use grub2 in this way.

The problem is that some updates can break grub2's operation when installed in this way, as files can get moved about.

I would point out though that it is likely that grub2 once installed to the mbr of the boot drive, would boot all of your operating systems, dispensing with the need for a separate boot manager.

---

### Post by oldfred on 2011-08-20
I used to chainboot everything, but since I primary boot one Ubuntu version, I have it's grub2 in the MBR and manually add entries for the other system into 40_custom just like I used to do to edit menu.lst.

I also have a flash drive with just grub2 installed. It does not have any system and will not create any grub.cfg. I totally manually maintain it and it is just like maintaining menu.lst was with grub legacy. And I still use chainload to load anything that is chainloadable or grub2 partition entries for Debian based systems that have a link in root to the latest kernel.

If you want lots of examples I can post them.

This is one chain load example with grub2 formating:

menuentry "Chainload Other Systems Grub Menu on sdc1" {
set root=(hd2,1)
chainloader +1
}

---

### Post by ottosykora on 2011-08-22
well the thing is that I use other boot manager . particularly because it is more simple and reliable, can be installed and uninstalled with a mouse click. On older systems boot magic from power quest, on current systems acronis. 

This whole chainloding is nice , but one has to remamber where all is stored, if more then one linux is on the drive.
So where I use more then one linux, I have separate grub partition. But then I am back to similar problem: I have to have something in each linux root partition to load the linux. 
Installing any current ubuntu for example, will install grub2 into the PBR as nothing else is available as standard. And this has all the described problem with files moving etc.
Installing 'nothing' (if this possible at all) or removing grub2 will also make it impossible to chainload it unless some other thing as lilo is present.

So the Q would be what to install into partitions which are supposed to be chainloaded and do contain linux.

I do not recall any option in any installer of linux where I can select that only the last files of a grub should go to partition .
The selection is to install whole grub into the partition or mbr. Nothing between.

So when installing let say ubuntu, I can only select to install the whole grub to the partition, which will lead to the problems if parts of it are moved. Experienced myself already.

So it looks like the grub is operational only when in mbr and even when installed in separate grub partition it still needs other grub in the root partition and so we back to square.

BTW: what is this VLM or what do they call it. Seems somethig Fedora is promoting. Is this proper boot manager?

---

### Post by Luke M on 2011-08-22
> **srs5694 said:**
> [GRUB Legacy]("http://www.gnu.org/software/grub/") -- Simpler than GRUB 2 and used by many distributions other than Ubuntu.

 Something to be aware of with grub1: it doesn't support drives larger than 1TB (i.e. will fail if any boot files are located above 1TB) due to using 32-bit signed integers for sector numbers (grub2 uses 64-bit unsigned).

---

### Post by Luke M on 2011-08-22
> **YesWeCan said:**
> What you can do is to install Grub to the MBR area as usual. But then copy the Grub MBR boot code (bytes 0 to 445 in sector 0) to a PBR, leaving the Grub boot program in the 50 or so sectors after the MBR. When you chain-load the PBR it will load the Grub program at sector 1. Then you can put back standard MBR boot code in sector 0.
Not advisable unless you know what you are doing; an error in copying could trash a partition.

 Yes, I've done this and it works fine. I can also boot grub2 from Windows XP boot loader by placing the grub2 boot sector in a file and adding c:\file="Grub" to boot.ini.  Further, if you have extra room (e.g. if your first partition starts at sector 2048 rather than 63), you can place core.img somewhere other than sector 1. This requires manually changing the sector number in the boot sector to point to the chosen location.  Lots of options. :-)

---

### Post by YesWeCan on 2011-08-22
> **Luke M said:**
> Yes, I've done this and it works fine. I can also boot grub2 from Windows XP boot loader by placing the grub2 boot sector in a file and adding c:\file="Grub" to boot.ini.  Further, if you have extra room (e.g. if your first partition starts at sector 2048 rather than 63), you can place core.img somewhere other than sector 1. This requires manually changing the sector number in the boot sector to point to the chosen location.  Lots of options. :-)
Thats a good idea. I think for same drive dual boots with Windows it is much better (especially for people new to linux) to leave the MBR alone and boot Ubuntu from the Windows bootloader. Unfortunately, the Ubuntu installer doesnt care about Windows users.
The other method I use is to make all Ubuntu partitions logical and embed Grub in the extended partition.

---

### Post by ottosykora on 2011-08-22
>The other method I use is to make all Ubuntu partitions logical and embed Grub in the extended partition.<

hmm, this is is interesting idea, never thought of it.

How do you do this?

Wher I see the problem, is how do one install something like ubuntu with just the last part of grub in the partition? The installer has no option for such things either.

Let say even in the case I use separate grub partition, the mbr is pointed to it and from there the other linux systems are booted.
One has still to have something inside the actual partition of that linux partition to be able to start it.

I know that we can load it via XP boot (very convenient) and also w7 can do all that, but it will all still need something in the root partition to start somehow. 

So when I install ubuntu with the option 'bootmanager to root partition' is there something later I could delete so it does not break when incidently moved around?

Imagine:
grub in mbr, its second part in extra partition (logical volume)
here the menu is configured by hand if needed

and it starts from there

7 different os , inclusive 4 linux distros

The other 3 os are MS versions, so they have some bootloader on board which does not break during updates, defrags etc.

now what exactly do I put into the partitions (all logical)with the linux distros in it so it does not break during updates etc by moving parts of it.
Not installing anything does not work, as grub will find such partition a dummy data aprtition and try to boot from it.

Linux installers currently have only option to install full grub into the PBR/root partition.

I have no idea if the thing Fedora is promoting does something else/more or better, but the last fedora version I installed, also offered only to install full grub into PBR/root and nothing else.

So which part of the grub should I copy where to make system resistent against break after updates etc?


Clear, the placing the grub in mbr first, then copying only the mbr to pbr , then replace the mbr with some generic or original mbr will probably work, thought I am not sure then how it will work as generic mbr might not look for further files just before the partition table.
But this is very complex operation and smallest mistake will make the whole system unbootable.

---

### Post by YesWeCan on 2011-08-22
I assume that the Windows file systems have the built-in facility to store non-movable files, possibly non-fragmentable. I assume this is how PBR booting can work reliably. I have to do some research to confirm that, but that's what I imagine. Either that or you can leave enough space before the fs start to embed a boot loader.

The linux file systems (which are inherited from UNIX - probably the root cause of this problem) presumably do not. Again, I don't know for sure but I can only infer it from the unexpected symptom that no linux OSs that I am aware of are IBM MBR boot system compliant, even though linux is meant to be UNIX for the IBM PC.

So if those are true, it makes me wonder whether a practical approach would be to install Grub to a dedicated partition in NTFS format and make the core.img file unmovable; I suppose it would be installed as a "hidden system" file or something. I'm just thinking out loud here but I may look into this further.

Of course this idea may be considered heresy by some linux purists - the notion that a Microsoft file system might be better in some way - shock horror! ;) :P

---

### Post by srs5694 on 2011-08-22
> **Luke M said:**
> [quote=srs5694][GRUB Legacy]("http://www.gnu.org/software/grub/") -- Simpler than GRUB 2 and used by many distributions other than Ubuntu.Something to be aware of with grub1: it doesn't support drives larger than 1TB (i.e. will fail if any boot files are located above 1TB) due to using 32-bit signed integers for sector numbers (grub2 uses 64-bit unsigned).[/QUOTE]

A 32-bit pointer to 512-byte sectors works out to a 2 TiB (2 x 2^40 bytes) limit, not 1 TB (10^12 bytes). This is the source of MBR's limit of 2 TiB on most hard disks, since the partitions are defined by means of 32-bit sector pointers. That said, it's conceivable that the GRUB Legacy code uses *signed* 32-bit integers somewhere, which would effectively halve the range to 1 TiB. I've not looked into this detail, though.

In any event, I've seen claims of a [BIOS-based 2 TiB boot limit](http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/2tib-disc-limit.html#BIOSParameterBlockLimit) that affects all boot loaders for BIOS-based computers. I've done a few small tests in a VirtualBox "computer," and I was unable to get GRUB 2 to boot a Linux kernel that was stored above the 2 TiB mark, which tends to support these claims; however, it could be that VirtualBox's BIOS implementation is outmoded. I don't yet have any physical disks larger than 2 TiB, so I can't test this with my "real" computers.

---

### Post by oldfred on 2011-08-22
You really only need one full install of grub2. You then can use that to chain load to your other installs whether grub or grub2. I recommend installing grub legacy to the PBR so you can use chain loading but do not have to.

menuentry "Chainload Other Systems Grub Menu on sdc1" {
set root=(hd2,1)
chainloader +1
}

This is a boot to a partition of another install (from Ranchhand):

menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

Grub to grub2:

root (hdX,Y)
kernel /boot/grub/core.img
boot

I also created a USB boot of a win7 repairCD (FAT32) and overwrote the windows boot loader with grub2. Then created a chain load entry to the windows PBR and it still boots the win repair. I have grub2 installed in FAT32, NTFS & Linux file systems.

---

### Post by ottosykora on 2011-08-22
>I recommend installing grub legacy to the PBR so you can use chain loading but do not have to.
<

this is what I still do not understand.

If I do not install any bootloader into the partition, then how should the grub load that system?

I am probably not expressing myself well, but exactly at this point are all my questions.

I know I can chainload, but some kind of loader has to be installed in the partition, beside the pointer set to the actual kernel. Where to take such loader?


If I do not install any loader, even grub2 with its first part in mbr and second part in some other partition will not be able to boot such system.

Or is it just possible to copy some grub files there simply so grub where ever it is will be able to boot from it?


So far I did meet options either to install grub to mbr and rest to the partition of the /boot of the particular distro just installing, or to install the whole grub to the partition with the /boot so grub starts in PBR and ands in /boot folder.

---

### Post by ottosykora on 2011-08-22
@YesWeCan

well with the potential move of files, windows must be completely immune against that by design for historical resons. From DOS times, MS starts writing from the begining of the drive (volume) and when files are deleted or replaced all gets fragmented as we know and there are many utils to defrag it again thus all is moved very often.

I know ext4 can also be defraged somehow, but for ext2 and 3 this was not supposed to be done. They do write more less in the middle of the partition and leave enough space around fragments, so often changing files finds enough space around its original and nothing has to be moved.
But if the drive becomes full even here things can start move, and I assume this the case when big upgrade is done in a linux distro and then it comes to moving files incl grub parts and then we have hundreds of help requests in the forum...

---

### Post by oldfred on 2011-08-22
Grub2's os-prober looks for grub.cfg, menu.lst (grub legacy) or other  menus to build new grub2 entires. But it will directly boot many systems without using that system's grub. 

If you do not have an install with the full grub2, you can manually create grub.cfg and boot just about anything. While I install grub2's boot loader to a drive I boot with my sdb drive and directly boot other installs. I also can boot my installs with just the manually created entires I have in my grub.cfg on my flash drives.

We are discussing to many generalities, if you have specific examples from a bootscript report then we can show specifics.

---

### Post by YesWeCan on 2011-08-22
> **ottosykora said:**
> >If I do not install any bootloader into the partition, then how should the grub load that system?
A particular OS can be booted without having its own Grub files. It has vmlinuz and initrd files for booting. All (almost) Grub does is load and run those files.
So A Grub located somewhere else can scan a partition to find the boot files and be able to boot that OS.

---

### Post by YesWeCan on 2011-08-22
@oldfred
Do you know whether grub legacy can reliably boot when installed to PBR or not? I assume it also has to run a kernel image that cannot fit in the space between PBR and ext fs start.

Also, can you confirm whether FAT & NTFS cater for immovable/unfragmentable files?

---

### Post by oldfred on 2011-08-22
I used old grub legacy in PBRs for a while and many used it that way for quite a while. Grub legacy was a lot smaller as it did not support many newer systems. Ubuntu modified its version of grub legacy ( still 0.97) to allow ext4 partitions. But other distributions with grub legacy (0.97) may not work with ext4 for example.

chainboot 145 systems grub legacy - saikee
[http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)

Do not know about FAT or NTFS. Whenever you do a defrag it moves things around. 

My  NTFS windows partition boot sector has to have the correct code, starts & ends of partition (that are the same  as partition table), location of backup boot sector, and name of file to boot XP - ntldr & Vista/7 - bootmgr. There are also some other bits different between PBRs for XP & Vista/7, but I used win7 repairUSB to run chkdsk on my XP partition and it put a Vista/7 boot sector in and it still booted??

---

### Post by Luke M on 2011-08-22
> **srs5694 said:**
> A 32-bit pointer to 512-byte sectors works out to a 2 TiB (2 x 2^40 bytes) limit, not 1 TB (10^12 bytes). This is the source of MBR's limit of 2 TiB on most hard disks, since the partitions are defined by means of 32-bit sector pointers. That said, it's conceivable that the GRUB Legacy code uses *signed* 32-bit integers somewhere, which would effectively halve the range to 1 TiB. I've not looked into this detail, though.

In any event, I've seen claims of a [BIOS-based 2 TiB boot limit]("http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/2tib-disc-limit.html#BIOSParameterBlockLimit") that affects all boot loaders for BIOS-based computers. I've done a few small tests in a VirtualBox &quot;computer,&quot; and I was unable to get GRUB 2 to boot a Linux kernel that was stored above the 2 TiB mark, which tends to support these claims; however, it could be that VirtualBox's BIOS implementation is outmoded. I don't yet have any physical disks larger than 2 TiB, so I can't test this with my &quot;real&quot; computers.

 Grub1 uses signed ints everywhere, not just somewhere. And does things like "if sector < 0". Regarding >2TB drives, the LBA BIOS functions take a 64-bit sector number. It should work, but I haven't tried it either.

---

### Post by YesWeCan on 2011-08-22
> **oldfred said:**
> Do not know about FAT or NTFS. Whenever you do a defrag it moves things around. 

My  NTFS windows partition boot sector has to have the correct code, starts & ends of partition (that are the same  as partition table), location of backup boot sector, and name of file to boot XP - ntldr & Vista/7 - bootmgr. There are also some other bits different between PBRs for XP & Vista/7, but I used win7 repairUSB to run chkdsk on my XP partition and it put a Vista/7 boot sector in and it still booted??
It's hard to find any information online about how the PBR boot code works. It has to locate and load either NTLDR or BOOTMGR as you say. I want to determine whether it does this by using a fixed location or whether it reads the file system table of contents. It only has 440 bytes or so of code.

Disassemble this for me would you? :P
```
00000000  eb 58 90 4d 53 57 49 4e  34 2e 31 00 02 40 74 00  |.X.MSWIN4.1..@t.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  ff 5b 63 02 1b 13 00 00  00 00 00 00 02 00 00 00  |.[c.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 f3 16 61 14 4e  4f 20 4e 41 4d 45 20 20  |..)..a.NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 08  |{......|.N..V@..|
00000070  cd 13 73 05 b9 ff ff 8a  f1 66 0f b6 c6 40 66 0f  |..s......f...@f.|
00000080  b6 d1 80 e2 3f f7 e2 86  cd c0 ed 06 41 66 0f b7  |....?.......Af..|
00000090  c9 66 f7 e1 66 89 46 f8  83 7e 16 00 75 38 83 7e  |.f..f.F..~..u8.~|
000000a0  2a 00 77 32 66 8b 46 1c  66 83 c0 0c bb 00 80 b9  |*.w2f.F.f.......|
000000b0  01 00 e8 2b 00 e9 48 03  a0 fa 7d b4 7d 8b f0 ac  |...+..H...}.}...|
000000c0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|
000000d0  ee a0 fb 7d eb e5 a0 f9  7d eb e0 98 cd 16 cd 19  |...}....}.......|
000000e0  66 60 66 3b 46 f8 0f 82  4a 00 66 6a 00 66 50 06  |f`f;F...J.fj.fP.|
000000f0  53 66 68 10 00 01 00 80  7e 02 00 0f 85 20 00 b4  |Sfh.....~.... ..|
00000100  41 bb aa 55 8a 56 40 cd  13 0f 82 1c 00 81 fb 55  |A..U.V@........U|
00000110  aa 0f 85 14 00 f6 c1 01  0f 84 0d 00 fe 46 02 b4  |.............F..|
00000120  42 8a 56 40 8b f4 cd 13  b0 f9 66 58 66 58 66 58  |B.V@......fXfXfX|
00000130  66 58 eb 2a 66 33 d2 66  0f b7 4e 18 66 f7 f1 fe  |fX.*f3.f..N.f...|
00000140  c2 8a ca 66 8b d0 66 c1  ea 10 f7 76 1a 86 d6 8a  |...f..f....v....|
00000150  56 40 8a e8 c0 e4 06 0a  cc b8 01 02 cd 13 66 61  |V@............fa|
00000160  0f 82 54 ff 81 c3 00 02  66 40 49 0f 85 71 ff c3  |..T.....f@I..q..|
00000170  4e 54 4c 44 52 20 20 20  20 20 20 00 00 00 00 00  |NTLDR      .....|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 4e 54  |..............NT|
000001b0  4c 44 52 20 69 73 20 6d  69 73 73 69 6e 67 ff 0d  |LDR is missing..|
000001c0  0a 44 69 73 6b 20 65 72  72 6f 72 ff 0d 0a 50 72  |.Disk error...Pr|
000001d0  65 73 73 20 61 6e 79 20  6b 65 79 20 74 6f 20 72  |ess any key to r|
000001e0  65 73 74 61 72 74 0d 0a  00 00 00 00 00 00 00 00  |estart..........|
000001f0  00 00 00 00 00 00 00 00  00 ac bf cc 00 00 55 aa  |..............U.|
```

---

### Post by srs5694 on 2011-08-22
> **ottosykora said:**
> If I do not install any bootloader into the partition, then how should the grub load that system?

I am probably not expressing myself well, but exactly at this point are all my questions.

I know I can chainload, but some kind of loader has to be installed in the partition, beside the pointer set to the actual kernel. Where to take such loader?

I suspect you're suffering from a  subtle but fundamental misunderstanding of what's necessary in a boot loader. Expressed very broadly, what happens is:


[list=1]
[*]The computer's firmware loads code from the hard disk (or other disk -- CD-ROM, floppy, etc.).
[*]The code just loaded optionally loads additional boot loader code and perhaps configuration files from the disk. This process can repeat for several iterations, particularly if one boot loader chainloads another. Note that this step is *optional*.
[*]Ultimately, the boot loader code loads an OS kernel file, and optionally support files, and gives control to the OS kernel.
[/list]


In the case of GRUB 2 and Linux on a BIOS-based computer, step #1 usually involves code stored in the MBR, step #2 involves code stored in the officially-unallocated post-MBR sectors of an MBR disk, in a GPT disk's BIOS Boot Partition, and in the /boot/grub directory, and step #3 involves the Linux kernel and initial RAM disk files in /boot. There's nothing about this process that *requires* that a partition boot record (PBR) be involved. When booting Windows in a stock BIOS-based system, the PBR is normally involved just because that's the way Microsoft built their particular boot loader. The GRUB developers chose a different path, though. I don't know their exact reasoning, but in any event, GRUB doesn't necessarily tie its basic operation or its ability to boot to PBR-based code. Because Windows boots via a PBR-based boot loader and GRUB can't boot a Windows kernel directly, booting Windows via GRUB still involves chainloading a Windows partition's PBR. This need not be true of kernels that are more directly supported by GRUB 2, such as Linux or GNU HURD.

FWIW, most of what you know about how computers boot is about to change. The new [UEFI](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface) firmware is finally taking off, and one of its most important features, particularly from a user's perspective, is an entirely new boot system. Under UEFI, instead of loading the first sector of a hard disk (normally 512 bytes) and executing it as the first stage of the boot loader, the firmware looks for boot files on hard disk partition, known as the [EFI System Partition (ESP).](http://en.wikipedia.org/wiki/EFI_System_partition) In theory, this lets the firmware host a boot selector menu and each OS can drop an OS-specific boot loader in the ESP to have it added to the menu. In practice, unfortunately, most UEFI implementations provided pretty poor boot selector menus, so a lot of people set up GRUB 2, rEFIt, or some other boot loader that can present a good menu and use that menuing boot loader as the default boot loader. Even so, under UEFI you don't need to worry about what's in the MBR, and AFAIK no UEFI boot loader stores stuff in partitions' PBRs, either. Use of the MBR and the PBR was desirable 30 years ago because of code space limitations in the firmware. It's easy to tell the firmware to load sector 0 of a hard disk and execute it, and then have sufficient code in there to load the PBR of a partition and execute it, and then have that code load some other hard-coded set of sectors and execute them. UEFI is much bigger and much more capable, so it can understand FAT well enough to enable loading boot code by filename, which eliminates many of the problems with doing it in the BIOS way.

[quote=Luke M]Grub1 uses signed ints everywhere, not just somewhere. And does things  like "if sector < 0". Regarding >2TB drives, the LBA BIOS  functions take a 64-bit sector number. It should work, but I haven't  tried it either.[/quote]

I wasn't aware that GRUB Legacy used signed integers. That would certainly limit it to booting kernels from under the 1 TiB mark.

As to the LBA BIOS functions, they do use 64-bit numbers on modern BIOSes, but the point of the [article I referenced](http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/2tib-disc-limit.html#BIOSParameterBlockLimit) is that one key data structure, the BIOS parameter block, remains 32-bit and this limits the ability of a BIOS to boot anything from above this value in sectors. Apparently this is unlikely to change because the VBR is incorporated into many filesystems, so converting to a 64-bit VBR would require new filesystems. I know relatively little about this topic, though -- just what's written in the article to which I linked and the results of one test with a virtual machine in VirtualBox using GRUB 2. I was unable to boot from a Linux installation with a /boot partition above the 2 TiB mark in that test, but it worked fine when I moved that partition below the 2 TiB mark and re-installed GRUB 2. This tends to support the claims in the article, but of course there are other possible explanations, such as a filesystem-specific limit, a limit in the BIOS in VirtualBox, a bug in the specific version of GRUB 2 I used, or a flaw in my test procedure.

---

### Post by oldfred on 2011-08-22
@YesWeCan
You have FAT and I do not know all the details but hve some links. I think the starman site also has info on FAT.

Details on how NTFS works:
[http://technet.microsoft.com/en-us/library/cc781134%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/cc781134%28WS.10%29.aspx)
FAT
[http://support.microsoft.com/kb/140418](http://support.microsoft.com/kb/140418)
[http://thestarman.pcministry.com/asm/mbr/VistaVBR.htm](http://thestarman.pcministry.com/asm/mbr/VistaVBR.htm)
[http://mirror.href.com/thestarman/asm/mbr/MSWIN41.htm](http://mirror.href.com/thestarman/asm/mbr/MSWIN41.htm)
Boot sector - Bootable partition that stores information about the layout of the volume and the file system structures, as well as the boot code that loads Ntdlr (XP).  
BIOS >> MBR >> Boot Sector >> the NT Loader (NTLDR) >> hardware detection >> Core OS loads (Ntoskrnl.exe) >> Services Start >> Logon. 
[http://mirror.href.com/thestarman/asm/mbr/NTFSBR.htm](http://mirror.href.com/thestarman/asm/mbr/NTFSBR.htm)
[http://bootmaster.filerecovery.biz/appnote3.html](http://bootmaster.filerecovery.biz/appnote3.html)
[http://www.ntfs.com/boot-sector-damaged.htm](http://www.ntfs.com/boot-sector-damaged.htm)
[http://technet.microsoft.com/en-us/library/cc976796.aspx](http://technet.microsoft.com/en-us/library/cc976796.aspx)

---

### Post by YesWeCan on 2011-08-22
Thanks oldfred, I'm working my way through those links. So far, they all say the the PBR bootstrap code "finds" NTLDR but not how it does it.

So I decided to make a simple test. I used Ubuntu to copy my XP's ntldr file to a new file with a different name. Then I changed the name of ntldr. Then changed th new file name back to ntldr. So the ntldr file can no longer be in the same location as before. XP rebooted fine.

Now this suggests (can't yet say it proves) that the 440 byte (or so) bootstrap code can search the FAT32 fs for the location of the ntldr file and load it into RAM. What I don't yet know is whether the space between the PBR and the FAT table start (and I don't know exactly how big this is yet) could possibly contain an intermediate booter.

However, if the PBR code finds and boots ntldr this begs the question why the Grub PBR code cannot find and load core.img (as has been explained, the Grub PBR code is hard-coded with the absolute sector address of the first sector of core.img when grub-install is run).

[edit] This link: [http://thestarman.pcministry.com/asm/mbr/NTFSBR.htm](http://thestarman.pcministry.com/asm/mbr/NTFSBR.htm) says that the NTFS partition consists of a 1 sector PBR and another 15 sectors available for a second boot code to find and boot BOOTMGR. This makes sesne because 440 bytes is too little I imagine to navigate an NTFS file system and load and execute a file. I will therefore assume the same is true for FAT32 - perhaps not 15 sectors but enought to find and load NTLDR.

[COLOR=Navy]Therefore, Windows boots like this:
MBR code loads PBR code and runs it
PBR code loads up to 15 sectors of a file system searcher that locates the boot loader file and loads and runs it
[/COLOR] 
[COLOR=DarkRed]Grub works like this (in a PBR):
MBR code loads PBR code and executes it
PBR code uses an absolute sector address to load and execute the core.img file (BTW this file's 1st sector is another bootstrap loader)[/COLOR]

So why the difference? Why doesn't Grub's PBR load a second loader that can search the ext fs to find core.img so that it will always find it? Well, I reckon it is because the ext fs only leaves a 2 sector gap between partition start and fs start for boot code. Presumably this is not enough to navigate ext4.

---

### Post by ottosykora on 2011-08-22
@YesWeCan

>It has vmlinuz and initrd files for booting. All (almost) Grub does is load and run those files.<

so you say, I need only to install a distro like ubuntu or so and try to order it during the install process to install *no* bootloader at all?
(not just sure if the installer alowes me to do it)

And then the grub installed somewhere in an other partition for example, will go and simply load those initram etc if entry done in its config? I mean ok, they were prepared by the installation of some kernel, but so far I was only successful when installed at least Lilo or in present times grub in the partition. 

I tried with legacy grub in mbr and separate partition. The separate partition contains the stage1_5 and stage2 of the legacy grub as well as the menu.lst which I managed to set up in a way I can understand and can set the order of everything in it very simple.

But the individual os distros were installed so , that each had own grub copy in its partition and 'my grub' was chainloading.

example of one of my menu.lst

title		Windows XP
hide 		(hd0,1)
hide		(hd0,2)
unhide		(hd0,0)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader +1

title		Windows 7
hide		(hd0,0)
hide		(hd0,1)
unhide		(hd0,2)
rootnoverify	(hd0,2)
savedefault
makeaktive
chainloader +1

title		Ubuntu 10.10
root		(hd0,12)
chainloader +1


title		Debian Leny
root		(hd0,13)
chainloader +1

title           Fedora12
root            (hd0,11)
chainloader +1


title		W98/DOS
hide		(hd0,0)
hide		(hd0,2)
unhide		(hd0,1)		
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader +1

this is obviously still somehow simple, compared to what grub2 needs for syntax. 
This resides in a small partition called grub and from there all other things are called up.
But all those linux in this example , have grub legacy or grub2 (fedora) in the partition.

So what to do? Insdtall grub what ever into the partition first, then simply delete the files in question and leave only the kernel files in place and leave out the chainload command and use only the pointing to the root?

---

### Post by ottosykora on 2011-08-22
@srx5694

well, ok, so far I have nothing to do with UEFI, and it will still take some time until I will meet something like that. My computers are always given to me because someone does not need them anymore, I have never bought one in my life yet, thought I am 58...;-)

But back to mbr booting:

how do I set up leat say 4 linux distros and 2 windows distros on one drive? OK the windows *has* to be chainloaded as I undersstood from your text, due to the fact that we do not know with absolute certainity how their booting works, so just calling up their bootloader.

But how do I install a linux distro without bootloader and it still works? 
I tried few times with suse, but given up that , as I was never able to start it with anything that time (grub2 was just some early beta then).
Used Lilo then with all its problems instead.


For some time I used also XP boot manager and copied this famous 512b from the linux partition, but there I had grub installed when the distro did install itself.

---

### Post by YesWeCan on 2011-08-22
> **ottosykora said:**
> So what to do? Insdtall grub what ever into the partition first, then simply delete the files in question and leave only the kernel files in place and leave out the chainload command and use only the pointing to the root?
Exactly. Just delete the whole grub directory.
sudo rm -r /boot/grub

I'm not familiar with grub-legacy but you probably don't want to use chainloader. You'll need something like this structure:
```
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro
initrd        /boot/initrd.img-2.6.17-10-generic
boot
```

If you are using Grub2 then the update-grub command will automatically find the vmlinuz and initrd files and add an entry to grub.cfg. Note the OS-prober program that update-grub uses is not actually part of Grub (it is written by different people) so if you were to make a separate Grub partition as an OS-independent boot-loader you would not have this automatic OS search facility. Which sucks because the OS-prober is a major advantage of Grub2 over Grub-legacy IMO.

---

### Post by YesWeCan on 2011-08-22
> **srs5694 said:**
> I wasn't aware that GRUB Legacy used signed integers. That would certainly limit it to booting kernels from under the 1 TiB mark.
You were not aware because it is not true [for the boot sector code that is: see post #50]. ;) Grub-legacy uses a 4 byte, unsigned representation of the sector address; Grub2 uses 8 bytes. However, how many bytes are actually effective depends on the BIOS firmware as you have already alluded to.

---

### Post by ottosykora on 2011-08-22
OK, I will try on some next complex multiboot fun.

I have to figure out how to point in that case to a kernel but not with its proper name.

Hmmm, I know this was the advantage of the grub legacy in separate partition! List done once, and never changes, no editing needed as it does not point that way to exact kernels , but to a grub in the partition.

To have this situation with grub2 , well it would probably list all kernels found on the whole computer, but will on the other hand do the update at least to this complex looking list.

So to have nice streamlined menu, either one has to edit the files frequently (in case of grub legacy) or accept to have all kernels on the computer listed, but the editing might go automatic with grub2.

Actually, I have two systems with the legacy grub in separate partition and legacy grub in each other partition. This did so far not fail. 

What did fail one time, was grub2 in 10.04 , upgrade to 10.10 and nothing did move any more. Pèrobably something did 'move'.

---

### Post by oldfred on 2011-08-22
I posted an example in post #24 on how to boot a partition with grub2. Debian based system put a link in root that is updated with each kernel update. So all you have to do is boot the links. There also are links to  previous if you want that also. I like os-prober for new users, but once you understand grub2 it is often easier just to edit like old grub and put a boot stanza in 40_custom or a chain boot entry to old grub for those systems that still use grub legacy.

---

### Post by srs5694 on 2011-08-22
> **YesWeCan said:**
> So I decided to make a simple test. I used Ubuntu to copy my XP's ntldr file to a new file with a different name. Then I changed the name of ntldr. Then changed th new file name back to ntldr. So the ntldr file can no longer be in the same location as before. XP rebooted fine.

Now this suggests (can't yet say it proves) that the 440 byte (or so) bootstrap code can search the FAT32 fs for the location of the ntldr file and load it into RAM.

Not necessarily (although your conclusion is probably correct; see below). Unless you used a tool that's designed to securely erase data, the procedure you describe would leave the ntldr file's contents at its original sector locations on the disk, so if the PBR code used block lists, it would still work.

I tried a variant of your procedure to test this hypothesis on a Windows XP system: I created a new file the same size as ntldr but containing nothing but 0 values. I then renamed ntldr to foo and renamed the new file to ntldr. If the boot loader were using block lists, it would still be able to run the old ntldr code from the foo file. This didn't work, though; the system failed to boot (I just got a black screen). There's still one flaw with my test procedure, though: The PBR code could be using block lists to load part of ntldr, which might contain an NTFS driver that's used to read the rest of ntldr and other files. If this were the case, the results might be difficult to distinguish from a completely deleted ntldr file. Offhand, I can't think of a reliable way to test this hypothesis experimentally.

[quote=ottosykora]how do I set up leat say 4 linux distros and 2 windows distros on one  drive? OK the windows *has* to be chainloaded as I undersstood from your  text, due to the fact that we do not know with absolute certainity how  their booting works, so just calling up their bootloader.

But how do I install a linux distro without bootloader and it still works? [/quote]

There are several ways to do this. The way I'd probably do it (on a BIOS system) would be:


[list=1]
[*]Set up partitions ahead of time: Two primary partitions for the two Windows installations, possibly a logical Windows-only partition (to hold programs or Windows-only data files), one or possibly two NTFS or FAT logical partitions for Linux/Windows data sharing, as many logical partitions as desired for the Linux installations, and one primary or logical partition to serve as an OS-independent boot loader partition. (This last partition might serve as the final Linux distribution's /boot partition; see below.)
[*]Install both Windows versions, each on its own primary partition, perhaps hiding them from each other during installation by fiddling with partition type codes to keep them from messing with each others' configurations.
[*]Install the first three Linux distributions. If possible, I'd tell them to either not install boot loaders or to install their boot loaders in their root (/) or /boot partitions' boot sectors.
[*]Install the final Linux distribution. There would then be at least two options for boot loader configuration, and which I'd choose would depend on the final distribution's options on that score and what I wanted to use as a boot loader:

[list]
[*]Use the boot loader partition mentioned earlier as the distribution's /boot partition and install the boot loader in the MBR. This would enable boot loader maintenance from that distribution.
[*]Install no boot loader, or install it to the root (/) or /boot partition's boot sector, and then manually install another boot loader of my choice (probably GRUB Legacy, GRUB 2, or GRUB4DOS) in the boot loader partition mentioned earlier and in the MBR.
[/list]

[*]Reconfigure the boot loader installed in the boot loader partition so that it gives proper options for all of the OSes. With this many OSes, it's virtually certain that auto-configuration tools will get something wrong, so this reconfiguration will require enough understanding of the boot loader files to get things right by hand.
[/list]


The final result is that the boot loader installed to the MBR and the boot loader partition will control the boot process. It will chain load to Windows and can be configured to boot each of the Linux OSes directly. (It could also chain load to the other Linux distributions' boot loaders if they were installed in their partitions' boot records.) The trickiest part of this is likely to be the reconfiguration noted in the final step; you'd need to understand your chosen boot loader's configuration files, as well as the options used by all your distributions, in order to get it to work. (Cutting and pasting boot stanzas from the original installations' boot loader configuration files is likely to work *if* the two boot loaders are the same, but if not you'll need to modify some things.) This configuration will also require maintenance as you upgrade all your distributions; kernel changes might require manually updating the entries in the GRUB menu.

FWIW, my own experience is that it gets very difficult to manage more than two or three distributions on a single computer. I'm using virtual machines (in VirtualBox) more and more for access to multiple distributions. With VirtualBox, you don't need to worry about getting the distributions to play nice together; each one thinks that it's got its own dedicated computer. You can also run several of them simultaneously, assuming you've got enough RAM. Making backups of the virtual machines is also pretty easy. (I used a virtual machine to run the Windows XP test described above, and I copied the ~4GB disk image to a backup file so that if something went disastrously wrong I'd be able to recover just by renaming the backup.)

---

### Post by YesWeCan on 2011-08-22
> **srs5694 said:**
> Not necessarily (although your conclusion is probably correct; see below). Unless you used a tool that's designed to securely erase data, the procedure you describe would leave the ntldr file's contents at its original sector locations on the disk, so if the PBR code used block lists, it would still work.

I tried a variant of your procedure to test this hypothesis on a Windows XP system: I created a new file the same size as ntldr but containing nothing but 0 values. I then renamed ntldr to foo and renamed the new file to ntldr. If the boot loader were using block lists, it would still be able to run the old ntldr code from the foo file. This didn't work, though; the system failed to boot (I just got a black screen). There's still one flaw with my test procedure, though: The PBR code could be using block lists to load part of ntldr, which might contain an NTFS driver that's used to read the rest of ntldr and other files. If this were the case, the results might be difficult to distinguish from a completely deleted ntldr file. Offhand, I can't think of a reliable way to test this hypothesis experimentally.
Good point. I didn't account for the residue of the original file when its name is changed. I am inclined based on your experiment and the knowledge that there is an intermediate loader in sectors just after the PBR and that Windows can reliably boot from the PBR that the hypothesis that NTLDR is found by searching the file system is very likely true.

I suppose that if one created a separate boot partition for a Ubuntu installation and made it FAT32 or NTFS format, that the Windows boot code could be deployed, with minor modifications, to find and run core.img. Or a custom Grub code could be written. Hmm. Ha - what if one just called core.img ntldr! :D - no, that would be too easy. ;)

---

### Post by Luke M on 2011-08-23
> **srs5694 said:**
> As to the LBA BIOS functions, they do use 64-bit numbers on modern BIOSes, but the point of the [article I referenced]("http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/2tib-disc-limit.html#BIOSParameterBlockLimit") is that one key data structure, the BIOS parameter block, remains 32-bit and this limits the ability of a BIOS to boot anything from above this value in sectors. Apparently this is unlikely to change because the VBR is incorporated into many filesystems, so converting to a 64-bit VBR would require new filesystems. I know relatively little about this topic, though -- just what's written in the article to which I linked and the results of one test with a virtual machine in VirtualBox using GRUB 2. I was unable to boot from a Linux installation with a /boot partition above the 2 TiB mark in that test, but it worked fine when I moved that partition below the 2 TiB mark and re-installed GRUB 2. This tends to support the claims in the article, but of course there are other possible explanations, such as a filesystem-specific limit, a limit in the BIOS in VirtualBox, a bug in the specific version of GRUB 2 I used, or a flaw in my test procedure.

 The "BIOS" in "BIOS parameter block" refers to part of MS-DOS, not the system BIOS. The BIOS does not use it.

---

### Post by Luke M on 2011-08-23
> **YesWeCan said:**
> You were not aware because it is not true. ;) Grub-legacy uses a 4 byte, unsigned representation of the sector address; Grub2 uses 8 bytes. However, how many bytes are actually effective depends on the BIOS firmware as you have already alluded to.

 Ugh, I think you just called me a liar. I actually went to some lengths to try to get grub1 to work. Made about 10 patches (binary since I didn't want to mess with trying to recompile it) but there were still more signed int bugs. Not only the low level code, but also the filesystem code uses signed ints.

---

### Post by YesWeCan on 2011-08-23
> **Luke M said:**
> Ugh, I think you just called me a liar. I actually went to some lengths to try to get grub1 to work. Made about 10 patches (binary since I didn't want to mess with trying to recompile it) but there were still more signed int bugs. Not only the low level code, but also the filesystem code uses signed ints.
Sorry about that! I could be mistaken or we could be talking about different things. I had the boot sector code in mind which I believe uses a 4 byte absolute block address which it sends to the BIOS to load the next file. What parts of grub-legacy are you referring to?

---

### Post by ottosykora on 2011-08-23
@srs5694

do you know  when using w7 boot manager there has to be a loader in a linux partition or would also this be able to load linux kernel directly?

XP boot manager was definitely not able to do it, it was essential to have grub or something similar in partition then 


So summarizing:
only probably grub (legacy or 2) can boot a kernel in other partition directly

grub can load MS systems via chainload (calling up their native loaders)

As I am not aware of any current bootmangers (except grub) being able to start linux directly, in such case grub needs to be in partition.

When in partition, grub legacy might give more reliable results as code is shorter thus less danger of moving it during upgrades etc.
(no guarantee still)



This leaves me with some thoughts about general user friendliness of any linux and its ability to 'live' with other systems on one drive.
The grub system is not very user friendly, as it either works or not works, very difficult to configure as one needs probably programming experience to understand those fancy syntax of the config files.

Current versions of commercial products are not able to load linux directly, so again some loader needed.

Apparently no way out of the problem to have more systems on one computer, keep them functioning and be able to uninstall them any time.

---

### Post by Luke M on 2011-08-23
> **YesWeCan said:**
> Sorry about that! I could be mistaken or we could be talking about different things. I had the boot sector code in mind which I believe uses a 4 byte absolute block address which it sends to the BIOS to load the next file. What parts of grub-legacy are you referring to?

 The main part (stage1_5 / stage2).

---

### Post by YesWeCan on 2011-08-23
> **Luke M said:**
> The main part (stage1_5 / stage2).
I haven't looked at the stage1_5 or stage_2 code. What led you to notice this signed int problem? What is your finding...that grub1 is not always reliable when used on disks larger than 1TiB?
fedora still uses grub1 and I think SuSE does too.

---

### Post by Luke M on 2011-08-23
> **YesWeCan said:**
> I haven't looked at the stage1_5 or stage_2 code. What led you to notice this signed int problem? What is your finding...that grub1 is not always reliable when used on disks larger than 1TiB?
fedora still uses grub1 and I think SuSE does too.

 I installed Fedora in a partition above 1TB. That never works. If the partition is located entirely below 1TB, then grub1 will always work. If the partition spans 1TB, then grub1 may or may not work depending on the location of files.

---

### Post by YesWeCan on 2011-08-23
:shock:

---

### Post by srs5694 on 2011-08-23
> **Luke M said:**
> [quote=srs5694]As to the LBA BIOS functions, they do use 64-bit numbers on modern BIOSes, but the point of the [article I referenced]("http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/2tib-disc-limit.html#BIOSParameterBlockLimit")  is that one key data structure, the BIOS parameter block, remains  32-bit and this limits the ability of a BIOS to boot anything from above  this value in sectors.The "BIOS" in "BIOS parameter block" refers to part of MS-DOS, not the system BIOS. The BIOS does not use it.[/QUOTE]

As I said, I'm not an expert on this topic; however, a test installation of Ubuntu to a partition above the 2 TiB mark on a VirtualBox drive failed to boot when using GRUB 2, which suggests there's some sort of limitation that will become important in the near future, as >2TiB disks become more common. OTOH, it could be that something else is causing this problem -- a GRUB-specific bug, a limitation in the VirtualBox BIOS, an error in my test procedure, etc.

The bottom line for me is that I recommend ensuring the kernel and other boot files all fall below the 2 TiB mark. If and when I learn more about what caused the failure in my test, I might modify that advice appropriately.

> **ottosykora]do you know  when using w7 boot manager there has to be a loader in a  linux partition or would also this be able to load linux kernel  directly?[/quote]

AFAIK, neither the XP nor the Vista/7 boot code can directly boot a Linux kernel.

[quote=ottosykora]only probably grub (legacy or 2) can boot a kernel in other partition directly[/quote]

The range of boot loaders isn't that limited. There's LILO, Syslinux, LOADLIN, and probably others that are more obscure. These can all load Linux kernels, although some have their own limitations. (LOADLIN is a DOS program, for instance, so it requires the kernel to be on a partition that DOS can read -- normally FAT, but some Linux filesystems should be OK if you've got DOS drivers for them.)

[quote=ottosykora]This leaves me with some thoughts about general user friendliness of any  linux and its ability to 'live' with other systems on one drive.
The grub system is not very user friendly, as it either works or not  works, very difficult to configure as one needs probably programming  experience to understand those fancy syntax of the config files.[/quote]

I both agree and disagree with this assessment. Certainly messing with the GRUB 2 configuration files created by Ubuntu's installer is a pain said:**
> Apparently no way out of the problem to have more systems on one  computer, keep them functioning and be able to uninstall them any time.

An OS-independent boot loader partition, as outlined in my procedure in post #42, is the best way to do this, IMHO. This requires manual maintenance, but it at least keeps things functioning when you remove or upgrade any OS.

UEFI does it this way by default; its EFI System Partition (ESP) is the OS-independent boot loader partition (among other things, but they aren't directly relevant to this discussion). The way some boot loaders work on UEFI, though, pushes it to act more like a BIOS-based system. We'll have to wait for the dust to settle with UEFI to see how it works in the long run. Personally, I'd like to see two types of independent UEFI boot loaders:


[list]
[*]Boot selectors, which present menus to the user and enable selection of an OS-specific boot loader, but that can't load OS kernels directly. Currently, [rEFIt](http://refit.sourceforge.net) is the only example of this type of boot loader. In theory, the UEFI firmware itself should fill this role, but most implementations to date have awkward boot selectors.
[*]Kernel loaders, which present limited or no menu options but that load an OS kernel and any necessary associated files. The Windows UEFI loader and [ELILO](http://elilo.sourceforge.net) fall into this category, although ELILO does optionally give a menu that enables selection from multiple Linux kernels.
[/list]


GRUB 2 on UEFI attempts to do both tasks, and as a result it suffers from "kitchen sink-itis" -- too many features that makes the whole thing overly complicated.

---

### Post by YesWeCan on 2011-08-23
> **ottosykora said:**
> So summarizing:
only probably grub (legacy or 2) can boot a kernel in other partition directly

grub can load MS systems via chainload (calling up their native loaders)
Just to clarify, the IBM MBR boot system is a universal boot system. It is very simple and very effective. The first sector of the primary partition (the PBR) that has its boot flag set is loaded into RAM and executed. That's it.

So each partition that contains an OS is supposed to have bootstrap code in it first sector. Chain-loading just means loading and running that sector. If Ubuntu installed bootstrap code in its PBR it could be chain-loaded by another boot-loader, such as the Windows one.

> As I am not aware of any current bootmangers (except grub) being able to start linux directly, in such case grub needs to be in partition.Or Grub needs to over-write the MBR code and be chain-loaded from there.

> This leaves me with some thoughts about general user friendliness of any linux and its ability to 'live' with other systems on one drive.Ubuntu is basically not MBR system compliant and I am not aware of any linux distros that are (there probably are some knowing the rich diversity of linux). Which is odd considering linux is meant to be unix for the PC. From my time spent in the installation forum I know that this causes all sorts of problems for same-drive dual boots with Windows.

---

### Post by YesWeCan on 2011-08-23
> **Luke M said:**
> I installed Fedora in a partition above 1TB. That never works. If the partition is located entirely below 1TB, then grub1 will always work. If the partition spans 1TB, then grub1 may or may not work depending on the location of files.
Am I alone in thinking this is a major design flaw in grub-legacy? I mean, it has been around for years...how can this not have been fixed?

---

### Post by srs5694 on 2011-08-23
> **YesWeCan said:**
> Just to clarify, the IBM MBR boot system is a universal boot system. It is very simple and very effective. The first sector of the primary partition (the PBR) that has its boot flag set is loaded into RAM and executed. That's it.

So each partition that contains an OS is supposed to have bootstrap code in it first sector. Chain-loading just means loading and running that sector. If Ubuntu installed bootstrap code in its PBR it could be chain-loaded by another boot-loader, such as the Windows one.
...
Ubuntu is basically not MBR system compliant.


You've made this claim before, but I've never seen you provide any documentation that supports your claim about how the system is "supposed" to work. If you have a standards document that says the system should work the way you say it should, please produce a reference; otherwise what you're posting is your *opinion*, nothing more. In the absence of a formalized description by a standards body or a creator of the system, speaking of something being "compliant" or "not compliant" is meaningless.

---

### Post by srs5694 on 2011-08-23
> **YesWeCan said:**
> Am I alone in thinking this is a major design flaw in grub-legacy? I mean, it has been around for years...how can this not have been fixed?

I tend to agree; but:


[list]
[*]GRUB Legacy has officially been abandoned for quite a while in favor of GRUB 2. I'm not sure exactly when official development on GRUB Legacy stopped, but it was at least a couple of years ago.
[*]IIRC, one of the reasons cited for ceasing development of GRUB Legacy is that the code base is too difficult to maintain. A mish-mash of signed and unsigned integers in different parts of the code could be one of the problems with it -- but that's speculation by me.
[*]When it was last officially supported, >1TiB disks were extremely rare or non-existent. This means there would have been little incentive to fix this limitation at the time.
[/list]


I'm not trying to justify the limitation, but to suggest possible causes for its continued existence. As a practical matter, unless somebody formally and completely adopts GRUB Legacy, it's likely to go the way of the dodo as disks get bigger and as computers adopt UEFI. At the moment, Fedora uses a very heavily-patched version of GRUB Legacy that adds support for features like GPT and even UEFI; however, AFAIK they're treating their efforts as patches to the original code base rather than as a complete fork of the project.

---

### Post by ottosykora on 2011-08-23
> **YesWeCan said:**
> Just to clarify, the IBM MBR boot system is a universal boot system. It is very simple and very effective. The first sector of the primary partition (the PBR) that has its boot flag set is loaded into RAM and executed. That's it.

So each partition that contains an OS is supposed to have bootstrap code in it first sector. Chain-loading just means loading and running that sector. If Ubuntu installed bootstrap code in its PBR it could be chain-loaded by another boot-loader, such as the Windows one.

.

well yes this is somehow I understand it and covers with my experience playing with all sorts of multiboot set up.

Some years ago, I was keen of Knoppix and had numerous installs of it, boot manager was the one of XP.
But, in order to make it work, we used to install lilo with each knoppix distro. This did provide exactly what you say, the bootstrap and with the aid of the copy of the first sector, we could boot the linux without big hassle of configuring complex config files. The entries in the boot menu of XP were rather self explaining.

But this was OK for knoppix, this had no updates at this time, was  not even supposed to be installed, the kernel never changed.


So otherwise as I see it, when continuing to use some simple  managable boot managers (recent installs I use acronis) , I have to keep using legacy grub in the partition for chainloading otherwise none of the boot managers I know of will be able to work, apart from grub itself of course.

Hmm pitty, I always thought if someone put all the energy which was used to create things like unity into a project to create decent boot manager with somehow current technology, then we had not such problems and hundreds of support calls in forums today.

---

### Post by Luke M on 2011-08-23
> **YesWeCan said:**
>  Ubuntu is basically not MBR system compliant and I am not aware of any linux distros that are (there probably are some knowing the rich diversity of linux). Which is odd considering linux is meant to be unix for the PC. From my time spent in the installation forum I know that this causes all sorts of problems for same-drive dual boots with Windows.

 There's a major benefit to the grub approach, though: you can boot from a non-primary partition.

---

### Post by Luke M on 2011-08-23
> **YesWeCan said:**
> Am I alone in thinking this is a major design flaw in grub-legacy? I mean, it has been around for years...how can this not have been fixed?

 It was! The fix is called grub2. The final version of grub1 was released in 2005.

---

### Post by srs5694 on 2011-08-23
> **ottosykora said:**
> in order to make it work, we used to install lilo with each knoppix distro.
...
So otherwise as I see it, when continuing to use some simple  managable boot managers (recent installs I use acronis) , I have to keep using legacy grub in the partition for chainloading otherwise none of the boot managers I know of will be able to work, apart from grub itself of course.

LILO is still available and usable. I did a Slackware install in a virtual machine a few weeks ago, and it installed LILO (its default, IIRC). There's also Syslinux, although I've never done much with it so I'm not sure of its exact capabilities and limitations. Even LOADLIN could still be used, AFAIK, although it's rather specialized and isn't likely to be practical in most modern environments.

Ubuntu's default is GRUB 2, but that doesn't mean you're tied to it. I'm using ELILO to boot my MythTV box, which runs Ubuntu 11.04 on a UEFI-based computer. ELILO works more reliably than GRUB 2 on this particular machine. The catch, of course, is that to use something other than the default boot loader, you have to know enough about the topic to install it and maintain it.

---

### Post by YesWeCan on 2011-08-23
> **Luke M said:**
> There's a major benefit to the grub approach, though: you can boot from a non-primary partition.
You can anyway. The Extended Boot Record partition table entries also contain boot flags.

---

### Post by YesWeCan on 2011-08-23
> **Luke M said:**
> It was! The fix is called grub2. The final version of grub1 was released in 2005.
True - but have the fedora and OpenSuSE design teams been told? :P
The thing that is making me shudder is that when grub was first designed it was known that the MBR partition tables supported up to 2TiB disks. So to design grub not to, or heaven forbid not to test it,...what's that all about?

---

### Post by YesWeCan on 2011-08-23
> **srs5694 said:**
> You've made this claim before, but I've never seen you provide any documentation that supports your claim about how the system is "supposed" to work. If you have a standards document that says the system should work the way you say it should, please produce a reference; otherwise what you're posting is your *opinion*, nothing more. In the absence of a formalized description by a standards body or a creator of the system, speaking of something being "compliant" or "not compliant" is meaningless.
:P Ok then. For example, Grub ignores the MBR partition table boot flags. You may think that is just my "meaningless opinion" but I have reviewed the Grub source code and run experimental trials.
You know very well there are gazillions of documents out there that describe how the system works that IBM and Microsoft pioneered in the 1970s. I'm not going to bite any more on this matter.

Seriously though. I had a look at mkfs.vfat and mke2fs.extN and whereas I can see a means with FAT32 to specify the number of reserved sectors prior to the FAT start (that can be used for embedding) I see nothing for extN. I know that the ext4 superblock starts 2 sectors into the partition and there is no PBR header, like Windows fs use, to specify the start of the superblock. The linux fs is the UNIX fs; I'm not sure whether it is any different at all. So my conjecture, at the momnet, is that in the early days linux just decided to use the UNIX fs without modification and it did not and does not cater for PC-style boot-loader embedding.

---

### Post by YesWeCan on 2011-08-23
> **srs5694 said:**
> I tend to agree; but:


[LIST]
[*]GRUB Legacy has officially been abandoned for quite a while in favor of GRUB 2. I'm not sure exactly when official development on GRUB Legacy stopped, but it was at least a couple of years ago.
[*]IIRC, one of the reasons cited for ceasing development of GRUB Legacy is that the code base is too difficult to maintain. A mish-mash of signed and unsigned integers in different parts of the code could be one of the problems with it -- but that's speculation by me.
[*]When it was last officially supported, >1TiB disks were extremely rare or non-existent. This means there would have been little incentive to fix this limitation at the time.
[/LIST]

I'm not trying to justify the limitation, but to suggest possible causes for its continued existence. As a practical matter, unless somebody formally and completely adopts GRUB Legacy, it's likely to go the way of the dodo as disks get bigger and as computers adopt UEFI. At the moment, Fedora uses a very heavily-patched version of GRUB Legacy that adds support for features like GPT and even UEFI; however, AFAIK they're treating their efforts as patches to the original code base rather than as a complete fork of the project.
Sure, I agree with your practical points. I think it remiss, tho, (assuming they knew about this problem at the time) that the maintainers didn't fix it as I would have thought it was obviously bound to be a future problem and, besides, just how hard would it have been to fix? Perhaps they expected it to be replaced sooner: how can it be that a mainstream distro like fedora (meant to be the ultimate statement in linux, isn't it?) carries on today with a boot loader with this problem...
Well, linux development works in mysterious ways, I suppose. ;)

---

### Post by oldfred on 2011-08-23
Windows only boots from primary partitions and one is the active partition. MBR was not designed for multi-boot and the windows work around is to literally move all the boot files from second installs to the active partition. Then users delete the old install and wonder why they cannot boot.

meierfra. has posted instructions to get XP to boot directly from a logical partition but you cannot use the windows boot loader. Lilo does not care if the boot flag is on a logical and then jumps to the PBR of a logical and windows then can be booted from a logical partition. Not sure if Vista/7 have more checking to not work or not. I have not seen it work. You then have to create a windows boot primary partition.

---

### Post by YesWeCan on 2011-08-23
> **oldfred said:**
> Windows only boots from primary partitions and one is the active partition. MBR was not designed for multi-boot and the windows work around is to literally move all the boot files from second installs to the active partition. Then users delete the old install and wonder why they cannot boot.

meierfra. has posted instructions to get XP to boot directly from a logical partition but you cannot use the windows boot loader. Lilo does not care if the boot flag is on a logical and then jumps to the PBR of a logical and windows then can be booted from a logical partition. Not sure if Vista/7 have more checking to not work or not. I have not seen it work. You then have to create a windows boot primary partition.

How I think it would work is that the extended primary partition would have its boot flag set as well as a logical partition. Each relevant EBR would contain a boot code (for which it has provision) much like the MBR, with the difference that the EBR partition table specifies sector offsets from the EBR start as opposed to absolute sectors addresses.

Microsoft never bothered implementing this, it seems. But I don't see why Ubuntu could not have done (if it also supported PBR booting - either in the root or as a separate partition such as the GPT bios-grub).

---

### Post by srs5694 on 2011-08-23
re: The claim that GRUB violates MBR boot "standards"

> **YesWeCan said:**
> [quote=srs5694]You've made this claim before, but I've never seen you provide any  documentation that supports your claim about how the system is  "supposed" to work. If you have a standards document that says the  system should work the way you say it should, please produce a  reference; otherwise what you're posting is your *opinion*, nothing  more. In the absence of a formalized description by a standards body or  a creator of the system, speaking of something being "compliant" or  "not compliant" is meaningless.:P Ok then. For example, Grub ignores the MBR partition table boot flags. You may think that is just my "meaningless opinion" but I have reviewed the Grub source code and run experimental trials.
You know very well there are gazillions of documents out there that describe how the system works that IBM and Microsoft pioneered in the 1970s. I'm not going to bite any more on this matter.[/quote]

Sure there are "gazillions of documents," but to the best of my knowledge, they all *describe* the system as it exists rather than *define* how the system should work. As such, many of those documents are contradictory and some of them describe things in ways you say are violations of the "standard." The [GRUB documentation](http://www.gnu.org/software/grub/manual/html_node/index.html) is a prime example. If you know of an actual standards document, please reference it. Otherwise, the claim that GRUB violates a standard is incorrect, or at least unsupported.

> Seriously though. I had a look at mkfs.vfat and mke2fs.extN and whereas I can see a means with FAT32 to specify the number of reserved sectors prior to the FAT start (that can be used for embedding) I see nothing for extN. I know that the ext4 superblock starts 2 sectors into the partition and there is no PBR header, like Windows fs use, to specify the start of the superblock. The linux fs is the UNIX fs; I'm not sure whether it is any different at all. So my conjecture, at the momnet, is that in the early days linux just decided to use the UNIX fs without modification and it did not and does not cater for PC-style boot-loader embedding.

I wouldn't agree that "the linux fs is the UNIX fs," at least not with "filesystem" (or "fs" for short) taking on its usual meaning of a specific and clearly-defined set of data structures, as in ext4fs or NTFS or HFS+. A quick check on Wikipedia or many other sources will reveal something of the history of Linux filesystems. Early on, Linux used the Minix filesystem, but later, the Extended Filesystem (extfs) was developed *specifically for Linux*. Although some of its data structures were inspired by those of the [Unix File System (UFS),](http://en.wikipedia.org/wiki/Unix_File_System) extfs was a unique filesystem. It eventually gave rise to ext2fs, ext3fs, and now ext4fs. At around the time ext2fs was developed, Xiafs was created for Linux (based on the Minix filesystem, IIRC). ReiserFS was another independent development for Linux, as is the newest major one for Linux, Btrfs. JFS was donated by IBM and was originally developed for AIX, while XFS was originally developed for IRIX. Linux has long included a separate UFS driver, but to the best of my knowledge nobody's ever made a serious attempt to use it as a native Linux filesystem. (Despite the fact that it's existed for well over a decade, the kernel  configuration tools still list its write support as "DANGEROUS," in  all-caps.) Today, extfs is defunct (it's no longer in the kernel), as is Xiafs.

All of these filesystems have some similarities at a conceptual level. For instance, they all support mixed-case filenames and Unix-style ownership and permissions. These similarities aren't enough to qualify them as being the same filesystem, either IMHO or in any way I've seen the word "filesystem" used. These features can all be implemented in any number of ways that have little or nothing to do with how an OS boots from a disk. At the very low level of data structures in sectors on the disk, these filesystems are all unique (although there's sometimes some degree of compatibility within a family).

I'm not a filesystem developer, so I don't know precisely what sorts of issues they have to deal with or precisely how similar or dissimilar specific filesystems' data structures are. I'm very skeptical of the notion that the lack of reserved sector data in the ext?fs family has anything to do with UFS influences, except perhaps to the extent that the developers were familiar with UFS and, given that familiarity, just didn't see a need for such information, particularly given the boot loaders of the day. LILO and extfs were both introduced in 1992, but I don't know which one was introduced first. I'm not sure how Linux users booted the OS prior to LILO -- perhaps LOADLIN, or maybe something else that's too old for me to remember. (I first began using Linux in 1995.) If it was LOADLIN, that boots a Linux kernel as a file from DOS, so the computer would first have to boot DOS and then load a kernel from a filesystem DOS could read.

Another point is that OS kernels require different types of information to be passed to them by their boot loaders. You can't boot a Linux kernel using an unmodified Windows boot loader; nor can you boot a Windows kernel directly using LILO or GRUB. (That's why chain loading is so important.) In the mid-1990s, a specification called [Multiboot](http://www.gnu.org/software/grub/manual/multiboot/multiboot.html) was created to attempt to impose some order on this chaos, but it never really took off. A handful of OS kernels are Multiboot-compliant, but AFAIK the list doesn't include any of the big ones. (The [Wikipedia article on Multiboot](http://en.wikipedia.org/wiki/Multiboot_Specification) provides a list.)

---

### Post by Luke M on 2011-08-24
> **YesWeCan said:**
> Perhaps they expected it to be replaced sooner: how can it be that a mainstream distro like fedora (meant to be the ultimate statement in linux, isn't it?) carries on today with a boot loader with this problem...
Well, linux development works in mysterious ways, I suppose. ;)

 As it happens, Fedora 16 alpha was just released and guess what? It uses grub2.

---

### Post by ottosykora on 2011-08-24
>If it was LOADLIN, that boots a Linux kernel as a file from DOS, so the computer would first have to boot DOS and then load a kernel from a filesystem DOS could read.<

my first contact with linux was like this,sometimes in the 90ties, as it was all booting and running from a single floppy. That time I could not discover any useful functions in it for me.

---

