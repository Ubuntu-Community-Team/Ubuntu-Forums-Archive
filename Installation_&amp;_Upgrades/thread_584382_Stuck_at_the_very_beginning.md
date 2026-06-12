---
title: "Stuck at the very beginning"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by arjun.attam on 2007-10-20
Was trying to install Gutsy (final) on my system, and ditch Windows (XP SP2). After downloading the torrent, got it burnt, started it, and can't go after the loading screen, or the brown caterpillar that bangs alternatively against walls.

Specs:
Pentium 4 630, 3ghz (I have the 32 bit version of Gutsy)
1 gig of RAM
80 GB SATA HDD (20 gb NTFS: XP SP2; 20gb NTFS; 40gb NTFS)
Intel 845 chipset

Did all the CD checks, the disc is all fine, even works on my other computer. Can't load in the safe graphics mode either. Was having some problems with Fiesty, it always got stuck at 'intel_rng : FWH not detected'.

Any help is appreciated. If there's no solution, please mention the next best distro for normal usage, really want to ditch Windows forever.

---

### Post by Clonester on 2007-10-21
I'm having the same (or a similar) problem.  The CD boots but when I select "Start and Install", "Safe Graphics Mode" and "Check CD for errors" it locks up.

Laptop: AMD Sempron 3000+, 512 MB RAM, ATI Xpress 200, 40 GB IDE hard drive (currently not partitioned, NTFS, and Windows XP).

---

### Post by PmDematagoda on 2007-10-21
Why don't you try installing Ubuntu using the alternate CD?

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by arjun.attam on 2007-10-21
I was thinking of the alternate CD only, but will installing from the CLI help, without booting as the live cd?

---

### Post by SquishyMarbles on 2007-10-21
Is this a problem that could be fixed by hitting F6, and changing "splash" to "nosplash"?  I was trying desperately to boot the amd64 version, and somehow I had to re-figure this out.  I think it's amd64 specific, though.  Please let me know if that works or doesn't work.

---

### Post by peitschie on 2007-10-21
Something that may help provide us with more information...

After the splash screen appears, hit CTRL+ALT+F1, which should make the splash screen disappear and give you rolling text showing which things are being loaded.  If that works, post the last few entries on the forums here and we may be able to help you troubleshoot further :)

Clonester:
Sounds like either a bad burn of the ISO (is possible), or maybe even a hardware issue?!  Do you have another computer you can test the installer on?

---

### Post by arjun.attam on 2007-10-24
After the ctrl+alt+f1 thing, here's what I get at the very beginning:

Buffer I/O error on device fd0, logical block 0
Buffer I/O error on device fd0, logical block 0
Buffer I/O error on device fd0, logical block 0

Then, there's a series of lines coming out, and all that stops here:
[<c011e4b6>] native_apic_write_atomic+0x6/0x10
[<c011563d>]send_IPI_mask_bitmask+0x4d/0xc0
BUG: Unable to handle kernel paging request at virtual address 00074360
printing eip:
c0105822
*pde=00000000
Recursive die() failure, output supressed
Kernel panic - not syncing: Fatal exception in interrupt
BUG: Unable to handle kernel paging request at virtual address ffffd310
printing eip:
c011e466
*pde=00004067
*pte=367a2021
Oops: 0003 [#60]
SMP
Modules linked in: intel_agp slipchp pci_hotplug agpgart evdev battery squashfs loop unionfs nls_cp437 isofs sd_mod sg sr_mod cdrom 8139too usbhid hid ata_piix floppy 8139cp mii ata_generic libata scsi_mod elia_mod uhci_hcd usbcore thermal processor fan fuse apparmore commoncup
CPU:0
EIP: 0060: [<c011e4b6>] Not tainted VLI
EFLAGS: 00010006 (2.6.22-14-generic#1)
EIP is at native_apic_write_atomic+0.6/0.10

@SquishyMarbles:
nosplash doesn't help my cause

Thanks again.

---

### Post by Titonus on 2007-12-23
I'm having the same thing. Here are the last two lines sent.

[   70.729162] code: 27 00 00 00 00 8b 0d f0 24 3b c0 81 e9 00 20 00 00 01 c1 89 11 c3 eb 0d 90 90 90 90 90 90 90 90 90 90 90 90 90 8b 0d f0 24 3b c0 <87> 94 01 e0 ff ff c3 90 90 55 89 d5 57 56 89 ce 53 83 ec 10
[   70.731889] EIP: [<c011e4b6>] native_apic_write_atomic+0x6/0x10 ss:esp 0068:d5965e10

Nothing about an error was visable.

---

