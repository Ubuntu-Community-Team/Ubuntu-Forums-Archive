---
title: "Can't install 10.10 on 2 TB drives for RAID 1"
date: 2011-01-20
forum: Installation &amp; Upgrades
---

### Post by Widescreen on 2011-01-20
I've searched through the forums and I get pieces of what I might need to do, but I can't find anything **specific** to what I want to do.  

I just got two Samsung 2 TB hard drives that I want to boot into a mirrored RAID 1.  Unfortunately, I can't set any partition to be bootable.  If I let the install continue, when it gets to the point of installing GRUB it bombs out that it can't install GRUB on sda. 

Apparently, the issue is with having >=2TB drives.  I did some searching and found tips about getting GRUB installed manually, but all of the topics seem to refer to a single disk.  But when it comes to  a bootable mirror, the vast majority of what I'm finding says to use the alternate CD and create the mirror from the start of the build.  Well, *that's what I'm trying to do* but I'm getting slammed by this 2TB issue!

I'm halfway tempted to install Solaris x86 and mirror the disks with DiskSuite (SVM) if they accept the 2TB disks, but I'd like to stay with Ubuntu.

Would I be better off booting of disks that are less than 2 TB?  I planned on adding my existing 1.5 TB disks later to make a 3.5 TB mirror; but if it's easier to boot from 1.5 TB disks and add the 2 TB as extra storage, so be it. (I can't add the 2TB disks to my existing server because there aren't enough SATA ports and I don't want an expansion card as another point failure.)

Has anyone successfully been able to mirror 2TB disks together without having to do a ton of steps?

---

### Post by serge_o on 2011-02-19
> **Widescreen said:**
> I've searched through the forums and I get pieces of what I might need to do, but I can't find anything **specific** to what I want to do.  

I just got two Samsung 2 TB hard drives that I want to boot into a mirrored RAID 1.  Unfortunately, I can't set any partition to be bootable.  If I let the install continue, when it gets to the point of installing GRUB it bombs out that it can't install GRUB on sda. 

Apparently, the issue is with having >=2TB drives.  I did some searching and found tips about getting GRUB installed manually, but all of the topics seem to refer to a single disk.  But when it comes to  a bootable mirror, the vast majority of what I'm finding says to use the alternate CD and create the mirror from the start of the build.  Well, *that's what I'm trying to do* but I'm getting slammed by this 2TB issue!

I'm halfway tempted to install Solaris x86 and mirror the disks with DiskSuite (SVM) if they accept the 2TB disks, but I'd like to stay with Ubuntu.

Would I be better off booting of disks that are less than 2 TB?  I planned on adding my existing 1.5 TB disks later to make a 3.5 TB mirror; but if it's easier to boot from 1.5 TB disks and add the 2 TB as extra storage, so be it. (I can't add the 2TB disks to my existing server because there aren't enough SATA ports and I don't want an expansion card as another point failure.)

Has anyone successfully been able to mirror 2TB disks together without having to do a ton of steps?

I have encountered the same problem. As far as I know (now that I have searched through many forums including this one) Ubuntu 9 onwards, (10.04, 10.10) do not work with boot on RAID1+2TB HDDs.
I tested that several times, including one guided partitioning install where I changed nothing and just chosen "guided" and clicked through it.

I have seen many separate threads about this, but no official description of the bug.

the issue is this. Ubuntu supports GTP (this is official). GRUB2 supports GPT (this is official).  All New versions of Ubuntu use GRUB2 (this is official).

But Ubuntu+GRUB2+2TB+RAID1 does not work (got the same error as you - it does not install) - I wonder why I could find this bug description on launchpad.

regards,
Serge

---

### Post by rickbeton on 2011-02-19
I had the same issue but my PC also happens to have a non-raid disk for Windows. So I snaffled some space (as ext4) and simply set Ubuntu up to boot from that.

My original plan had been to have a raid0 partition and a raid1 partition; I wanted to boot from the raid0 partition.  But this proved unreliable - it kept messing up and I'd have to use mdadm to rebuild the raid arrays. I got tired of that.

So I simplified it, putting / on my non-raid disk and keeping /home on my raid1 array. If I lose the non-raid disk ever, then I'll need to re-install Ubuntu but I won't lose my personal data so easily. It'll only cost me the time of re-installing, which isn't hard.

But even this is still not really sufficient for my paranoia, so I also keep my important work backed up in my Subversion server (separate on the LAN) and achieve another layer of backup that way. And the Subversion server itself has a slave server backing it up too (ideally, this would be in a different place).

Belt, braces and the rest!

Rick

---

### Post by serge_o on 2011-02-19
This is nice that one can work around this issue (this is mostly the case, however, - there is hardly an issue without any workaround).

I too have several other servers with 1 and 1.5 TB and it works perfectly there so there is nothing thaaat urgent. this is however, important to fix, cause soon I will have to upgrade to 3TB in all servers - and I want to keep original Ubuntu, no alternate CDs.

---

