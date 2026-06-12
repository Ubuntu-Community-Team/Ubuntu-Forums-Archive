---
title: "Getting Windows back on a linux laptop..."
date: 2011-12-01
forum: Installation &amp; Upgrades
---

### Post by Jedwinjim on 2011-12-01
HI hi,

simple question really, I've been solely using Ubuntu on my laptop for the last couple of years, before which I was dual booting with windows vista. Well now I need to go back to dual booting for a couple of reasons. Anyway, if I put the windows CD in & boot up it tells me it can't install as it needs to write to ntfs, and of course my hard drive is not ntfs because it's running Ubuntu in ext3 (or whatever it is).

So how do I get my hard drive back to ntfs so I can install windows is basically my question? once I've got windows back on I can put Ubuntu back on with it's 'run side by side' option on installation.

As you can probably tell I'm not that great with computers & technical terms so if I can get responses in 'laymen' language that would be great, although obviously I hugely appreciate any help you offer my way :)

---

### Post by ajgreeny on 2011-12-01
You will need to boot to a live CD/USB and shrink one of your ubuntu partitions with gparted, leaving either unallocated space, or making a new ntfs partition in the space you have made.  You have to have the partition you are shrinking unmounted, hence the use of a live CD.

Installing windows will wipe off the grub bootloader used for ubuntu and replace it with the windows bootloader, but it is the job of a few seconds to restore grub, boot to ubuntu and run the command ```
sudo update-grub
``` and you can then continue using grub as your bootloader for both ubuntu and windows.

Go to [Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275") for details of restoring grub.

---

### Post by Jedwinjim on 2011-12-01
Easy as pie and well on the way to where I wanna be, thanks for the help!

:)

---

### Post by Mark Phelps on 2011-12-01
Just to make sure we are all talking about the same thing ... presuming you're going to reinstall Vista, it didn't come on a "CD", it came on a "DVD".

Mentioning this, because if the PC came preinstalled with Vista, any "CD" is likely to be only a Restore CD -- which, if it works, is likely to ERASE your drive in the process of reinstalling Vista.

Don't want you to end up losing Ubuntu in the process of trying to reinstall Vista.

---

