---
title: "Windows no longer in grub menu"
date: 2015-09-02
forum: Installation &amp; Upgrades
---

### Post by connorschwing on 2015-09-02
I had windows 10 installed, I dual booted ubuntu. I f'd something up, and now my grub boot menu doesn't show windows. However, if I press F12 on boot, I can boot straight to my hard drive and load windows. Is there a fix for this?

---

### Post by yancek on 2015-09-02
> Is there a fix for this? 		

Maybe, but not with the information you have posted.  Did you install windows 10 or update it from an earlier version?  Did you just install Ubuntu or did you have it installed before windows 10?  One hard drive or multiple hard drives?  UEFI or MBR?

Best thing to do is to go to the site below and get the boot repair software and run it to get info to post here.  There is an option when running boot repair to "Create BootInfo Summary".  Select that rather than trying to repair and post the output here.

---

### Post by connorschwing on 2015-09-02
Apologies, was in a rush when I wrote the original post. I installed the free upgrade of Windows 10 through Windows 8 about a month ago, then I installed Ubuntu 15.04 alongside on the same drive, on a 30gb partition. It's UEFI.

---

### Post by oldfred on 2015-09-02
Install or major update of Windows will turn its always on hibernation or fast start up setting. Make sure that is off.
The Linux NTFS driver does not see NTFS partitions that are hibernated or need chkdsk to prevent damage that could occur if it tries to mount it.

Then try 
sudo update-grub

If not run Boot-repair's summary report as suggested by yancek.

---

### Post by connorschwing on 2015-09-02
I think it may be fixed, but I'm not sure if this is a permanent solution. Before, my grub menu showed ubuntu, windows, and a couple of other things (system setup, and something else). I just disabled secure boot, and in the grub menu it says Windows Boot Manager, and if I select that, it boots into windows. Not sure if this is ok, or if I should address it. Also I don't know what boot repair is, everyone online says to run it, but I don't know what it is or where to get it.

---

### Post by yancek on 2015-09-02
I forgot to post the link in my last post.  The site is the link below and gives a brief description.  Usually what should be done is just select the option to "Create BootInfo summary" and that is explained at the bottom of the page at the link below.  It generally provides detailed information on drives/partitions and boot files for Linux and windows systems. You can then post the output here and get advice from others who know a little more about it. 

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

