---
title: "Installer recognizes hard-drive, but not NTFS partitions..."
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by gkverne on 2006-06-03
I've had great experiences with Ubuntu and Kubuntu in the past, and now that 6.06 is out, I thought I'd install it and see if I can finally get rid of XP.  In the past, when I've installed Ubuntu, I have been able to use the free 10GB between two of my NTFS partitions (out of three total) to install Ubuntu (and all of the other *nixes I've tried).

In the past, I could just ask the installer for manual control over partitioning, and then ask it for guided partitioning in the next menu, and it would create the needed / and swap partitions in my free space.

Now... when I get to the "partition" step in the install process, none of my partitions are recognized by the installer.  The installer shows my 300GB drive as blank, and offers to install using the entire drive.

So far in trying to figure this one out...

I've booted into a custom rescue cd and used PQMagic and Partition Table Doctor to make sure that my partition table and MBR are clean and intact.

I've re-built my partition table using PTDD to make sure that it wasn't some sort of non-standard configuration that was throwing the installer.

Booted back into Ubuntu's live CD, ran GParted (still nothing).

And I'm running out of ideas.  Has anyone had a similar experience?  Any ideas as to how to fix this on my end?

Thanks for listening.

---

### Post by jrd on 2006-06-03
Are you using Breezy now? If so why don't you just upgrade to Dapper through Adept? When you get to the partition screen what happens if you scroll down and select "manualy edit partitions" (Or something like that)?

---

### Post by gkverne on 2006-06-04
I should have made myself clear in my initial post, but no (right now) I'm not using linux at all.

My partition layout is as follows...

1 [Primary] NTFS label="System"
2 [Primary] NTFS label="Swap"
3 10GB Free Space (where I want to install Ubuntu)
4 [Primary] NTFS label="Home"

I've tired installing from my old Breezy disk, from the Desktop and Alternate Dapper disks, and I've just burned FC5 to try that as well.

Basically, when I start up GParted from the LiveCD, select "manual partitioning" in the installer, or try to install from my old Breezy CD (manually as well), my hard drive shows as "blank" (no partitions at all).

---

