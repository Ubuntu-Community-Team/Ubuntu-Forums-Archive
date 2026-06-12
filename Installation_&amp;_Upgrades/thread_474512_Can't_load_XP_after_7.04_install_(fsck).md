---
title: "Can't load XP after 7.04 install (fsck?)"
date: 2007-06-15
forum: Installation &amp; Upgrades
---

### Post by ubanksy on 2007-06-15
I have a IBM T41 notebook that I'm trying to get dual boot (via GRUB) working on, but after installing Ubuntu 7.04 (off Alternate CD) I can never load Windows XP after this.  - I get the Windows BSOD with an UNMOUNTABLE_BOOT_VOLUME error message.

I think it's related to the following error I get during first Linux boot:

fsck died with exit status 3

Here's the way I have been doing it:

-delete all existing partitions on 35GB HDD via gParted
-install XP off CD, but only create a 25GB NTFS partition
-disable swap space, defrag drive a few times
-install Ubuntu 7.04 off Alternate CD, manually configure the following partitions roughly as per [http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm) (but don't have resize NTFS)

At the first boot of Ubuntu, there is a lot of text before the splash screen loads.  What I believe is relevant is the following (hard to read accurately as I took a photo of page instead of viewing a log):

[...]
Checking root file system [...]
fsck 1.40 WIP [...]
/dev/sda2: Superblock last mount time is in the future
/dev/sda2: Superblock last write time is in the future
/dev/sda2 has gone 49710 days without being checked, check forced
/dev/sda2 ***** REBOOT LINUX *****
/dev/sda2: 103796/1221600 files (0.4% non-contiguous), 546639/2440800 blocks [...]
fsck died with exit status 3

The file system check corrected errors on the root partition
but requested that the system be restarted
[...]

Ubuntu then restarts, and runs perfectly.  It can even read the Windows XP NTFS drive.

GRUB gives me the choice to boot into Windows XP, which if I try successfully hands over to the Windows Boot loader, which then immediately Blue Screens (BSOD) with UNMOUNTABLE_BOOT_VOLUME.

I have replaced GRUB with Windows boot loader via SuperGrub, and tried running Repair Mode under XP's install CD (to run chkdsk) but it reports an unfixable error.  The fact I can see the files via Ubuntu (and of course gParted shows the partition being there) stumps me.

Any ideas or workarounds?  Have seen threads that hint towards timezones being a problem, but I'm not convinced.  

Thanks, Rich

---

### Post by Herman on 2007-06-15
Hello ubanksy,
It's fairly normal for your newly installed Feisty to do a file system check before it boots completely for the first time. All my i386 Alternate CD installs seem to do that for some reason, but my AMD64 Alternate CD install didn't.

You can read the official documentation for how to resize partitions with GParted, especially NTFS partitions here, [http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)
Note that it recommends you reboot Windows and let Windows run its own file system check on the partition before performing any more operations.

Probably all your NTFS partition needs is a good file system check. [GParted -- LiveCD]("http://gparted.sourceforge.net/") has its own file system check now for NTFS, you might be able to use that, or you could use your Windows CD.                Just put in your Windows XP install CD, and boot into the [recovery console]("http://www.kellys-korner-xp.com/win_xp_rec.htm") and use the  'chkdsk /r' command.
That should fix it.

Regards, Herman :D

---

### Post by ubanksy on 2007-06-15
Thanks Herman.  I have rebuilt the machine again and am stuck with the same problem.  During the first boot of Ubuntu fsck ran and failed (but not on subsequent boots).  Boot failure error: 

[IMG]http://i77.photobucket.com/albums/j43/pbanksy/boot2.jpg[/IMG]

I'm not concerned the fsck is running, but I am concerned that it's failing.
After booting into Ubuntu and playing around (even viewing the NTFS files) I tried booting into windows (via GRUB) but it fails with the blue screen of death.

After that I did the following:
-ran gParted Live CD and checked the NTFS partition (took 1 second) - it gave no feedback as to whether it found or fixed anything (suspect it didnt')
-tried booting into Windows and got the BSOD
-restarted and inserted the XP CD and went to the Recovery console.

[...]
C:>dir
Directory of C:\

An error occurred during directory enumeration.

C:\>chkdsk

The volume appears to contain one of more unrecoverable problems.

C:\>chkdsk /r

The volume appears to contain one of more unrecoverable problems.
[...]

Note at this stage the MBR still has GRUB in it, so that may confuse the XP CD?

Note if I don't go into recovery mode of the XP CD, and instead go into Install / Setup area, it only detects the following on the drive to install Windows onto:

C: Partition1 [Unknown] 34274 MB ( 34274 MB free)

At this stage I cancelled the XP setup and have booted back into Ubuntu - still works fine and can still view the NTFS partition via Nautilus.

Any other ideas?  I have replicated my current situation 3 or 4 times now.  Should I try installing Ubuntu but not doing the disk stuff manually?

---

### Post by ubanksy on 2007-06-15
SOLVED!  Google came good and found the following:

IBM Thinkpads have a thing called the PreDesktop area (stores the OS image) - Windows can't see this - hence the 35 GB figure above seen in XP despite it being a 40 GB HDD.  However Linux can see the 'hidden' area, so it adjusts the partitions / MBR that freaks out Windows.

So all I had to do was disable PreDesktop via the BIOS Setup, then Security -> Predesktop Area -> Disabled.  F10 Save and Exit

It's flagged as a Ubuntu bug here and has more details for Thinkpadders:

[https://bugs.launchpad.net/ubuntu/+bug/25451]("https://bugs.launchpad.net/ubuntu/+bug/25451")

---

### Post by Herman on 2007-06-15
Wow! I never would have thought of that! Thanks for sharing, I'll have to bookmark that and study up on it.
Regards, Herman  :D

---

