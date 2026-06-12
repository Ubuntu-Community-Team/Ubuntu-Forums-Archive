---
title: "cannot mount cdrom during new 7.10 install"
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by adlerschrei on 2007-11-03
I am trying a new install of ubuntu 7.10 server. After picking the keyboard configuration the cdrom cannot be mounted and the installation aborts.

The computer is an ancient HP Celeron [Model HP Pavilion 6642F] that I am planning to use as a file server. The CDRW drive is a Sony.

I have tried ubuntu 7.10 server, desktop, kubuntu, xubuntu and 7.04 server. I have also tried to install with Fedora [since I used to run an older Fedora on this machine before I had to replace the harddisk] but get the same error messages:

[ 0.000000] no DMI bios year, ACPI=force is required to enable ACPI
My understanding is that this is for power features only and the installation kept going. I did not think this is related. Not sure now.

A second set of error messages is [like the first set, with all install CDs]:
[101.588703] ata2.00: exception Emask 0x0 SAct 0x0 SeErr 0x0 action 0x2 frozen
[101.588802] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0cdb 0x5a data 128 in
These two lines are repeated 3 times with different numbers in the [] until it continues with something like:
Starting .... daemon: syslog...
[Sorry, I m copying from the screen. So the last line is incomplete]

When opening a terminal window from the install menu, I can see /dev/scd0.
Mounting with $ sudo mount /dev/scd0 /media/cdrom returns " .... failed: No such file or directory"
$ cat /etc/mtab | grep cd returns nothing, just a new prompt.
I also changed the settings for the CCDRW drive in the BIOS to the absolute basics, played with master/slave etc. - no difference.
The CDRW works fine when I run it through XP from the same harddisk.

Any help is highly appreciated.

[ps: since I did not receive any further messages on my previous post at [http://ubuntuforums.org/showthread.php?p=3685337#post3685337](http://ubuntuforums.org/showthread.php?p=3685337#post3685337) , I am posting this again here]

---

### Post by ofb on 2007-11-03
Since you're having no luck with 7.10, 7.04, and Fedora, I'd be suspecting the drive is failing.

I think what I'd do next is load the Knoppix LiveCD to see if that works okay, and maybe Puppy Linux, which loads into RAM, freeing the drive up to test burning. If I still got errors I'd feel pretty sure the CDRW has gone south.

---

### Post by adlerschrei on 2007-11-04
Thanks for your response. 

I have downloaded Knoppix 5.1.1 and Puppy 3.01. Under Knoppix the drive seems to work fine. 

Under Puppy it works but the Puppy Drive Mounter first issues an Error: " Failure! In the case of a removable media, the most common reason is the media is not currently inserted. If so, please remedy". When I ignore this I can open folders and read files on the drive - despite the error.

FYI, the drive is a Yamaha CRW 8824E [not a Sony drive as previously stated].

---

### Post by adlerschrei on 2007-11-04
I just tried an old Hitachi CDR and it seems to work. I am going to buy a new DVDRW tomorrow and will then proceed with the installation.

---

### Post by ofb on 2007-11-04
FWIW, there are a number of threads with 7.10 having trouble with IDE devices and/or not being able to burn, but reading okay.

I certainly haven't got to the bottom of this one yet, but thought I should mention that before you spend money on a new drive.

If the Hitachi works, I'd be tempted to just proceed with it for now. There may be less trouble in general once the developers can make head&tail out of the current slew of bug reports and put some fixes in the pipeline.

---

### Post by adlerschrei on 2007-11-05
Thanks for letting me know. I didn't make it to the store today anyway. I will probably just do that tomorrow, install with the (borrowed, slow and old but free) CDR. I could then afterwards try to hook my Yamaha CDRW back up. At least the system will be running by then. I hate to spend money on that old computer.

---

