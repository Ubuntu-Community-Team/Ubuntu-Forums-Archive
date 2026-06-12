---
title: "How does 13.04 handle RAID?"
date: 2013-04-29
forum: Installation &amp; Upgrades
---

### Post by ladasky on 2013-04-29
Hi folks,

I'm asking a lot of questions today... I'm contemplating an upgrade to 13.04.  I have the ISO for my system (AMD 64-bit).  I could not seem to find an "alternate install" file for 13.04.  My current system has mirrored hard disks in RAID1, administered using **mdadm**.

Has RAID management finally been incorporated into the standard installation of Ubuntu?  That would be great, I have been hoping for that.  But I have read some forum posts which indicate that people are having trouble with RAID on 13.04.  I have a full backup of my /home directory made, but I went through a huge hassle once with a degraded RAID when I did an Ubuntu upgrade (from 10.10 to 11.10, as I recall). 

Any advice?  Thanks!

---

### Post by darkod on 2013-04-29
I haven't looked at 13.04 yet myself, but I believe mdadm is still not included on the live cd. But you can easily boot into live mode first, add the package and assemble the array, and only then start the install from the icon on the desktop/unity. Do not restart as any packages added in live mode are not there after a reboot (without persistancy).

You can easily see whether the package is included by trying to list the mdadm details for example:
```
sudo mdadm -D /dev/md0
```

If that says mdadm is not installed, it's not included on the live cd by default.

The commands to add it in live mode and assemble all arrays would be like:
```
sudo apt-get install mdadm
sudo mdadm --assemble --scan
```

Once you have that, the installer should see it as present and you can use it any way you want during the installation, instead of trying to add it later.

---

### Post by ladasky on 2013-04-30
Thanks for your reply, darkod.

I have confirmed that the **mdadm** package is not included on the 13.04 live ISO.  _And I BEG for this to change!_

Whenever I have used an Ubuntu live CD, I have always noticed how slow it is.  I am not exactly sure why it is so slow.  This time I made a bootable USB thumb drive.  I don't know whether the fact that this was 13.04, or the fact that I used a USB device was the reason -- but everything was UNBELIEVABLY slow.  I often wait for nearly a minute for an Ubuntu Forums web page to load in Firefox, and the window grays out for most of that time.  

The following **mdadm** installation took nearly an hour to run, with warnings as you can see:

```
ubuntu@ubuntu:~$ sudo apt-get install mdadm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  postfix
Suggested packages:
  procmail postfix-mysql postfix-pgsql postfix-ldap postfix-pcre sasl2-bin
  dovecot-common postfix-cdb postfix-doc
Recommended packages:
  default-mta mail-transport-agent
The following NEW packages will be installed:
  mdadm postfix
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/1,872 kB of archives.
After this operation, 4,735 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Selecting previously unselected package mdadm.
(Reading database ... 161462 files and directories currently installed.)
Unpacking mdadm (from .../mdadm_3.2.5-5ubuntu2_amd64.deb) ...
Selecting previously unselected package postfix.
Unpacking postfix (from .../postfix_2.10.0-3_amd64.deb) ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 32 changed doc-base files, 6 added doc-base files...
Processing triggers for ufw ...
WARN: uid is 0 but '/' is owned by 1000
Setting up mdadm (3.2.5-5ubuntu2) ...
Generating mdadm.conf... done.
 Removing any system startup links for /etc/init.d/mdadm-raid ...
update-initramfs: deferring update (trigger activated)
 * Starting MD monitoring service mdadm --monitor                        [ OK ] 
Setting up postfix (2.10.0-3) ...
Adding group `postfix' (GID 125) ...
Done.
Adding system user `postfix' (UID 116) ...
Adding new user `postfix' (UID 116) with group `postfix' ...
Not creating home directory `/var/spool/postfix'.
Creating /etc/postfix/dynamicmaps.cf
Adding tcp map entry to /etc/postfix/dynamicmaps.cf
Adding sqlite map entry to /etc/postfix/dynamicmaps.cf
Adding group `postdrop' (GID 126) ...
Done.
setting myhostname: ubuntu
setting alias maps
setting alias database
mailname is not a fully qualified domain name.  Not changing /etc/mailname.
setting destinations: /etc/mailname, ubuntu, localhost.localdomain, localhost
setting relayhost: 
setting mynetworks: 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
setting mailbox_size_limit: 0
setting recipient_delimiter: +
setting inet_interfaces: all
/etc/aliases does not exist, creating it.
WARNING: /etc/aliases exists, but does not have a root alias.

Postfix is now set up with a default configuration.  If you need to make 
changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
 * Stopping Postfix Mail Transport Agent postfix                         [ OK ] 
 * Starting Postfix Mail Transport Agent postfix                         [ OK ] 
