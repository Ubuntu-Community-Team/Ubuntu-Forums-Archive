---
title: "Weird issue in Beta 2 - 'phantom' Audio Disc on desktop"
date: 2010-04-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by bluelamp999 on 2010-04-09
After installing the latest tranche of updates on Beta 2, a 'phantom' Audio Disc has appeared on the desktop. See attached image for properties...

Nautilus thinks it is ```
cdda://sr0/
```

It can't be ejected or deleted, it just sits there bugging the hell out of me...

I'm running Beta 2 in VirtualBox 3.1.6 and there are no CDs of any description mounted and certainly not an audio disc.

Any ideas?

---

### Post by ranch hand on 2010-04-09
Big disk.  Have you rebooted to see if anything changes?  Make sure that all externals are turned off.

---

### Post by bluelamp999 on 2010-04-09
> **ranch hand said:**
> Big disk.  Have you rebooted to see if anything changes?  Make sure that all externals are turned off.

Rebooted host (9.01 btw) and, obviously, Beta 2 guest and it's still there. Mocking me...

It's odd that it's exactly a Gigabyte in size...

---

### Post by novafluxx on 2010-04-09
Just updated to Beta 2 - Same problem lol

I'm running 10.04 in VirtualBox so I know what hardware is there...

OK, so I removed the IDE controller and hence the optical drive from the VM - that Audio Disc is no longer there.


I re-enabled the IDE controller and set the ODD to primary master - Audio Disc is there again.

---

### Post by ranch hand on 2010-04-09
Maybe call Ghost Busters.  Beats me.

You might want to check your /etc/fstab.  Doesn't sound like that is the problem but if you have nautilus up you, at least, won't see the desktop.

---

### Post by bluelamp999 on 2010-04-09
> **novafluxx said:**
> Just updated to Beta 2 - Same problem lol

I'm running 10.04 in VirtualBox so I know what hardware is there...

OK, so I removed the IDE controller and hence the optical drive from the VM - that Audio Disc is no longer there.


I re-enabled the IDE controller and set the ODD to primary master - Audio Disc is there again.

At least it's not just me!:P

---

### Post by cariboo on 2010-04-09
I was playing with the Live CD this morning, and had a icon for a blank cd on the desktop, that was supposedly mount on /media/cdrom0, while the Live CD was mounted on /cdrom.

The icon showed up the second time I booted from the Live CD.

---

### Post by bluelamp999 on 2010-04-09
Just downloaded the latest batch of updates, rebooted and it's still there...

---

### Post by linuxman94 on 2010-04-09
Just filed a bug report for this:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/559723]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/559723")

---

### Post by novafluxx on 2010-04-10
I wonder if its with all IDE Optical drives or just a virtualbox problem

---

### Post by lonniehenry on 2010-04-10
Shows in an install of the daily from 4/6/10 on a desktop 386 machine. Can't be umounted or ejected.

---

### Post by null_pointer_us on 2010-04-10
Not affected here. EDIT: udev version 151-8

I'm running 10.04 amd64 beta 1 (w/ all updates as of now) in vbox 3.1.6 w/ guest additions installed from the cd (and then ejected many boots from now, so the drive is "empty").

Unlike other reports, this is with a Windows 7 x64 host.

Those who are affected, are you using 32-bit or 64-bit, and do you have the guest additions installed?

---

### Post by npeobe on 2010-04-10
Definitely seems to be tied to the VirtualBox guest additions kernel modules. Running VirtualBox 3.1.6-r59338 on a Windows 7 64-bit host. With the modules loaded I get the phantom Audio Disc. If i manually remove them from /lib/modules/`uname -r`/misc & reboot, no phantom Audio Disc anymore. I should also note that I'm running 10.04 x86, not amd64.

---

### Post by Elfy on 2010-04-10
Not as far as I am concerned - I have 2 machines here both running and completely updated. One is a clean install the other has updated from alpha3 (I think) and both show a phantom blank cd.

The clean install has never seen vbox and this one does not have it installed any longer.

---

### Post by novafluxx on 2010-04-10
> **null_pointer_us said:**
> Not affected here. EDIT: udev version 151-8

