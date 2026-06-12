---
title: "CD ejection on Intrepid"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by wpshooter on 2008-10-31
On Intrepid that I just installed, when I attempt to eject a CD that I have placed in the CD drive (NOT the installation CD) (either by software command or by hardware button) the tray opens but immediately closes back of it's own accord.  

How do I stop this action ?

Thanks.

---

### Post by cameran on 2008-11-01
I have the EXACT same problem and am looking for a solution as well.

---

### Post by Sslaxx on 2008-11-01
It's bitten me, too. I'm curious as to how many people this bug has bitten...

---

### Post by glenngds2007 on 2008-11-01
It has bitten me too.  I do not know whether the problem is with the kernel or hal or just what. So far I scratched a movie DVD that I just bought and is now unplayable and I destroyed (broke) a Ubuntu 8.10 installation CD.  I swear if this is not fixed by this time tomorrow I will send the bill for all the damaged CDs and DVDs to Ubuntu.  This crap called 8.10 should have never been released with a bug in it so serious that a person can destroy CD/DVD disks and drives just trying to eject a CD/DVD.

---

### Post by OrangeCrate on 2008-11-01
Is is a known bug. The fix will come through normal updates.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/283316](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/283316)

---

### Post by lukjad on 2008-11-01
> **glenngds2007 said:**
> It has bitten me too.  I do not know whether the problem is with the kernel or hal or just what. So far I scratched a movie DVD that I just bought and is now unplayable and I destroyed (broke) a Ubuntu 8.10 installation CD.  I swear if this is not fixed by this time tomorrow I will send the bill for all the damaged CDs and DVDs to Ubuntu.  This crap called 8.10 should have never been released with a bug in it so serious that a person can destroy CD/DVD disks and drives just trying to eject a CD/DVD.
You must not have read the part of the license agreement that says:

> Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by applicable law.
;)

For what it's worth, I think that this is too bad and should be a priority, but I don't think that they put this out with such a serious bug on purpose. If they did, I think that some torches and pitchforks should be grabbed right quick. :D

---

### Post by wpshooter on 2008-11-01
Does anyone have an inkling as to when this might be fixed or do we just have to keep testing to see if it will correctly eject the CD ever time a new batch of updates are released ?

Thanks.

---

### Post by dwasifar on 2008-11-01
I remember this was a problem back in Dapper, or possibly Hoary.

---

### Post by ciscosurfer on 2008-11-01
Known bug.  Been a problem for a while now.  Here are some links that discuss workarounds:

[http://ubuntuforums.org/showthread.php?t=942553&page=3](http://ubuntuforums.org/showthread.php?t=942553&page=3)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/283316/comments/34](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/283316/comments/34)

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/280931/comments/37](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/280931/comments/37)

---

### Post by dwasifar on 2008-11-01
There is a workaround for this.  I got the following from the bug report at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/283316:](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/283316:)


[COLOR="Navy"]...a one-line fix to /etc/udev/rules.d/60-persistent-storage.rules seemed to solve the problem without even rebooting the machine, it was mentioned in another thread...look for the following in said file:

# skip unpartitioned removable media devices from drivers which do not send "change" events
ENV{DEVTYPE}=="disk", KERNEL!="sd*|sr*", ATTR{removable}=="1", GOTO="persistent_storage_end"

just beneath the second line, add the following (make sure to back up your original):

ENV{DEVTYPE}=="disk", KERNEL=="sd*|sr*", ATTR{removable}=="1", GOTO="persistent_storage_end"

(the subtle difference is in the "KERNEL" portion)[/COLOR]

So far this has solved the problem for me.

---

### Post by glenngds2007 on 2008-11-02
Did not have any affect on my ejection problem.:mad:

---

### Post by davidshere on 2008-11-03
I have this problem too.  It makes Ubuntu look like it's retarded.  Not a good thing for someone looking at Ubuntu for the first time.

---

### Post by wpshooter on 2008-11-03
I have tried this on 2 different computers and I get this same CD ejection problem on both computers.  So this does not look like it is isolated to just limited hardware.

---

### Post by lukjad on 2008-11-03
Just to know, are the two computers similar in age?

---

