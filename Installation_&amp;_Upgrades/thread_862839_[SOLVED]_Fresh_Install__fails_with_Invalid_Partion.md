---
title: "[SOLVED] Fresh Install  fails with Invalid Partion Table every time"
date: 2008-07-17
forum: Installation &amp; Upgrades
---

### Post by nrdlevans on 2008-07-17
I am having problems installing Ubuntu.  I recently dropped by Best Buy and purchased the latest copy of Ubuntu.  While I know I could have downloaded the software, I wanted to help promote the selling of Linux at a favorite retailer.

After having installed multiple flavors of Linux before I expected to plop my new CD into my drive, nuke all the partitions and load a fresh operating system.  The same physical hardware had previously had multiple flavors of Suse and Mandrake and should easily run Ubuntu.

Ubuntu does boot into the installation and installs.  Upon performing the initial boot, the system dies with a "Invalid Partition Table" message.  It does this if I use all the default or attempt to manually partition the drives.

I suspect the problem might be related to how Ubuntu sees the hard drives.  My system has two controllers holding a total of 4 IDE chains.  I have a single IDE drive which I plan on hosting the OS.  A Promise Ultra 133TX2 holds four 300 GB IDE drives which has, on other flavors, held a RAID system.  I completely wiped all drives prior to installation.

Other Linux flavors see the motherboards IDE drive first, Ubuntu sees the Promise drives first.  Ubuntu identifies the first drive as sda through sdd.  The motherboards drive is seen as sde.

If I physically remove the promise controller or the motherboard ide chain things work.  If I keep them both installed everything dies.

Anyone have any good ideas for me?

---

### Post by tommcd on 2008-07-17
Remove the Promise controller and disconnect all the drives except the one IDE drive that you plan to install Ubuntu on. I assume this hard drive is plugged into the IDE controller on the motherboard. Is that right? You may need to disable RAID in the BIOS also. Once you get Ubuntu installed to this one drive you can add the other drives later and create mount points for them and use them how ever you want.
What chipset does the motherboard have?

Oh, and welcome to the Ubuntu forums!!!

I didn't know Best Buy was now selling Ubuntu. Did you get the current version, 8.04 "Hardy Heron"?

---

### Post by Sef on 2008-07-18
> I didn't know Best Buy was now selling Ubuntu. Did you get the current version, 8.04 "Hardy Heron"?

8.04, Hardy Heron is what Best Buy is selling.

---

### Post by nrdlevans on 2008-07-18
Yes, Best Buy is selling 8.04.  I felt that for $20.00, I could afford to support the effort.  Now if more folks would do so.


While I can remove the controller, I was hoping to avoid cracking the case open.  I gather that no boot option exists for the installer then?

---

### Post by nrdlevans on 2008-07-18
Thank you for your assistance.  Upon removal of my promise card, the system installed without issues.  I was then able to reconnect the drives.

Problems solved for now.:)

---

