---
title: "Filesystems (/home)"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by cc48510 on 2007-10-21
I currently have Windows XP and Kubuntu 7.10 dual booting with the following partitions:

/ (root) - ext3 (8 GB)
/home - ext3 (8GB)
swap (2 GB)
/windows - NTFS (Windows XP Pro. SP2 installation - remaining free space)

I recently purchased a 120GB USB Hard Drive that I would like to install Kubuntu 7.10 on. I would like to have my /home directory accessible from both Kubuntu (on the USB Drive) and Windows XP (on the Internal IDE Drive). Ideally, I would like to remove Kubuntu from the internal IDE Drive and make it strictly Windows XP and the USB Hard Drive would be strictly Kubuntu 7.10 so that I would no longer have to have both systems on one drive [not to mention it would free up some more space - on the Windows HD - for my iTunes library to expand]. Would it be possible to use an NTFS partition for /home as my understanding is that 7.10 now has full support for NTFS (read and write) ? If not, could I use FAT32  or something else that both systems support ? Does /home have to be ext2/ext3 ?

/ (root) - ext3 (8 GB)
swap (2 GB)
/home - NTFS (or FAT32) (110 GB)

---

### Post by MrNiceguy on 2007-10-21
I too am trying to find out how to run /home from an NTFS partition.  I get an error during the install if I try to set it up that way.  Anyone know how to bypass this?  According to the NTFS-3G page, you can even run /root from NTFS, so /home should be doable.  I'm downloading the alternative install disk now to see if it's more cooperative.

One thing that does work is to set up /home on an ext3 partition, the install the Windows ext3 driver.  I currently have my laptop set up that way.  The only problem with it is that if Linux doesn't shut down properly, then Windows can't access the drive.  To fix, simply boot into Linux, then shut down and restart properly.

You can get the ext3 driver for Windows here:  [http://www.fs-driver.org/]("http://www.fs-driver.org/")

I can't remember if I've ever installed with /home on FAT32.  I know I've considered it but I can't remember if I actually followed through.

I will suggest that you move "My Documents" to a sub-folder of your home directory, rather than setting your home directory as "My Documents".  Linux drops so much stuff in the home directory that it looks really crowded under Windows.  All the files and directories that are hidden under Linux show up in Windows.

One thing that's really handy on a dual-boot machine is to set Firefox to use the same profile under both operating systems.  Hit up Google for the process - it's very simple to do and well worth the effort.

---

### Post by MrNiceguy on 2007-10-22
I just found a problem with using FAT32 for /home.  FAT32 doesn't support links.  I think that NTFS has the same problem, but if anyone knows otherwise, feel free to correct me.

Too bad.  I'd really like to use NTFS for /home.  I guess it's back to my old system with the Windows Ext3 driver.

---

