---
title: "Ubuntu Installation Partition Problems"
date: 2008-02-27
forum: Installation &amp; Upgrades
---

### Post by OvenMitt Bandit on 2008-02-27
I am having some partition problems. I've seen alot of threads dealing with problems similar to mine, but none of the solutions given in those threads worked for me.

I wiped my 400GB hard drive and installed Windows XP. I then loaded the Ubuntu Gutsy disc and began the installation process. When I have installed Ubuntu in the past, the partition step had a slider that would let me choose how much space to take away from the NTFS partition and give to Ubuntu. This time, that option wasn't present, and it wouldn't let me install without writing over my Windows partition. I went into Gparted to try and shrink the NTFS partition, but it wouldn't let me, saying that the disk had bad sectors. I booted into Windows and ran chkdsk /f , and rebooted afterwards several times. Still no luck, it won't let me shrink my NTFS partition. I have no idea what to try now, any help or ideas would be greatly appreciated.

---

### Post by Pumalite on 2008-02-27
Try Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it.

---

### Post by dstew on 2008-02-27
You might have immovable files on your XP partitions. These are usually page files, like swap in Linux. You should go into Windows, memory control panel, virtual memory and turn off paging (disable page file). Reboot, then defragment. Then try and shrink again.

Sometimes it helps to remove the page file itself, after you turn off paging. I think its name is pagefile.sys.

---

### Post by OvenMitt Bandit on 2008-02-27
@Pumalite:
I booted using the Gparted disc, but it still gave me the same problems.

@dstew:
Going to try that right now. :)

---

### Post by Pumalite on 2008-02-27
I hope dstew's suggestion works. Otherwise, you might have a drive going south.
Check with:
[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)
Or:
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

---

### Post by OvenMitt Bandit on 2008-02-27
Yeah, so disabling Virtual Memory then defragmenting didn't work. I haven't tried actually deleting the pagefile.sys file, I guess I can try that next.

What exactly do the programs that you linked do, Pumalite? If they're just straight Data Recovery programs, I don't need them at the moment, because I have no data to recover....yet.

---

### Post by Pumalite on 2008-02-27
You can run all kind of tests on your hard drive. Read the documentation.

---

### Post by OvenMitt Bandit on 2008-02-27
The programs just said that the partition's structure was "ok". I think that I am just going to reformat once again and start over. My previous Ubuntu installations went off without a hitch, on the same hard drive, with more than 40GB of data on the Windows partition. Why it isn't working now, with a fresh Windows install with almost no other data on that partition, is a mystery to me.

---

