---
title: "Uninstalled Ubuntu via Windows, unable to boot into Windows (grub rescue prompt)"
date: 2013-08-11
forum: Installation &amp; Upgrades
---

### Post by ajay3 on 2013-08-11
Hello,
I uninstalled my Ubuntu partition in Windows 8 and reclaimed my free space. However, when I try to reboot, I see the infamous "error: no partition found"  and the "grub" rescue prompt. After doing a lot of reading on this, I read that the only way to fix this is to use a Windows 8 disk and run the recovery tools. The problem is that I don't have access to my Windows 8 disk, since my laptop did not come with it. Additionally, I read that I can fix the problem from live booting Ubuntu. So, I set up my flashdrive using LinuxLiveUSB Creator (LiLi), and downloaded the latest version of Ubuntu 13.04 64-bit from the official website. When I select my flashdrive and boot into it, I get the same exact grub rescue error. Any help would be much appreciated! One thing I noticed was that when I downloaded the OS from the site, the MD5s didn't match. Is there a better place I can download it from? 

Thanks much, I really need to get my Windows back!

EDIT: I've also tried using PenDriveLinux, Unetbootin. All with the same result.

---

### Post by davetv on 2013-08-11
You are going to need a Windows 8 disk. No other way around it that I can think of.

---

### Post by Mark Phelps on 2013-08-11
I know it's a little late now, but when you get Win8 running again, you should use the option to create a "recovery drive" -- and despite that name, it will actually create a recovery Disk -- which you could use in the future to make these kinds of repairs.

Also, since this is purely a Win8 problem, my suggestion is for you to visit the Windows 8 forums (eightforums.com) and post your question there.  They may be able to tell you how to do this without having to go out and buy a Win8 disk.

---

### Post by oldfred on 2013-08-13
Is this a UEFI system or BIOS system? If Windows 8 pre-installed it will be UEFI.
Can you go into UEFI menu, turn secure boot back on and select the Windows boot choice?

---

