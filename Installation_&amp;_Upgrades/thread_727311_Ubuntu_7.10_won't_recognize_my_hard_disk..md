---
title: "Ubuntu 7.10 won't recognize my hard disk."
date: 2008-03-17
forum: Installation &amp; Upgrades
---

### Post by mhoolehan on 2008-03-17
I'm trying to install 7.10 on my PC and the LiveCD boots up just fine (and checks out, so there are no errors there), but when the time comes to partition and install the hard drive is just not detected at all. I tried the GNOME partition tool, and it didn't register the disk, either. The installer *does* recognize my 512 MB flash drive, so obviously the problem doesn't lie in the installer. The drive is a Western Digital 80GB drive, and it's in good working order. The operating system on there right now is Ubuntu 6.10, which detected the drive and installed without a hitch (and this was just a few days ago).

---

### Post by taurus on 2008-03-17
Open a terminal from the LiveCD and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by mhoolehan on 2008-03-17
I get literally no output-- no error message, either, just a blank line.

I get the following output when I do the same command in Edgy:
```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9351    75111876   83  Linux
/dev/sda2            9352        9729     3036285    5  Extended
/dev/sda5            9352        9729     3036253+  82  Linux swap / Solaris
```

---

### Post by mhoolehan on 2008-03-17
Posting again to add: I just tried switching out my 80GB HD for an older drive I had (a 40GB Western Digital) and got the exact same problem with the Gutsy installer not detecting the hard drive; Edgy detects it just fine. So it's most likely not hardware failure in the hard disk!

---

### Post by PopnPaul on 2008-03-17
I have the exact same problem with my WD 80gb hdd.

---

### Post by mhoolehan on 2008-03-26
Updating to say that I managed to get Gutsy installed on the 40GB by using the alternate install CD, but now that it's installed it hangs on the boot-- it will boot into GRUB, but then go to a black screen and do nothing. Can anyone help me out?

---

### Post by chrisp6825 on 2008-03-28
Same problem here. I also have a WD 80 gig HD.
I think its the Western Digital thats messing up.

Right now I'm downloading the alternate cd so, I'll see how it goes from there.

kinda sucks though... i thought it was cause of my windows installation (i wanted to dual boot but thought it wasn't possible) so i formatted my hard drive completely. Now I know i didnt need to....



I'll post back with what happens after I try the alternate CD.

---

### Post by OhioLen on 2008-03-28
Looks like a pattern:

Gutsy LiveCD + dual-boot Windows + Western Digital = gparted can't detect HDD's

~~HARDWARE~~
**Invisible Western Digital HD0 mst, 40gb**
This drive is Linux and data on separate partitions:

13.4gb FAT32 ||| 1.0gb FAT32 | 8.46gb NTFS | 14.16 gb FAT32

First partition (left) is primary, active. Other 3 are logical drives in an extended partition. The FAT32's on the left are empty for Ubuntu and swap, the NTFS and FAT32 on the right are data that has to be kept safe.

**Invisible Maxtor HD1 slv, 10gb**
This drive is NTFS Win2kPro SP4 (some stuff I use doesn't work in WINE). One partition only, annoying but no big deal if wiped out. I know how to fix Windows.
~~/HARDWARE~~

The **WD 40gb** had a fully functioning installation of Feisty 3 days ago in exactly those partition spaces, but I wanted to start fresh with Gutsy. I killed the system and swap EXT3's (13.4gb & 1.0gb, respectively) from Win2kPro's disk management snap-in and just left them as unassigned space, but the liveCD's gparted didn't see either drive. 

Then I tried the old Win98/DOS version of FDISK with the same results, also ran FDISK /mbr to remove any residue from the earlier GRUB install. Jumped back into Win2K and partitioned again, formatting them with FAT32 for the broadest cross-compatibility. No dice. Gutsy simply can't see either of my hard drives, much less the shiny new FAT32 partitions that are sitting on HD0 waiting for it.

I guess I'll try the alternate CD and see if that works, but good grief. How is it that the next release is less than a month away and this serious installation bug hasn't been fixed yet? :confused:

---

### Post by robertchahine on 2008-03-28
try to install sdm or gparted from add/remove list

---

### Post by OhioLen on 2008-03-28
> **robertchahine said:**
> try to install sdm or gparted from add/remove list
WTF for? Gparted is native to the LiveCD, and it seems to be the problem in the first place. SDM isn't in that list, and even if it was you can't install anything to the LiveCD anyway...it's on READ-ONLY MEDIA!

The problem is not the CD itself: I MD5-checked the ISO, I had Nero verify the data post-burn, then ran Ubuntu's integrity check on first boot. All came back fine. 

That was a remarkably unhelpful comment.

---

### Post by robertchahine on 2008-03-28
> **mhoolehan said:**
> Updating to say that I managed to get Gutsy installed on the 40GB by using the alternate install CD, but now that it's installed it hangs on the boot-- it will boot into GRUB, but then go to a black screen and do nothing. Can anyone help me out?

did you tried to press ctrl+alt+F1 ?

---

### Post by robertchahine on 2008-03-28
> **OhioLen said:**
> WTF for? Gparted is native to the LiveCD, and it seems to be the problem in the first place. SDM isn't in that list, and even if it was you can't install anything to the LiveCD anyway...it's on READ-ONLY MEDIA!

The problem is not the CD itself: I MD5-checked the ISO, I had Nero verify the data post-burn, then ran Ubuntu's integrity check on first boot. All came back fine. 

That was a remarkably unhelpful comment.

i just misunderstood the subject, i thougt he's adding a new HDD to his pc.

---

### Post by OhioLen on 2008-03-28
I don't get this. After downloading and verifying the MD5, the alternate install CD doesn't see my HDD's either.  ](*,)

[LIST]
[*]They are both Basic (not Dynamic) disks.
[*]Prior versions of Ubuntu had no problem with either drive. 
[*]Win2k has been running on them in various configs for years (including *right now*). 
[*]A Win98 boot floppy's FDISK can see both drives and all partitions (EXT3 detected as NON-DOS).
[/LIST]

Apparently I can't install Ubuntu 7.10 on my machine. Guess I'll have to find an earlier release that can tell I own hard drives. This **FATAL ERROR** is making me reconsider the wisdom of buying a [_Dell laptop with 7.10 preinstalled_]("http://www.dell.com/content/topics/segtopic.aspx/linux_3x?c=us&cs=19&l=en&s=dhs"), and I *like* Ubuntu! Is the release team aware of this problem, since it's apparently not just me? Is there a workaround? WTF? :confused:

---

### Post by mhoolehan on 2008-03-29
> **OhioLen said:**
> Looks like a pattern:

Gutsy LiveCD + dual-boot Windows + Western Digital = gparted can't detect HDD's

I was not dual-booting Windows; it was a clean format and install and the operating system I was formatting from was Ubuntu Edgy.

And I figured out the black screen-- it was booting, it just takes *twenty minutes* to do so. I'll go ahead and blame that on Western Digital, too.

---

### Post by OhioLen on 2008-03-29
OK I had seen other dual-boot scenarios having similar problems and assumed you were in that category. But, as I sit here typing this response from my newly-reinstalled Feisty Fawn 7.04 (residing on the 2 Western Digital partitions I mentioned in an earlier post), somehow I don't think it's WD's fault. 

If Win2k/XP, Edgy and Feisty will all run/install flawlessly on any given HDD *but Gutsy won't*, then logically the problem has to be with Gutsy. This isn't hardware failure, it's an installation bug.

---

