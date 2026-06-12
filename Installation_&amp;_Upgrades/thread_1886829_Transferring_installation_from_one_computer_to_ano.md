---
title: "Transferring installation from one computer to another"
date: 2011-11-25
forum: Installation &amp; Upgrades
---

### Post by rmcellig on 2011-11-25
I have Ubuntu 11.04 installed on an old Dell Desktop for my Mom. She has been using this for a little over a year now. She now has a HP laptop and would like to have what is on her Dell transferred over to the HP. It has to be an exact transfer. Would I use something like Remastersys to do this? What would be the easiest way for me to do this?

---

### Post by SteveDee on 2011-11-26
> **rmcellig said:**
> ...What would be the easiest way for me to do this?

Linux is not like Windows, as Linux loads the kernel modules required for the hardware when the system boots. So you can normally transfer the hard drive from one computer to another without problems (other than any hardware which is not supported anyway).

So if you can swap the disk, try that first.

Otherwise download Clonezilla and burn to a CD. This will allow you to make an exact copy (a clone) which you will save to a USB drive/memory stick. You then use Clonezilla on the new system to "Restore" to the new drive. The new drive must be no smaller than the source drive. (Post again if you want some guidance on this procedure).

The third option is Remastersys which will make an install disk based on the original. But I think this is generally used when you want to create a distribution and is not an exact copy.

---

### Post by rmcellig on 2011-11-26
I'm running into a problem and I am not sure what it could be. The source disk is 80GB (This is the one running Ubuntu 11.04. The target disk is a 1GB external USB drive that I want to save the image to. I ran Clonezilla selecting the source and target disks but when it went to proceed with the Clone to an image file, Cloezilla reported an error and to check the log file. I forgot to do this so I will run the clone again and post back the error.

Late breaking update: I think I spoke too soon. Looks like the backup is going fine so far. Will post back  with an update. :)

---

### Post by rmcellig on 2011-11-26
Success!! Worked fine. Thanks!!

---

