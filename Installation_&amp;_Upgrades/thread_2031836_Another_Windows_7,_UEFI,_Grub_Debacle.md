---
title: "Another Windows 7, UEFI, Grub Debacle"
date: 2012-07-22
forum: Installation &amp; Upgrades
---

### Post by drmrgd on 2012-07-22
Just set up my new system, which has UEFI enabled in the BIOS (and no obvious way to disable).  I put two drives in there and would like to dual boot Windows 7 and Kubuntu as I did before.  However, I can't get Grub2 to see Windows 7.  I've spent the day reading forum posts, Launch Pad bug reports, and whatnot, and while I'm close, I can't quite get this to work.  I can boot into each system from BIOS if I force it.  Not very elegant and useful, though!  I know I must be missing something really obvious, but I just can't see it.  I know oldfred has been hacking away at this for some time now, hopefully he at least has a fix!

I'm attaching the results of the latest version of bootinfoscript for reference.  However, the basic architecture is:

```
/sda1 = /boot
/sda2 = swap
/sda3 = /
/sda4 = /home

/sdb1 = EFI
/sdb2 = Windows Reserved
/sdb3 = Windows

```

After reading a ton of posts, seems like the most obvious is to point grub to the bootmgfw.efi on the EFI partition of that drive.  So, I edited /etc/grub.d/40_custom like so:

```
menuentry "Windows 7" {
    search --fs-uuid --no-floppy --set=root 1261-7FB0
    chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

```

However, when I run grub-update, I don't specifically see that entry in the list, and when I reboot and try to select the entry, I get a partition not found error.  I'm sure that I have the correct UUID for that partition, although I did try using both (hd1,1) and (hd1,gpt1) without any success.

I did try going the other way as well (i.e. use the Windows 7 bootloader to add linux) with EasyBCD, but that doesn't seem to work either, and it looks like there is no real solution that I can see on the support forums (they basically say that even the most recent beta version is not supporting UEFI/GPT at this time).  

I would forever be indebted to anyone who can point out what I'm doing wrong and help me get a reasonable boot management solution.  If there's any info I left out that would be helpful, just ask!

---

### Post by darkod on 2012-07-22
I don't use UEFI, but I was under the impression you are not using grub2 any more. You use the built-in UEFI bootloader.

Did you install ubuntu in EFI mode too? You have to be careful whether you boot the cd in the standard bios mode, or efi mode. It seems it will not install in efi unless you boot it in efi.

Look in bios in the boot devices and make the cd-rom (uefi) before the cd-rom (standard). It seems you will have both options on uefi boards.

---

### Post by jonnyboysmithy on 2012-07-22
So installing grub the usual way on one harddisk doesn't work? 
> Run the following, with X being the your Ubuntu drive:
          Code:
     sudo grub-install /dev/sd[COLOR=DarkRed]**X**[/COLOR] 
