---
title: "(ask) GRUB2 on RAID0 installed to patition boot record"
date: 2010-09-16
forum: Installation &amp; Upgrades
---

### Post by phillipdhall on 2010-09-16
First, thank you to those who have been helping me, and others on the forum with similar problems. 

I'm looking for an alternative to grub2 or some other method of booting Ubuntu 10.4.1 from the partition boot record.

From what I understand, GRUB2 does not interpret FAKERAID correctly, and therefore cannot be installed to the partition. (It was hard enough to get it installed at all!)  This causes a couple problems for me:

* I run 5 OS installations on my array, move them around occasionally, and really would prefer to stick with a  third-party boot manager at the MBR. GAG had been working well for me.

* GRUB2 is not loading my Win 7 partitions correctly (maybe not setting destination as active?).

* I hate the way GRUB2 is configured. As partitions change, I will need to reconfigure the MBR loader frequently, and the methods grub present for editing menu entry text and defaults seem a little ridiculous.

So the question is, has anyone found a way to force GRUB2 to install to the root partition on a fakeraid array?

Is there another bootloader that could be installed to the root partition?

If all else fails, could I create a /boot partition on a separate, non-raid drive that would load Ubuntu on my raid root partition?

Again, I really appreciate any help that can be offered, and a shout out to ronparent and xenton for getting me this far.

Phil

---

### Post by ronparent on 2010-09-16
> So the question is, has anyone found a way to force GRUB2 to install to the root partition on a fakeraid array?

The short answer is yes. I've done it following method 1 in this reference: [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

The trick is to be sure to designate the symbolic link for the overall raid rather than one of the component disks or a raid partition. I can tell from your question that you recognize what the root partition is on a fakeraid, but, I can't see why it is not working for you!

---

### Post by phillipdhall on 2010-09-16
Thank you for your response. I have seen you patiently sharing your expertise through the forum for several people. You rock!
 
Please correct me if I am misunderstanding... I believe the method you mention, using the symbolic link for the overall raid rather than one of the component disks or a raid partition, will replace the MBR of the array. I was able to get GRUB installed at the MBR and successfully boot *most* of my OSes. However, I am really hoping to keep GAG in the MBR, and GRUB (or whatever would work) at the partition boot record.
 
In the mean time, I was able to successfully create a /boot partition on a non-raid drive for loading my Ubuntu installation from GAG. This will likely make things more difficult when I image and restore my partitions to other locations, but at least the windows installation my wife uses will still work, and its easier than booting from the Super GRUB2 disk each time :-)
 
Thank you again for your help, and let me know if I am misunderstanding the method you mentioned.
 
Phil

---

