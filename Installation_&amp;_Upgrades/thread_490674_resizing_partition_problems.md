---
title: "resizing partition problems"
date: 2007-07-02
forum: Installation &amp; Upgrades
---

### Post by rubikfreak on 2007-07-02
when i try to resize the partition on my laptop hard drive, it almost instantly says "An error occured while writing the changes to the storage devices." and fails. i'm using the alternate cd. what could be going wrong?
i'm on a dell inspiron 6000.
i'm wanted to show people at camp tomorrow, but it's not working :(

---

### Post by Pumalite on 2007-07-02
If dual booting with XP> defrag several times, get rid of all temp files and anything you don-t need, then use Gparted to make new partition. If dual booting with Vista< do the same, and then partition FROM Vista.

---

### Post by rubikfreak on 2007-07-03
that still doesn't work :(
i tried to get the error report from gparted but it saves it to a big htm file.
the cd has no htm/html viewer so i can't see the report.
looking at it with a text editor doesn't do much good.

---

### Post by Jacemg on 2007-07-03
Resizing partions is a hit and miss type of function i've noticed.
Rarely ever gets through without a problem because microsoft deemed it unessesary for end users to even have the worry of a flexible resizable partition. They are beyond mere 'innovation', they prefer 'market domination'. NTFS = gg

going to take a clean reformat and custom partitioning job

---

### Post by dabl on 2007-07-03
If you've got Vista on that drive, you have to do the resizing from within Vista.

If that's not the problem, then I recommend you download and burn the GParted Live CD ISO from here:

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

and use that for your disk partitioning adventures.  Then boot the Ubuntu Alternate Install CD and proceed with installation, skipping the partitioning part of it.  :)

---

### Post by rubikfreak on 2007-07-04
I can't do a format because the Windows on it is needed and it's my Dad's laptop. I wouldn't want to go through reinstalling Windows, so I'll just keep using Ubuntu on my desktop. :)

---

