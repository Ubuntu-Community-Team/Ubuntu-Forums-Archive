---
title: "No partition resize on install / live gparted crashes"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by genedsmith on 2010-10-10
Want to repartition/resize existing 1/2 full 60MB sda2 currently containing NTFS. The "Allocate drive space" does not seem to have a resize option (the 10.04 docs claim there was a resize option here). When I run 10.10 gparted in live mode gparted crashes for unknown reason before it even finishes scanning the disk.  Am I missing something here? (Never tried to resize an ntfs part. with Ubuntu.) The laptop I am installing this on currently has XP that crashes a lot for unknown reasons.

---

### Post by genedsmith on 2010-10-10
I meant a 60GB partition, not 60MB, just to be clear.

---

### Post by oldfred on 2010-10-11
Gparted & Ubuntu do not like opening NTFS partitions that need chkdsk (flag set). You do need to leave 20-30% free space or a NTFS partition has issues with writing and slows down or stops working.

I would first try running chkdsk on the NTFS partition & repeat until there are no errors as it does not always fix everything on one pass.

I usually repartition separately from the install and often use a separate download of gparted liveCD rather than the gparted with Ubuntu. you could try that also.

---

### Post by genedsmith on 2010-10-14
Thanks! Made a live cd of gparted (after chkdsk /f twice) fixed the problem. Was able to successfully resize the ntfs partition.

However, installed gparted and it also fails to run (crashes) when I try to run it from 10.10. So I suspect gparted in Ubuntu 10.10 has a bug.

---

### Post by Mark Phelps on 2010-10-15
Are you able to reboot into XP -- now that you've done the resize?

Also, you could download and burn a GParted LiveCD from distrowatch.com, boot from that, and see if that version of GParted crashes as well.

---

### Post by kansasnoob on 2010-10-15
> **genedsmith said:**
> Thanks! Made a live cd of gparted (after chkdsk /f twice) fixed the problem. Was able to successfully resize the ntfs partition.

However, installed gparted and it also fails to run (crashes) when I try to run it from 10.10. **[COLOR="Red"]So I suspect gparted in Ubuntu 10.10 has a bug.[/COLOR]**

I suspect so from reading the forums recently, but I've not been able to reproduce it on either of my machines.

I hope someone will take the time and effort to file a bug report :)

I certainly would if I could reproduce it.

If you already have a Launchpad account you could boot a Live CD and if it fails to recognize your partitions filing the bug should be as simple as pressing Alt + F2, then typing **ubuntu-bug parted** while still booted into the Live CD.

Then just wait while "parted info" is collected and next provide the same info you provided here.

---

### Post by srs5694 on 2010-10-15
> **kansasnoob said:**
> I hope someone will take the time and effort to file a bug report :)

FWIW, I've tried filing bug reports against libparted in the past. The Web page bug reporting system rejected my reports, claiming they were spam. I've given up on it.

In my experience, libparted is very useful for resizing and moving existing partitions on disks with partition tables that the program finds acceptable. It's also easy to use when creating new partitions -- or at least its GUI applications are. I don't trust it for anything complex, though, and it's useless at repairing damaged disks.

genedsmith, please post the output of "sudo fdisk -lu", typed in a Linux shell (Terminal). Please post the output between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility. This command will show us your partition table in a way that may enable detection of whatever problem is causing libparted to flake out on you.

---

### Post by janclod on 2010-10-19
i tried to launch with this command

sudo gparted /dev/<your device>

it semms work, but i haven't yet tried to do some basical operations as resize or format... from terminal don't appear errors about the errors above (glibmm-ERROR).

i hope this can bring some help

P.S.: sorry for my bad english

---

