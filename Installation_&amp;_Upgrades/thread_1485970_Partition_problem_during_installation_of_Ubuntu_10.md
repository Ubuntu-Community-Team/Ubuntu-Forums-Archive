---
title: "Partition problem during installation of Ubuntu 10.4"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by Jabz.biz on 2010-05-17
I'm currently trying to install Ubuntu on a HP Compaq nc6220 via Live CD, next to an already existing Win XP. 

During manual partitioning I ran into trouble:

**"No root file system is defined. Please correct this from the partitioning menu."**


There is only on partition present: /dev/sda1 37,25 GB (Win XP). Another 7.38 MB are unassigned free space. 

I have tried to use gparted to manually add/ change partitions, but this does not work. Can anybody help me? Thanks.

---

### Post by kansasnoob on 2010-05-17
Could you post a screenshot of Gparted using the Live CD? I just explained how to do that here:

[http://ubuntuforums.org/showpost.php?p=9314782&postcount=35](http://ubuntuforums.org/showpost.php?p=9314782&postcount=35)

Ignore all but the last paragraph :)

---

### Post by darkod on 2010-05-17
> **Jabz.biz said:**
> 
There is only on partition present: /dev/sda1 37,25 GB (Win XP). Another 7.38 MB are unassigned free space. 


If this is all you've got, where do you plan to install ubuntu?

You got that error because you selected manual partitioning but you are trying to proceed without specifying a root partition. Don't use Gparted for creating the partitions, not in this case.

You can and should create them using the install process, when you selected manual partitioning.

And if you plan to shrink XP, usually it's better to boot ubuntu live mode and use Gparted to shrink the XP system partition. After that boor XP few times to do its disk checks.

Then start the ubuntu installer and use manual partitioning or the automatic Use Largest Available Free space option (after shrinking XP you will have unallocated space on the disk).

---

### Post by Jabz.biz on 2010-05-17
@darkod I'm already trying to install via Live CD (ain't that "live mode"?!) I'm not sure what I understand what you mean. How do I boot ubuntu in live mode?

---

### Post by oldfred on 2010-05-17
A liveCD is both an installer and an operating ssytem that you run from the CD. You can then test that your system works or do some things like use gparted to modify/repair your existing system(s).

Initial boot should give you a choice to use or install. Once booted your are in Ubuntu and can under system, administration, gparted use gparted to edit partitions. You do not have a lot of space either for windows or Ubuntu but it should just fit.

To see install screens. 
This is Karmic the screens are essentially the same (except color)
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

This is  a lucid install to a EeePC but shows the install screens:
ASUS EeePC netbook PC 10.04 install
[http://members.iinet.net/~herman546/p28.html](http://members.iinet.net/~herman546/p28.html)

---

### Post by Jabz.biz on 2010-05-17
This screen (where you can adjust partition sizes) [IMG]http://i1-news.softpedia-static.com/images/extra/LINUX/small/ubuntu910installation-small_007a.png[/IMG] does not show.

---

### Post by darkod on 2010-05-17
That screenshot does not correspond at all with your first post.

What is the linux distribution reported on /dev/sda1?

This looks like 8GB SSD disk, is that what it is? Do you plan to dual boot XP and Ubuntu on 8GB?

---

### Post by Jabz.biz on 2010-05-17
@darkod The Screenshot is from Softpedia (oldfred's post). The Screen does not show my setup at all. Sorry for the confusion.

---

### Post by Jabz.biz on 2010-05-17
This is the actual Screenshot:

[IMG]http://img689.imageshack.us/img689/6116/screenshotphx.png[/IMG]

I can't reduce the size of the NTFS partition.

---

### Post by psusi on 2010-05-17
You got the error because you chose to do manual partitioning, and then did not do any partitioning.  Just choose the install side by side option and it will take care of shrinking your windows partition.

---

### Post by Jabz.biz on 2010-05-17
Unfortunately this is not the case. I can only choose between full-overwrite or manual partitioning. 

I've done around 60 Ubuntu installs in my life so far, I've never run into this kind of trouble.

---

### Post by darkod on 2010-05-17
The exclamation mark next to /dev/sda1 is your problem. That is why Gparted doesn't offer resize, and also the installer doesn't offer side-by-side because that needs to include resize of /dev/sda1. There is some 'error' on /dev/sda1.

On another note: using side-by-side option when you have XP quite often ends up corrupting the XP system partition. This is because windows wants to do its disk checks after a resize, but the ubuntu installer is doing the resize and installation in one step if using side-by-side. And especially XP is touchy about this.
The resize is always better to be done as separate step first, reboot windows few times, and only then install ubuntu. For vista and win7 the Disk Management can be used. For XP you need third party tool, or Gparted, etc.

Now back to the issue. If you right-click /dev/sda1 in Gparted it should give you the option Check. Maybe it will have some answers why the exclamation mark.

Also, in terminal in live mode try:

sudo ntfsfix /dev/sda1

It can't really fix problems on ntfs, but it will do basic check and most importantly it will set a flag for XP to do chkdsk next time you boot it. On that note, try doing chkdsk from XP yourself.

If you try using ntfsfix and it's not there, you might need to install ntfsprogs, not sure if the live mode has it.

sudo apt-get install ntfsprogs

Something from the above options should hopefully sort it out.

---

### Post by Jabz.biz on 2010-05-18
@darkod What an Odyssey. :) I made it, your last post was very helpful to understand and fix the problem. Thank you.

---