I'm running 10.04 amd64 beta 1 (w/ all updates as of now) in vbox 3.1.6 w/ guest additions installed from the cd (and then ejected many boots from now, so the drive is "empty").

Unlike other reports, this is with a Windows 7 x64 host.

Those who are affected, are you using 32-bit or 64-bit, and do you have the guest additions installed?

Host is Win7 x64 here as well. Latest VBox additions installed as well.

---

### Post by AClark on 2010-04-10
I have Lucid with all updates on two different machines an old IBM A30 Thinkpad and a desktop with an ASUS p4pe MB & ATI graphics card.

VirtualBox 3.1.6 installed on both.

The Blank CD-ROM Disc icon has come and gone a couple of times. If my memory serves it showed up shortly after Alfa1. 

It's there now and has been for about a week after having disappeared for a week or so before that.

This phantom icon has never been seen on the Thinkpad.

I'm having a great time testing this prerelease - lots of opportunity to learn new stuff!

EDIT: Just to be clear - Both machines running Lucid as host - Not in Vbox

---

### Post by mikeyrb on 2010-04-10
Definitely seeing it here too.  Not a virtualbox issue, and not nautilus' fault.  Udev is reporting the empty disc, as is the Disk Utility app.  This occurs on my IDE CD-RW drive, but not the IDE DVD drive.

---

### Post by mikeyrb on 2010-04-11
Created a new bug filed against udev.  [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/560469](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/560469)

At least for me, reverting udev and libudev0 to version 151-7 fixed the issue with a blank cd showing.

---

### Post by forcecore on 2010-04-12
[http://ubuntuforums.org/showthread.php?t=1452160](http://ubuntuforums.org/showthread.php?t=1452160)

i had this issue only with Virtualbox, no real hardware (3 pc-s tested)

---

### Post by Milind on 2010-04-13
I'm having the same problem on a fully updated Lucid Lynx machine though I don't have VirtualBox. Seems to be a new bug. :confused: See the screenshot.

[IMG]http://farm5.static.flickr.com/4049/4518245662_67e76437a2.jpg[/IMG]

---

### Post by null_pointer_us on 2010-04-13
Milind, what is your version of udev?

```
apt-cache policy udev
```

Someone said 151-8 had the audio cd issue and 151-7 was fine.

---

### Post by Milind on 2010-04-13
> **null_pointer_us said:**
> Milind, what is your version of udev?

```
apt-cache policy udev
```

Someone said 151-8 had the audio cd issue and 151-7 was fine.

milind@milind-desktop:~$ apt-cache policy udev
udev:
  Installed: 151-9
  Candidate: 151-9
  Version table:
 *** 151-9 0
        500 [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) lucid/main Packages
        100 /var/lib/dpkg/status

Hope that helps. :(

---

### Post by bluelamp999 on 2010-04-13
Yaay! It's gone!

After the latest round of updates (including kernel 2.6.32-20-generic) the phantom audio disk is no more (for now!:))...

---

### Post by Elfy on 2010-04-13
still got the blank cd on the desktop - all updated

---

### Post by Milind on 2010-04-15
> **forestpiskie said:**
> still got the blank cd on the desktop - all updated

Same here! Any solutions, anyone? :confused:

---

### Post by Milind on 2010-04-18
Today, the phantom disc has disappeared from my desktop. How? No idea.

---

### Post by Elfy on 2010-04-18
udev update

---

### Post by Krovas on 2010-04-18
Oh no, not again. I remember a problem like this in Feisty Fawn.

---

### Post by gregbzh on 2010-04-18
i have the same problem and I do have virtual box.  Any ideas?

---

### Post by mmmmna on 2010-04-18
Had the same issue, but the install was quickly trashed. On the NEXT install, I booted from the OTHER optical disk drive and all was fine after installation. Booting and installing from my SATA DVDRW resulted in the phantom disk drive, Booting and installing from the IDE DVDROM drive had no phantom disk drive problems. I wonder if this might be related to information hanging over from the installation environment being exported to the installed OS configuration.

---

