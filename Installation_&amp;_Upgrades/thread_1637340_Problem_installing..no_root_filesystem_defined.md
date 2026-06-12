---
title: "Problem installing..no root filesystem defined"
date: 2010-12-04
forum: Installation &amp; Upgrades
---

### Post by sweetandsour on 2010-12-04
I had a problem with my 9.8 version of ubuntu. It sort of crashed,showed up a grub error.

So I thought,I will install 10.04...But when i started on with the installation

While I was doing the installation process,in step 5 it came like this

"No root file system is defined. 

Please correct this from the partitioning menu". 

I guess my disk space is less or should i change hardware?

Would be greatful if anyone can help me out here!


I tried sudo apt-get dmraid
ubuntu@ubuntu:~$ sudo apt-get remove dmraid
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  dmraid
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 184kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 129800 files and directories currently installed.)
Removing dmraid ...
update-initramfs is disabled since running on read-only media
Processing triggers for man-db ...
ubuntu@ubuntu:~$ 

between i am not much into all these stuffs..please help me out with the steps...

---

### Post by dino99 on 2010-12-04
welcome :)

your issue is all about how to format: you need to make the "/" partition "bootable": take time to set the formatting choices correctly then validate them step by step (for each created partition)

installing dmraid can bring you in troubles if you are not used with raid.

sudo dmraid -rE

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by sweetandsour on 2010-12-04
> **dino99 said:**
> welcome :)

your issue is all about how to format: you need to make the "/" partition "bootable": take time to set the formatting choices correctly then validate them step by step (for each created partition)

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

When i open gparted it doesnt show anything.

[IMG]http://oi56.tinypic.com/2ebs7it.jpg[/IMG]

---

### Post by dino99 on 2010-12-04
so is there an hdd or ssd inside your system ?

as you have tried dmraid previously, boot on a livecd and run the command given to remove dmraid before doing anything else.

---

### Post by sweetandsour on 2010-12-04
> **dino99 said:**
> so is there an hdd or ssd inside your system ?

You mean hard disk?..Yes i do have..I have been upgrading different versions of ubuntu for the past 4,5 years...never came across this problem..

---

### Post by sweetandsour on 2010-12-04
i am booting from live cd only now

---

### Post by oldfred on 2010-12-04
Two things to review:

Run chkdsk on any NTFS partitions even if they currently work.

[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

You could also download the very newest gparted liveCD and see if that sees your drive.
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

### Post by sweetandsour on 2010-12-05
ubuntu@ubuntu:~$ sudo ntfsfix /dev/disk
Mounting volume... Error opening partition device: Is a directory.
Failed to startup volume: Is a directory.
FAILED
Attempting to correct errors... Error opening partition device: Is a directory.
FAILED
Failed to startup volume: Is a directory.
Volume is corrupt. You should run chkdsk.
ubuntu@ubuntu:~$ 

how do you run chdsk?

---

### Post by oldfred on 2010-12-06
You have to run it from a windows CD. And you have to rerun it until there are no errors as it does not fix everything on one pass.

XP CHKDSK
chkdsk drive /p /r
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information. Run chkdsk several times, until no more errors are detected.
chkdsk c: /r

Vista/7 CHKDSK
chkdsk C: /f /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

