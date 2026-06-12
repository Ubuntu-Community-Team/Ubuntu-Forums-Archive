---
title: "Install Boot Menu missing"
date: 2014-08-25
forum: Installation &amp; Upgrades
---

### Post by newone2 on 2014-08-25
Not sure this is the place to post this but here we go:

I need to repair the boot files on an older machine with Debian 5.0.8 (Lenny) and I have the live CD that goes with that. But the machine boots using the CD but never gives me the "Install Menu Options", it goes instead into the "Boot Menu" (where I do not have the option to install/repair the system).How can I go into into the "Install Menu"?

Thanks

---

### Post by Bashing-om on 2014-08-25
newone2; Hello ;

It has been ages and ages since I booted 'debian' , but ->
What results:
As soon as the bios screen clears, depress and hold the right shift key
language screen ? -> escape key to accept the default ->
Disk options screen ?
Keep in mind, to (re-)install the boot code, all you need is a terminal interface from the liveCD.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by newone2 on 2014-08-25
Just a dumb question: how do i re-install the boot code from terminal?

Thank you so much!!!

---

### Post by Bashing-om on 2014-08-25
newone2; Well ..

No longer a simple little thing,, got to consider is this a UEFI system (newer) ?,
What hard drive is the boot code to be installed to ?
Where on the hard drive is the boot code to be installed ?

To look at the hard drive(s), and how (it is) partitioned:
```

sudo fdisk -lu

```

Is this disk the legacy MBR partitioning ?
Is there NO separate /boot partition ?
What partition is linux installed to ?

Then DO you want the boot code installed to the 0th sector of the hard drive ? ( standard with MBR partitioning)

IF and only IF this is a MBR partitioned disk, AND linux is installed onto the 1st hard drive's 1st partition, AND the boot code is to be installed to the MBR, AND the liveCD is the same version as the installed operating system -> then:
```

sudo mount /dev/sda1 /mnt
sudo grub-install --boot-directory=/mnt /dev/sda
sudo umount /mnt

```
Will do the job.
ELSE: Make adjustments to suite your application.

Reboot into the installed operating system and:
```

sudo update-grub

``` to put things current, and pick up any other installed operating systems.


Reboot once more and see what is.

[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT]

---

### Post by newone2 on 2014-08-26
Bashing-om... thank you so much!!!

Can anyone take a look at:

[http://paste.ubuntu.com/8144188/](http://paste.ubuntu.com/8144188/)

and modify the code to repair the boot files from terminal?

---

### Post by Bashing-om on 2014-08-26
newone2; Morning !

Whoah ! I do not think we want to do this !
1) Separate /boot partiton.
2) xfs file system, - as versatile as grub is, I do not know that grub will deal with 'xfs'.
3) The 'lenny' release, is that not End_Of_Life and out of support ( 404 errors) ?
4) grub legacy. who can remember how it operates ? -? /grub/menu.lst  ! It has not been used in years for the mainstream releases.
5) boot the .iso from the hard drive, setting a permanent mount point in /etc/fstab ? what is this all about ?

------------------------
My thought at this time is to mount the installed file system and copy off your files, and install a current release !

[INDENT][INDENT]there is no point in beating
[INDENT][INDENT][INDENT][INDENT]on a dead horse
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by newone2 on 2014-08-26
Thank you so much again.

Looks like I might start with a newer version and try to manually re-install the software on that work station... not an easy task as I do not have distribution disks for such software.

---

### Post by Bashing-om on 2014-08-26
newone2; Yeah !

A work station, you might consider either a 'server' install or a minimal "build your own" install:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems) <-install directions
[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)

Else a standard desk top install for older hardware:
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

Download the .iso ( check integrity), burn to CD (DVD for desktop), install !

[INDENT][INDENT][INDENT]ain't no big deal
[/INDENT][/INDENT][/INDENT]

---

### Post by yancek on 2014-08-26
I don't know what happened but you have no menu.st or boot files in either sda1 (boot partition?) or sda3 your system partition which would easily explain why you can't boot.   Since your system is outdated, you would be better off using a newer system.

> grub legacy. who can remember how it operates ? -? /grub/menu.lst  ! It has not been used in years for the mainstream releases.

That seems like a bit of an exaggeration as it is only in the last 1-2 years that non-Ubuntu systems like Fedora, Opensuse, etc. have started using Grub2.  The developers at Red Hat and PCLinuxOS would be surprised to hear that as they still use Legacy.  I think it's interesting that the oldest currently existing Linux distribution (Slackware) still uses Lilo.  Just about the only system which does.

---

