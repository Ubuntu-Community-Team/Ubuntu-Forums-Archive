---
title: "Installing Ubuntu 13.10 (can't fin partitions &amp; low graphic mode error)"
date: 2014-04-06
forum: Installation &amp; Upgrades
---

### Post by hellgren on 2014-04-06
Hello,

I've been trying to install Ubuntu on my latest laptop a few times but always given up because of errors, I'll see if there's anyone who can help me out this time before I give up again. (heh)

I have an Acer Aspire V, about 1 year old. Pre-installed with Windows 8, uninstalled it and it now runs Windows 7. (in legacy boot)
I'm trying to install Ubuntu 13.10 from a USB stick, it boots up to the installation screen OK, but when you try to get the installation going it will not recognize any of the partitions on the hard drive but considers everything as 'free space' and only gives me the option to format the entire hard drive.

On the other hand, trying to skip the installation and run it live from the USB stick results in it throwing me a 'the system is running in low graphic mode', telling me to reconfigure and stuff, but regardless of what you press nothing happens (as in nothings solves the problem, and boot is unsuccessful).

I'm guessing I'm facing a 2-sided problem here, any tips would be very much appreciated!

---

### Post by 23dornot23d on 2014-04-06
Sounds as if the partition tables are in a mess to me 

As the only times I have seen the full disk as available - were when either a sector was outside the disk ... or partitions crossed one another.

Some information here for dos users ......... [http://gparted.org/h2-fix-msdos-pt.php](http://gparted.org/h2-fix-msdos-pt.php)

but this is not something I can help you with as windows installs and problems caused from it may better be sorted in a windows forum

before attempting to run Linux .... the partitions really would be better if they were sorted first.

But saying that ......... you can run Linux and there are tools in Linux for sorting the disk out ..........

__________________________________________________

The thing to do - is to first get some background information on how you have partitioned the drive ........

Then if you can run Ubuntu ..... from USB ....... then do some checks 

Download and run bootinfoscriptinfo ......... from using the live USB/CD and then follow the instructions on this page

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Reason being it will give lots of information in one fell swoop as to what is going on with the disk.

Best I can do for now ......... until we can find some more information on why the full disk is being shown as free ........ when it obviously is not.
( but there will be a error somewhere causing that to happen ) as I say bootinfoscript gives lots of valuable information back even though linux may
not be on that drive .......... 

If you know of any faults being reported with your disk - please cut and paste them back here too - as they may help in solving the problem.

---

### Post by grahammechanical on 2014-04-06
Can you provide a Windows 7 screenshot of your disk partitions as Windows 7 sees them? If they are listed as Dynamic drives/partition then the Linux installer/partitioner cannot read them because the disks are in a Microsoft Proprietary format.

As you have installed Windows 7 in legacy boot mode then I guess that the 4 primary partition limit is now in effect. How many primary partitions is Windows 7 using. 

Ubuntu needs to be able to create at least one Primary partition and turn it into an Extended partition into which it can create two Logical partitions, one to install into and one for swap. Or, for there to be one Primary partition that has been turned into an Extended partition, then we can use the something Else option to direct Ubuntu to install into the Extended partition and create its two partitions as Logical partitions.

Regards.

---

