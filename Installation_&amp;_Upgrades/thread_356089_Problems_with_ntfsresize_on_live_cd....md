---
title: "Problems with ntfsresize on live cd..."
date: 2007-02-08
forum: Installation &amp; Upgrades
---

### Post by lan56 on 2007-02-08
Hello,

I am trying to install Xubuntu 6.10 and make a dual boot computer alongside Windows XP SP2. I am installing from a live cd I burned. Everything is smooth until I reach the part where the installer asks about partitioning. I can't use the installer's partition GUI (gparted) because my hard disk has "at least" 14 bad sectors (yes, I have already done chkdsk and stuff to give it some care) and I need to pass along the "--bad-sectors" option to ntfsresize, which gparted has no way of letting me do. So, I tried partitioning using ntfsresize manually through the terminal. It goes smooth, but a few minutes after it says, "Resetting $LogFile ... (this might take a while)", it then crashes and reports, "*** glibc detected *** double free or corrupted" and aborts. I have defragged my hard drive twice on Windows and have run chkdsk /r /f once and both of those completed normally. Every time I try ntfsresize it gives the same error and the exact same time.

Any ideas?

Thanks,
-lan56

---

### Post by Vox754 on 2007-02-08
You could try a different Live CD. You could use Knoppix (also based on Debian) or the GParted Live CD.
It seems, though, that yours is a hardware problem, so no application might work correctly. Bad luck maybe.

I originally had a single 80 GB NTFS partition for Windows XP. I defragmented the disk many times, then used the SUSE Linux installation DVD to resize the partition to 30 GB. After that I've been using the Knoppix CD with good results.

---

