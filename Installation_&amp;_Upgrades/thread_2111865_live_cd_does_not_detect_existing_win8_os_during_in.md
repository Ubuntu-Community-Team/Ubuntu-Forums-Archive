---
title: "live cd does not detect existing win8 os during install"
date: 2013-02-03
forum: Installation &amp; Upgrades
---

### Post by carusoswi on 2013-02-03
Trying to set up dual boot on a win8 laptop. 12.10 setup states that no other operating system was found on the computer, so no option to install alongside is available.

I can view the ntfs partition, so I could install to another, I suppose, but what will happen when I reboot.  I'm guessing that Grub will not setup the dual boot options properly if the Win8 os was not initially detected by the live cd.

Suggestions?  Anyone else experience this?  Would installing a previous version of Ubuntu work?

Thanks.

Caruso

---

### Post by darkod on 2013-02-03
With win8 and new machines coming with uefi boot you have to be careful and boot the ubuntu cd in uefi mode, not legacy.
Also, you might need to go into the BIOS and disable Secure Boot.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Mark Phelps on 2013-02-03
Also, BEFORE you attempt the dual-boot setup, if you want to ensure that Win8 will work afterward, you should do the following:
1) Use the Backup feature to create and burn a Win8 Repair CD.  If your Win8 boot loader or the Win8 OS gets corrupted during the dual-boot setup, you will need this to repair Win8 so it will boot again.
2) Shrink the Win8 partition ONLY using the Win8 Disk Management utility.  IF you use the Ubuntu installer to do this, or use GParted, you risk corruping Win8 and rendering it unbootable.

---

### Post by carusoswi on 2013-02-09
> **Mark Phelps said:**
> Also, BEFORE you attempt the dual-boot setup, if you want to ensure that Win8 will work afterward, you should do the following:
1) Use the Backup feature to create and burn a Win8 Repair CD.  If your Win8 boot loader or the Win8 OS gets corrupted during the dual-boot setup, you will need this to repair Win8 so it will boot again.
2) Shrink the Win8 partition ONLY using the Win8 Disk Management utility.  IF you use the Ubuntu installer to do this, or use GParted, you risk corruping Win8 and rendering it unbootable.

Thanks for the replies.  I did boot in UEFI mode, and I have used the Win8 disc management to shrink the win8 partition.

When we first bought this machine, the install went fine, except, I suspect, due to a faulty live cd, the completed installation would not run.

After several restorations and a rety with a new disc, I made a mistake that corrupted the win8 partition.

Additionally, whatever bit of software allows one to remove the cd was also corrupted.  I sent the machine back to the manufacturer who removed the cd and re-imaged the hard drive.

Since then, (and I'm not saying that the re-imaging has caused this problem) after getting the machine back from the manufacturer, Ubuntu states during the install process that no other OS is installed on the system.

As mentioned previously, the NTFS containing win8 shows up in the partitioner, I am just reluctant to proceed.  Not anxious to have to send the machine back a second time (although the re-imaging charge was quite reasonable).

Thanks again for your suggestions.

Caruso

---

### Post by darkod on 2013-02-09
Well, it's up to you.

Even if ubuntu doesn't detect win8, you can still make custom entry which should boot win8 if its boot files are really fine.

If that fails too, you can easily put windows bootloader back on the machine using the win8 repair cd Mark suggested to make before doing the ubuntu install. You also have options to write generic MBR using linux tools too.
So, going back to windows bootloader is not a big issue in my opinion.

One thing that could make ubuntu not detect win8 is a confusion in the partition table. For example, I have noticed that windows tools do not convert from gpt to msdos table correctly. They delete only the primary gpt table and replace it with msdos but gpt has also a backup table that windows tools don't remove. So, linux is confused not sure which table to read.

If this is really the case (just my assumption), you can fix the backup table removal with fixparts.
[www.rodsbooks.com/fixparts/](www.rodsbooks.com/fixparts/)

What ever you do, just make sure during installation not to overwrite your win8. It's best to use manual partitioning for the ubuntu install (Something Else) especially since it doesn't see win8 on the disk. You need total control what partition you use and what for. There is a chance that fixparts can sort this for you if you run it before trying the install.

---

### Post by Mark Phelps on 2013-02-09
> **carusoswi said:**
> Since then, (and I'm not saying that the re-imaging has caused this problem) after getting the machine back from the manufacturer, Ubuntu states during the install process that no other OS is installed on the system.

As mentioned previously, the NTFS containing win8 shows up in the partitioner, I am just reluctant to proceed.  Not anxious to have to send the machine back a second time (although the re-imaging charge was quite reasonable).

IF you use Win8 regularly, you need to spend some time on the Windows 8 forums (eightforums.com) reading through the different recovery tutorials.  Win8 comes with both "reset" and "refresh" -- different recovery versions.

Also, before you try dual boot again, seriously consider using the Win8 option to create the Recovery Image.  The Win8 forums have a tutorial on how to create that.

---

### Post by carusoswi on 2013-02-13
> **Mark Phelps said:**
> IF you use Win8 regularly, you need to spend some time on the Windows 8 forums (eightforums.com) reading through the different recovery tutorials.  Win8 comes with both "reset" and "refresh" -- different recovery versions.

Also, before you try dual boot again, seriously consider using the Win8 option to create the Recovery Image.  The Win8 forums have a tutorial on how to create that.

Thanks for the replies/suggestions.  Not in a rush on this, as I am very busy at the offie.  Didn't think about checking out Win8 forums, but it seems like a good suggestion.

May just give up and install WUBI (or whatever it's called).

The computer is for my grown son, and he could care less, really.  Prefers Ubuntu to windows, but has plenty of reasons why he needs windows, still.

Thanks again.

Will report back how things go.

Caruso

---

### Post by carusoswi on 2013-04-13
Sent the computer along with son, no 'buntu installed.  We just didn't have enough time to fool around with it.
Today, I find myself out on the road, my own 'buntu installation upgrades itself and no longer presents a desktop when I boot.
I'm not going to attempt to re-install from here.
Will try when I get home.

Caruso

---

