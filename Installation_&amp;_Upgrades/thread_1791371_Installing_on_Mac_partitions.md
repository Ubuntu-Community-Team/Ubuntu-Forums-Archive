---
title: "Installing on Mac partitions?"
date: 2011-06-26
forum: Installation &amp; Upgrades
---

### Post by Chris Richard on 2011-06-26
Background: I'm new to Unbuntu/Linux as far as installing and using on my own computers, but do have quite a bit of background with formatting and partitioning drives. 

Can Ubuntu be installed on the _MAC_ partition of an Intel Mac, or not?

Every time I google this question with various phrasing I end up with instructions to use either standard Unbuntu intallation, or use a combination of rEFIt! and Bootcamp. I already have a Windows XP installation on this Mac, and both ways only offer the option to use the Widows partition of the Mac drive, NOT the Mac partition. It appears to me that Ubuntu can only be installed on an NTFS or FAT formatted drive?

I really don't WANT to use the Windows partition, since one computer I have has far more space on the Mac formatted side. Is this even possible, and if so, why am I having such a hard time finding how that's done?

Additionally, I have a second Mac with the exact same setup, but neither partition has a lot of room left. I do though, have two other drives on it with plenty of room. One Mac formatted, and the other NTFS. I can find all sorts of instructions on how to create a bootable usb drive, but nothing on partitioning and installing on a SATA. At least it sure isn't as easy to find.

So the three questions are:

1) is it possible to install Ubuntu on the *_MAC_* partition of an Intel Mac?

2) Can, and if so how, I install Unbuntu on a totally separate SATA drive partition?

3) if the above is possible, can I install it on a MAC SATA (Mac OS Extended (Journaled)) drive, and if so, how?

Thanks.

---

### Post by srs5694 on 2011-06-26
Ordinarily, Linux installs in its own partitions, not on either Mac or Windows partitions. There is a way of installing Ubuntu, known as WUBI, that installs Ubuntu to a file in a Windows partition. I dont' know if a WUBI install to Windows on a Mac would work, though.

The usual way of installing Linux to a Mac that already has both OS X and Windows is to use the OS X partitioning tools to shrink one or both of your existing partitions and then run the Ubuntu installer, which has its own tools for creating Linux partitions. There are quite a few guides online to help you do this, but I don't happen to have any URLs handy, except to [my own,](http://www.rodsbooks.com/ubuntu-efi/index.html) which doesn't really fit exactly what you want to do.

Unfortunately, you are heading into a minefield. The problem is the [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) partitioning system that Apple chose to use to enable Windows and OS X to coexist on a single disk. Hybrid MBRs are dangerous to mess with, and it's entirely possible you'll break Windows' ability to boot by installing Linux. Such problems can be overcome, but doing so requires a lot of knowledge. You might want to consider running Ubuntu and/or Windows in a virtual machine inside OS X rather than deal with the complex partitioning and boot loader issues involved in a triple-boot like this.

---

### Post by Chris Richard on 2011-06-27
> **srs5694 said:**
> Unfortunately, you are heading into a minefield. The problem is the [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) partitioning system that Apple chose to use to enable Windows and OS X to coexist on a single disk. Hybrid MBRs are dangerous to mess with, and it's entirely possible you'll break Windows' ability to boot by installing Linux. Such problems can be overcome, but doing so requires a lot of knowledge. You might want to consider running Ubuntu and/or Windows in a virtual machine inside OS X rather than deal with the complex partitioning and boot loader issues involved in a triple-boot like this.

I already have it running on OS X through Virtualbox, which is fine for learning, but is definitely NOT the best way to operate. I need this thing to boot up and run on it's own. The ultimate goal is to wipe out the entire Windows XP system on a second computer (Windows only), to use as a server (not sure if I really want Unbuntu for that just yet, but we'll  see ~ I do plan to test some other Linux builds as well). 

You could say I'm in the "educational" stage of this, and I want to learn to do it right, not just play with it, if you know what I mean. First step was virtual machine, second step is dual-boot installation. Final step, once I decide which build suits me best, is a full install on one of my windows machines.

As I mentioned, I have quite a lot of experience formatting drives, but never before on a Bootcamp system, which I know can get quite hairy, but I'm fairly confident I know what I'm doing as far as avoiding the pitfalls. In other words, I don't mess with nothin' I ain't 100% certain of. I do my due diligence and research before moving forward with anything. All my experience, until now, has been with formatting for read/write storage only. This is the first time I'm trying to create a boot volume from  a partition.

I think I've already sidestepped that minefield you mentioned by creating a partition using a windows utility from the Windows bootcamp side, on an already NTFS drive that currently is used for nothing but storage. I forget at the moment what the software was exactly, but I remember selecting "primary" which the software recommended for using as a boot partition. It shows up fine in Mac, and Windows, and Ubuntu install sees it, but of course (as I read from many other posts trying to do similar installs), I get the "No root" error when trying to install it, and don't yet know how to fix that.

Any clues on that? Is there an option in Ubuntu install process I'm Missing?

---

### Post by Chris Richard on 2011-06-27
Yeah, I don't know if this came across very clearly:

What I'm actually trying to do is install Unbuntu on one of two separate storage drives, not the Mac OS drive, where Mac and Windows already are. There simply isn't enough room on it.

I have two other drives installed. One NTFS, and one Mac journaled. The Mac drive has a lot more room on it, so I was hoping to use that one, but before even reading what you said here, quickly became uncomfortable with even trying that, so that's when I decided to just boot up in Windows and format a new partition on the NTFS drive instead.

So I've already got a 60 GB NTFS partition ready and waiting for Ubuntu, but not sure how to proceed using the "I want to do something else" install option. No trouble identifying which drive it is, just what to do about the "root problem." This is either a little bit new to me, or I've forgotten something (it has been a while).

---

### Post by Chris Richard on 2011-06-27
Okay, in spite of the many posts I've seen on that last question (about the root problem), it's kind of sad how many folks all over the web seem to be so protective of what they know. 

Anyway, I did finally find the setting, and it's up and running right where I want it now. 

Thanks for nothin'. 

:P  Just kidding.

---

