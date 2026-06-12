---
title: "Non-existant UUID number prevents boot up"
date: 2010-02-01
forum: Installation &amp; Upgrades
---

### Post by Caps18 on 2010-02-01
So, I put my two SATA hard drives in a new computer (new mb, cpu, no pci SATA adapter, built-in nVidia graphics), and I thought everything was going well. The Mythbuntu logo came up, but the bar at the bottom did not move. It eventually dropped me out to a (initramfs) prompt.

When I used the recovery mode, this is where it had problems:

[ 4.756000]ata1:SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 5.068000]ata2:SATA link down (SSTatus 0 SControl 300)
[ 5.552000]ata3:SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 5.864000]ata4:SATA link down (SSTatus 0 SControl 300)
[ 6.176000]ata5:SATA link down (SSTatus 0 SControl 300)
[ 6.488000]ata6:SATA link down (SSTatus 0 SControl 300)


*(After about 30-45 seconds)

Done.
Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/9d7cb373-3914-4d84-aab0-ddc4e7cb000c does not exist. Dropping to shell!



I had a SATA PCI card in my old computer, would adding that to the new system make it work? Or is there some way to fix this problem? Is there someway to update the UUID numbers (I think I have done this before).


Thanks!

---

### Post by byStanderone on 2010-02-01
...do a sudo blkid, and update your fstab file, hope this solves the problem.

---

### Post by djchandler on 2010-02-01
> **Caps18 said:**
> So, I put my two SATA hard drives in a new computer (new mb, cpu, no pci SATA adapter, built-in nVidia graphics), and I thought everything was going well. The Mythbuntu logo came up, but the bar at the bottom did not move. It eventually dropped me out to a (initramfs) prompt.

When I used the recovery mode, this is where it had problems:

[ 4.756000]ata1:SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 5.068000]ata2:SATA link down (SSTatus 0 SControl 300)
[ 5.552000]ata3:SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 5.864000]ata4:SATA link down (SSTatus 0 SControl 300)
[ 6.176000]ata5:SATA link down (SSTatus 0 SControl 300)
[ 6.488000]ata6:SATA link down (SSTatus 0 SControl 300)


*(After about 30-45 seconds)

Done.
Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/9d7cb373-3914-4d84-aab0-ddc4e7cb000c does not exist. Dropping to shell!



I had a SATA PCI card in my old computer, would adding that to the new system make it work? Or is there some way to fix this problem? Is there someway to update the UUID numbers (I think I have done this before).


Thanks!

Adding the old PCI SATA adapter will probably not help. and could actually make the system un-bootable due to inadequate power.

This is being caused by a hardware problem. Your computer read a UUID on the drive it was booting from, then couldn't find it anymore, probably due to less and less power flowing to it as you continued the boot process.

Three possibilities:

1. You need a new power supply. As the GPU was being called to do more work, it drained enough power from the overall system to cause part of your system to drop out. During boot up, especially with two drives in the system, the first device(s) to suffer from this power drain was (is/will be) your hard disk subsystem. This is many times the first indication that the power supply is inadequate, especially on an upgraded system.

2. The hard drive itself is going bad. If there was no indication of this on the prior system, see #1.

3. The least likely problem is the SATA interface or components thereof are faulty. If drives were properly detected and identified with full manufacturer and model name in BIOS and operated until the splash screen appeared, see #1.

Did you do an upgrade in an existing system where you swapped a motherboard, basically leaving everything else in place? If you swapped a motherboard/CPU/RAM combination significantly more powerful than the prior components, this is not unusual, especially upgrading from a system with fewer CPU cores than the new system.

To see if this may be the case, first try unplugging one of your SATA drives and see if it continues to boot-up. If it stops in the same place, that doesn't necessarily mean I'm wrong. But if it starts all the way up, that's a very good indication the power supply is inadequate. It's not bad necessarily, just too weak.

Please list your components, including your PS and wattage.

One thing you can't get away with on a multi-core system is a weak or intermittently weak power supply. Same holds true when upgrading graphics cards from integrated or mainstream to high performance. Good power supplies are expensive for very good reasons. And just because a manufacturer slaps a wattage rating on the box doesn't mean that's what it will output.

My suggestion is to get a power supply at least rated 50 watts if not 100 watts more than the motherboard manufacturer recommends, particularly when running a multi-core CPU and more than a couple of gigabytes of RAM. You may want to read some power supply reviews. In my recent experience, the power supply can easily be the weak link in an otherwise nicely specified system, particularly on a system running 24/7.

---

### Post by Caps18 on 2010-02-01
I'm pretty sure it is my fstab file.  I remember having to update that when I installed my second drive.  (I wrote a post about how that is a major problem for the Linux OS)

But I can't run blkid from the command prompt I get.  Is it hiding outside of /bin/sh?

(I have a 450 Watt power supply and no CD-Rom drive.  I only have a single core AMD 2 CPU.  I was using a 250 Watt power supply previously.)

---

### Post by presence1960 on 2010-02-01
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page and all credit is his.

---

### Post by Caps18 on 2010-02-01
There was one setting in the BIOS that needed to get switched from SATA to ACHI.

I was able to update the UUID for the second sdb drive, but I'm not sure that was a problem or not.  It didn't hurt anything.

Now on to updating the video card driver...

---

