---
title: "Ubuntu installer's partitioner doesn't see Windows partitions."
date: 2015-01-15
forum: Installation &amp; Upgrades
---

### Post by david12 on 2015-01-15
I have installed Windows 8.1 64-bit on a new System 76 box.  (I've followed System 76's instructions regarding a Windows dual boot set up. They advise installing Windows first, which means overwriting the Ubuntu install that the System 76 computer comes with,  then re-installing Ubuntu.)
Windows works.  I am typing this query in it now.

There is one hard drive on the machine. It is 2TB in size. There are two Windows partitions on the hard drive: a "main" partition and a "reserved" partition.  The "reserved" partition is small (350MB); I reduced the "main" Windows partition to 500GB+- using GParted from a live GParted disk. Approximately 1.4TB+- remain for the Ubuntu installation.  This 1.4TB is "unallocated."

Running Ubuntu 14.04.1 LTS from a DVD works fine.  The main Windows partition is visible and accessible from Ubuntu Live. (Sidebar:  In order to make the partition accessible it was necessary to disable a not-particularly-obvious hibernation function in Windows.  The Windows command to do that is:[COLOR=#ff0000] powercfg /h off[/COLOR]. It needs to be run from the command line as an administrator.)

The problem arose when I tried to install Ubuntu.  _[COLOR=#006400]The partition manager within the Ubuntu installer does not see either of the Windows partitions.[/COLOR]_  The entire disk, all 2TB, is shown as "unallocated."  To underscore:  Windows is installed and functioning.  I can access the "main" Windows partition from live Ubuntu when it is running on the computer, but when I go to install Ubuntu the installer doesn't see the Windows partitions.

Windows describes (in 'Disk Management') hard drive partitioning as: "Partition Style: Master Boot Record".  It shows two partitions, then unallocated space as described above.

The Ubuntu installer's partitioning software (but not GParted Live) presents a 'yes' or 'no' query asking whether the disk is MBR or GPT.  I've answered the question both ways, but neither seem to have effect.  (One response, returns a red "[COLOR=#ff0000]![/COLOR]" next to the unallocated line. The other doesn't.  I don't remember which is which, but neither was any help.

I contacted System76 and asked for assistance, but they are not familiar with the problem.

---

### Post by oldfred on 2015-01-15
I saw one other thread where they now use gpt as it is an improved partitioning system.
But Windows only boots from gpt with UEFI. So when you install Windows in BIOS boot mode, it incorrectly converts gpt to MBR(msdos) partitioning. It leaves the backup gpt partition table which confuses Linux tools that see both MBR & gpt.

You need to remove backup gpt partition table.
       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
sudo fixparts /dev/sda

---

### Post by david12 on 2015-01-15
Thanks, Oldfred, it worked.  I will pass this thread along to System76.  They might need the information in the future. ;)

---

