---
title: "Vista Compatibility Problems?"
date: 2008-12-01
forum: Installation &amp; Upgrades
---

### Post by Gunmetal_Ghoul on 2008-12-01
I tried to boot the disk and install Ubuntu on my brand-new Sony Vaio (w/ Vista, of course), but right after the Linux Kernel loads up I am taken directly to the command line where I am shown some text that basically says the following: 

[B]BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash) 
Enter ‘help’ for a list of built-in commands.
(initramfs) [210.487401] ata 2.00: revalidation failed (errno=-5)
[210.503360] ata2: COMRESET failed (errno=-16)
[210.532900] ata2: exeption Emask 0x1 stct 0x0 Serr 0x0 action 0x0 t4
[210.532948] ata2: irq_stat 0x40000008[/B]

Is this some kinda compatibility issue w/ the Vista or something else I could never have guessed?

---

### Post by Mark Phelps on 2008-12-02
OK, from experience, you are going to run into problems loading Ubuntu onto a pre-installed Vista machine. You will need to create an empty space on your drive to make room for Ubuntu (unless you want to install it INSIDE Vista -- which is another whole set of issues), and you will be told it's OK to use the Ubuntu installer (or the GParted tool) to do that.  It is not!!  If you have a Vista DVD or Vista Recovery CD, you can try that (using Linux to shrink the Vista partition) and if it fails (which it does some times), you will need to boot using either Vista DVD/CD and run Startup Repair to restore your Vista boot.

Second, if you use the default LiveCD installer, it will overwrite your MBR, meaning that you will then be booting into GRUB instead of Vista -- which is OK if GRUB creates the correct entry to allow you to choose between Vista and Ubuntu.  While it usually does this, it doesn't always do this -- meaning that you will then have to learn about GRUB and how to modify the menu.lst file.

Third, strongly suggest that you boot into the LiveCD before you do an install.  This will give you first-hand experience regarding how well Ubuntu detects your hardware and loads the correct drivers.  Any hardware-related problems you notice running in LiveCD mode are likely to take a LOT of work resolving after you install.

Not badmouthing GNU/Linux or Ubuntu, I use it every day since switching over from Vista months ago, just letting you know that there is some "learning" involved in moving to Linux.  It's not yet the one-click-install-and-you're-done experience you may be used to in Windows.

---

### Post by Gunmetal_Ghoul on 2008-12-02
> **Mark Phelps said:**
> Not badmouthing GNU/Linux or Ubuntu, I use it every day since switching over from Vista months ago, just letting you know that there is some "learning" involved in moving to Linux.  It's not yet the one-click-install-and-you're-done experience you may be used to in Windows.

How sad...I'm disappointed but willing to go on with the installation. On another subject, would I expect similar problems with a computer running XP?

---

### Post by oilchangeguy on 2008-12-02
> **Gunmetal_Ghoul said:**
> How sad...I'm disappointed but willing to go on with the installation. On another subject, would I expect similar problems with a computer running XP?

the operating system already on the computer has nothing to do with trying to install ubuntu. if you're running the computer from a cd. the hard drive is not involved. most likely some hardware issue. try the alternate cd, it's a text based installer.

---

### Post by Gunmetal_Ghoul on 2008-12-03
Would that mean I would have to download and burn another ISO image again? Just downloading the thing took me 4 hours (somebody was playing WoW!) and I would need to invest a big hunk of my precious time to do it. It may just be worth it in the long run, though. Optimism is key...;).

---

### Post by caljohnsmith on 2008-12-03
> **oilchangeguy said:**
> the operating system already on the computer has nothing to do with trying to install ubuntu. 
Actually, that's not true in the case of Vista. As Mark Phelps pointed out, if you use Ubuntu's partition editor gparted to shrink a Vista partition, it will almost always break Vista until you can repair Vista using a Vista Install/Recovery CD. The reason is because Vista maintains its own partition table outside of the main partition table in the MBR (Master Boot Record), so using any partition tool other than Vista's Disk Management will not update Vista's own partition table with the new changes, causing Vista to temporarily break. Therefore, as Mark Phelps mentioned, it is much more ideal if you can use Vista's Disk Management to shrink the Vista partition to make room for Ubuntu so that Vista doesn't temporarily break and require fixing afterwards. Unfortunately though, often Vista will not let you shrink its partition past some point even though there is enough free space in the partition to do so; in that case there's not much choice but to use another tool like gparted to shrink Vista, and then just fix Vista afterwards. Fortunately, it's not usually a problem to fix Vista after-the-fact.

Gunmetal_Ghoul, you shouldn't need to download any other ISOs at this point if you can get the Ubuntu Live CD to work OK. When you boot the Live CD, do you at least get the first main menu where the first option is to "try Ubuntu without making changes"? If you can get that far, press F6 for "other options" at that menu, and then add the following option to the end of the text line:
```
acpi=off
``` 
See if that works to boot Ubuntu, and if not, try adding all the following options:
```
noapic nolapic acpi=off
```
How about giving that a shot and let us know how it goes.

---

### Post by oilchangeguy on 2008-12-03
> **caljohnsmith said:**
> Actually, that's not true in the case of Vista. As Mark Phelps pointed out, if you use Ubuntu's partition editor gparted to shrink a Vista partition, it will almost always break Vista until you can repair Vista using a Vista Install/Recovery CD. The reason is because Vista maintains its own partition table outside of the main partition table in the MBR (Master Boot Record), so using any partition tool other than Vista's Disk Management will not update Vista's own partition table with the new changes, causing Vista to temporarily break. Therefore, as Mark Phelps mentioned, it is much more ideal if you can use Vista's Disk Management to shrink the Vista partition to make room for Ubuntu so that Vista doesn't temporarily break and require fixing afterwards. Unfortunately though, often Vista will not let you shrink its partition past some point even though there is enough free space in the partition to do so; in that case there's not much choice but to use another tool like gparted to shrink Vista, and then just fix Vista afterwards. Fortunately, it's not usually a problem to fix Vista after-the-fact.

Gunmetal_Ghoul, you shouldn't need to download any other ISOs at this point if you can get the Ubuntu Live CD to work OK. Let us know if you run into any problems. :)

you're not reading the op's post correctly. they did not even get to the point of partitioning. and my answer is correct. if all that is being done with the live cd is to test drive ubuntu, no changes are made to the os already on the computer. and the op's problems are not related to vista, they are hardware related.

---

### Post by Mark Phelps on 2008-12-03
The op's original question concerned a possible incompatibility with Vista that was preventing Ubuntu from installing. The basic answer is no -- an installation of Vista will not prevent Ubuntu from installing.  The error message the op is getting has nothing whatsoever to do with Vista.

I added more comments to my original post because I was trying to prevent the op from hosing their Vista installation as a byproduct of getting their Ubuntu install to work.

I ran into a similar error message trying to install Xubuntu 7.10 on an old laptop using the LiveCD.  In that case, it had to do with insufficient memory to run the graphical installer properly and a weird requirement to have a diskette in the drive during installation.  Using the text installer (alternate CD) and inserting a blank diskette solved the "busybox" problem.

But I suspect with a newer machine, neither of these is the case.

---

### Post by Gunmetal_Ghoul on 2008-12-07
I have already downloaded the alternative installation ISO and have partitioned my hard drive and installed the dual-boot Ubuntu. The problem now is when I rebooted and chose to run Ubuntu the screen became scrambled and I could not go any further in the setup. Methinks that this must be a hardware problem, particularly with the video. This could be the last known obstacle before I become a happy Ubuntu user!

---