### Post by Mr_and_Mrs_D on 2010-10-29
My story - brand new unformatted 1 Tb hard drive - boot into live 10.10 (x64) - run gparted make 2 partitions (leave 128 gigs space for windows then 64 gigs partition for ubuntu and the rest "Storage" - all primary and only Storage formatted as ntfs). I save the log :```

GParted 0.6.2
 Libparted 2.3
    Create Primary Partition #1 (unformatted, 64.00 GiB) on /dev/sda  00:00:01    ( SUCCESS )             create empty partition  00:00:01    ( SUCCESS )             path: /dev/sda1
start: 268435456
end: 402653183
size: 134217728 (64.00 GiB)          ========================================
    Create Primary Partition #2 (ntfs, 739.51 GiB) on /dev/sda  00:00:02    ( SUCCESS )             create empty partition  00:00:00    ( SUCCESS )             path: /dev/sda2
start: 402653184
end: 1953523711
size: 1550870528 (739.51 GiB)          set partition type on /dev/sda2  00:00:00    ( SUCCESS )             new partition type: ntfs          create new ntfs file system  00:00:02    ( SUCCESS )             mkntfs -Q -v -L "FILES" /dev/sda2             Cluster size has been automatically set to 4096 bytes.
Creating NTFS volume structures.
Creating root directory (mft record 5)
Creating $MFT (mft record 0)
Creating $MFTMirr (mft record 1)
Creating $LogFile (mft record 2)
Creating $AttrDef (mft record 4)
Creating $Bitmap (mft record 6)
Creating $Boot (mft record 7)
Creating backup boot sector.
Creating $Volume (mft record 3)
Creating $BadClus (mft record 8)
Creating $Secure (mft record 9)
Creating $UpCase (mft record 0xa)
Creating $Extend (mft record 11)
Creating system file (mft record 0xc)
Creating system file (mft record 0xd)
Creating system file (mft record 0xe)
Creating system file (mft record 0xf)
Creating $Quota (mft record 24)
Creating $ObjId (mft record 25)
Creating $Reparse (mft record 26)
Syncing root directory index record.
Syncing $Bitmap.
Syncing $MFT.
Updating $MFTMirr.
Syncing device.
mkntfs completed successfully. Have a nice day.
            ========================================

```and Gparted crashes
I do not pay much attention (though didn't like it) - go ahead install (DVD) Win 7 ultimate 64 in first 128 gigs partition (unallocated space actually) - which (7 ultimate) creates an additional "System" partition of about 100 mb and suits itself to the rest of the 128 gigs. All fine - i reboot the live ubuntu 10.10 to delete my ultimate install and Gparted won't start (crashes on start with uknown error). No failing hdd or anything - must be a bug - feedback needed

Thanks

---

### Post by Mr_and_Mrs_D on 2010-10-29
Using sudo I get :[HTML]ubuntu@ubuntu:~$ sudo gparted
======================
libparted : 2.3
======================

glibmm-ERROR **: 
unhandled exception (type std::exception) in signal handler:
what: basic_string::_S_create

aborting...
ubuntu@ubuntu:~$ 
[/HTML]
Guess I should add a path to a drive ? What would that be ?

---

### Post by oldfred on 2010-10-29
May be separate issue.

Command line programs use sudo to have administrative privileges.

Graphic programs use gksudo to  have administrative privileges. Sometimes the wrong version of sudo can cause issues.

Also sudo often not required with the liveCD. I have only used the command line to launch graphic apps when they do not work, to see if there are error messages. 

Did you try from System, Administration, gparted?

---

### Post by Mr_and_Mrs_D on 2010-10-30
Hey - thanks for the reply - hadn't seen the second page hrmpff

>  Did you try from System, Administration, gparted?     That's how I tried initially - new to all this

  Apparently it is a well known bug :[https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/617885](https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/617885)

Seems fixed - how can I apply the fix ?

Thanks :)

---

### Post by madmaze on 2010-10-31
Im getting the same error after i resized some partitions.. before it worked great..
```

madmaze@madmaze-laptop:~$ sudo gparted /dev/sda
======================
libparted : 2.3
======================

glibmm-ERROR **: 
unhandled exception (type std::exception) in signal handler:
what: basic_string::_S_create

aborting...

madmaze@madmaze-laptop:~$ sudo gparted
======================
libparted : 2.3
======================

glibmm-ERROR **: 
unhandled exception (type std::exception) in signal handler:
what: basic_string::_S_create

aborting...

```

---

### Post by madmaze on 2010-10-31
Yea.. nevermind.. running the update manager fixed it =)


> **madmaze said:**
> Im getting the same error after i resized some partitions.. before it worked great..
```

madmaze@madmaze-laptop:~$ sudo gparted /dev/sda
======================
libparted : 2.3
======================

glibmm-ERROR **: 
unhandled exception (type std::exception) in signal handler:
what: basic_string::_S_create

aborting...

madmaze@madmaze-laptop:~$ sudo gparted
======================
libparted : 2.3
======================

glibmm-ERROR **: 
unhandled exception (type std::exception) in signal handler:
what: basic_string::_S_create

aborting...

```

---

### Post by ahoros on 2010-11-20
I have updated all the packages but on my machine (ubuntu 10.10) the problem remains:

:~$ sudo gparted
======================
libparted : 2.3
======================

glibmm-ERROR **: 
unhandled exception (type std::exception) in signal handler:
what: basic_string::_S_create

aborting...

---

### Post by ahoros on 2010-11-20
OK - found  new posts in this thread:

[https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/617885](https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/617885)


they recommended installing package:
 gparted_0.7.0-1_i386.deb 

from:

[http://launchpadlibrarian.net/58607123/gparted_0.7.0-1_i386.deb](http://launchpadlibrarian.net/58607123/gparted_0.7.0-1_i386.deb) 


This has worked for me.

---

