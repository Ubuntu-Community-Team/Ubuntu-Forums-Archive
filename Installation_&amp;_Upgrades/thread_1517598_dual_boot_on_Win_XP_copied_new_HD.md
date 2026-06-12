---
title: "dual boot on Win XP copied new HD"
date: 2010-06-25
forum: Installation &amp; Upgrades
---

### Post by mkham on 2010-06-25
Can anyone give me links for installing Lucid on an single disk Win XP with 5 partitions as a separate DUAL BOOT system - esp screen shots? I want to install it in a 8gig EXT3 partition without touching or messing up the others, but the default seems to want unassigned space. I want to make sure I pick the right alternatives, which are never properly explained on installation.

This is a new bigger laptop hard drive that I copied over the Win XP partition (1), 2 data partitions (from an external drive), a 8.04 Ubuntu Ext3 partition (which I finally formatted with GParted), and a last NTFS partition. If you say "install inside a partition", will it also make the SWAP partition from that space?  It had GRUB on it, when I formatted the Ubuntu on the old drive, I lost the GRUB on that partition so it wouldn't boot without installing syslinux w SUPERGRUB boot disk. 

On the new disk that hasn't been done, so it won't boot as of now. **Will installing Lucid Lynx with GRUB2 find the Win XP and make the proper shortcut to it or should I fix the MBR w SUPERGRUB disk or something else first?**

I have a Acer Aspire 5003Wlmi Turion 64 ML32 1.8Gh, 1gig ram. Before I used the AMD64 Hardy, but was disappointed at limitations of software I could use (and never knowing what would work or not). After a half year, the Hardy broke irretrievably and I could never login (even with every trick). Do you recommend using the i386 or AMD64 version of LL? Any known problems with Lucid Lynx on this machine (now 4 years old)?
Thanks, all.

---

### Post by darkod on 2010-06-25
OK, one thing at a time.
1. Of course deleting the 8.04 made grub unbootable. You needed to restore the windows bootloader from XP after that (or before that even better), not use SGD. Lot of people seem to recommend SGD but I say stay away from it, especially if planning to use linux on your computer. SGD can mix up the grub versions and get you into real trouble. Any linux version you decide to use will come with its own bootloader.

2. It's best to make XP boot first, to make sure it's booting fine. If it isn't, it won't be after installing Lucid too and you won't be sure if Lucid is to blame. Even if you don't have XP install cd, it's easy to install generic mbr with linux tools. Just boot the Lucid cd in live mode and under assumption your hdd is /dev/sda, in terminal execute:
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

After the first command there will be some warnings about Lilo, ignore them, you will not use it anyway. Just ignore them and once the command prompt shows run the second command. After that rebooting should load XP directly.

3. You can install Lucid into your 8.04 partition but it can't create a swap partition out of it too. One option if you want swap partition is during the Manual Partitioning in the installer to delete the 8GB partition, and in its place create a partition for / and for swap. Although 8GB is rather small to have swap in that too.
Otherwise, for simply using the existing partition, use Manual Partitioning in the installer, click on it and the Change button at bottom, select filesystem (ext4 or ext3, as you wish), mount point / and tick the format box.

4. I have no problems running 64bit Lucid, it's up to you which version you want to use. Try the live mode first and that would show you potential issues.

Otherwise, here are screenshots of 9.10, Lucid is almost identical if not 100% identical:
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

But they don't pay too much attention to manual partitioning. With the above info I'm sure you'll get it right.

5. After installing Lucid and grub2 to the MBR it should detect and boot XP just fine, provided XP worked fine on its own in point 2.

---

### Post by mkham on 2010-06-26
Thanks. But if the Windows booted fine before, the Windows boot info must still be there,  GRUB just made a shortcut to itself on Ubuntu, where it must have had the redirect back to boot sector or Windows partition to run Windows. Won't Grub2 do the same thing- analyze the system, figure out where Windows is, install its pointer in the boot sector, then make the menu to boot Lucid or Windows?? Wasn't the MBR reformed by expanding the Linux partition to 8gig with GParted? 

Can that MBR instruction mess up the other full data partitions? Is that designed to boot the first active partition, or to boot Windows only.

---

### Post by darkod on 2010-06-26
I didn't understand anything except the last question. Booting doesn't work by "shortcuts". Yes, grub2 from the new install will find XP and create the dual boot menu, provided the XP boot process is fine.

The commands to install generic mbr can't do anything to the data on any partition. And yes, it is designed to boot the partition with the boot flag on, which should still be your XP partition.

Trying to see if XP will boot is just a precaution. You can skip 1 and 2 and start directly from point 3.

---

### Post by mkham on 2010-06-27
Jeez Darkman, you're the expert. Either it has to boot OK in XP first, or it doesn't and GRUB2 finds it and boots it fine?

Since I copied C drive + others with GParted, another post said I had no MBR at all, which maybe I need to make, or doesn't GRUB2 do this? Doesn't adjusting any partition with GParted rewrite the whole MBR, or just for that partition? I don't know, but are you sure that LILO MBR maker works- that it's more or less the same as XP MBR, or recognized as such by Grub2, once that's installed? Lilo just looks at the disk and makes a master boot record of all the partitions, right? 

I'm just afraid of destroying my XP and other data partitions, because I accidentally did that with SuperGrub Disk, before I understood that right arrow was ENTER (argh).  Anybody else have any ideas??????????

---

### Post by oldfred on 2010-06-27
Grub or grub2 do not use the windows MBR for booting. Windows MBR or Lilo only have logic to scan the partition table in the MBR and find a boot flag (active partition in windows speak) and jump to the PBR or partition boot sector to continue booting. 

Grub skips the MBR and just jumps to the PBR to boot windows. Windows has to be working for grub to be able to boot it.

Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by Sub101 on 2010-06-27
> **mkham said:**
> 
This is a new bigger laptop hard drive that I copied over the Win XP partition (1), 2 data partitions (from an external drive)

I would check XP is working before continuing. My understanding of what you have done is that you have copied XP to your current PC from another source, rather than installing? 

If this is the case I would be very suprised if it would boot at all.... not to mention any legalities.

---

### Post by mkham on 2010-06-27
Yeah, if GRUB2 jumps to the PBR, i think it doesn't need anything- according to GParted, the partition is ACTIVE or BOOT, but what is the LBA flag someone said to set on the active partition?  Before Windows didn't boot up when I first tried this 8 months ago, but I got it working beautifully with SuperGrub Disk (fix Win + MBR, I think), so presumably a normal Lucid Grub2 installation should find and boot it....   I think. Then I accidentally destroyed the C drive trying to reinstall GRUB1 with the SuperGrub Disk (I didn't know right arrow was ENTER).

---

