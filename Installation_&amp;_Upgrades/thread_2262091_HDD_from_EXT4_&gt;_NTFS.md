---
title: "HDD from EXT4 &gt; NTFS"
date: 2015-01-22
forum: Installation &amp; Upgrades
---

### Post by flameproof on 2015-01-22
Here is my problem:


&#8226; I have Ubuntu 14.04 on a 1Tb EXT4 HDD
&#8226; HDD is near empty (<10Gb)
&#8226; I just installed Windows 7 on a separate SSD
&#8226; To boot to Win7 I need to press F8 while booting and chose the SSD (it's OK for me)
&#8226; Windows 7 shows the EXT 4 HDD, but doesn't mount it
&#8226; Ubuntu sees the SSD


What I want:
Windows 7 having read/write access to the 1TB HDD

If there is no other way I am thinking of this:

&#8226; Making a backup directory on the SSD for all of the Ubuntu files
&#8226; Changing (formating?) the 1TB drive to NTSF
&#8226; Moving all Ubuntu files back to the 1TB drive.


But I have a little doubt that this will work out of the box. Any help in any direction is highly appreciated.

---

### Post by CharlesA on 2015-01-22
You can use a third party file system driver to mount ext4 file systems in Windows, but it is usually easier to partition that 1TB drive and have a part of it running NTFS for sharing files between the two OSes than trying to fudge with third party drivers to get it working.

---

### Post by flameproof on 2015-01-22
> **CharlesA said:**
> You can use a third party file system driver to mount ext4 file systems in Windows, but it is usually easier to partition that 1TB drive and have a part of it running NTFS for sharing files between the two OSes than trying to fudge with third party drivers to get it working.

So you suggest to keep Ubuntu on EXT4 and have part of 1TB drive converted to NTFS?

Would make sense. I just need access to a few directories. 

Is it save to partition a HDD that is in use? (I presume yes)

---

### Post by fantab on 2015-01-22
> **flameproof said:**
> ...
Is it save to partition a HDD that is in use? (I presume yes)

Oh NO, it not safe!

Use gparted tool from Live Ubuntu DVD/USb...

---

### Post by CharlesA on 2015-01-23
> **flameproof said:**
> So you suggest to keep Ubuntu on EXT4 and have part of 1TB drive converted to NTFS?

Yes.

> Is it save to partition a HDD that is in use? (I presume yes)

No. See fantab's post.

> **fantab said:**
> Oh NO, it not safe!

Use gparted tool from Live Ubuntu DVD/USb...

---

### Post by flameproof on 2015-01-23
Ok, I burned a new LiveDVD and manage to get over the black screen. But when I open GParted min and max size are the same and I can't edit the size. What now?

[COLOR="#FF0000"]Update:[/COLOR]
Got it, I had to unmount the partition.

[COLOR="#FF0000"]Update 2:[/COLOR]
Took a hour so, but Ubuntu boots again to the HDD. Due to lack of cables the SDD wasn't connected, I guess Win7 will boot too. Haven't tried to access the new HDD from Win7, but can't see why it shouldn't work.

Maybe one last question: Instead of pressing F8 and chosing a drive, is it possible to add a boot manager?

---

### Post by Impavidus on 2015-01-23
If Ubuntu can access the Windows file system when it updates grub, it should automatically add an entry for Windows in the grub menu. Do you get a grub menu when you boot from the Ubuntu drive? If not, have a look at the file **/etc/default/grub** and search for a line containing **GRUB_TIMEOUT=0**. Change that number to 10 or something else suitable (it's in seconds) and run **sudo update-grub**.

And as nobody mentioned it, Linux may be able to read and write NTFS, but it can't run from NTFS. So converting the entire 1TB drive to NTFS was out of the question.

---

