---
title: "exception Emask"
date: 2007-12-30
forum: Installation &amp; Upgrades
---

### Post by emcus on 2007-12-30
I have tried to install Ubuntu as well as Xubuntu on a Celeron 1.8 GHz machine with an ASUS P4S8X-X motherboard without success. It starts of fine booting from the live CD, I select the first option and the progress bar shows for about 10 seconds before I get messages of the following kind:

[FONT="Courier New"]BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) [   84.362085] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action
0x2 frozen
[   84.362153] ata1.01: cmd a0/01:00:00:00:00/00:00:00:00:00/b0 tag 0 cdb 0x12 d
ata 96 in
[  114.988572] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  114.988644] ata1.01: cmd a0/01:00:00:00:00/00:00:00:00:00/b0 tag 0 cdb 0x5a d
ata 128 in[/FONT]

I get a few of these messages and then nothing happens. I have read a bit on the forum and tried
- different hard drives
- different ide channels
- hard drive and cd on different ide channels
- connecting a floppy drive
- without a floppy drive (with and without disabling it in BIOS)
- Ubuntu cd, Ubuntu alternate cd, Xubuntu cd (all with the same result)
- running the cd:s on another computer (works fine)
- different memory configurations (256-512 Mb)
- different cd players

Is my motherboard/processor doomed not to run Ubuntu/Xubuntu?

---

### Post by Partyboi2 on 2007-12-30
What happens if you try adding noapic acpi=off to the boot options?
At the Main menu Screen press F6 and at the end of the line add
```
noapic acpi=off
```
then press enter.
If it works you will need to add it to grub menu.lst

---

### Post by emcus on 2007-12-30
Thanks, but that gives the exact same result unfortunately.

---

### Post by dburnett77 on 2007-12-30
Need another spin of Ubuntu.  The ash shell is more picky than Bash.  Which, would be more compatible for booting.  I see you have someone's compiled version of "busy_box".

Try the official CD, and check the MD5 checksum.

Where the Ramdisk/Memory relay is being initialized, it looks like the cmds are choking, and trying to access memory at double rate.
In the case of Bash, this is done via mounting instead.  During the boot process, that is...

---

### Post by emcus on 2007-12-31
But I do have the official cd (I think, at least). I have downloaded it from [http://www.xubuntu.org/get](http://www.xubuntu.org/get). And the checksum matches the one on [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes).

---

### Post by Justin_C on 2007-12-31
I'm getting the same exact error messages emcus, and have been trying several different hard drive, cd-rom configurations as well, not to mention different ram configurations (not very many since I only have 2 x 1GB).  What are your specs? Maybe its a motherboard or processor issue?

---

### Post by Justin_C on 2007-12-31
Trying to do as much research on this exception emask and found several people with very similiar conditions to mine.  Also, it doesn't look like there is a solution to this problem.  Does this mean that ubuntu just can't see certain hard drives?

---

### Post by Partyboi2 on 2007-12-31
Here is a bug report relating to this. Not sure if this will help
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106864](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106864)

---

### Post by emcus on 2008-01-01
Nice to hear from someone else with the same problem. That means I'm not crazy after all...
These are the specs:
Motherboard - ASUS P4S8X-X S-478 533MHZ DDR LAN ATX 
Processor - INTEL CELERON 1.8GHZ 128KB CACHE 400MHZ SOCKET478
Memory - DIMM DDR 256MB PC2700 333MHZ, KVR (have tried with 1 and 2 units of this)
So you get the error even with a lot of memory?

---

### Post by Justin_C on 2008-01-01
Yes I did, and I have 2GB of memory!  I delted the ubuntu partition and restored my mbr until I can find an answer to our problem.  I'll post as soon as I can find more info.

---

### Post by Partyboi2 on 2008-01-04
Came across this post might be useful if using sata drive
[http://ubuntuforums.org/showthread.php?t=651872](http://ubuntuforums.org/showthread.php?t=651872)

---

### Post by emcus on 2008-01-13
I tried yet another cd player and now it works! Must have been a problem with both other ones I tried.
Thanks for your input!

---

### Post by slayer^_^ on 2008-03-09
i found that unplugging sata drives and the relative power cables, replugging them in a different order and, if you can, changing the data calbes with different ones was the solution. Give it a try (sata cables are perhaps more fragile than the legacy ide?)!

---

