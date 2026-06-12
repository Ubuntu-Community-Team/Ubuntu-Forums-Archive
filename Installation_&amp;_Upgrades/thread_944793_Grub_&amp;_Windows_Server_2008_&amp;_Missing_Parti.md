---
title: "Grub &amp; Windows Server 2008 &amp; Missing Partitions??"
date: 2008-10-11
forum: Installation &amp; Upgrades
---

### Post by jorwex on 2008-10-11
Hey all,

I thought I'd give Windows Server 2008 a try because Microsoft's Dreamspark had it available for free. I installed it on an extra sata drive I had and started playing around with it and eventually yearned for Ubuntu again and rebooted and changed my harddrive priority back to the drive w/ Ubuntu & grub.

I guess Windows rewrote the MBR on both drives because no matter the drive I chose to boot to, the Windows menu came up. So I popped in my LiveCD and reinstalled grub. Now I'm back in Linux.

I was trying to add Server 2008 to my grub menu so I don't have to keep going into the BIOS to switch, but I get a "BOOTMGR not found" error that I've been reading about here and lots of other places & I think I can eventually sort out.

What I'm more concerned about is that in gParted, if I select that 2nd drive where Windows is installed, the whole thing shows up as unformatted space....

<----Confused

I set up two partitions on the 320GB drive that it's on, and put it in the first one as a primary partition. The only thing I could think of is that it's using a filesystem that Ubuntu doesn't understand, but I thought it used NTFS. I had the whole disk as a GPT previously, and reformatted the drive in the Windows installer if that might have something to do with all of this.

Any ideas?? Thanks again everyone!

---

