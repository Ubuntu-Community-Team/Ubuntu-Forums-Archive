---
title: "Help mounting second hard drive"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by greenhornet on 2007-04-26
I've got a compUSA PCI RAID card.  It's set to RAID 0 and both the 6.10 installer and the gparted live cd can 'see' the drive.  I've formatted it ext3.  I'm a total noob and can't get the drive to show up in my GUI (so I can use it).  Gparted does not 'see' the drive when booted to the primary HD.  I'm sure this is simple but I can't seem to figure it out.  Thanks in advance for any help.

---

### Post by greenhornet on 2007-04-27
As an update it appears the device manager shows the PCI raid card.  I just can't figure out how to mount the drive.

---

### Post by red777 on 2007-04-28
sorry I'm not able to help you either because I've got the same issue.I'll track any posts as well.Just so you don't feel alone:guitar:

---

### Post by greenhornet on 2007-04-30
I'm just about to give up and switch back to Windows.  I would expect that an older device like this that's been out for several years and has drivers available in other flavors of linux would be supported.

---

### Post by bulldog on 2007-04-30
> **greenhornet said:**
> I'm just about to give up and switch back to Windows.  I would expect that an older device like this that's been out for several years and has drivers available in other flavors of linux would be supported.

The answer could be simple,like a driver needed.
I'm pretty sure you need to do the same on windows,for that matter.

---

### Post by greenhornet on 2007-04-30
I'm sure you're right.  It probably IS a driver issue.  The problem is that there ISN'T one available for Ubuntu.  That's the disappointing part.  It's a pretty common device that has been around a while.  Yet, no Ubuntu driver.

---

### Post by bulldog on 2007-04-30
Well that's one of the main problems with Linux,if the manufacturer isn't writing a driver for Linux,you depend on someone who does.
This makes it not easier to find it.
I suppose you did a search on the forums and Google as well?

Is it not much easier to disable the raid for now and use the hdd's on their own?

---

### Post by greenhornet on 2007-04-30
I did search and check.  There's plenty of discussion about the ITE8212.  Some of it in these forums.  The ONLY solution I have seen (other than installing Debian) is to rebuild the kernel.  I'm not near skilled enough for that.

I could disable the RAID.  I could also tape a trash bag over my car window.  Neither of which appeal to my needs.

---

### Post by bulldog on 2007-04-30
> **greenhornet said:**
> I did search and check.  There's plenty of discussion about the ITE8212.  Some of it in these forums.  The ONLY solution I have seen (other than installing Debian) is to rebuild the kernel.  I'm not near skilled enough for that.

I could disable the RAID.  I could also tape a trash bag over my car window.  Neither of which appeal to my needs.

Yes you could :) ,but there's a huge difference between those options.

But do as you like,never rebuild a kernel myself,so can't help you with that.

---

### Post by sgoodall on 2007-04-30
I have an ite8212 based card in my machine and the only way I have feisty working is by using the edgy kernels (im running 2.6.17-11-generic).
This card works fine in both edgy and fedora 6, the problem is the new sata driver not working well with these raid cards. Hopefully this issue will be resolved sometime soon.

---

