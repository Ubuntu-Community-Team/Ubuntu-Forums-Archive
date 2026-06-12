---
title: "cannot boot windows 7 x64"
date: 2011-08-30
forum: Installation &amp; Upgrades
---

### Post by glentakahashi on 2011-08-30
All right, so I'm basically running a brand new installation of ubuntu 11.04 x64 but I cannot get Windows 7 to boot. update-grub shows Windows 7 appearing, but when I select it from grub2, all I get is a blank screen. There are no errors at all, and it just stays like the infinitely. I have done startup repairs on the windows installation with an install disk, but it says everything is working properly. I have fooled around with menuentries with GRUB2 but none seem to work. It's boggling my mind what is wrong. Any ideas?

Thanks,
Glen

---

### Post by tommpogg on 2011-08-30
How did you install the Operative Systems? Which one first?
Are you sure you haven't overwritten or damaged the Windows 7 partition while installing Ubuntu?

---

### Post by glentakahashi on 2011-08-30
how would I know that it's corrupted and not just that GRUB2 isn't working? Is there a certain procedure i should follow?

-Glen

---

### Post by Mark Phelps on 2011-08-30
> **glentakahashi said:**
> how would I know that it's corrupted and not just that GRUB2 isn't working? 

Good question -- and unfortunately, you really have no way of knowing whether or not it is actually corrupted.

However, to find out if it's still in place, you should do two things.

First, when inside Ubuntu, open a terminal and enter "sudo fdisk -lu" (that's a lowercase L, not a one).  This will list out the partitions on your drive.  If you see NTFS partitions, then Win7 should still be in place.

Second, click the Home icon in the upper left portion of the screen and look through the list.  Open each item and see if there is one with your Win7 files in it.  IF so, this confirms that Win7 is still intact.

You may actually have to run Startup Repair from the Win7 disk three times to get it to actually work.

---

### Post by glentakahashi on 2011-08-30
I've checked the windows 7 partition and everything is there. I also ran a chkdsk on it and there were no errors at all. I guess just run startup repair a few more times?

---

### Post by glentakahashi on 2011-08-30
After more experimentation I've figured out how to fix it, but I still don't understand what the problem was. I popped in my Windows 7 installation disk again, and ran these commands:
```
bootsec /fixboot
bootsec /fixmbr
```
After that happened, GRUB2 was deleted and it would boot directly into Windows 7.
I then popped in my Ubuntu live cd again, and then did [this]("https://help.ubuntu.com/community/Grub2#Copy LiveCD Files") process, which reinstalled GRUB2 and allowed me to boot into Windows 7 for some reason.

Hope this helps.

-Glen

---

