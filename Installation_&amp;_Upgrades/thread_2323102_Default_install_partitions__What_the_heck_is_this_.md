---
title: "Default install partitions?  What the heck is this sda2?"
date: 2016-05-02
forum: Installation &amp; Upgrades
---

### Post by Ronald_F._Guilmett on 2016-05-02
I'm not really all that well-versed with Ubuntu, so please forgive if this is an FAQ.

I just now installed 16.04 onto a 16GB USB3 flash drive.  That all went well, and I've already installed some apps I wanted.  But I just now used "Disks" to look at the actual partitioning of the USB3 flash drive, and it's totally perplexing.  Here's what I've got:

/dev/sda1   12GB    /  (ext4)
/dev/sda2    3.4GB  ???? (note: extended partition)
/dev/sda5    3.4GB (swap)

OK, so the sda1 and sda5 partitions make obvious sense.  What I'm totally mystified by is what that sda2 partition is all about.  What is it?  Why was it created?  What does it contain?  Why does the "Disks" GUI tool not indicate that it has any specific type of filesystem within it?

When I did the install of 16.04, I didn't do anything strange, or out-of-the-ordinary, or even non-default.  I let the Ubuntu installer decide for itself how to partition the USB stick.  Now I am just slightly annoyed that I've apparently ended up losing about 3.4 GB out of my 16GB flash stick, and I can't even see that it is being used for anything at all, let alone anything that I might actually view as being useful.

So, um, what is this sda2 partition?

---

### Post by ubfan1 on 2016-05-02
If you look at the actual start and end blocks on each partition, you will see that the sda2 and sda5 are the same.  The msdos partitioning only allows for 4 primary partitions, but one of those four may be a container for 128 more logical partitions -- this is the "extended" partition.  You have nothing to worry about.

---

### Post by Ronald_F._Guilmett on 2016-05-02
OK.  I get it now.  So sda2 is just a container containing sda5.  Understood.  Thanks.  Now it all makes sense.

P.S.  It's kinda too bad that the "Disks" GUI thingy doesn't show (and apparently doesn't have any options to show) the start sector, number of sectors, etc. for each partition.  Also, the graphical representation that "Disks" shows for sda1, sda2, and sda5 certainly is not conducive to understanding that sda5 is actually *_within_* sda2.

P.P.S.  Next time I install Ubuntu, I'll know to ***not*** just allow it to do default partitioning, but instead to manually partition... when I will select GPT instead of this old and confusing MBR rubbish.  Sigh.  I suppose that MBR is still the "right choice" for a default Ubuntu install, given the possible limitations of older hardware, but I've become a fan of GPT, precisely because it avoids all of this silliness of primary versus "extended" partitions.

---

### Post by grahammechanical on 2016-05-03
> I suppose that MBR is still the "right choice" for a default Ubuntu install, given the possible limitations of older hardware,

If the motherboard has a BIOS boot system then MBR partitioning will be the default used by the Linux installer. But GPT is backwards compatible with the BIOS boot system even though it is part of the UEFI specification. But we have to assign the hard disk partition table as GPT. and then install using the something else option.

I agree that GPT is much better. I wish I was aware of its backwards compatibility the other year when I restructured my installs of Ubuntu. Do not forget that with GPT we need a bios_boot partition when installing on a disk with a GPT.

Regards

---

### Post by Ronald_F._Guilmett on 2016-05-03
> **grahammechanical said:**
> If the motherboard has a BIOS boot system then MBR partitioning will be the default used by the Linux installer. But GPT is backwards compatible with the BIOS boot system even though it is part of the UEFI specification. But we have to assign the hard disk partition table as GPT. and then install using the something else option.

Right.

Next install, I'll be doing that.

Four may be enough for oatmeal cookies, consumed in one sitting, but for disk partitions, not so much.


P.S.  Now that USB3 flash drives are becoming cheaper & faster, having Linux (e.g. Ubuntu) on one is making a lot more sense.  I put Ubuntu 16.04 onto a Sandisk Flair 16GB (USB3), which cost me about eight bucks on Fleabay, and it actually boots significantly faster than the Ubuntu I already had installed on a 320GB 2.5" 5400rpm laptop drive (WD Blue).

---

