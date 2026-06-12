---
title: "(Karmic) One or more of the mounts listed in /etc/fstab/ cannot yet be mounted:"
date: 2009-10-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by oooooops on 2009-10-26
Had been running Karmic since last Friday and things were OK.  Rebooted today after updates and now every time I reboot I get an error that says 

"One or more of the mounts listed in /etc/fstab/ cannot yet be mounted:
<all of my file systems are listed here>'

I can get into "Recovery mode" and the file systems seem to be fine. If I try to boot into non Recovery mode the error shows a couple of times then the screen (text login) just flashes repeatedly.  

I don't see anything in /var/logs to give further details.  

Can anyone point me in the right direction?

I should mention that the thread about dpkg -configure -a did not help

---

### Post by punkdrummer09 on 2009-10-26
Same problem here..

---

### Post by shram on 2009-10-26
Same notice here.  It says waiting for /dev/mapper/cswap
I use encrypted swap and luks partitions, and none are recognized at startup with mini.iso, Xubuntu, Ubuntu, or Alternate install.  Also using /dev/sda5, not UUIDs in crypttab and fstab.

---

### Post by Merovius on 2009-10-26
Same here.

---

### Post by MadCow108 on 2009-10-26
had this problem when I upgraded from 9.04 to 9.10 beta over update manager. Maybe the reason of your problem is similar:
(no warranty on anything as I'm just a novice)

The reason was one update failed and I rebooted without fixing it.
I solved it by booting into a recovery console
(I had to edit the grub kernel line, the offered one didn't work [press e and add a single behind the kernel line])
then I needed to remount the filesystem as read write: (warning your root and can break even more!)
mount -o remount,rw /dev/sdaX / (replace X by number)

now I fixed the upgrade with:
apt-get -f install
and finished the upgrade
apt-get dist-upgrade (in your case probably just a normal apt-get upgrade)

I hope this helps

---

### Post by slakkie on 2009-10-26
That is because it is doing checks on the fs. 

[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/215666](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/215666)

The message it self is harmless.. for me at least, since all partitions are mounted.

---

### Post by MadCow108 on 2009-10-26
also in my case the last message I saw was unrelated to the problem.
All was mounted and I could remount all disks without problem. It was something else which hanged and didn't output.

But I also had the flashing screen, so I guessed there may be some correlation between my problem and theirs

---

### Post by shram on 2009-10-26
Boot hangs for me with the following configuration.    crypttab= ```
 cswap           /dev/sda5               /dev/urandom      cipher=aes-cbc-essiv:sha256,swap 
``` fstab= ```
 /dev/mapper/cswap   none        swap    sw              0       0 
``` ```
 tmpfs              /tmp         tmpfs   size=6144M,mode=1777          0    0 
``` ```
 tmpfs              /var/tmp     tmpfs   size=6144M,mode=1777          0    0 
```

---

### Post by oooooops on 2009-10-26
I'm not running any encrypted partitions at all.  

As stated if I go into recovery mode everything mounts seemingly fine.

And the latest update is that I'm back up & running.  

I went into the recovery console, and edited my Xorg conf file.  I removed the reference to fglrx.  I then did a reboot and things were back working.

Now if I can just figure out what is going on with my networking back that is another story and thread.

I hope this bit of news helps someone else in some way.

---

### Post by Findarato on 2009-10-27
I have exactly the same problem. My system only gives this message for only 1-2 seconds and then it boots normally.

---

### Post by ENigma885 on 2009-10-27
It ends up with unmounted SWAP that i have to remount every boot.

---

### Post by emarkay on 2009-10-27
Why then, is this marked "Solved" - I see this too; no apparent harm, but...

---

### Post by ENigma885 on 2009-10-27
> **emarkay said:**
> Why then, is this marked "Solved" - I see this too; no apparent harm, but...

Any suggestions?

---

### Post by hanzomon4 on 2009-10-27
It was [fixed]("https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/459859") for me with latest mountall update

---

### Post by oooooops on 2009-10-27
> **ENigma885 said:**
> Any suggestions?

I marked as solved as I can successfully boot now (even before the latest mountall fix).

My problem was solved by doing what I outlined wherein I went to recovery console and it did an fsck.

Then I removed the entry for fglrx from my X Config which was causing my issues surrounding the "flashing" of hte screen.

---

### Post by bcasanov on 2009-10-27
I'll add myself to the "me, too" list for this problem.  I did a fresh install of Karmic and decided to go with an encrypted home directory option (which includes encrypting swap) and whenever I boot up, I get the "one or more of the mounts..." message.

---

### Post by unsungboxer on 2009-10-28
I am also getting this on a fresh install of 9.04, freshly updated to 9.10 on an HP mini 311.
(dual booting w/ windows 7 starter)

update: official release of 9.10 installer solved my issue, boots properly.

---

### Post by AlexDudko on 2009-10-28
Updates didn't solve the problem. It still exists (for me), though this error doesn't make any harm.

---