### Post by glenngds2007 on 2008-11-03
> **dwasifar said:**
> There is a workaround for this.  I got the following from the bug report at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/283316:](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/283316:)


[COLOR="Navy"]...a one-line fix to /etc/udev/rules.d/60-persistent-storage.rules seemed to solve the problem without even rebooting the machine, it was mentioned in another thread...look for the following in said file:

# skip unpartitioned removable media devices from drivers which do not send "change" events
ENV{DEVTYPE}=="disk", KERNEL!="sd*|sr*", ATTR{removable}=="1", GOTO="persistent_storage_end"

just beneath the second line, add the following (make sure to back up your original):

ENV{DEVTYPE}=="disk", KERNEL=="sd*|sr*", ATTR{removable}=="1", GOTO="persistent_storage_end"

(the subtle difference is in the "KERNEL" portion)[/COLOR]

So far this has solved the problem for me.

Did not repeat did not work for me.

---

### Post by wpshooter on 2008-11-03
> **lukjad007 said:**
> Just to know, are the two computers similar in age?

Both are ASUS motherboards.  1st is P4G8X, 2nd is P4C800-E deluxe.

Both CD drives are CD-RWs but I am not sure about brand.  Both are good qualitiy / well known brand name drives. 

Not exactly a scientific sampling, but this test convinces me that this is not an isolated problem.

Reading the bug report seems to indicate to me that they have not come up with a definitive answer for this problem yet.

I sure would not want to be demonstrating this O/S to one of my friends and have this happen.  I really can NOT understand how an O/S could be released with a problem like this.  I still think the testing processes on this O/S are just a hodge-podge.  I think the developers of this O/S need to come up with a better quality control system than the one they are currently using.

Thanks.

---

### Post by everthonvaladao on 2008-11-03
Hey, I applied the fix from bugs.lauchpad.net and it works!!!

===> here's a quick FIX: [[Ubuntu Intrepid BUGFIX: CD-ROM tray closes automatically after eject]("http://mobilevs.blogspot.com/2008/11/ubuntu-intrepid-bugfix-cd-rom-tray.html")]

---

### Post by lukjad on 2008-11-03
Cool! Now I'll think of upgrading to Ibex!

---

### Post by glenngds2007 on 2008-11-05
I just downloaded a new kernel for Ubuntu 8.10 Ibex and my ejection problem was fixed with the download.

---

### Post by davidshere on 2008-11-05
I also have the kernel update, and the problem remains.

---

### Post by rfurman24 on 2008-11-06
My problem is still present on my second drive with all suggested fixes.

---

### Post by wpshooter on 2008-11-06
Did you apply all proposed Intrepid updates via Update Manager ?  That fixed mine.

Thanks.

---

### Post by rfurman24 on 2008-11-06
Yes, I did. Still broken on one of two drives.

---

### Post by Sslaxx on 2008-11-10
> **wpshooter said:**
> Did you apply all proposed Intrepid updates via Update Manager ?  That fixed mine.

Thanks.

All updated, still doing the eject problem.

---

### Post by wpshooter on 2008-11-10
> **Sslaxx said:**
> All updated, still doing the eject problem.

Are you checking the box for **PROPOSED** updates in software sources ?

---

### Post by Sslaxx on 2008-11-10
> **wpshooter said:**
> Are you checking the box for **PROPOSED** updates in software sources ?
I wasn't aware of this option. But why?

---

### Post by rfurman24 on 2008-11-10
Yes. I did. I am on udev 124-9. Apparently no one cares that some people are still having problems. The bug page is going nowhere and I know I am not the only one having the problem.

---

### Post by wpshooter on 2008-11-10
> **rfurman24 said:**
> Yes. I did. I am on udev 124-9. Apparently no one cares that some people are still having problems. The bug page is going nowhere and I know I am not the only one having the problem.

Have you tried switching the drives to see if the problem follows a certain drive ?

May not be part of the problem (probably in O/S) but how do you have the drive(s) connected to the M/B and how are they jumpered ?

---

### Post by rfurman24 on 2008-11-10
They work fine in Hardy.

---

### Post by kansasnoob on 2008-11-11
> **rfurman24 said:**
> They work fine in Hardy.

Well, I'm Erick Brunzell @ launchpad, so let's get through this!

