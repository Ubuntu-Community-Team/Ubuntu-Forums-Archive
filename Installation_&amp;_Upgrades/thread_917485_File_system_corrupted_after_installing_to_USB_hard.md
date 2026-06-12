---
title: "File system corrupted after installing to USB hard drive"
date: 2008-09-11
forum: Installation &amp; Upgrades
---

### Post by zxtonl on 2008-09-11
After installing Ubuntu/Kbuntu 8.04.1 to a partition of an external USB hard drive, many errors are reported when running fsck on that partition.

I tried installing many times, using the desktop cd, using the alternative cd, using different computers, even tried inside vmware. I always got a corrupted file system. 

This problem seems Debian related, for Debian 4.0 also gives a corrupted installation.

OpenSUSE and Gentoo do not have this problem.

The file systems I tried are ext2/ext3.

Anybody knows the reason?

---

### Post by Herman on 2008-09-12
I don't know the reason, but with ext2 or ext3 you should be able to run a file system check on your USB partition and that should fix it,
```
sudo e2fsck -C0 -p -f -v /dev/sdb1
```
If your USB partition is '/dev/sdb1', this should help, if not, please alter the command to suit your hard disk and partition arrangement, use 'sudo fdisk -lu' to check of open Gnome Partition Editor to take a look.
That command is a safe command to run as often as you like and will fix most problems keep your ext2 or ext3 file system in good shape.
If there is a major problem that this command can't cope with it will let you know.
[Running a filesystem check on an ext3  filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem") - from a Live CD - command line

---

### Post by zxtonl on 2008-09-12
Thanks Herman for the reply.

Yeah, that can fix the file system, and unfortunately can also make some files disappear or damaged.

I searched this forum and found no similar reports. The ugly is this problem is quite hidden. The installation process does not say anything abnormal, and most possibly the system will function well unless some vital files are damaged.

Have you guys installed ubuntu to external USB drives? Have you checked the file system afterwards? I am just curious.

---

### Post by Herman on 2008-09-12
> Thanks Herman for the reply.
Yeah, that can fix the file system, and unfortunately can also make some files disappear or damaged.No it won't, because the -p option tells e2fsck to only 'preen' the file system. Quite possibly that will fix it. If it encounters a problem that can't be fixed automatically, then it will let you know and you can decide what to do next.
From the manual:
>  -p     Automatically repair ("preen") the file system.  This option will case e2fsck to automatically fix any filesystem problems that can be safely fixed without human intervention.  If  e2fsck
              discovers  a  problem  which may require the system administrator to take additional corrective action, e2fsck will print a description of the problem and then exit with the value 4 logi&#8208;
              cally or&#8217;ed into the exit code.  (See the EXIT CODE section.)  This option is normally used by the system&#8217;s boot scripts.  It may not be specified at  the  same  time  as  the  -n  or  -y
              options.
Therefore the command is quite safe, and has already been used by myself and many other people and successfully fixed many file systems. If you have files missing after running that command then I would say they weren't there in the first place.
Only when you apply e2fsck with the -y option, such as in '[SIZE=-1][FONT=Bitstream Vera Sans Mono]sudo e2fsck -y -f -v /dev/sda2'[/FONT][/SIZE] will it move files to the /lost+found. 
Since we're talking about a new install here, you would only have operating system files, therefore any files being moved to /lost+found would likely be detrimental to the new operating system though.
> Have you guys installed ubuntu to external USB drives? Have you checked the file system afterwards? I am just curious.      Yes, many times, both to external USB hard drives and also to USB flash memory sticks. I have never had any problems.
I believe in running file system checks quite frequently.

Have you checked the health of your external hard drive? 
```
sudo badblocks -sv /dev/sdb1 >> badblocks.report

```(checks the partition for bad blocks and writes any information to a text file)

You may be able to check your external hard drive with smartmontools if your external hard disk supports 'smart'. 
```
sudo apt-get install smartmontools
``````
sudo smartctl -a /dev/sdb >> harddisk.report
```

---

### Post by zxtonl on 2008-09-12
Herman, thanks for the good suggestions. Frankly, I didn't notice the -p option you mentioned. I will try fsck with -p and other commands as you suggested and report what happen.

---

### Post by Herman on 2008-09-13
> **zxtonl said:**
> Herman, thanks for the good suggestions. Frankly, I didn't notice the -p option you mentioned. I will try fsck with -p and other commands as you suggested and report what happen.
  :shock: **No! STOP!**

**Not fsck** with -p, use **e2fsck** instead.
```
e2fsck -C0 -f -p -v /dev/sdb1
```fsck is a good program to use for running a non specific file system check from some other program that doesn't know what file system(s) you might want to check.
fsck runs e2fsck for you but it doesn't give you a chance to choose your own options.

When you know exactly what file system you want to check, it's better to use the proper file system checking program for that specific file system yourself directly, rather than running it via fsck. That way you can set your own special options necessary to fix whatever it is you need to fix.  :)

[-X  Please do not run fsck -P, that means,
>  -P     When  the  -A  flag  is  set,  check the root filesystem in parallel with the other filesystems.  This is not the safest thing in the world to do, since if the root filesystem is in doubt
              things like the e2fsck(8) executable might be corrupted!  This option is mainly provided for those sysadmins who don&#8217;t want to repartition the root filesystem  to  be  small  and  compact
              (which is really the right solution).

---

### Post by zxtonl on 2008-09-13
Thanks Herman.

What I mean by fsck is actually fsck.ext3, which I believe is the same as e2fsck? Anyway, for safety's sake, I will use e2fsck.

[NOTE: I tried cut&paste the content of file err2.log into the post, but when I submitted, I got the following error 
> The following errors occurred with your submission:

   1. You have included 10 images in your message. You are limited to using 8 images so please go back and correct the problem and then continue again.

      Images include use of smilies, the BB code [img] tag and HTML <img> tags. The use of these is all subject to them b&eing enabled by the administrator.
No clue to this error. So I have to attach it. Sorry for the inconvinience]

Following is what I did.

1. A clean install of Ubuntu 8.04.1
To save some time, I used the alternate desktop CD and installed a command-line system to /dev/sdb1.

2. Booted with 8.04.1 Live CD. The freshly installed partition is /dev/sdb1 again, but mounted on /media/disk-4.

3. Unmounted /dev/sdb1
```
sudo umount /dev/sdb1
```

4. Did a bad blocks check
> ubuntu@ubuntu:~$ sudo badblocks -sv /dev/sdb1 >badblocks.report
Checking blocks 0 to 9767487
Checking for bad blocks (read-only test):         8321536/        9767487
ubuntu@ubuntu:~$ cat badblocks.report 
ubuntu@ubuntu:~$ 
So file badblocks.report is empty, no bad blocks found.

5. Had a safe file system check with e2fsck
> ubuntu@ubuntu:~$ sudo e2fsck -C0 -f -p -v /dev/sdb1 >err1.log 2>&1
ubuntu@ubuntu:~$ cat err1.log
/dev/sdb1:                                                                    Inode 293959 has illegal block(s).  

/dev/sdb1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)
ubuntu@ubuntu:~$ 
Here comes the ugly UNEXPECTED INCONSISTENCY.

6. Ran e2fsck without -p option but with -y option
> ubuntu@ubuntu:~$ sudo e2fsck -vfy /dev/sdb1 >err2.log 2>&1
ubuntu@ubuntu:~$ cat err2.log
!!!!!!!!!! DELETED, see the attachment !!!!!!!!!!
ubuntu@ubuntu:~$
From the log, obvious some files are damaged.

What's your opinion?

---

### Post by Herman on 2008-09-13
Okay, thank you for trying the command I recommended. :)

