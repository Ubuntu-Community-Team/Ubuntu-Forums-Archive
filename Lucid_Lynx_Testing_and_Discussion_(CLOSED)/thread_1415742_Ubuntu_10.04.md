---
title: "Ubuntu 10.04"
date: 2010-02-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Denton Larson on 2010-02-25
Hi everybody

The machine I have the Ubuntu 8.04 is a Dell Optiplex GX260 and I am considering putting a Ubuntu Alpha 10.04. Would I have to do a full restore to the machine or would it be fine to do a upgrade to it? 
Just a question.

Denton Larson
WB0ZUR

---

### Post by MooPi on 2010-02-25
I've never done an upgrade your suggesting but to be on the safe side always backup critical data,before attempting this. I personally would back up all data and install a clean 10.04. It is still alpha and may have a bug that renders your machine problematic.

---

### Post by woland on 2010-02-25
Unless you intend to use you computer as a testing platform, try the Alpha on a virtual machine.
Alpha versions are extremely unstable and buggy.

---

### Post by ssulaco on 2010-02-25
You shouldn't be getting an option to Upgrade yet since Lucid is still in alpha,but apparently some are.
[http://ubuntuforums.org/showthread.php?t=1404716](http://ubuntuforums.org/showthread.php?t=1404716)

---

### Post by Jackzor on 2010-02-25
I upgraded with minor problems.

---

### Post by Mark Phelps on 2010-02-25
Well ... I have a laptop running 8.04 and every LiveCD since then has yielded major compatibility problems ...

You would do best booting from a LiveCD of 10.04 before you attempt to do an install.  LOTS of stuff has changed since the Hardy-era  kernels.

---

### Post by skymera on 2010-02-25
Been using Lucid for 4 weeks, no crashes and no kernel panics.
Managed to get a 14second boot time 4 weeks ago, seems about 17 is possible now.

Had some app crashes, all in all, it's not too different from 9.10, which is stable.

I'd suggest a fresh install of 10.04

---

### Post by snowpine on 2010-02-25
I'd recommend a fresh install to a second partition or virtual machine. Definitely keep 8.04 as a fallback.

---

### Post by cong06 on 2010-02-25
I agree about the fresh installs.

Sometimes I go for the "download the deb files and see what happens" install that the update manager will give you. Ever time that's only one step (8.04 > 8.10 etc). And each time I get annoyed because of how many things break or seem to be acting strange and end up doing a fresh install of 8.10. (for example).

Just start with the fresh install and save yourself the trouble.

That being said, this is advice for non alpha/beta versions...

---

### Post by Sef on 2010-02-25
Moved to Lucid forum.

---

### Post by jppr on 2010-02-25
> **Mark Phelps said:**
> Well ... I have a laptop running 8.04 and every LiveCD since then has yielded major compatibility problems ...

You would do best booting from a LiveCD of 10.04 before you attempt to do an install.  LOTS of stuff has changed since the Hardy-era  kernels.

You can also use alternate install [http://cdimage.ubuntu.com/daily/](http://cdimage.ubuntu.com/daily/)  why use live-cd when it don´t work?

---

### Post by kevpan815 on 2010-02-25
The Upgrade (Using Sudo Update-Manager -D) Works A Whole Lot Better If You Upgrade From 9.10 Rather Than 8.04 (Although I Have Not Re-Tried It Since 8.04.4 Came Out)!

---

### Post by ranch hand on 2010-02-25
I have tried this upgrade 4 times.  It has worked once.

Not only is 10.04 just at alpha3 but the upgrade from LTS to LTS is also being tested.

10.04 is very stable for this point in its development.  I am on it now with the cpus cranking at about 100% with boinc running.  I have a number of other things going too.  Works great.

I would do a clean install and transfer your data.

You give no details on your box but  I would really go to a dual boot with 8.04 if you have any space to spare at all.  Or try it on an external.

8.04 is not real exciting but it is solid as a rock.  Hang on to it.

---

### Post by ssulaco on 2010-02-25
> **ranch hand said:**
> 8.04 is not real exciting but it is solid as a rock.  Hang on to it.+1

---

### Post by Denton Larson on 2010-02-25
I upgraded to Ubuntu 10.04 and for the most it works woo hoo! 
I did make a dual boot on it, VLC now works!


Denton Larson

---

### Post by ranch hand on 2010-02-25
That is great.

I never understood why vlc was in the repo for 8.04.  The bugger never worked.  It really is a great player.

You ought to get an ISO and try 10.04 on ext4.  It runs better, I think, than on ext3.  Might just be my box but it is a little loggy in ext3.

---

### Post by ssulaco on 2010-02-26
> **ranch hand said:**
> 
You ought to get an ISO and try 10.04 on ext4.  It runs better, I think, than on ext3.  Might just be my box but it is a little loggy in ext3.
ranch hand,I'm probably going to hang on to Hardy as long as I can,but if I do decide to upgrade to Lucid,will the file system remain ext3 or can it be converted to ext4 (on the fly)....if that's possible.

---

### Post by Merk42 on 2010-02-26
> **ssulaco said:**
> ranch hand,I'm probably going to hang on to Hardy as long as I can.
So one more year then. I doubt you're running the server.

> **ssulaco said:**
> if I do decide to upgrade to Lucid,will the file system remain ext3 or can it be converted to ext4 (on the fly)....if that's possible.
Why stick with ext3?
It can't be converted on the fly

---

### Post by ssulaco on 2010-02-26
> **Merk42 said:**
> So one more year then. I doubt you're running the server.Desktop

> **Merk42 said:**
> Why stick with ext3?
Ive never had an issue with it.
[http://ubuntuforums.org/showthread.php?t=1133719&page=31](http://ubuntuforums.org/showthread.php?t=1133719&page=31)

---

### Post by seeker5528 on 2010-02-26
> **Merk42 said:**
> Why stick with ext3?
It can't be converted on the fly

It's not done on the fly, but that doesn't mean it can't be done.

[http://ext4.wiki.kernel.org/index.php/Ext4_Howto](http://ext4.wiki.kernel.org/index.php/Ext4_Howto)

But as the notes say, existing files are not converted to use extents. Don't know that that really makes that much difference.

> To change an ext2 filesystem (should you still have one) to ext3 (enabling the journal feature), use the command:

# tune2fs -j /dev/DEV

To enable the ext4 features on an existing ext3 filesystem, use the command:

# tune2fs -O extents,uninit_bg,dir_index /dev/DEV

WARNING: Once you run this command, the filesystem will no longer be mountable using the ext3 filesystem!

After running this command (specifically, after setting the uninit_bg parameter), you MUST run fsck to fix up some on-disk structures that tune2fs has modified:

# e2fsck -fDC0 /dev/DEV

Notes:

    * Running fsck will complain about "One or more block group descriptor checksums are invalid" - this is expected and one of the reasons why tune2fs requests to fsck.
    * by enabling the extents feature new files will be created in extents format, but this will not convert existing files to use extents. Non-extent files can be transparently read and written by Ext4.
    * If you convert your root filesystem ("/") to ext4, and you use the GRUB boot loader, you will need to install a version of GRUB which understands ext4. Your system may boot OK the first time, but when your kernel is upgraded, it will become unbootable.
    * If you do the conversion for the root fs on a live system you'll have to reboot for fsck to run safely. You might also need to add rootfstype=ext4 to the kernel's command line so the partition is not mounted as ext3.
    * WARNING: It is NOT recommended to resize the inodes using resize2fs with e2fsprogs 1.41.0 or later, as this is known to corrupt some filesystems.
    * If you omit "uninit_bg" on the tunefs command, you can skip the fsck step. 

Later, Seeker

---

### Post by ranch hand on 2010-02-26
It is much easier to do a clean install and shift your files.  They will become ext4 files the first time they are opened and closed either way.  I like running them through an ext4 partition and opening them in batches and closing them before putting them on the new OS.

You get some fragmentation do to the difference in sector size and this keeps the fragmentation off the new install.

I really do not have any drives large enough to "need" ext4.  But on this box,starting with 9.04, 64bit runs better on ext4.  It wasn't much on 9.04.  It was more on 9.10.  10.04 just runs a whole lot better on ext4 than on ext3.

I have no idea about 32bit.

---

### Post by katie-xx on 2010-02-26
> **ranch hand said:**
> 
I really do not have any drives large enough to "need" ext4.  But on this box,starting with 9.04, 64bit runs better on ext4.  It wasn't much on 9.04.  It was more on 9.10.  10.04 just runs a whole lot better on ext4 than on ext3.
I have no idea about 32bit.
[SIZE=2][COLOR=Blue]
I dont have any scientific measurement but my perception is its a lot quicker transferring between two ext4 boxes than it was ext3 boxes.

Kate
[/COLOR][/SIZE]

---

### Post by ssulaco on 2010-02-27
I've clean installed all my other Distros,and have been using Hardy ever since,this time I would like to try an upgrade,but will probably run Hardy to the very end of its cycle.....solid distro;)

---