I'm quite tired at the moment but if you would please post the output of:

```
cat /etc/udev/rules.d/60-persistent-storage.rules
```

I'll check back tomorrow and we'll try to work thru this.

---

### Post by rfurman24 on 2008-11-11
Thanks Eric. I don't care how long this takes to fix. I just feel better knowing someone is trying to help. I have two ide drives. The slave works fine. It gets mounted as /media/cdrom. The master only works on dvds or plain audio discs with no other media on the disc i.e. pictures/video. It gets mounted as /media/"name of disc". I am using udev 124-9.

# do not edit this file, it will be overwritten on update

# persistent storage links: /dev/disk/{by-id,by-uuid,by-label,by-path}
# scheme based on "Linux persistent device names", 2004, Hannes Reinecke <hare@suse.de>

# forward scsi device event to corresponding block device
ACTION=="change", SUBSYSTEM=="scsi", ENV{DEVTYPE}=="scsi_device", TEST=="block", ATTR{block/*/uevent}="change"

ACTION!="add|change", GOTO="persistent_storage_end"
SUBSYSTEM!="block", GOTO="persistent_storage_end"

# skip rules for inappropriate block devices
KERNEL=="ram*|loop*|fd*|nbd*|gnbd*|dm-*|md*", GOTO="persistent_storage_end"

# never access non-cdrom removable ide devices, the drivers are causing event loops on open()
KERNEL=="hd*[!0-9]", ATTR{removable}=="1", DRIVERS=="ide-cs|ide-floppy", GOTO="persistent_storage_end"
KERNEL=="hd*[0-9]", ATTRS{removable}=="1", GOTO="persistent_storage_end"

# ignore partitions that span the entire disk
TEST=="whole_disk", GOTO="persistent_storage_end"

# /sys/class/block will export this
ENV{DEVTYPE}!="?*", ATTR{range}=="?*", ENV{DEVTYPE}="disk"
ENV{DEVTYPE}!="?*", ATTR{start}=="?*", ENV{DEVTYPE}="partition"

# for partitions import parent information
ENV{DEVTYPE}=="partition", IMPORT{parent}="ID_*"

# by-id (hardware serial number)
KERNEL=="hd*[!0-9]", IMPORT{program}="ata_id --export $tempnode"
KERNEL=="hd*[!0-9]", ENV{ID_SERIAL}=="?*", SYMLINK+="disk/by-id/ata-$env{ID_MODEL}_$env{ID_SERIAL}"
KERNEL=="hd*[0-9]", ENV{ID_SERIAL}=="?*", SYMLINK+="disk/by-id/ata-$env{ID_MODEL}_$env{ID_SERIAL}-part%n"

KERNEL=="sd*[!0-9]|sr*", ATTRS{ieee1394_id}=="?*", ENV{ID_SERIAL}="$attr{ieee1394_id}", ENV{ID_BUS}="ieee1394"
KERNEL=="sd*[!0-9]|sr*", ENV{ID_SERIAL}!="?*", SUBSYSTEMS=="usb", IMPORT{program}="usb_id --export %p"
KERNEL=="sd*[!0-9]|sr*", ENV{ID_SERIAL}!="?*", IMPORT{program}="scsi_id --export --whitelisted -d $tempnode", ENV{ID_BUS}="scsi"
KERNEL=="cciss?c[0-9]d[0-9]", ENV{ID_SERIAL}!="?*", IMPORT{program}="scsi_id --export --whitelisted -d $tempnode", ENV{ID_BUS}="cciss"
KERNEL=="sd*[!0-9]|sr*|cciss?c[0-9]d[0-9]", ENV{ID_SERIAL}=="?*", SYMLINK+="disk/by-id/$env{ID_BUS}-$env{ID_SERIAL}"
KERNEL=="sd*[0-9]|cciss*p[0-9]", ENV{ID_SERIAL}=="?*", SYMLINK+="disk/by-id/$env{ID_BUS}-$env{ID_SERIAL}-part%n"

# libata compat (links like hd*)
KERNEL=="sd*[!0-9]|sr*", ENV{ID_VENDOR}=="ATA", PROGRAM="ata_id $tempnode", RESULT=="?*", ENV{ID_ATA_COMPAT}="$result", SYMLINK+="disk/by-id/ata-$env{ID_ATA_COMPAT}"
KERNEL=="sd*[0-9]", ENV{ID_ATA_COMPAT}=="?*", SYMLINK+="disk/by-id/ata-$env{ID_ATA_COMPAT}-part%n"

KERNEL=="mmcblk[0-9]", SUBSYSTEMS=="mmc", ATTRS{name}=="?*", ATTRS{serial}=="?*", ENV{ID_NAME}="$attr{name}", ENV{ID_SERIAL}="$attr{serial}", SYMLINK+="disk/by-id/mmc-$env{ID_NAME}_$env{ID_SERIAL}"
KERNEL=="mmcblk[0-9]p[0-9]", ENV{ID_NAME}=="?*", ENV{ID_SERIAL}=="?*", SYMLINK+="disk/by-id/mmc-$env{ID_NAME}_$env{ID_SERIAL}-part%n"

# by-path (shortest physical path)
ENV{DEVTYPE}=="disk", IMPORT{program}="path_id %p"
ENV{DEVTYPE}=="disk", ENV{ID_PATH}=="?*", SYMLINK+="disk/by-path/$env{ID_PATH}"
ENV{DEVTYPE}=="partition", ENV{ID_PATH}=="?*", SYMLINK+="disk/by-path/$env{ID_PATH}-part%n"

# skip unpartitioned removable media devices from drivers which do not send "change" events
ENV{DEVTYPE}=="disk", KERNEL!="sd*|sr*", ATTR{removable}=="1", GOTO="persistent_storage_end"
# skip optical drives without media
ENV{DEVTYPE}=="disk", KERNEL=="sr*", ENV{ID_CDROM_MEDIA_TRACK_COUNT}!="?*", GOTO="persistent_storage_end"

# import filesystem metadata
IMPORT{program}="vol_id --export $tempnode"

# by-label/by-uuid links (filesystem metadata)
ENV{ID_FS_USAGE}=="filesystem|other|crypto", ENV{ID_FS_UUID_ENC}=="?*", SYMLINK+="disk/by-uuid/$env{ID_FS_UUID_ENC}"
ENV{ID_FS_USAGE}=="filesystem|other", ENV{ID_FS_LABEL_ENC}=="?*", SYMLINK+="disk/by-label/$env{ID_FS_LABEL_ENC}"

LABEL="persistent_storage_end"

---

### Post by lukjad on 2008-11-11
rfurman24, don't forget the CODE tags! :D

---

### Post by davidshere on 2008-11-11
I can post mine too if needed.  I'm not now because I figure you want to troubleshoot one at a time...

---

### Post by kansasnoob on 2008-11-13
> **kansasnoob said:**
> Well, I'm Erick Brunzell @ launchpad, so let's get through this!

I'm quite tired at the moment but if you would please post the output of:

```
cat /etc/udev/rules.d/60-persistent-storage.rules
```

I'll check back tomorrow and we'll try to work thru this.

Sorry it's taken so long to respond. I got busy with other "life" issues and just now had time to fiddle some more. 

First off I want to clear up any confusion about who I am. When I said "I'm Erick Brunzell @ launchpad" I didn't mean to imply that I work in connection with the devs! I've just noticed your posts at Launchpad and wanted you to know my Launchpad ID.

I'm just an Ubuntu end-user that likes to play with things! So I did that this morning. I first checked your "/etc/udev/rules.d/60-persistent-storage.rules" against mine to be absolutely sure there wasn't just some kind of glitch, none found! Yours was identical to mine.

I then copied and printed both the newest 8.10 and an 8.04.1 "/etc/udev/rules.d/60-persistent-storage.rules" and made some comparisons. I should also note that I was never able to duplicate your problem with the new udev, but I certainly believe you.

Anyway I replaced the newest 8.10 "/etc/udev/rules.d/60-persistent-storage.rules" with a copy of 8.04.1's completely and I've rebooted, tried almost every possible scenario to be sure all internal and external drives function properly and they do! (I should add that the one scenario I did NOT try was the possibility of having two internal hard drives!

I just didn't want to spend the time to fiddle with internal cables anymore than I already had trying different CD/DVD drive scenarios, but I did try mounting and unmounting various hard drive partitions and also mounting, unmounting, ejecting various internal and external CD/DVD drives.

So, IMHO, it would be perfectly safe to replace the text of your "/etc/udev/rules.d/60-persistent-storage.rules" with the text of 8.04.1's. Plus it's fully reversible as long as you create a backup of the original, so if it doesn't solve your problem you'd be none the worse for wear!

So, you know of course, to accomplish this run:

```
sudo gedit /etc/udev/rules.d/60-persistent-storage.rules
```

I then right clicked an open area in the text file - then clicked "select all" > copy, and pasted the original into a word document. You can name it anything you'd like, then just save it where you can find it. Then I went back to open file in Gedit and again "right clicked" > select all > cut!

I then went to my previously saved 8.04.1 file and simply using copy-n-paste pasted the entire thing into the now "blank" open file in Gedit. I then proofread just to be sure I didn't miss any parts during the copy-n-paste procedure, and then clicked Save and then File > Quit. Clear as mud:confused:

I'll include a copy of the 8.04.1 "/etc/udev/rules.d/60-persistent-storage.rules" if you should choose to try this. It's up to you! I see no "ill effects" from doing so, but I guess it's a "buyer beware" kind of thing. Here's the 8.04.1 "/etc/udev/rules.d/60-persistent-storage.rules" text:

> # do not edit this file, it will be overwritten on update

# persistent storage links: /dev/disk/{by-id,by-uuid,by-label,by-path}
# scheme based on "Linux persistent device names", 2004, Hannes Reinecke <hare@suse.de>

ACTION!="add|change", GOTO="persistent_storage_end"
SUBSYSTEM!="block", GOTO="persistent_storage_end"

# skip rules for inappropriate block devices
KERNEL=="ram*|loop*|fd*|nbd*|gnbd*|dm-*|md*", GOTO="persistent_storage_end"

# never access non-cdrom removable ide devices, the drivers are causing event loops on open()
KERNEL=="hd*[!0-9]", ATTR{removable}=="1", DRIVERS=="ide-cs|ide-floppy", GOTO="persistent_storage_end"
KERNEL=="hd*[0-9]", ATTRS{removable}=="1", GOTO="persistent_storage_end"

# ignore partitions that span the entire disk
ATTR{whole_disk}=="*", GOTO="persistent_storage_end"

# /sys/class/block will export this
ENV{DEVTYPE}!="?*", ATTR{range}=="?*", ENV{DEVTYPE}="disk"
ENV{DEVTYPE}!="?*", ATTR{start}=="?*", ENV{DEVTYPE}="partition"

# for partitions import parent information
ENV{DEVTYPE}=="partition", IMPORT{parent}="ID_*"

# by-id (hardware serial number)
KERNEL=="hd*[!0-9]", IMPORT{program}="ata_id --export $tempnode"
KERNEL=="hd*[!0-9]", ENV{ID_SERIAL}=="?*", SYMLINK+="disk/by-id/ata-$env{ID_MODEL}_$env{ID_SERIAL}"
KERNEL=="hd*[0-9]", ENV{ID_SERIAL}=="?*", SYMLINK+="disk/by-id/ata-$env{ID_MODEL}_$env{ID_SERIAL}-part%n"

KERNEL=="sd*[!0-9]|sr*", ATTRS{ieee1394_id}=="?*", ENV{ID_SERIAL}="$attr{ieee1394_id}", ENV{ID_BUS}="ieee1394"
KERNEL=="sd*[!0-9]|sr*", ENV{ID_SERIAL}!="?*", SUBSYSTEMS=="usb", IMPORT{program}="usb_id --export %p"
KERNEL=="sd*[!0-9]|sr*", ENV{ID_SERIAL}!="?*", IMPORT{program}="scsi_id --export --whitelisted --fallback-to-sysfs -s %p -d $tempnode"
KERNEL=="cciss?c[0-9]d[0-9]", ENV{ID_SERIAL}!="?*", IMPORT{program}="scsi_id --export --whitelisted --ignore-sysfs -s %p -d $tempnode", ENV{ID_BUS}="cciss"
KERNEL=="sd*[!0-9]|sr*|cciss?c[0-9]d[0-9]", ENV{ID_SERIAL}=="?*", SYMLINK+="disk/by-id/$env{ID_BUS}-$env{ID_SERIAL}"
KERNEL=="sd*[0-9]|cciss*p[0-9]", ENV{ID_SERIAL}=="?*", SYMLINK+="disk/by-id/$env{ID_BUS}-$env{ID_SERIAL}-part%n"

# libata compat (links like hd*)
KERNEL=="sd*[!0-9]|sr*", ENV{ID_VENDOR}=="ATA", PROGRAM="ata_id $tempnode", RESULT=="?*", ENV{ID_ATA_COMPAT}="$result", SYMLINK+="disk/by-id/ata-$env{ID_ATA_COMPAT}"
KERNEL=="sd*[0-9]", ENV{ID_ATA_COMPAT}=="?*", SYMLINK+="disk/by-id/ata-$env{ID_ATA_COMPAT}-part%n"

KERNEL=="mmcblk[0-9]", SUBSYSTEMS=="mmc", ATTRS{name}=="?*", ATTRS{serial}=="?*", ENV{ID_NAME}="$attr{name}", ENV{ID_SERIAL}="$attr{serial}", SYMLINK+="disk/by-id/mmc-$env{ID_NAME}_$env{ID_SERIAL}"
KERNEL=="mmcblk[0-9]p[0-9]", ENV{ID_NAME}=="?*", ENV{ID_SERIAL}=="?*", SYMLINK+="disk/by-id/mmc-$env{ID_NAME}_$env{ID_SERIAL}-part%n"

# by-path (shortest physical path)
ENV{DEVTYPE}=="disk", IMPORT{program}="path_id %p"
ENV{DEVTYPE}=="disk", ENV{ID_PATH}=="?*", SYMLINK+="disk/by-path/$env{ID_PATH}"
ENV{DEVTYPE}=="partition", ENV{ID_PATH}=="?*", SYMLINK+="disk/by-path/$env{ID_PATH}-part%n"

KERNEL=="sr*", GOTO="persistent_storage_end"
KERNEL=="hd*[!0-9]", ATTR{removable}=="1", GOTO="persistent_storage_end"

# by-label/by-uuid (filesystem properties)
IMPORT{program}="vol_id --export $tempnode"
ENV{ID_FS_USAGE}=="filesystem|other|crypto", ENV{ID_FS_UUID_ENC}=="?*", SYMLINK+="disk/by-uuid/$env{ID_FS_UUID_ENC}"
ENV{ID_FS_USAGE}=="filesystem|other", ENV{ID_FS_LABEL_ENC}=="?*", SYMLINK+="disk/by-label/$env{ID_FS_LABEL_ENC}"

LABEL="persistent_storage_end"

---

### Post by rfurman24 on 2008-11-13
That did nothing. Thanks for helping. If I can not fix this I am going to switch back to Mint and never come back to Ubuntu. I will still be part of the community. I have about had it with all the Ubuntu bugs.

---

### Post by rfurman24 on 2008-11-13
> **davidshere said:**
> I can post mine too if needed.  I'm not now because I figure you want to troubleshoot one at a time...

I take it you are still having the problem. I guess we are the only two because no one else seems to care.

---

### Post by kansasnoob on 2008-11-13
> **rfurman24 said:**
> That did nothing. Thanks for helping. If I can not fix this I am going to switch back to Mint and never come back to Ubuntu. I will still be part of the community. I have about had it with all the Ubuntu bugs.

Well, I currently have 8.10, Mint 6 RC1, and a tiny 8.10 on this drive for testing:

[ATTACH]92523[/ATTACH]

Mint 6 is based on Ubuntu 8.10 and used the same udev update.

One additional thing that may or may not help, assuming you left the  8.04.1 "/etc/udev/rules.d/60-persistent-storage.rules" text in place is simply running:

```
sudo apt-get install --reinstall udev
```

Which also updates "initramfs" as seen here:

> lance@lance-desktop:~$ sudo apt-get install --reinstall udev
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/264kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 111838 files and directories currently installed.)
Preparing to replace udev 124-9 (using .../archives/udev_124-9_i386.deb) ...
Unpacking replacement udev ...
Processing triggers for man-db ...
Setting up udev (124-9) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.27-7-generic


And I've checked and it does NOT revert the text in "/etc/udev/rules.d/60-persistent-storage.rules"!

Most importantly I want to stress one more time that i'm just an "end-user" like you! I'm in no way connected with the devs!

I only identified myself@launchpad to let you know I'd been following your posts there as well as here at the forums!

---

### Post by rfurman24 on 2008-11-13
I do realize everything you said. I appreciate your attempt to help. I have even started a new bug report and no response. I would put money on it that Mint has this concern fixed in a few weeks when it is released. All the problems I had with Gutsy were not in the Mint version. It seems to me that they spend a little more time making sure the system is actually ready. I also realize this would be much more difficult with Mint using a strong base such as Ubuntu. Either way I would never choose Windows over linux. I appreciate everyone in the linux community.

---

### Post by davidshere on 2008-11-19
This problem appears to have gone away for me.

---

### Post by fr34k on 2008-12-06
Copy-Paste and execute the following two commands. It instantly fixed my problem , without any Internet updates or Reboots. The first command is just to backup the rules files before editing.

```

sudo cp /etc/udev/rules.d/60-persistent-storage.rules /etc/udev/rules.d/60-persistent-storage.rules_bkp

```

```

sudo sed -i 's/ENV{DEVTYPE}=="disk", KERNEL!=/ENV{DEVTYPE}=="disk", KERNEL==/g' /etc/udev/rules.d/60-persistent-storage.rules

```

From : [http://mobilevs.blogspot.com/2008/11/ubuntu-intrepid-bugfix-cd-rom-tray.html](http://mobilevs.blogspot.com/2008/11/ubuntu-intrepid-bugfix-cd-rom-tray.html)

---

### Post by rfurman24 on 2008-12-18
I had already tried that but tried again anyway. Still broke. I do not think my problem is related to udev.

---

### Post by wpshooter on 2008-12-26
> **rfurman24 said:**
> I had already tried that but tried again anyway. Still broke. I do not think my problem is related to udev.

Rfurman24:

Have you ever gotten your problems with CD ejection solved ?

I am now having a similar problem.

I switched some of the equipment/hardware in one of my computers and since I switched the CD-RW drive from a model of a Plextor drive to a Sony model CRX230ED, I can not get the ejection problem to go away/fixed.

This is on a fresh Intrepid installation on which I have applied ALL of the available updates including the Proposed updates and also the Backport updates, still CD ejects and then immediately closes right back up on its own.

Is this a problem that has developed and the fixes that have been published is only going to work for certain brands/models of CD drives ?

When I was using the Plextor drive in this machine, I had the problem after the initial installation of Intrepid BUT after I applied the updates, the problem immediately went away.

Do you or anyone else know if this problem is still being worked on ?

Thanks.

---

### Post by wpshooter on 2008-12-26
> **fr34k said:**
> Copy-Paste and execute the following two commands. It instantly fixed my problem , without any Internet updates or Reboots. The first command is just to backup the rules files before editing.

```

sudo cp /etc/udev/rules.d/60-persistent-storage.rules /etc/udev/rules.d/60-persistent-storage.rules_bkp

```

```

sudo sed -i 's/ENV{DEVTYPE}=="disk", KERNEL!=/ENV{DEVTYPE}=="disk", KERNEL==/g' /etc/udev/rules.d/60-persistent-storage.rules

```

From : [http://mobilevs.blogspot.com/2008/11/ubuntu-intrepid-bugfix-cd-rom-tray.html](http://mobilevs.blogspot.com/2008/11/ubuntu-intrepid-bugfix-cd-rom-tray.html)

Fr34k:

Applying ALL of the Intrepid updates (including proposed updates) did not fix my CD ejection/closing problem BUT your 2 lines of terminal command codes DID fix it.

You would think that if you know about this ERROR in coding, that the developers of Ubuntu would know about this and correct this coding error.

If I have misinterpreted what is going on here, someone please correct me.

But in any case the above commands finally fixed my problem.

Thanks.

---

### Post by rfurman24 on 2008-12-30
My problem is not fixed and I have tried everything I have read on the net.

---