Processing triggers for ureadahead ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-19-generic
cryptsetup: WARNING: failed to detect canonical device of overlayfs
cryptsetup: WARNING: could not determine root device from /etc/fstab
Processing triggers for ufw ...
WARN: uid is 0 but '/' is owned by 1000
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
W: Operation was interrupted before it could finish
ubuntu@ubuntu:~$ sudo mdadm --assemble --scan
mdadm: /dev/md/1 has been started with 2 drives.
mdadm: /dev/md/2 has been started with 2 drives.
mdadm: /dev/md/3 has been started with 2 drives.
ubuntu@ubuntu:~$ 
```

This was only a 1.9 MB download, which expands into 4.7 MB of disk space, so adding it to the live ISO would be trivial.  Ubuntu has now decided to exceed the CD-ROM size anyway, so what's a little extra?  

I don't understand why **mdadm** depends on **postfix** either (an email server?).  Half the installation time was spent on **postfix**, and several of the warnings seem to be connected to it.

I will now try installing 13.04 to an empty partition on my RAID (saved just for this purpose) and report back.  I hope I get the kind of performance I have come to expect from Ubuntu, this slow installation is scaring me!

---

### Post by darkod on 2013-04-30
I fail to see why mdadm would require postfix too. Maybe because of the feature of mdadm to be able to send you a warning email if disks fail, so it needs some mail delivery agent to do that, but installing full postfix for that seems way too much.

---

### Post by ladasky on 2013-04-30
Followup:

It looked like 13.04 was going to install (SLOWLY) to my empty partition, but it failed.  I got a **grub-install** error message:

```
Unable to install Grub in /dev/sda.
Executing 'grub-install /dev/sda' failed.
This is a fatal error.
```

After retrying a few times, I selected the "proceed without bootloader" option.  The installer reported success (albeit without GRUB) and exited.  I then _[downloaded]("https://help.ubuntu.com/community/Boot-Repair")_ **boot-repair** and prepared a boot report, which I've placed on Pastebin _[here]("http://paste.ubuntu.com/5619787/")_.

I may attempt the "standard repair," but I am not encouraged that it will work.  I am no expert in reading the boot reports, but I see two things that I do not like.  First, the system cannot detect the operating system that I have supposedly just installed on */dev/md/2* (lines 83-88).  Second, I noticed that the system installer made me do something annoying, creating what I think is best described as a "logical" partition, */dev/md2p1*, inside the "physical" RAID partition */dev/md/2*.  This anomaly shows up on lines 148-152.

I am pretty sure that my 12.04 installation is intact, and I may just return to using that for a while.  I don't want to break it until I am sure I can proceed.  My goal is to have 12.04 installed alongside 13.04, until I am sure that 13.04 is working for me.

---

### Post by darkod on 2013-04-30
Hmm, very strange. There is no need to make you create p1 on the md device, unless you are trying to use it wrongly. I have seen cases when md device has p1 on it, but I don't know when and why it happens.

Maybe you tried to create partition table on it? In that case it could create p1. The md devices are used directly, and only for a single mount point. Hence if you want multiple mount points, you need multiple md devices with their size already planned in advance, because you can't repartition and resize them.

---

### Post by ladasky on 2013-04-30
I burned a DVD from the 13.04 ISO, and booted it.  It is MUCH faster.

I am proceeding with the installation after installing **mdadm** and assembling my RAID.  Aside from being faster, so far it looks like it proceeded the same way.

I did not mention this last time, but the installer believes that there are no operating systems currently installed on the machine.  I know this isn't true, I have 12.04 installed on */dev/md1*.  Also, I mount */dev/md3* as */home*.  So I chose "something else" on the menu after the device scan.  I will specify the partitions and mount points manually.  

From the "installation type" window, I can at least_[ get a snapshot]("http://www.flickr.com/photos/15579975@N00/8697436662")_ of how the system sees the RAID partitions.  (The list continues, but as you can see from the bottom line, it just enumerates physical partitions, from */dev/sda* onward.)  As you can see, I have that baffling */dev/md2p1*.  I tried deleting it in **gparted**, but it comes right back in the installer.  _Edit_: actually, no it doesn't come back, even though it is displayed.  If I try to proceed with an installation after deleting */dev/md2p1*, I immediately get an "Error: failed to create a file system in */dev/md2p1*".  I have to have my partition specified and formatted before the installation will proceed.

The system says it wants to install GRUB on */dev/sda*.  (Later, you will see that it might also want to install to */dev/sdb*.)

I'm about to press "Install Now", but I'm going to send this post before I do, in case the system crashes.  I will return and edit this post when this installation attempt completes.

_Edit #2_: Well, it happened a lot faster than yesterday, thanks to the DVD, but... the installation failed.  It is almost certainly the same as last time, but Ubiquity is working through a long pause right now, and I can't be sure until it completes.

Most of the installation proceeded smoothly after selecting my partitions and mount points.  The status line of the Ubiquity window read: "Running 'grub-install /dev/sda /dev/sdb'..." (which is exactly what I expect for my RAID1 configuration).  And then up popped a dialog box stating: "Unable to install GRUB in /dev/sda. Executing 'grub-install /dev/sda' failed. This is a fatal error."  I clicked OK, and then chose to continue without a bootloader.  I was warned that I will need to install it manually.  After clicking OK, I'm seeing my first long pause.  Fortunately, the rest of my system isn't lagging.  

If Ubiquity ever releases the installation process, I could use some advice as to how to proceed.  As I mentioned before, I would like to use boot-repair, but I'm scared of breaking my link to my working 12.04 system.  Thanks!

_Edit #3_: After twenty minutes, I went over to the menu bar and forced Ubquity to quit.  I then got a "We're sorry; the installer crashed" dialog box.  Till next time...

---

### Post by darkod on 2013-05-01
You made me download 13.04 and make a small simulation in VBox. :)

I first booted into live mode and made a raid1 md0 device from two 8GB virtual disks in the VM. That's to simulate existing array. I also formatted md0 with ext4.
After that I rebooted like starting the installation from new, booted into live mode again to install the mdadm package and assemble the md0 array. By the way, it asked to install postfix too, like it did for you, and I let it install but in the configuration screen I just selected No Configuration since postfix doesn't interest me.

Then with the md0 assembled I started the installation by clicking the icon in the Unity toolbar, and selected Something Else.

The md0 device was shown as expected, like /dev/md0 only, not like /dev/md0p1 or similar. I don't know why it shows p1 for you, you might have created or manipulated the arrays differently.
As far as I have understood mdadm, the devices are used and formatted directly, like /dev/md0, and they have no type of partition table or partitions on them.

I am attaching a screenshot from the VM.

---

### Post by michellestrade on 2013-05-01
Hi,

I'm also having some issues with RAID in 13.04. In my case, it is a Lucid upgrade that did not go smoothly. I eventually managed to fix it and have apt-get update all the Raring packages correctly but when it came time to reboot, my GRUB2 settings were incorrect. After booting to the live DVD and running boot-repair, things do not crash in the same way as before but I get a completely blank screen after the default GRUB boot menu option. Using the Recovery option from the menu gives a bit more information: first a warning about degraded mode and then a read error for md1 (the raid swap). In the live DVD, mdadm reports md0 as clean and I could never get the details of md1 (disks busy).

The diagnostics from boot-repair are here: [http://paste.ubuntu.com/5624031/](http://paste.ubuntu.com/5624031/). Does anyone have an idea of what values are incorrect ? I am trying to boot from /dev/md0 so the problems of /dev/md1 ought to be of no consequence, right ?

---

### Post by ladasky on 2013-05-14
I have gotten nowhere.  My attempt to add 13.04 to my RAID1 system (in an unused partition, while preserving my 12.04 root partition) continues to fail at the grub-install.  But after doing some more reading, I have an additional question.

My system was configured using the old Master Boot Record (MBR) method of partitioning, used with PC BIOS, that I have known and used for twenty years.  However, many of the references that I have found on installing Ubuntu on a RAID without using the alternative install disks (which no longer exist for 13.04) make reference to the LVM.  Now from what I understand from _[darkod's post, above]("http://ubuntuforums.org/showthread.php?t=2140218&p=12628145#post12628145")_, I don't think that he is using LVM.  But darkod, are you in fact using LVM?  Does the integration of RAID into the Ubuntu installation process *expect* the RAID to be built with the Logical Volume Manager (LVM)? 

Do I have to start over, reformat my hard drives, and make LVM partitions rather than MBR partitions?  It will be a hassle, but I will do it, IF it guarantees me the configuration and future upgrade path that I want.  

For years, my dream system has been one that allows me to install two versions of Ubuntu side by side, choose which one to boot, and share data between them.  That way, if I'm having problems with a new version of Ubuntu, I can still fall back on my older one.  I only need three partitions to get this done: one for each OS's root directory, and one which can be mounted as /home by either OS.  Since the number of partitions I need is less than four, it never occurred to me to think about LVM.  This would probably work fine for me, were it not also for the desire for RAID.

I make regular backups of my /home partition to an external drive, so if I have to reformat, I won't lose any personal data.  I am not sure whether/how I can also back up the rest of my 12.04 root partition in a way that won't require me to download all of my applications from repositories all over again... :(

Any further advice would be appreciated.  Thanks!

---

### Post by ladasky on 2013-06-13
One frustrating month later, I am submitting what I expect to be the closing article in this thread.

After several unsuccessful attempts to get 13.04 installed on my *mdadm*- and MBR-based RAID1 (how DID I manage to do it with 11.10, and with 12.04?), I took the hint from the 13.04 installer, which gently suggests using LVM.  I disassembled my RAID (which _[was surprisingly difficult]("http://ubuntuforums.org/showthread.php?t=2153731")_), and built an LVM configuration instead.  I am now operating 13.04 on my system. 

However, I am currently only using one of my two internal hard drives.  I am operating without the automatic backup that the RAID1 provided me.  That backup saved me days of hassle once, when one of my two drives failed.  It is my understanding that LVM offers a mirroring feature.  I have the second hard drive waiting.  I am hoping to set up a fully-bootable mirror of my hard drive (that means mirroring every partition).  This probably isn't the thread in which to pursue that discussion.  So I guess I'll end things here, unless someone wants to chime in.  ;)

---

