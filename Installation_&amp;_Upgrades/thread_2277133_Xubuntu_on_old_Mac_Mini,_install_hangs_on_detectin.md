---
title: "Xubuntu on old Mac Mini, install hangs on detecting file systems?"
date: 2015-05-06
forum: Installation &amp; Upgrades
---

### Post by James_Earle on 2015-05-06
I have tried MANY different tutorials, guides, and programs that are aimed at installing a linux distro on a mac mini, however this is a very old mac mini (2007-2008) and it refuses to cooperate. I have tried multiple distros from different providers and it seems I can make the most progress when using something Ubuntu based (others fail in the partitioning phase of the install, or do not boot at all). 

I am using UNetbootin and rEFIt to perform the installation with a bootable USB. I have a partition on the main drive as a FAT system, and in the Xubuntu installer I reformat it as ext4 with a smaller space used as bios reserved settings. I was able to successfully perform these actions and move to the final phase of the install but the system gets stuck on "detecting file systems." 

This is not the first time I have installed a linux distro, so I know it takes a while but it shouldn't take too long. Anybody have advice for working around this? Or better yet an overall guide on getting Ubuntu (or variant) on the device?

If it is useful, I repeatedly am receiving warnings during the install:

/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:18: Warning: Source ID 23712 was not found when attempting to remove it 
Glib.source_remove(self.timeout_id)

/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:131: Warning: Source ID 23776 was not found when attempting to remove it 
Glib.source_remove(self.rows_changed_id)

---

### Post by axel19 on 2016-01-28
Exactly the same problem here. Xubuntu15.10 built up with UNetbootin. Now I'm hanging in this error loop. What to do?

---

### Post by Bucky Ball on 2016-01-28
> **axel19 said:**
> Exactly the same problem here. Xubuntu15.10 built up with UNetbootin. Now I'm hanging in this error loop. What to do?

You mean you are trying to install Xubuntu on a 2007 vintage Mac Mini??? If not, best start a new thread to improve your chances of support.

@OP: Welcome. How much RAM does that Mini have and did you check the install media's integrity prior to attempting to install? Check the ISO md5sum and when you boot the install media you make, there is an option to 'Check for defects'. Run that.

Also, prior to using UNetbootin, you should wipe the USB, delete and recreate partition table, and create one FAT32 partition on the stick. Nothing else. Then let UNetbootin do its thing.

---

