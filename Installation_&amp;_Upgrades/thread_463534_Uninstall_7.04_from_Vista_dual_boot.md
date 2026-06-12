---
title: "Uninstall 7.04 from Vista dual boot"
date: 2007-06-03
forum: Installation &amp; Upgrades
---

### Post by paraplier on 2007-06-03
Too many problems with ATI card. I want to go back to just win Vista.  so what is the best way to uninstall 7.04 from a Vista dual boot? I am using the boot selector that installed with Umbuntu.

I have a partition utility that can see and act upon the Ubuntu partition from within Windows if simply reformating the partition is a safe and easy way to go.

TIA
Paraplier

P.S. I did a search for keyword "uninstall" site wide and didn't find anything specific. Plus I browsed about ten pages deep in this and a few other categories and still came up empty.

---

### Post by Bohlio on 2007-06-03
I think just deleting the partition and then expanding the Windows partition to fill the empty space is the way to go. I dont know what to do about the boot selector (Im pretty sure its Grub).

But i could be wrong, Im by no means an expert :-)

---

### Post by louieb on 2007-06-03
make sure it boots visa without going through the grub menu the grub program is inside your ubuntu install. deleting ubuntu before getting it to boot straight to vista will leave you with no boot able operating system at all.

---

### Post by Frederick J. Harris on 2007-06-04
I'd be very careful with this.  Last week I decided to re-install Windows 2000 on an old laptop that I was dual booting for awhile with Xubuntu and Win 2000.  I decided to just stick the Win 2000 Restore disk in and just give it the whole computer.  The Restore program was an operating system image of Win 2000 which of course is self-bootable.  All it did was copy the files and did nothing to re-pair the master boot record.  After I tried to start windows the 'Loading Grub' screen came up, then reported a Grub Error Message, and the thing locked up.  No doubt the Win 2000 re-install overwrote part of the Grub bootstrapping sequence without repairing the MBR and I was SOL!  To fix it I had to re-format some FAT16 partitions so that I could get a DOS boot disk to work.  I had an old set of DOS 6.21 disks (3) and when I booted from them and ran Setup it must have FDISK'ed and MBR'ed the disk, cuz after that I was able to re-install Win 2000.

In terms of severity of damage to a computer, I'd rate destroying its master boot record just a tad below grabbing a big hammer, rearing back, and clobbering it.  Dual booting two operating systems on a computer sounds really neat, but what I've just described is the down side few people realize.

---

### Post by paraplier on 2007-06-04
Thanks all for your replies. I'm amazed that I can find no documentation on uninstalling ubuntu from a dual boot. Anyway, I'm almost back to normal. See my post above with the title "Uninstall Grub?

Thanks again,
paraplier

---

### Post by louieb on 2007-06-04
> **paraplier said:**
> Thanks all for your replies. I'm amazed that I can find no documentation on uninstalling ubuntu from a dual boot. Anyway, I'm almost back to normal. See my post above with the title "Uninstall Grub?
Thanks again,
paraplier
You did not look very hard or your like the song and looked for love in all the wrong places. The folks in Redmon are all to happy to help.
[How to Remove Linux and Install Windows on Your Computer]("http://support.microsoft.com/kb/247804")

---

### Post by Frederick J. Harris on 2007-06-04
I just read that link to Microsoft and I want to thank you for it.  Essentially, that is what I did in a somewhat indirect way.

I'm interested in this issue due to the fact that I still have a dual boot setup with Win XP and Ubuntu 6.1 on my 'good' computer, which I can't afford to get 'screwed up'.  I'm not anti-linux or anything like that.  I'm still trying to learn Linux, but at the level I'm approaching it it is difficult (learning xlib programming and so forth).

Back around 2000 or so I played around with Partition Magic and Caldera Open Linux on a Win 95 desktop.  I still have it on that machine, but I never managed to learn Linux.  I just didn't 'make it'.  Now I'm trying again.  I seem to remember though that with Partition Magic (now owned by Symantic), when it installed its own boot manager program to support dual booting, it made a copy of all the original MBR, VBR, etc. stuff it changed so that it could be un-installed if the user wanted to revert the computer to its original configuration.  I can't imagine that GRUB doesn't have some such capability.  If it does it would be good to post that somewhere in documentation, the Ubuntu Wiki, or something?  

