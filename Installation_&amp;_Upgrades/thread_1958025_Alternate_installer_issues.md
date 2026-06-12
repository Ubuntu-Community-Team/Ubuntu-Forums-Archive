---
title: "Alternate installer issues"
date: 2012-04-13
forum: Installation &amp; Upgrades
---

### Post by axeman71 on 2012-04-13
I want to install 12.04 Beta2 on a usb hard drive (physical HD not flash drive) with full disk encryption.  I downloaded the alternate installer iso copied it to a usb flash drive using unetbootin to make a bootable usb drive.

I choose the guided partitioning option to create an encrypted LVM using the entire usb HD.  When the installer got to the point of installing the unbuntu desktop I would get an error message saying an error had occurred.  I retried a few times but got the same error at the same place.

After reading on the forums I found others had had this problem but no real solution was found.  One suggestion was to re-download the iso and make sure the md5sum was correct.  

I re-downloaded the iso, checked the md5sum and everything was good.  I used unetbooting again to make a bootable usb flash drive from the iso and tried again.  Now I get an error during the system install saying it can't download various modules.

Am I making some fundamental error I'm not aware of?  Is there some other special steps I need to take to have it installed on an encrypted drive?

---

### Post by Herman on 2012-04-14
I'm installing from a CD, not a USB. 
I am interested in trying to use the Alternate CD from a USB, the last  time I tried it I wasn't able to, it used to fail on mounting the CDROM.  I have read there's a workaround for that but I haven't tried it yet.

Anyway installing from CD in one LUKS encrypted Ubuntu installation I had a red screen with an error message something about not being able to configure the kernel. I chose <Go Back> and scrolled up one line in the Alternate Installer's Main Menu and tried again. The installation turned out to be successful.

A second installation went right through without a hitch.

I'm not sure if it matters what the developers are doing in the repositories at the same time we're running our installations. 12.04 is not released yet at this time and the software in the repositories could be in a state of flux. The installer does download updates from the internet unless we unplug. 
Maybe just try again and hope your timing is lucky or try with the internet unplugged to avoid broken packages.

---

