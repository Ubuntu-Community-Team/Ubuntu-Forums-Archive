---
title: "Trouble Installing with Software RAID0 as root Partition"
date: 2007-01-22
forum: Installation &amp; Upgrades
---

### Post by unperson on 2007-01-22
Hi, I'm trying to install Ubuntu Edgy Eft (6.10) and setup a software RAID during the installation.  I downloaded and burned the Edgy Alternate CD for AMD64 arch, thinking based on [this page]("http://users.piuha.net/martti/comp/ubuntu/raid.html") that that would let me do what I wanted.

The machine has two identical SATA disks in it.  Using the installer, I put 4 partitions on each, setup as follows:

/dev/sda1 swap
/dev/sda2 ext2 for /boot
/dev/sda3 for raid
/dev/sda4 for raid

/dev/sdb1 swap
/dev/sdb2 unused
/dev/sdb3 for raid
/dev/sdb4 for raid

I then used the "configure software RAID" option to combine /dev/sda3 and /dev/sdb3 into a RAID0 for / (the root partition), and I combined /dev/sda4 and /dev/sdb4 into a RAID0 for /home.

The install proceeded as normal until the point where it asks you to reboot.  Upon rebooting, grub comes up normally, it says "loading kernel", it brings up the Ubuntu title/logo, and then it spits me out into BusyBox at a prompt marked "(initramfs)" with the message "/bin/sh can't access tty; job control turned off."  

I ran across [these](https://launchpad.net/ubuntu/+source/initramfs-tools/+bug/79204) [two](https://launchpad.net/ubuntu/+source/evms/+bug/11838) bugs in looking for an answer, but I couldn't determine if they were related to my problem.

Anyone have any idea what's going on here and how to fix it?  This is the first time I've had serious problems installing Ubuntu, so I'm hoping I can sort them out without too much pain.


Thanks,
Nick

---

### Post by unperson on 2007-01-22
A bit more information that could be useful:  Once it's kicked me out to BusyBox during boot, the output of mount shows the only disk partition mounted (not counting non-disks like /dev, /proc. and /sys) is /dev/md1 which is mounted as /root.  Going to /root I see what looks to be the contents of the partition that I configured for /home.  I don't know what should be in /root at this point, so I don't know whether this is normal.

What's odd is that I would have thought the problem was the system not being able to read the RAID from which / is to be mounted, but here it appears to already have a RAID drive (/dev/md1) mounted.  What's more, I can use the mount command to mount /dev/md0 which appears to contain the contents intended for /, as I would expect.  Since I seem to be able to mount the RAID0 drives, I don't understand what the problem is.  But then, I don't understand the error about not being able access a tty.

Oh, though I doubt it's relivent, all the RAID partitions are formated with XFS.

---

### Post by unperson on 2007-01-22
A bit more looking around shows many problems like this with using a RAID for / in Edgy and few if any solutions.  I haven't had much luck getting help with this problem, and I don't think I know enough to figure it out alone.  I can see 3 possible courses of action now:
[LIST=1][*]Try some scheme where I put in a 3rd, non-RAID disk with an existing Ubuntu install on it and copy it over.  Not sure how/if that would work.[*]Try using the fakeRAID on my motherboard instead.  This isn't my preffered option, but there seems to be a lot more written about doing this in Ubuntu.[*]Try installing another distribution with better support for RAIDs.  I've been told that Fedora and related distributions have very good support for creating/using RAIDs on install.  All things being equal, I'd rather stick with Ubuntu, but it doesn't seem like I'm making any headway on this issue.
[/LIST]

---

### Post by IntuitiveNipple on 2007-01-22
Before you go to so much trouble, have you considered what if any performance benefits you'll actually see?

I've had extensive experience of RAID - hardware, 'fake' and software - and the configuration you seem to be aiming for - striping file-systems over 2 disks increases the risk of data-loss. If one of those disks develops errors, all your file-systems can become unusable immediately.

The performance increase from striping is negligable too.

---

### Post by unperson on 2007-01-24
Well, after a lot of help from IntuitiveNipple and others on the #ubuntu IRC channel I got the problem straightened out.  It turns out that for the installer setup grub with the wrong location for the / device!  It was looking for root at /dev/md1 when it was actually located at /dev/md0 (and I set this up with the installer, so it ought to have known.  For anyone with similar problems, here's how I fixed it:

To test, I booted from a live CD, and mounted the device containing /boot.  I then changed directories to the where I mounted that device and edited the grub/menu.lst file (well, actually I made a backup copy before editing it).
```
gedit grub/menu.lst &
```
I don't recall if I had to add sudo at the beginning because of file permissions.  At the end of the menu.lst file are the sections for the various entries that come up in the grub menu.  The first entry looked something like this:
```

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/md1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
savedefault
boot

```

 I copied and pasted it to make a second, identical entry.  I then edited it to fix the location of the root device, gave it a distinctive name, and removed the line setting it as the default.  So the new entry I added to the list looked something like this: 
```

title           Ubuntu, kernel 2.6.17-10-generic (modified root)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/md0 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
boot

```
I then saved the new menu.lst and rebooted the system.  It spits out the CD before reboot, and you have to make sure to remove it at that point because you want the system to boot from the hard drive.  When the system rebooted, I hit escape when grub came on the screen to bring up the menu.  Then I chose the new entry I created.  The system started up normally, confirming this was the problem.

In order to make the fix perminent, I again backed up /boot/grub/menu.lst, then I edited it once again (this time I DID need to use sudo).  This time I went to the default kernel options section and changed
```
kopt_2_6=root=/dev/md1 ro
```
to
```
kopt_2_6=root=/dev/md0 ro
```
There was also an entry that read
```
kopt=root=UUID=...
```
but this one seemed to be correct (the UUID listed matched the one shown by 'ls /dev/disk/by-uuid -alh'), so I left it alone.  I then saved the file and ran 
```
sudo update-grub
```
which used those kopt lines to update all the entries in the grub menu with the correct information (and removed my now superfluous entry).

I also looked at /etc/fstab.  There again the UUIDs looked fine, but there were comments showing the location of drives, and all of the ones for the RAID drives were one number too high.  I fixed those for good measure, though AFAIK they don't do anything, since they're commented out.

After doing all that I rebooted the system and now it boots just fine!

It seems like this is a bug in the installer, so I guess I need to see if it's already been reported and, if not, report it.

---

