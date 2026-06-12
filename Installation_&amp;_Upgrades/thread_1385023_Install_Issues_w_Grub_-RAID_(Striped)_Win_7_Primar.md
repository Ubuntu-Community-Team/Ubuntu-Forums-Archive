---
title: "Install Issues w/ Grub -RAID (Striped) Win 7 Primary, Ubuntu on Separate Non-Raid HDD"
date: 2010-01-19
forum: Installation &amp; Upgrades
---

### Post by unique2 on 2010-01-19
I am not sure if this has been covered because I have read countless threads about dual-booting win 7 and ubuntu 9.10 and honestly it seems like everyone is having issues with it for different reasons, and a lot of times I am finding there aren't definite solutions that work for everyone.

I have win 7 installed on (2) RAID (Striped) drives, so it essentially 1 HDD.  I read lots of threads that said people were having trouble with fakeraid, and dmraid, when trying to partition a RAID'd Win 7 partition to install ubuntu on.  I didn't really want to go into all of that ... being unsure personally if my system was going to be stable with all of the issues everyone was having.  So I have decided to wait for that issue to get worked out to a more definite end all solution.

My solution was to buy an extra HDD and install it into my current system and then use that entire drive as my ubuntu drive, and then my two other drives can stay unmodified using the already set up RAID (striped) in win 7.

So I followed the directions that most of the posts about separate drives said. That was to change the BIOS to boot to the new drive (empty non-raid one) first.  Then install ubuntu on that drive, and then install grub to that drive as well.  So I put in the Live CD and did just that.  Now after install, you can stay on the live cd and play around a bit.  So I decided to open gparted to view how linux was viewing my drives after a "successful" install.  Here's what it sees:

**/dev/mapper/pdc_jececidh (297.97 GiB)** <---- this is my "mapped" RAID'd windows drive? weird...
**/dev/sda/ (149.05 GiB)** <--- one win raid drive
**/dev/sdb/ (149.05 GiB)** <--- other win raid drive
**/dev/sdc/ (465.76 GiB)** <--- Ubuntu

So I decided to test out my grub to see if I could boot up to both OS's.  

*Note: my new non-raid'd drive is still the first boot device.*

When Grub opens it says:

"*Grub stage1.5 is loading*" then it gives me a couple of choices (Please note, I make a comment about updating to Grub2 below)

[I]----------------------------------------------------
Ubuntu 9.10, kernel 2.6.31-14-generic
Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
Ubuntu 9.10, memtest86+
Other Operating Systems:
Windows 7 (loader)
----------------------------------------------------[/I]

If I choose nothing it attempts to boot to ubuntu.  The little ubuntu icon comes up and then it fails to boot with this message:

[I]"Gave up waiting for root device.  Common problems:
-Boot Args (cat /proc/cmdline)
- check root delay = (did the system wait long enough?)
- check root = (did the system wait for the right device?)
-Missing Modules (cat /proc/modules; ls /dev)
ALERT! /dev/mapper/pdc_cjhddhbbd1 does not exist. Dropping to a shell!

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built in shell (ash)

(initramfs) _"[/I]

I don't really know many useful commands I can type here to help me. Any ideas?

If I try to boot to windows 7 it fails with the error:

*Error 21: Selected disk does not exist*

So, finally, I after all of that, I am happy to say, I am still able to boot to windows 7 if I switch the boot order in my BIOS.  However, i am not able to get to my Linux installation from any of the options above.  So something went seriously wrong.  It is possible that the install went wrong, which I can understand and won't mind re-installing.  

I have seen quite a few posts about upgrading to grub2 from commandline, but I am unable to boot into my linux installation at all, and when I select 'c' from the grub menu, to get the command-line I don't get a normal command lines where i can do sudo commands.  So here I am...

What next? :-/

I found this thread which seems close to my issue, but not exactly:
[http://ubuntuforums.org/showthread.php?t=1380615&highlight=about+separate+hdd+windows](http://ubuntuforums.org/showthread.php?t=1380615&highlight=about+separate+hdd+windows)

I tried pretty much everything in that thread.

**Update:**
Downloaded and attempted to install from the Alternate CD.  When I got to the "Detect Disks" step, it only recogized my 319 GB hard drive as pdc_jececidh**1**

No idea why it won't recognize my other 500 GB hard drive as the only thing that is on that drive is supposedly an Ubuntu Install.

---

### Post by unique2 on 2010-01-19
Well looks live I am not crazy. There's a bug tracker for this:

[https://bugs.launchpad.net/ubuntu/+bug/488461](https://bugs.launchpad.net/ubuntu/+bug/488461)

I guess I'll just wait... once again.

---