It is now quite apparent that the problem isn't a simple one which can be easily fixed.
Likely there is something wrong with the Debian driver for your model of hard drive or the external hard drive controller, given that OpenSuSe and Gentoo don't have this problem and all Debian based distros do.
You probably should gather as much information as you can and report this as a bug.

The command '[FONT=Bitstream Vera Sans Mono]sudo lshw -C disk'[/FONT] can be used to give you a list of your hard disk drives with the basic information to begin with, (make, model, serial number and so on).
```
sudo lshw -C disk
```In the meantime, it seems as if you will either have to postpone using Ubuntu or any Debain based distros and keep using SuSe or Gentoo, or try some other hard disk.

Regards, Herman :)

---

### Post by zxtonl on 2008-09-15
Sensible guess and suggestion. Thanks for enlightening me.

---

### Post by Herman on 2008-09-15
:) Just so you know you're not the only one, I bought a nice new 250 GB 2.5" hard drive (laptop size), for a hard disk enclosure to replace a 40 GB hard disk after the hard disk enclosure had been dropped and the 40 GB hard drive was ruined.

Unfortunately, none of my computers have enough power in their USB ports to spin up the new 250 GB disk as an external USB hard drive. I even tried putting it in my laptop, but my laptop couldn't spin it up either.
It worked just fine as an IDE hard drive in one of my desktop PCs, but I already have enough hard drives for my desktop computers. SO I have this nice new 2.2" 250GB hard drive sitting around until I think of something to use it for. :)

---

### Post by pigphish on 2008-09-22
Off topic but worth noting. You should check the currency requirements of your 40gb. You'll notice the 40GB requires less amperage or wattage than your new drive. The good news is you can buy a larger capacity drive with as low a currency requirement or even lower (paerticularly with the new green stuff coming out).

For USB, my experience has been anything  with 800mA or less is good. I forget how this translates to watts so not to mispeak I bought a drive that had 500mA (0.5A) and 2.5W and worked perfectly in my usb only enclosure. You'll have to do some carefull shopping for a specific unit. I opted for WD3200BJKT because of the free fall sensor. No problems so far. 

For your external enclosure the new higher power consuming drive would work if it allowed you to give it extra power.

---

### Post by yottabit on 2009-05-16
p = vi

Where p = power in Watts
  v = volts
  i = current in amperes

USB is 5 volts, and mA is thousands of an ampere. Therefore, if you have a 500 mA requirement from your drive, that's 0.5 A,

p = 5 * 0.5 = 2.5 watts

Simple algebraic manipulation can also tell you how to watts to amperes, as well.

---