Maybe something screwed up in your fstab. :confused:
EDIT: Like Darkod says it probably a UEFI thing, (I'm a semi-noob :P)

---

### Post by oldfred on 2012-07-22
I really do not know if you can chain from a BIOS/MBR to efi partition. Most suggest having entire system boot with BIOS mode or entire system boot with UEFI mode. I know when booting from gpt drive with BIOS I had to have the insmod part_msdos to get it to work with the Windows XP in a MBR(msdos) drive. So I think you have to tell it that the drive is gpt and fat. Some of the mod files are built in, but do not hurt to add, others have to be added to get grub2 to work.

But I have seen these three different chain entries. I think you have to specify the {root} when it is a different drive.

Chainload entry:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801)
[http://ubuntuforums.org/showthread.php?t=1934773](http://ubuntuforums.org/showthread.php?t=1934773)
menuentry "Windows 7 UEFI" {
  insmod part_gpt
  insmod fat
  insmod search_fs_uuid
  insmod chain
  set root='(hd1,gpt1)'
  search --fs-uuid --no-floppy --set=root 1261-7FB0
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

menuentry "Windows 7 UEFI" {
  search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

[http://www.insanelymac.com/forum/lofiversion/index.php/t186440](http://www.insanelymac.com/forum/lofiversion/index.php/t186440)
menuentry "Windows 7 UEFI" {
  search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

---

### Post by Lyfang on 2012-07-22
See also: [UEFIBooting]("https://help.ubuntu.com/community/UEFIBooting")

---

### Post by drmrgd on 2012-07-22
> **darkod said:**
> I don't use UEFI, but I was under the impression you are not using grub2 any more. You use the built-in UEFI bootloader.

Did you install ubuntu in EFI mode too? You have to be careful whether you boot the cd in the standard bios mode, or efi mode. It seems it will not install in efi unless you boot it in efi.

Look in bios in the boot devices and make the cd-rom (uefi) before the cd-rom (standard). It seems you will have both options on uefi boards.

Hmmm...that's interesting.  I didn't install Ubuntu UEFI because I didn't realize there was a different way to install it at the time and at that time didn't understand the distinction.  I'm guessing that if I reinstall Ubuntu, selecting UEFI in the BIOS boot menu, then I might be able to either get the Windows boot loader or Grub to cooperate?  It might be to what oldfred was saying and that I'm mixing and matching here.

I could certainly give that a try.

---

### Post by drmrgd on 2012-07-22
> **oldfred said:**
> I really do not know if you can chain from a BIOS/MBR to efi partition. Most suggest having entire system boot with BIOS mode or entire system boot with UEFI mode. I know when booting from gpt drive with BIOS I had to have the insmod part_msdos to get it to work with the Windows XP in a MBR(msdos) drive. So I think you have to tell it that the drive is gpt and fat. Some of the mod files are built in, but do not hurt to add, others have to be added to get grub2 to work.

But I have seen these three different chain entries. I think you have to specify the {root} when it is a different drive.

Chainload entry:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801)
[http://ubuntuforums.org/showthread.php?t=1934773](http://ubuntuforums.org/showthread.php?t=1934773)
menuentry "Windows 7 UEFI" {
  insmod part_gpt
  insmod fat
  insmod search_fs_uuid
  insmod chain
  set root='(hd1,gpt1)'
  search --fs-uuid --no-floppy --set=root 1261-7FB0
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

menuentry "Windows 7 UEFI" {
  search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

[http://www.insanelymac.com/forum/lofiversion/index.php/t186440](http://www.insanelymac.com/forum/lofiversion/index.php/t186440)
menuentry "Windows 7 UEFI" {
  search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

Thanks for the tips Fred.  I think I see what's the problem here, and as you say I think I'm mixing and matching bootloader protocols here.  I did try the three iterations of grub entries for Windows, and they all failed. 

I did just retry the first selection you have since it has more mod files than one of my attempts.  I get a different error in that case, I get an "invalid signature" error.  I can't seem to figure out what that means, although I suspect it's saying that I have a syntax error with the drive location or something to that effect.

I'm sort of thinking now after reading all this that I need to reinstall Kubuntu as UEFI.

---

### Post by oldfred on 2012-07-22
Some more links on useful info:
Grub2 efi info ArchLinux - Arch but grub2 is grub2 with maybe minor differences by distribution
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)

[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

If you're using UEFI mode to boot, you don't need a BIOS Boot Partition with gpt partitions (only for BIOS), but you do need an EFI System Partition (ESP). This is entirely different; it should be a 200-300 MiB FAT32 partition that's flagged as an ESP and must be the first partition. In libparted-based tools, you'd give it a "boot" flag (which is entirely unrelated to the MBR boot/active flag, although libparted makes them look the same). In gdisk, you'd give it a type code of EF00.
An EFI System Partition EF00 (~100 to -256MiB, FAT32) for UEFI, a BIOS Boot Partition EF02 (~1MiB, no filesystem) for BIOS, and whatever partitions you want for Linux. You must set the partition type codes correctly, but how you do this depends on the utility you use to create them. Also, you should be sure to create a GUID Partition Table (GPT) on the disk, not a Master Boot Record (MBR) partition table. In BIOS mode, Ubuntu's installer defaults to creating MBR partitions, at least on sub-1TB disks, so you may need to use another utility to do the partitioning. You do not need both but it does not hurt as both are small, and then you can configure easily to boot with either UEFI or BIOS. You can boot via bios AND efi (after setting up your efi boot entry using efibootmgr or via efi shell and running the efi binary)

Most that have gotten UEFI to work with Ubuntu have partitioned in advance.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
If gpt(not MBR) partitioning include these first - all partitions with gpt are primary
    250 MB efi FAT32
    1 MB bios_grub  no format 
Ubuntu partitions - smaller root only where hard drive space is limited
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by drmrgd on 2012-07-22
Thanks for all the help and advice.  This makes total sense to me.  I'll partition ahead of time as you propose, and then I guess run gdisk to get up the GPT (I don't remember an obvious way to do this from KDE's flavor of gparted).  The only question I have is that I remember reading something about leaving a small amount of unpartitioned space at the end of the drive for a secondary GPT table.  Is that something you're familiar with? 

I do like to hibernate the system (although this one should boot a lot faster than the last one, so maybe that's moot), so I'll probably put a fairly large swap space in there.  Also, I have an external drive that I usually use as my main storage space / xfer stuff between Linux and Windows drive.  So, I won't include a NTFS partition on there.

I'm going to have to read up on EFI shell and efibootmanager as I'm not at all sure how to appropriately run those.  I do see a launch EFI shell option in BIOS, but it throws an error when I try to run it.

---

### Post by oldfred on 2012-07-22
You can also download a gparted liveCD. 

[http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)


When you partition with gpt it automatically creates the backup partition table at the end of the drive. I did not have to do anything special.

---

### Post by drmrgd on 2012-07-23
> **oldfred said:**
> You can also download a gparted liveCD. 

[http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)


When you partition with gpt it automatically creates the backup partition table at the end of the drive. I did not have to do anything special.

Oh, I see.  That's a much better way to go.  I'll use that strategy to partition.  

Boy, I really had no idea how different all of this is from BIOS / MBR, and was totally unprepared!  For all of the research I did on hardware for this build, I never thought to check out something as basic as drive partitioning.  Definitely learned something new here!

I'll likely try this all out tonight and post back how it goes.  Hopefully no hiccups!

---

### Post by oldfred on 2012-07-23
Good luck & let us know details.

As I understand it, the way you boot the install is the way in installs. Both Windows & Ubuntu install CD/DVDs from UEFI will show two ways to boot installer, one UEFI/efi and the other BIOS/legacy/AHCI or whatever that vendor calls it.

I believe if you have both efi & bios_grub partitions, you can install grub twice once grub2 (grub-pc) to MBR and once grub-efi to efi partition and boot either way. Not sure how that may work with two drives as I do not totally understand UEFI. I also am trying to learn as I hope to build new system soon.

---

### Post by wnelson on 2012-07-23
I found this a day or so ago it is for sony yet I it seems that the same process will work for most UEFI systems.

[http://www.hackourlife.com/sony-vaio-with-insyde-h2o-efi-bios-ubuntu-12-04-dual-boot/](http://www.hackourlife.com/sony-vaio-with-insyde-h2o-efi-bios-ubuntu-12-04-dual-boot/)

Walt

---

### Post by drmrgd on 2012-07-27
Well, work's been a bit on the hellish side, and so I've not had the chance to fully work on this until today really.  But, after a few days of trial and error, I finally have a working dual boot, UEFI system!  I'm hoping that a kernel upgrade does not break anything.  This seems pretty stable, though.  

For future people's sake, here's how I finally got it working.  Note, I'm working with two hard drives here, and the instructions will likely vary for those working from just one drive.  It's also worth noting that if you're working from two drives, it might be handy to unplug the Windows drive from the system to help diagnose problems.  I couldn't figure out what was going wrong until I realized that I couldn't even boot Kubuntu when it was the only drive in the system.  Final note is that this was with Kubuntu 12.04. Any other versions may stray from this (especially older versions).  However, I was happy to learn that I was over thinking things, and that out of the box it seems that Kubuntu 12.04 (and likely Ubuntu as well) set things up well right from the start.  

Anyway, here are the steps I took:

1.  Make an Ubuntu (or in my case Kubuntu) .iso boot disk as usual.

2.  In BIOS (if yours supports it) load the disk using UEFI mode.  If you don't specifically choose to boot the .iso as UEFI, you may be installing in BIOS mode instead of UEFI, which will cause problems later.  We *need* to make sure that both OSes are UEFI here or else going with the traditional BIOS approach is the best tack to take. 

3.  I tried as others have suggested to preformat the drive.  However, I was either doing something wrong or there is a bug / glitch here and I was unable to get a stable working Kubuntu system to boot.  Every time I would try to boot from a fresh install, I would get something like "Reboot and Select the Proper Boot Device" errors.  The goal here is to format the drive in GPT mode (instead of the old standby MBR mode), creating a new type of /boot partition as follows (let's assume the drive is /dev/sda for this):

```

Partition    Type    Mount Point    Size   Flags
/dev/sda1    fat32    /boot/efi    200MiB  boot
/dev/sda2    linuxswap (if you want one that is!)
/dev/sda3    ext4    /    
/dev/sda4    ext4    /home

```

This is all assuming you want those options.  Minimally, you need to have a FAT32 EFI partition at the start that is around 200MiB bit that is marked as /boot.  This option was selectable for me when I chose manual partition during the Kubuntu setup.  You may or may not find that pre-formatting the hard drive with a Gparted Live CD works better (which I've seen posted in several places around the net).  However, with 12.04, it seems like it handled the above scheme with no problems.  The rest of the partitions can be as you like following standard guidelines (if there is such a thing!).

4. During the partition phase of the installation, be sure to choose to have the boot loader installed on sda1.  Just leaving it as sda didn't seem to work well for me.

5.  Once the isntallation finishes, reboot the system and verify that when you choose to boot Kubuntu as UEFI it boots without problem.  You may or (more likely) may not see a Grub menu before it loads the system.  This is normal (even from the old days) if there were no other OSes present for Grub to present.  

If you're with me to this point, then we're in the home stretch.  If not, you may need to verify that you're indeed installing Kubuntu as UEFI, and that in the /boot/efi parition that you made, you see a similar file structure:

```
dave@CygnusX1:/boot$ ls
abi-3.2.0-23-generic     efi   initrd.img-3.2.0-23-generic  memtest86+_multiboot.bin     vmlinuz-3.2.0-23-generic
config-3.2.0-23-generic  grub  memtest86+.bin               System.map-3.2.0-23-generic

```

```
dave@CygnusX1:/boot/efi/EFI/ubuntu$ ls
grubx64.efi
dave@CygnusX1:/boot/efi/EFI/ubuntu$
```

```
dave@CygnusX1:/boot/grub$ ls
acpi.mod          datetime.mod                 gcry_twofish.mod    lsmmap.mod      parttool.lst         test_blockarg.mod
adler32.mod       dm_nv.mod                    gcry_whirlpool.mod  ls.mod          parttool.mod         testload.mod
affs.mod          echo.mod                     gettext.mod         lspci.mod       password.mod         test.mod
afs_be.mod        efi_gop.mod                  gfxmenu.mod         lssal.mod       password_pbkdf2.mod  tga.mod
afs.mod           efi_uga.mod                  gfxterm.mod         lvm.mod         pbkdf2.mod           trig.mod
aout.mod          elf.mod                      gptsync.mod         lzopio.mod      pci.mod              true.mod
appleldr.mod      example_functional_test.mod  grub.cfg            mdraid09.mod    play.mod             udf.mod
ata.mod           ext2.mod                     grub.efi            mdraid1x.mod    png.mod              ufs1.mod
ata_pthru.mod     extcmd.mod                   grubenv             memdisk.mod     probe.mod            ufs2.mod
at_keyboard.mod   fat.mod                      gzio.mod            memrw.mod       raid5rec.mod         uhci.mod
befs_be.mod       fixvideo.mod                 halt.mod            minicmd.mod     raid6rec.mod         usb_keyboard.mod
befs.mod          font.mod                     hashsum.mod         minix2.mod      raid.mod             usb.mod                      
bitmap.mod        fshelp.mod                   hdparm.mod          minix.mod       read.mod             usbms.mod                    
bitmap_scale.mod  fs.lst                       hello.mod           mmap.mod        reboot.mod           usbserial_common.mod         
blocklist.mod     functional_test.mod          help.mod            moddep.lst      regexp.mod           usbserial_ftdi.mod           
boot.mod          gcry_arcfour.mod             hexdump.mod         msdospart.mod   reiserfs.mod         usbserial_pl2303.mod         
bsd.mod           gcry_blowfish.mod            hfs.mod             multiboot2.mod  relocator.mod        usbtest.mod                  
btrfs.mod         gcry_camellia.mod            hfsplus.mod         multiboot.mod   scsi.mod             video_bochs.mod              
bufio.mod         gcry_cast5.mod               iorw.mod            nilfs2.mod      search_fs_file.mod   video_cirrus.mod             
cat.mod           gcry_crc.mod                 iso9660.mod         normal.mod      search_fs_uuid.mod   video_fb.mod                 
chain.mod         gcry_des.mod                 jfs.mod             ntfscomp.mod    search_label.mod     videoinfo.mod                
cmp.mod           gcry_md4.mod                 jpeg.mod            ntfs.mod        search.mod           video.lst                    
command.lst       gcry_md5.mod                 keylayouts.mod      ohci.mod        serial.mod           video.mod                    
configfile.mod    gcry_rfc2268.mod             keystatus.mod       part_acorn.mod  setjmp.mod           videotest.mod                
core.efi          gcry_rijndael.mod            linux.mod           part_amiga.mod  setpci.mod           xfs.mod                      
cpio.mod          gcry_rmd160.mod              loadbios.mod        part_apple.mod  sfs.mod              xnu.mod                      
cpuid.mod         gcry_seed.mod                loadenv.mod         part_bsd.mod    sleep.mod            xnu_uuid.mod                 
crypto.lst        gcry_serpent.mod             locale              part_gpt.mod    squash4.mod          xzio.mod                     
crypto.mod        gcry_sha1.mod                loopback.mod        partmap.lst     tar.mod              zfsinfo.mod                  
cs5536.mod        gcry_sha256.mod              lsacpi.mod          part_msdos.mod  terminal.lst         zfs.mod                      
datehook.mod      gcry_sha512.mod              lsefimmap.mod       part_sun.mod    terminal.mod                                      
date.mod          gcry_tiger.mod               lsefisystab.mod     part_sunpc.mod  terminfo.mod                                      
dave@CygnusX1:/boot/grub$
```

Again, with just one drive in the system so that you can diagnose things, be sure that you have a working UEFI install of Kubuntu that boots without problems before going on.  Until you have that, dual booting is impossible.

6.  Now if you have Kubuntu booting normally as UEFI, we need to add Windows to Grub.  First we need to know the UUID of its /boot/efi parition.  To find out, run (after plugging the Windows drive back in that is!):

```
sudo blkid
```

Then look for the UUID for that partition which will be vfat and have a short, 8 character UUID instead of the long one.  In my case, it was:

```
dave@CygnusX1:/boot/grub$ sudo blkid
/dev/sda1: UUID="DEEB-3A1A" TYPE="vfat" 
/dev/sda2: UUID="b170157f-8d99-4f06-8ce2-92e8e3f44f43" TYPE="swap" 
/dev/sda3: UUID="58702a5d-45aa-4c17-9de9-650e2d21d30e" TYPE="ext4" 
/dev/sda4: UUID="1b1c5499-2500-4432-a049-41c93399382d" TYPE="ext4" 
/dev/sdb1: UUID="1261-7FB0" TYPE="vfat" 
/dev/sdb3: UUID="4ECC6BF6CC6BD6AD" TYPE="ntfs
```

Since I know that the Windows drive is /dev/sdb, I know that the UUID of the Windows efi_boot partition is 1261-7FB0.  

7.  Add an entry to Grub to load the Windows EFI Bootloader by running:

```
sudo nano /etc/grub.d/40_custom
```

and add the following:

```
menuentry "Windows 7" {
    insmod part_gpt
    insmod fat
    insmod search_fs_uuid
    insmod chain
    search --fs-uuid --no-floppy --set=root 1261-7FB0
    chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

```

Note that where I have '1261-7FB0' in my entry, you'll want to replace that with the UUID you found in the last step.

8. Run:

```
sudo update-grub
```

in order to add the entry to the grub.cfg line.  On my system, I didn't specifically see it add an entry for Windows when it was discovering things.  I was worried this didn't work but decided to try it out anyway and rebooted.  I was pleasantly surprised to see a new Windows 7 entry in Grub, which loaded without any problems.

I believe that once you add the Windows entry to grub.cfg you should see the Grub menu when you reboot.  If not, then you'll want to edit /etc/default/grub and comment out the two GRUB_HIDDEN lines as such:

```
#GRUB_HIDDEN_TIMEOUT=0                                                                                                               
#GRUB_HIDDEN_TIMEOUT_QUIET=true
```

That will ensure that you see the Grub menu every time, without having to press 'shift' to see it.  

By the way, you'll also need to make sure that your Kubuntu hard drive is the default one in the Boot order so that the system knows to load it first.  Of course, if you try to have the Windows disk be the default, you'll never get to Grub and the whole thing falls apart.

Well, that's about it.  After messing around with a bunch of solutions, this seems to be working quite well, and barring any unforeseen breakage from Kernel updates (which I don't think will happen), I think this is the best way to go as it offers the most flexibility without really altering the finicky and fragile Windows boot loader (which I managed to break more than once - good thing it's easy to fix with the installation DVD!).  

I hope that helps someone in the future, and they don't spend nearly as much time as I did trying to figure this all out.

---

### Post by oldfred on 2012-07-27
Glad you got it working.

I think this is the first dual UEFI boot on two drives that I have seen work. Thanks.

---

### Post by Poutrathor on 2012-11-07
Drmrgd, Thank You ! Deeply!

**Oldfred send me to your solution and it works! I am very happy and grateful.**

Just if someone read this, my active EFI partition is on the Windows Hard disk (while drmrgd has his EFI with Linux). I suppose the important point is to have the correct chain:

Configure (U)EFI to start on the correct partition the one with Grub 
Configure the Grub files to have the correct pointer in the second drive.

I hope I did not write bs ;)

My thread : [http://ubuntuforums.org/showthread.php?t=2081220](http://ubuntuforums.org/showthread.php?t=2081220)

See you!

---

### Post by drmrgd on 2012-11-07
Wow, great!  I'm glad this was able to help you, although I would think the info is a bit outdated already.  Enjoy your new dual boot system.  I'm certainly very much enjoying mine!

---

### Post by grahammechanical on 2012-11-07
This will add the latest information into the mix now that Windows 8 machines are on the market:

[http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/]("http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/")

Regards.

---

