---
title: "Cannot resize XP partition"
date: 2010-03-03
forum: Installation &amp; Upgrades
---

### Post by SirTiger on 2010-03-03
Hi,

I am completetly new to Linux and Ubuntu. I have read several tutorials on how to install it on my Laptop with pre-existing XP without destroying XP in order to get a dual-boot system. For example on those two pages...

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

and 

[https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/non-debian-partitioning.html](https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/non-debian-partitioning.html)

...it reads that in the Ubuntu install menu I have to select "manually edit partition table", which I have found and selected, and then I should supposedly be able to edit the size of the desired partition. However, no option for changing the partition size appears. Instead I get a menu where I am asked to determine how I want to mount the partition (as ext4, ext3, etc.) and if I want to format it. However nowhere it mentions anything related to "change size" or similar.

What am I doing wrong here?

Thanks in advance!

---

### Post by byStanderone on 2010-03-03
...this thread would be of help: [http://ubuntuforums.org/showthread.php?t=96617](http://ubuntuforums.org/showthread.php?t=96617)

---

### Post by darkod on 2010-03-03
Those look like old documentation. The installer has visually changed a bit.

My suggestion:
First, always back up your important data from windows.
Boot with the ubuntu cd, Try Ubuntu option into the live desktop. Open Gparted in System-Administration. That should allow you to shrink your XP partition to the size you want. Leave the newly created space as unallocated. Click on the green button to apply the changes.
MAKE SURE you boot XP few times after that to figure out the shrink and do the disk checks.

After that just boot again with the ubuntu cd, Install Ubuntu option, and in step 4 tell it to Use Largest Available Free space. It will set it up in the unallocated space you left.

---

### Post by byStanderone on 2010-03-03
...yup you are right darkod, that's a concise one, thanks.

---

### Post by Detonate on 2010-03-03
I have found that resizing the windows partition will sometimes fail if the partition is badly fragmented.  I always run chkdsk and defrag on the windows partition before attempting to resize it.

---

### Post by underquark on 2010-03-03
> **Detonate said:**
> I have found that resizing the windows partition will sometimes fail if the partition is badly fragmented.  I always run chkdsk and defrag on the windows partition before attempting to resize it.First boot into Windows and disable the Windows swapfile and the restore points since these create fixed areas of disk that won't move with Windows defrag.

---

### Post by sam.reader on 2010-03-03
once we have installed OS into a partition we can't re-size it.
IF you try to do it with some programs then some problems are bound to occur
OS installation takes place keeping in mind the size of the partition.
Hope it helps.

---

### Post by darkod on 2010-03-03
> **sam.reader said:**
> once we have installed OS into a partition we can't re-size it.


Of course you can. I have resized vista system partition with Gparted, and it worked fine after that.
The main thing is to do the resize as separate step, especially if resizing windows partition, and then boot it to allow it to do the disk checks and figures out the new partition size.

---

### Post by Mark Phelps on 2010-03-03
Keep in mind that if you disable System Restore, it generally removes ALL your historical restore points as a byproduct -- which is OK if you don't need them.

Otherwise, look to see if you have a hibernation file, and if so, disable hibernation and remove that.  You can always restore hibernation later if you need it.

---

### Post by Objekt on 2010-03-03
> **darkod said:**
> Of course you can. I have resized vista system partition with Gparted, and it worked fine after that.
The main thing is to do the resize as separate step, especially if resizing windows partition, and then boot it to allow it to do the disk checks and figures out the new partition size.

Absolutely correct.

One more thought: The time to resize a partition will vary a lot, depending on how full the partition is.  Resizing a mostly-full partition can take hours, but I've also resized a mostly-empty 800 GB partition inside a couple of minutes.

---

### Post by sam.reader on 2010-03-03
I never realized we can do it.
Once when I did that I lost a lot of data.
Is there something we have to do to make sure that we can make the partition safely?

---

### Post by SirTiger on 2010-03-04
Thanks already for your helpful advice. I have followed it and have run chkdsk /f /r and defrag. Now I want to use gparted as suggested by one user to shrink the XP partition, but it won't let me with the following reason:

"ntfsresize: ERROR: This software has detected that the disk has at least 5 bad sectors
[...] you can resize NTFS nonetheless by additionally using the --bad-sectors option on ntfsresize"

So first of all, I knew already that the hard disk has bad sectors. Please spare me the advice on not to use Hard disks with bad sectors. I son't want to waste money on buying a new one, and since there is no valuable data on it, and I only want to use the laptop for occasionally surfing the web and the likes, it doesn't really matter. As long as it runs, I'm happy, and when it doesn't run any more, I'm gonna dump it completely and buy a new laptop anyways.

So my problem is, how do I apply the command line option --bad-sectors on the too ntfsresize? The tool is apparently used by gparted, but all this happens within the graphical user interface. Is there some kind of script or so where I can insert that option so gparted calls ntfsresize with the required option?

Thanks in advance,
SirTiger

---

### Post by darkod on 2010-03-04
> **SirTiger said:**
> Thanks already for your helpful advice. I have followed it and have run chkdsk /f /r and defrag. Now I want to use gparted as suggested by one user to shrink the XP partition, but it won't let me with the following reason:

"ntfsresize: ERROR: This software has detected that the disk has at least 5 bad sectors
[...] you can resize NTFS nonetheless by additionally using the --bad-sectors option on ntfsresize"

So first of all, I knew already that the hard disk has bad sectors. Please spare me the advice on not to use Hard disks with bad sectors. I son't want to waste money on buying a new one, and since there is no valuable data on it, and I only want to use the laptop for occasionally surfing the web and the likes, it doesn't really matter. As long as it runs, I'm happy, and when it doesn't run any more, I'm gonna dump it completely and buy a new laptop anyways.

So my problem is, how do I apply the command line option --bad-sectors on the too ntfsresize? The tool is apparently used by gparted, but all this happens within the graphical user interface. Is there some kind of script or so where I can insert that option so gparted calls ntfsresize with the required option?

Thanks in advance,
SirTiger

I haven't tried it, but in theory hdd manufacturers offer a tool on their website to check the hdd and I believe it marks bad sectors. So even though they will exist, they will be marked out. I think Gparted doesn't have issues with them after that.
Check the manufacturer website and the tool might come in version to run it from windows if you can boot it, or as a version that can boot your computer and run the check.

---

### Post by SirTiger on 2010-03-04
EDIT: Just found out that my hard drive manufacturer is Toshiba (MK8026GAX), and they don't offer any hard drive tools. So this is no longer an option. 

So - does anybody know a way to make gparted use the --bad-sectors option with ntfsresize? Can I enter it in some script or options file?

Thanks

---

### Post by darkod on 2010-03-04
> **SirTiger said:**
> OK I'll try that one. But I thought that's what XP chkdsk /f /r does, anyways? Or doesn't it? OK it's a windows tool and this is a linux forum, so maybe not the proper place to ask this kinda questions ;-) But maybe someone knows anyways?

Thanks

No, it's not the same. I can't specify the exact difference, but the manufacturer tool is far better than chkdsk.

---

### Post by SirTiger on 2010-03-04
Ok I have now manually run "sudo ntfsresize -b -s 60000000000" from the Ubuntu live CD terminal. It seems to have worked. I was required to run XP chkdsk /f afterwards which I did and which worked fine. In the XP file manager the C: file system is displayed with a size of around 60.000.000.000 bytes. (physical drive size is 80GB).

I am not sure on how to proceed. Gparted doesn't let me shrink the partition... 
How else can I shrink the partition size to match the successfully shrinked file system / volume size?

Thanks 
SirTiger

---

### Post by SirTiger on 2010-03-05
With the aid of this

[http://ubuntuforums.org/showthread.php?t=1244058](http://ubuntuforums.org/showthread.php?t=1244058)

excellent tutorial I could solve the problem.

Thanks to all who helped me.

Cheers
SirTiger

---

