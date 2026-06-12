---
title: "Wubi install error: No root file system is defined."
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by aachen on 2008-05-12
I tried to install ubuntu by Wubi. when i reboot the computer to complete further installation, it gives me error 'No root file system is defined. Please correct this from the partitions.' and then nothing works. i need to press the hardware button for reboot the computer. did anyone face this problem before ?

---

### Post by rstritmatter on 2008-06-09
> **aachen said:**
> I tried to install ubuntu by Wubi. when i reboot the computer to complete further installation, it gives me error 'No root file system is defined. Please correct this from the partitions.' and then nothing works. i need to press the hardware button for reboot the computer. did anyone face this problem before ?

Anyone have a clue on this?  I am getting the same error message trying to reinstall ubuntu on double boot system. Vista was working fine, but I had major screen management problems that I could not fix with ubuntu. So I tried reinstall from Ubuntu live disk and got a freezing screen that won't take me past "boot from cd option." So I am on live cd install again, and now getting this same error message. Any assistance is greatly appreciated!

Thanks.:guitar:

---

### Post by rstritmatter on 2008-06-09
Oops!  I sorted this out on my own: by using the "advanced" option of reinstalling bootloader while attempting reinstall of Ubuntu I apparently got Grub back in right location and it is now allowing boot for both Ubuntu and Windows, with Ubuntu new version without the screen problems!

Cheers.

:)

---

### Post by macross5 on 2008-09-18
Hello

I'm new to this and I have the same problem, could you tell me where can i find the "reinstall bootloader" option please?

thank you

---

### Post by Innicas on 2008-09-26
This seems to be the problem that has me on these forums, any further help would be great.

Thanks

---

### Post by jabela on 2008-10-28
I've got the same problem with Wubi too....Tried both Ubuntu 8.04 and Ubuntu 8.10 on a new Toshiba Vista install. 

James

---

### Post by Rickeo on 2008-10-30
Same problem here, how do we fix it? I can't get past this error to continue the install.

Intalling 8.10 on a Vista 64 system.

---

### Post by t1m on 2008-11-10
Hello all, same thing here.

The laptop I'm trying to install ubuntu to only has a 9-GB hard drive, and most of it's used up.

When I start Wubi, I get an error: "You have 255 MB of memory, the installer requires 256 MB." No big deal, right? So I click "yes" to continue. Then I get this: "You have 1458 MB free, the installer requires 5000 MB free." Obviously this won't work, but I didn't realize this "free memory" was *disk* space. So I installed Ubuntu, I got the "undefined root filesystem" error. I then realized that there wasn't enough hard disk space, so I tried Xubuntu. (It's supposed to be smaller, according to Xubuntu.com, so I assume Wubi-Xubuntu is the same.) When I boot, I still get the same error.

Also, I can't see the c:\ubuntu\disks\root.disk file, which is supposed to be where the wubi installation is. How on earth can I get up to the error message running on a file that doesn't seem to exist? Hmmm.

Anyone else think that your hard disk might not have enough space?


Cheers and :popcorn:

**Update: I simply did not have the space on the hard drive to install Ubuntu. The computer now has a bigger hard drive, and I have succesfully installed a normal (i.e. non-wubi) Ubuntu.**

---

### Post by saturngod on 2009-05-04
I have a same problem in Toshiba Satellite M200.... I just install 10 GB and I have free 36 GB... I wanna use it.... :(

---

### Post by demon36 on 2009-06-22
Iam having same problem .. about  a week till now and I cant install ubuntu .. Iva tried 9.04 , 8.04.2 , 8.10 every time I get a different error . I rlli need help .

---

### Post by demon36 on 2009-06-22
HEY ALL CHECK THIS
[http://ubuntuforums.org/showthread.php?t=948083](http://ubuntuforums.org/showthread.php?t=948083)
IT SHOULD HELP U ABOUT IT

---

### Post by demon36 on 2009-06-22
HEY ALL CHECK THIS OUT
[http://ubuntuforums.org/showthread.php?t=948083](http://ubuntuforums.org/showthread.php?t=948083)
IT SHOULD HELP U ABOUT IT

---

### Post by maopu on 2010-06-29
it has been 2 years!i am facing the same problem,and i am trying to install ubuntu 10.4 over 9.04.



it seems there is something wrong with hard disk,you've probably format your hard disk in many ways,so ubuntu can't detect it well.try to format it again,it may works

---

### Post by someshwar_m on 2010-07-09
Same problems, and I believe it has really to do with the type and number of partitions. I tried to install ubuntu 10.04 from the ISO image and wubi.exe. I wanted to have a frugal install since I have a lot of space in the C drive and don't want to create any dedicated partitions for Linux.

I am using a newly purchased Lenovo G460 laptop. It has pre-installed Windows 7. What I discovered is:

[LIST=1]
[*]All the 3 primary partitions and 1 extended partition have been created from the factory. The layout of the partitions is primary1, primary2, extended and primary3.
[*]Out of the 3 primary partitions, the first and the last are hidden partitions. Both show up as NTFS in the Windows disk manager, but are without any drive letters. The second primary partition (primary2) is C:\ for windows.
[*]In gparted, the disk is not recognized correctly at all! The size is reported to be a negative number. It cannot detect the 3 primary and 1 extended partitions.
[/LIST]
Since I don't want to screw up the 1 key recovery system that Lenovo supports, I do not wish to have to recreate the partitions myself. I know a dedicated primary partition for Linux might be able to solve the issue.

Does anybody have better ideas - or are facing the same issues?

Thanks,
- Somu

---

