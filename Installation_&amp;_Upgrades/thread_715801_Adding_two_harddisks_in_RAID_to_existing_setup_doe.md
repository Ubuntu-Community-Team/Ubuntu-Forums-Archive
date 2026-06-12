---
title: "Adding two harddisks in RAID to existing setup does not work"
date: 2008-03-05
forum: Installation &amp; Upgrades
---

### Post by BSalters on 2008-03-05
As a beginner, I have a freshly installed working Ubuntu install, on a single IDE harddrive. No problems here.

Now I am trying to add two SATA disks (in RAID if possible) to the systems. After turning the PC back on, Ubuntu fails halfway during the bootprocess, and I get a command prompt :
Busybox v1.1.3
Built-in shell (ash)
(initramfs) __

Now here perhaps is a reason. The SATA disks contain my (working) Windows Vista setup, in RAID0 setup. My ultimate goal is to obtain a dual-boot system, but so far I would be quite happy already if Ubuntu would just start.

I have read that dmraid is to be used for RAID arrays. I have two questions though:
- Is dmraid also required if I only want to be able to *boot*? That is, not even read-only access required, let alone write access. 
- Is installing dmraid truly safe for existing data on the new SATA drives? Of course, partitioning, formatting or creating new RAID arrays will destroy data on these disks. But can anyone guarantee that installing dmraid -such that the disks are correctly recognized - does not destroy data?

Thanks!

---

### Post by dgray_from_dc on 2008-03-05
I'm not sure I fully understand, was your preexisting RAID setup created by Vista?

If so, I don't know that Linux software RAID will be able to use it.

Was this a hardware implemented raid0?

If so, check to determine whether or not the hardware is supported.

Also, mdadm is the **software** raid app of choice.

Hope that helps!

---

### Post by BSalters on 2008-03-05
Yes, the RAID array was 'created ' using Vista. Well, to be more precise : created in the BIOS utility, and then VISTA was installed onto it. To install Ubuntu, I unplugged the two drives, and inserted a fresh new IDE disk (Safety first : you cannot accidentally erase disks if they are unplugged :))

That worked nicely, Ubuntu starts like a charm, and most stuff seems to work straight out of the box. Of course I now want to use my 'old' SATA disks as well. However, when connecting these, Ubuntu does not start at all.(well, aborts somewhere during the boot process).

Some system information:
Asus P5K-e motherboard with Intel ICH9R RAID controller onboard.
Q6600 
1* 160 GB IDE, for Ubuntu.
2*Samsung 500 GB Sata disks (in RAID0; hold previously installed Vista)

So, what do I do now? "Upgrade" or alter my current Ubuntu installation (while the RAID disks are unplugged)?

---

### Post by dgray_from_dc on 2008-03-05
This looks to be a hardware implemented RAID array.  (The hardware being your motherboard's built-in controller).  I doubt Vista explicitly set up your array (I could be wrong).  Linux may not be able to identify the hardware in the RAID configuration.  Your best bet is to try and determine whether or not Linux supports that board and/or chipset.  Perhaps searching for the ICH9R here or (if you can't find anything) starting a new thread with the ICH9R in the title.

---

### Post by BSalters on 2008-03-06
Hmm, from what I understood so far from my own attempts to solve this problem, all these "onboard" RAID controllers are no "real" RAID controllers. Instead, the CPU does all the processing for the RAID array. The motherboard only supplies some BIOS setup routine for RAID arrays, and (hence?) it is also possible to boot from such a RAID array.

I have once read a comment that "unless you pay >$200, it is NOT a real RAID controller".

Anyway, I know from watching the bootprocess (-nosplash and silent options), that the HDs are in fact recognized. That is, I see lines stating the drives, including size and name (Samsung 500 GB). To me it sounds they are at least detected! At some point, "hda" and "hdb" are 'assigned'.

Does this mean i still need to figure out whether Ubuntu supports the ICH9R chipset on the ASUS P5K-e motherboard? Or can that be answered positively already, based on the above?

---

### Post by dgray_from_dc on 2008-03-06
I think you're right.  It looks like the drives have been detected.

One thing that interests me is that you said that they were being assigned hda and hdb.  What is the designator for your boot disk?

If your PC is somehow booting from the third drive and then getting confused then that may explain it.

I remember you saying that these disks were disconnected when you did your initial install.  In that case, the IDE drive was identified as hda was it not?  What is it now that the SATA drives are in?

---

### Post by BSalters on 2008-03-06
I am almost certain the IDE drive is detected as 'hdc' when the SATA drives are plugged in. Without these drives being plugged in, I assume it was hda for the IDE drive.

I will *check* this when I get home again.... Is there an easy way for that by the way? Currently, I make a movie with my digital camera of the bootprocess (with 'nosplash' enabled), since hundreds of lines of text fly by, and I haven't found any option yet to log it to a file I can subsequently read from that (initramfs) prompt.....

---

### Post by BSalters on 2008-03-09
Ok, checked a few details:

- Started from the live-CD with my 2 SATA RAID disks + 1 IDE disk plugged in. This works nicely.

In the Device manager, all disks ARE detected! On the "82801 SATA RAID controller" I see three SCSI Devices. Both Samsung HD501LJ disks, and my DVD player. The Samsung disks are designated as /dev/hda and /dev/hdb. Interesting enough, the second harddrive also has several references to RAID. For instance : after the "Volume" entry, it reads (isw_raid_member), and the data-entry "volume.fsusage' = 'raid'.

The IDE harddrive is detected as well, and is /dev/hdc. Note that this is the drive that holds Ubuntu.

The problem still exists though. No matter what bootdisk I choose in my BIOS, it doesn't work;
- When choosing the SATA RAID disks as bootdisk, I get the Vista Bootmenu (correctly), which includes Ubuntu as an option by now. Selecting "Ubuntu" will start booting, but after the splashscreen and an apparent bootprocess, it fails with the (initramfs)__ prompt.
- When choosing the IDE disk as bootdisk, Ubuntu will directly start booting, though fail in the same way.

Since I can boot into Ubuntu with the Live-CD now, I can also study the contents of the IDE drive holding Ubuntu. Are there perhaps clues what goes wrong during the bootprocess?

Thanks!

---

### Post by dgray_from_dc on 2008-03-10
It looks like the Ubunutu installed on the IDE drive "thinks" it's on hda.  It starts to boot, and finds itself on hdc and the error occurs.  

The key is to tell your Ubuntu install what drive it's on.  Unfortunately, short of a reinstall, I don't know how to do that.

---

### Post by BSalters on 2008-03-11
OK, my problem is finally solved. Just to let everyone know what the problem was:

It appears that -when selecting "Ubuntu" from the Vista bootmenu - I was *not* booting the actual ubuntu, and associated menu.lst etc from the IDE disk.

Instead, a file c:\wubildr.mbr (on my SATA drive) was being used.It may or may not have started a further booting sequence from the IDe drive; I don't know. I do understand now however why all the suggestions above did not help; I only made changes to the IDE drive, which wasn't used at all.  Apparently, when the wubildr.mbr file was made (good question: why??), some errors seem to have been introduced in there.

Once I figured this out, I threw out c:\wubildr.mbr. I then used the program EasyBCD to add Ubuntu to my Vista boot menu. It also required checking the box 'Grub not installed on boot partition', and all of a sudden, Ubuntu starts from harddisk :)

Thanks all. Onto the next puzzle (how to access my RAID disks).

---

