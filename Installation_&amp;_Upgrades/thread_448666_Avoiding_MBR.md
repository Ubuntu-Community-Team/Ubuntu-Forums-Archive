---
title: "Avoiding MBR"
date: 2007-05-19
forum: Installation &amp; Upgrades
---

### Post by geno123 on 2007-05-19
How can I install Feisty Fawn without affecting the MBR?  Thanks.

---

### Post by mpvano on 2007-05-19
Apparently you cannot do this from the Desktop install.

You need to use the alternate installer disk.

At the end of the installation it will propose putting Grub on the MBR. Refuse, and instead install it to the root partition (This can only work easily if the ubuntu installation is on the first disk and on a primary partition (numbered 1-4, not >= 5).

For this to work, the grub partition must also be mark "bootable" or "activated", depending on which utility you use for the partitioning. If you forget to do this, the windows disk utilities can be used to mark the partition active.

If you don't understand what I'm talking about here, don't try messing with it. It's safe and reliable, but not easy for beginners to do.

After you do this, you'll still be using Grub to dual boot, but activating the original windows partition from any disk partitioning utility (including the ones on your Windows installation disks) will switch back to booting windows.

If you know what you are doing, you can also configure the Windows (or any other boot loader) to chain-load grub from it's menu.

Again - this is all too complicated for a beginner. There's enough information here to do it if you are qualified - if none of this makes sense, get help from a friend or just don't do it....

Mario

---

### Post by geno123 on 2007-05-21
Many thanks.  I have been messing with Linux (mostly SUSE) for about 5 years so giving your suggestions a try should not be a problem.  I will report back.

---

### Post by geno123 on 2007-05-26
Installation went fine.  However, when I bring up Ubuntu menu and try to start Ubuntu, I get an error message:

"Error 17: cannot mount this partition."

Partition being used is first partition on external USB drive.

Any thoughts?

---

### Post by mpvano on 2007-05-27
Are you sure that the partition is still in the same relationship to Ubuntu as it was when you installed GRUB?

There are two important places where the partition must be correct.

The first is in the Kernel command line in Grub. Are you sure that when you boot, the device name is still the same as when you installed Grub? You can experiment with fixing this by using the grub option to edit the command line. If you find that this is the problem you can edit the Grub menu file.

The second place the partition device information must be accurate at run time is in the mount table information. This is normally controlled by the file /etc/fstab. You can edit the device names there if needed to correct a problem using a recovery disk.

It's obviously important that the device names are the same when you install and when you try to boot. That's why you can't swap a drive in as an ide drive hda and then swap it to hdb and run the system. I think something like that is happening to you.

The best strategy I've found is to install to a non-primary device in it's final configuration, including the grub install to the partition you installed as /. Chainloading from another copy of grub or from any other boot loader that knows how to chainload will then transfer control to Grub on the final destination volume, which will boot everyting configured just as it was during install. I'm doing this right now on several different installs, with Fiesty and Debian Etch and several other types of OS'es.

Note especially, however that you must NOT tell your BIOS to swap or flip device ID's or anything like that. At boot time the disks need to be in their final relationship.

There are some funny things going on in the new GUID based mounting system in Ubuntu. There's some chance that you could be having a problem due to this, but I think the odds are that this will not be a problem if you made sure that you have all the pieces in the right spot.

Where did you install Grub?
What exactly gets booted first by the BIOS?
Where are it's various stages installed?
What is the configuration of the bootstrap program loaded by the BIOS?
Does it chainload another Grub? What is THAT one's configuration and where is it installed?
What is in the fstab of the final system.

Exactly WHERE is your error message coming from? Is it the first copy of Grub running? Is it a chainloaded one? Is it part of the the kernel boot process?

As I warned you, this can be tricky if you don't fully understand how Grub works and how the mount process works during boot.

Hope tis gives you some more ideas....

Mario

---

