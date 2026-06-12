---
title: "Dual Boot on 2 hard drives Vista and Ubuntu"
date: 2008-10-06
forum: Installation &amp; Upgrades
---

### Post by obliviongoty on 2008-10-06
Currently I dual boot Ubuntu 8.04.1 and Windows Vista Ultimate 32bit on a single 250gb Hard Drive. I am planning to buy a 500gb hard drive as i am running out of space, I would like to install Vista on the 500gb Hard Drive and I would like ubuntu on the 250gb hard drive. How would I go about doing this without purchasing any extra hardware/software? or Would it just work if I installed them as usual?

---

### Post by banditti on 2008-10-06
Have you checked this link out?

[https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

Also, I don't know anything about your PC config, but have you thought about running Vista in a VM?  That is how I do it.  You could also run converter from VMware to convert your current Vista install to a VM, done and easy.

---

### Post by caljohnsmith on 2008-10-06
It would be most ideal if you can disconnect the other drive when you install either OS. That way you are guaranteed that they won't touch each other, e.g. like installing their own MBR (Master Boot Record) to the other drive. Just make sure you have your Ubuntu Live CD and Vista Install CD, and you shouldn't need any extra software. :)

---

### Post by Modax42 on 2008-10-07
I would also like to do this with my Vista desktop.  It has two 320 GB Hard Drives.  One is unused and I would like to put Ubuntu on it.  

However, I have a phobia of doing any work inside my case, largely because my best friend once fried his CPU and motherboard with static electricity while attempting to upgrade his graphics card.  And I live in a very staticky house.

So, how big is the risk of messing up my vista installation if I do this installation procedure without cracking open my case?

---

### Post by Modax42 on 2008-10-07
****.  Now I've done it.  I decided to install Ubuntu onto a USB flash drive in the hopes that it would be a risk-free way of dual-booting.  Now It won't boot from the hard drive as it goes straight to Grub.

I got it to go into BIOS now, but I don't what I'm doing with it.  How do I tell it to boot into Vista again?

---

### Post by caljohnsmith on 2008-10-07
> **Modax42 said:**
> ****.  Now I've done it.  I decided to install Ubuntu onto a USB flash drive in the hopes that it would be a risk-free way of dual-booting.  Now It won't boot from the hard drive as it goes straight to Grub.

I got it to go into BIOS now, but I don't what I'm doing with it.  How do I tell it to boot into Vista again?
Most likely what has happened is that Grub installed itself into the MBR (Master Boot Record) of your internal Vista drive. Can you set your BIOS to boot from the external USB flash drive? If you can do that, I would restore your Windows MBR on the Vista drive, and then install Grub to the MBR of your flash drive; that way both drives are independent, and if one conks out for any reason, you'll be able to boot the other drive.

First I would start with restoring your Windows MBR so you can boot Vista. You'll need a Vista Recovery CD, so if you don't all ready have one, you can download one [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). Boot that CD, go to the command line, and run:
```
bootrec /fixmbr
```
That should make it so you can boot into Vista again if your Vista drive is first in the BIOS boot order. Let me know if you can get this far, or if you run into problems, and we can work from here. :)

---

### Post by Modax42 on 2008-10-07
Phew.  I've got it working now.  I just followed the instructions this guy gives in this thread [http://ubuntuforums.org/showthread.php?t=62717](http://ubuntuforums.org/showthread.php?t=62717) and now all is well.  Thank goodness for Supergrub CD!

I think I am going to stick with Ubuntu on my laptop and Vista on my desktop for the foreseeable future.  Dual booting is too complicated for me.

---

### Post by Mark Phelps on 2008-10-07
Obliviongoty:

I second what Caljohnsmithb says.  I have a multi-boot sytem and have Windows OS's installed on one drive and Ubuntu OS's installed on the other.  I disconnected the Windows drive when installing the Ubuntu OS's to ensure that I didn't accidentally overwrite the Windows drive MBR.

I'm able to boot into the various OS's from a single GRUB menu.

The only downside is that since the Windows drive is disconnected when I install new Ubuntu versions, GRUB doesn't automatically add entries for them to the menu.lst file.  But that's easily fixed by keeping a copy of that file on the side and editing the new file after it's created.

---

### Post by consilience on 2008-10-07
dual-booting is easy so long as you install vista first.  ubuntu recognizes this and can partition the disk during setup.

---

