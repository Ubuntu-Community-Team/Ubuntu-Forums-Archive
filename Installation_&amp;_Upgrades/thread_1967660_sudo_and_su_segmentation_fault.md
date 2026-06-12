---
title: "sudo and su segmentation fault"
date: 2012-04-28
forum: Installation &amp; Upgrades
---

### Post by bakinsoda on 2012-04-28
Hi,

I just did "do-release-upgrade" on my Natty(?) server to get to Precise.  The installation didn't exit with 0 errors as there were some packages that did not exist anymore.

Now, when I execute sudo or su, I get the "Segmentation fault" error.  I can't restart or do anything.  I did a hard reset on the server but I still have the same error.

What makes things complicated is that I don't have a video card (Acer Aspire NAS), so I can't do much at startup.

Anyone know what's wrong?

UPDATE: Also, I have ssh set up that it doesn't accept root, so I don't know how I can get root access to do some fixing!

---

### Post by dino99 on 2012-04-28
*****
I just did "do-release-upgrade" on my Natty(?) server to get to Precise.
******

you cant do that : this only upgrade to Oneiric (previous -> next release), only LTS (Lucid) can be dist-upgraded to Precise (LTS)

so as you have something still broken, maybe a fresh Precise install will be the right decision.

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by bakinsoda on 2012-04-28
Actually I think I was upgrading from lucid actually.

---

### Post by bakinsoda on 2012-04-28
Also, I think issue is with su as it also gives segmentation fault error. I suppose that sudo issue stems from su.

---

### Post by bakinsoda on 2012-04-29
FIXED.  Because of my constraints (no access to video output + no root access because of no root password set and ssh restriction), I had to remove the hard drive and mount it on my laptop with an IDE/SATA to USB adapter (you can also just mount by booting into a Live Disk via usb/cd if you did not have my constraints).  I then mounted the drive to get access to my broken system's files.  I first tried to edit /etc/shadow to have [enable no password]("http://www.debianadmin.com/forgot-root-password-or-reset-root-password-in-debian.html") for root and /etc/ssh/sshd_config to allow root login (permission and allow empty passwords).  However, when I plugged the hard drive back in I was not able to ssh in as root.  Don't know what the error was.

I mounted my system again and then [chrooted]("https://help.ubuntu.com/community/BasicChroot") to access the system as if it was running.  apt-get update, apt-get upgrade -f, apt-get install -f all yielded errors.  After many trials, I started attacking the errors one by one.  The error came from a custom package, [mediasmartserverd]("http://www.mediasmartserver.net/forums/viewtopic.php?f=23&t=7720&start=45"), I installed on my Acer H340 NAS.  More specifically, the description field in  /var/lib/dpkg/status and /var/lib/dpkg/available had some empty lines.  I kept fixing each error that occurred after apt-get install -f until things were successfully installed from it.  I then attempted apt-get upgrade but had issues (probably because my chroot wasn't set up properly).  I tried su and sudo and the segmentation fault errors were gone.  I plugged hard drive back into NAS and finished my upgrade to Precise.  Things are fine now.

What did I learn?  I love Linux and Ubuntu even more as I learned how powerful chroot could be!

NOTE: As my NAS had Ubuntu serve installed, the main partition was formatted as a Linux LVM.  I had to [setup]("http://www.linuxquestions.org/questions/fedora-35/how-can-i-mount-lvm-partition-in-ubuntu-569507/") a few things on my laptop before I was able to mount the disk properly.

---

