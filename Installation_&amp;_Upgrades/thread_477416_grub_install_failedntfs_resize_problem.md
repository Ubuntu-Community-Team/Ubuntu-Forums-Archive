---
title: "grub install failed/ntfs resize problem"
date: 2007-06-18
forum: Installation &amp; Upgrades
---

### Post by frenchie091 on 2007-06-18
Hi,
I have a 40GB disk dual-booting with WinXP(ntfs,hd0) and Ubuntu Feisty(ext3), and a 200GB (ntfs,hd1) disk for data. I recently needed to reinstall my Windows. I backed up my Ubuntu system into a tar file on the data disk, and reboot with the WinXP install disk. I used this to format the Windows partition and reinstall XP.

I then booted up the Ubuntu live CD, intending to reinstall grub on the MBR. I had tested this before I did anything, and it worked fine. But, alas, not now.  Here's the action replay:

grub> find /boot/grub/stage1
 (hd0,5)
grub> root (hd0,5)
grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+15 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 22: No such partition
grub> 


Things were not going to plan. and they continued that way. I didn't know what to do about this, so I installed a fresh Ubuntu on an ext3 partition on the 200GB disk, having used the Ubuntu partition manager to resize the NTFS partition. I untarred my Ubuntu backup to this partition, then ran grub install to see how things looked. 

grub> find /boot/grub/stage1
 (hd0,5)
 (hd1,2)

setting root(hd0,5) and setup (hd0) still fails. However, root (hd1,2) and setup (hd0) works. So, at least I can now boot into my Ubuntu system.

BUT: now windows can't see the ntfs partition on the data disk. It says it's raw and offers to format it. Which is awkward, I only use Windows for music production, and all my production files are on the data disk.

So, to my questions, of which there are two:
- Can anyone help me understand what the hell went wrong?
- How do I get Windows to see the ntfs partition, while preserving everything on it?

Thanks in advance, I'm stumped.
John.

---