What I'm guessing happened in my circumstance with that old Compaq Win 2000 I mentioned (and this is only my guess), when I installed Xubuntu as a dual boot with Win 2000, it probably inserted code into the first several hundred bytes of the MBR which then branched execution to wherever GRUB was stored, and the bootstrapping process with loading the Linux OS continued from there.  When I decided to just re-install the Win 2000 OS on the whole disk and eliminate Linux on that computer, Compaq's restore disk just recopied the OS to the disk, believing the MBR and bootstrapping mechanism was already in place.  It would have been had I not modified it by installing a Linux dual boot setup.  I might also point out that repartitioning alone DID NOT solve the problem.  After the re-install failure I repartitioned the whole harddrive with Acronis Disk Director suite running from a bootable CD, and according to this suite I had a perfect NTFS 20 gigabyte partition to which Win 2000 could be re-installed.  However, the partition info in the MBR might have been right, but the MBR code wasn't.  It was still trying to execute the old Grub inserted code to load Linux.

After doing quite a bit of research on the issue, I determined that there are three ways to fix the problem, i.e.,

1) If Windows 'Recovery Console' is installed and working, its FIXMBR command can be used.  That didn't help me as I had never installed the recovery console on that computer.  I had a Win 2000 install CD from Microsoft in addition to my 'Restore' CD from Compaq, but it wasn't 'self-booting', so was of no help;

2)Use FDISK from DOS.  I made a DOS boot disk, but it wouldn't recognize my C drive, as DOS doesn't recognize any file system (I think I'm right on this) but FAT16.  So that couldn't directly be done;

3)Use a 'disk editor' to write a correct MBR back on the disk.  This should conceptually work, but I don't have the knowledge of how to do it.  I doubt there are very many folks who could.  

After quite a bit of grief I realized I could get the problem solved by re-partitioning to FAT16 so the disk could be recognized by a DOS bootable disk and then FDISK it.  As I hope folks can realize, this is a pretty severe problem.  For awhile I thought the computer was 'done for'.   But now I've got it working like a charm again, and I'll probably at some point set it up again as a dual boot, but I'm a bit wiser now (and I made sure to install recovery console in Win 2000 this time).

But if there is some GRUB command or utility to replace the original MBR record, I believe that would be a major solution here.

---

### Post by Ted Nancy on 2007-06-07
Listen to the caution from LuisB above. Do not delete any partitions without first making sure Vista boots normally.

I had a similar problem. An OEM vista disc from HP, no restore partition to work with, and no desire to just restore factory default.

Here is what worked for me:

Download MbrFix.exe from [www.sysint.no](www.sysint.no) (click the downloads link, and read over the readme link beside the download link to the file.)

Then do from Vista:

>Start >Accessories and right-click "command prompt" and then choose "run as administrator"

Then type (without quotes):

"MbrFix /drive 0 fixmbr /vista"

And reboot. Grub should be gone and Vista should boot normally. If not, you'll have to review the documentation. It could be that drive should not = 0.

Once Vista boots normally, go to control panel and use the disk management utility to delete the non-windows partitions. Reboot again. Then use the same utility to expand the Vista partiiton to full size of hard disk.

Best,

---

### Post by phuturism on 2007-06-07
> **Ted Nancy said:**
> Listen to the caution from LuisB above. Do not delete any partitions without first making sure Vista boots normally.

I had a similar problem. An OEM vista disc from HP, no restore partition to work with, and no desire to just restore factory default.

Here is what worked for me:

Download MbrFix.exe from [www.sysint.no](www.sysint.no) (click the downloads link, and read over the readme link beside the download link to the file.)

Then do from Vista:

>Start >Accessories and right-click "command prompt" and then choose "run as administrator"

Then type (without quotes):

"MbrFix /drive 0 fixmbr /vista"

And reboot. Grub should be gone and Vista should boot normally. If not, you'll have to review the documentation. It could be that drive should not = 0.

Once Vista boots normally, go to control panel and use the disk management utility to delete the non-windows partitions. Reboot again. Then use the same utility to expand the Vista partiiton to full size of hard disk.

Best,

Can you do the same for an XP/fiesty dual boot?  I need to remove fiesty from my work PC - thankfully we have a dedicated ubuntu pc in the office now so I don't need fiesty on it.

would I replace "vista" with "xp" or "winxp"?

thanks

---

### Post by Ted Nancy on 2007-06-08
I have not tested this myself, as I had an XP disc and used recovery console when I needed to restore the MBR, however, the documentation on MbrFix says to just run the same command without the /vista switch.

---

### Post by phuturism on 2007-06-16
Thanks Ted.

---

