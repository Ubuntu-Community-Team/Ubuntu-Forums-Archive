---
title: "64bit AMD Athlon 3200 install with 7.04 failure at partition creation"
date: 2007-07-10
forum: Installation &amp; Upgrades
---

### Post by Rhemat on 2007-07-10
I'm trying to install Ubuntu 7.04 64bit AMD edition on a 64bit AMD Athlon 3200.  It works just fine until I get to the partition guide.
  It doesn't hang, but when I tell it to format the drive, it just tells me "The ext3 file system creation in partition #1 of SCSI1 (0,0,0) (sda) failed."  It then suggested I partition the system to use only 50% of the 200gb drive, and I try to do that, but then it gives another error informing the kernel about the modification to the drive, and it won't know about it until I reboot.  I click ignore, and it gives me the error again, so I click ignore again.  Then it just tells me that the partition had an error again, and that it is simply aborting the process.
  I can't leave the drive alone, nor can I partition it.  Should I try a different/older version, or what?
  Thanks in advance.

-Rhemat

---

### Post by misfitpierce on 2007-07-10
If you have windows on HDD insert windows disc and delete the paritions.. then reinsert feisty and go to gnome partitioner before the installer make sures partitions are clear... if not delete them and apply... then install and hope for the best?

---

### Post by Qrk on 2007-07-10
Ubuntu's gparted version is slightly out of date. Why don't you try the newer version of gparted to see if it helps?

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

---

### Post by Rhemat on 2007-07-10
Unfortunately I don't have the windows Cd, but I'll ask around to see if someone has one I can use.  About the gparted, that is something I could use in the Live desktop?  Otherwise, I'm not certain how else I'll get the Windows wiped from the drive.

Thanks for your expedious replies though.

----------------------

Ah, didn't know gparted acted as a live CD.  Thanks, I'm downloading it now.

-Rhemat

---

### Post by Qrk on 2007-07-11
My link is to the gparted live cd. You'd download and burn that cd, boot into it just like you would Ubuntu's live cd, partition, boot up Ubuntu's live cd, and install.

---

### Post by Rhemat on 2007-07-11
Thanks,  I booted gparted and told it to format the drive, and now Ubuntu is installed.

-Rhemat

---

### Post by Rhemat on 2007-07-12
Well, I'm having some problems running my games (Quake 3 and Enemy Territory) on the AMD, I found the program Linux32, but that isn't helping yet.  I was wondering if the 386 version of Ubuntu 7.04 would work on the AMD.  I know that if it does, I won't be getting the best performance out of the machine, but I know it should still be better than what this machine is able to do,  I guess for comparison:

686 machine:
1.3ghz, 512mb SDRAM

AMD64 machine:
3200+ AMD Athlon 64, 512 DDRRAM (at least I think)

Thanks again for your help.

-Rhemat

---

### Post by Rhemat on 2007-07-13
Well, I took the advice of a fellow Linux gamer, and ran the command as root, and the install went quickly.  I used the Linux32 utility, so this is what I typed in the console:

sudo linux32 [quake-point-release-file-here]

Hope that helps anyone else having troubles with this kind of thing.  I guess I'll keep the 64 bit edition after all.  Once again though, thanks to all who helped me.

-Rhemat

---

