---
title: "New user with Ubuntu troubles"
date: 2013-02-13
forum: Installation &amp; Upgrades
---

### Post by TheMagicHorsey on 2013-02-13
Hello everyone, I am a new Ubuntu user so please be patient.

**_Background_**
I recently decided to try Ubuntu and to do so I purchased a new hard drive.  I partitioned the hard drive as instructed by the installation directions, and installed the latest version of Ubuntu on it.

I thus got a stable working version of Ubuntu running on my home system, which worked harmoniously alongside my Windows 7 operating system (which exists on a different drive).

The GRUB boatloading system works great and allowed me to choose between Windows 7 and Ubuntu at start up.

***Problem***

Last night Windows 7 ran an automatic update.  After this update the GRUB bootloader would no longer appear on restart.  Rather the screen of my computer contains only a blinking prompt.

I troubleshooted the problem myself (with my limited skills) and was eventually able to discover that for some reason, when the computer boots by itself, GRUB does not load.  But if I go into the bios and select my primary boot device, overriding other boot devices, GRUB does load, and it presents me with the correct list of boot choices (i.e. Ubuntu, Windows 7, etc.)  However, while I can still enter Ubuntu and use it, if I select Windows 7 from the GRUB menu, Windows does not boot, and again I see the same blinking prompt that I described above.

It appears that two things have happened due to the Windows 7 update:
1) Windows update overrode GRUB so that now GRUB does not run by default when I restart my machine.
2) Windows update was not expecting GRUB to exist, and now somehow its own bootloader (or whatever it is, I'm not familiar with how Windows boots) does not run.

***Request***

If anyone has encountered such a problem, or if you have some idea of what might be going wrong, or how I can proceed to debug the issue, please let me know.  As I mentioned, I have access to my Ubuntu install and can use any Ubuntu tools to resolve the problem.  It is the Windows 7 install that no longer works.

Any help is greatly appreciated.

Cheers

---

### Post by ibjsb4 on 2013-02-13
A easy way to fix boot problems

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by TheMagicHorsey on 2013-02-13
> **ibjsb4 said:**
> A easy way to fix boot problems

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Thanks,  I will try that!

---

### Post by grahammechanical on 2013-02-13
What is your primary boot device? The Ubuntu drive? Microsoft has no reason in the world for making its OS co-exist with any other OS.

When you are in Ubuntu you could try running

```
sudo update-grub
```

That should detect the Windows OS that is on the other drive and re-write the Grub configuration files.

It is my guess that if we start off with the Ubuntu drive as the first drive and the Windows drive as the second drive then if the order gets changed Grub will find the Ubuntu OS if you boot into the Ubuntu drive with Grub installed on that drive but it will not find the Windows OS on the Windows drive. The drive designations are not matching up to what is listed in Grub configuration files.

Regards.

---

