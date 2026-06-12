---
title: "Help booting Windows again after installing Ubuntu and using EasyBCD"
date: 2014-03-19
forum: Installation &amp; Upgrades
---

### Post by DJ_McCarthy on 2014-03-19
Hi guys,

I tried to dual-boot Windows 7 Ultimate and Ubuntu 12.04 using EasyBCD to manage the boot process. I got Ubuntu installed fine (Windows was already installed/in use). When I booted back into Windows to use EasyBCD to manage the boot process, I made the suggested changes and nothing seemed to work to get Ubuntu to be recognized by the Windows boot loader. Consequently, I followed the following Q/A in order to try to fix my problem: [http://askubuntu.com/questions/124617/easy-bcd-help-dual-boot-win7-and-ubuntu-11-10-add-new-entry-for-ubuntu](http://askubuntu.com/questions/124617/easy-bcd-help-dual-boot-win7-and-ubuntu-11-10-add-new-entry-for-ubuntu). I used the suggestions that the first responder gave, replacing sda1 with sda3 as this was the partition I installed Ubuntu on. . . after this I attempted to reboot and could not boot anything.

I have now live-booted Ubuntu and used the boot-repair in order to try to fix the issue. I can now access the Ubuntu installation on the hard disk via the GRUB boot loader, but the Windows installation does not show up as an option. I feel like I am getting closer to a solution. Here is the results from the boot-repair: [http://paste.ubuntu.com/7122975/](http://paste.ubuntu.com/7122975/)

Any ideas of what I can do to get back to my Windows partition? Once again, I AM on the Ubuntu partition on the disk now, if that helps. Thanks very much!

---

### Post by Mark Phelps on 2014-03-20
From the boot-repair report, the two (former) NTFS partitions are hosed. It's unlikely that you will be able to get Win7 back in working order, but if you want to try, then do the following:
1) Download the ISO file for, and burn a CD of, the Minitool Partition Wizard Boot CD.  This is a Windows partitioning tool, and in my long experience, Windows tools do the best job of repairing Windows filesystems; Linux tools, for Linux filesystems.
2) Boot your PC from that CD and see if it offers you the option of repairing the partitions.  IF it does, try those.
3) When you reboot, you probably won't be able to boot into Win7 (that is a different fix), but you can at least mount your partitions from Ubuntu and see if the filesystems were restored.
4) IF the file systems were restored, then go to the link below, purchase the Win7 Repair CD ISO file, download it, burn it to CD -- and run Startup Repair three times, that's right, three times.  (Note: You could have make this Repair CD for FREE when you had Win7 working).  Link: [http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")
5) Once you can get back into Win7, you will need to restore boot capability to Ubuntu.  How you do that is up to you.

---

