---
title: "removing/resizing partitions"
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by mostlymental on 2009-12-02
I've had to load 9.04 and 9.10 on a partitioned drive also holding XP.  I've sorted out the various problems and now wish to remove both Ubuntu systems and reload a new one, or, resize one and delete the other.  But, I need to leave the XP partition intact.
Advice on how to achieve this would be greatly appreciated.

---

### Post by Mark Phelps on 2009-12-02
Fortunately for you, since you're NOT using Vista, you shouldn't have any problem using GParted to do this.  Best approach is to download and burn a GParted LiveCD from distrowatch.com, burn that to a CD, and boot from that.

It will start the partition editor app in its own window, and using that, you can move and resize partitions to your heart's content.

Just be prepared to wait a while, maybe a LONG while, because GParted isn't know for being speedy.

---

### Post by darkod on 2009-12-02
Unless you already have some settings in ubuntu that would take long to achieve, clean install is best.
Probably best option is to boot with the 9.10 cd, select Try ubuntu option and open Gparted. Make sure you know which partition is which and what is your XP. Delete the 9.04 and 9.10 partitions, the swap partition(s), all partitions ubuntu related.

Then boot again with the cd, select Install Ubuntu, and select whatever choice you want. For example Use Largest Continuous Free Space, or manual partitioning, etc.

PS. I prefer clean install as opposed to resizing because resize can still create corruption or similar. Not often but it can. If you don't mind doing clean install, the resizing is a hassle. Plus you can only expand into unpartitioned space right next to the partition and it all depends what your current layout is. You have Gparted on the ubuntu cd.

---

### Post by RegB on 2009-12-09
> **darkod said:**
> Unless you already have some settings in ubuntu that would take long to achieve, clean install is best.
Probably best option is to boot with the 9.10 cd, select Try ubuntu option and open Gparted. Make sure you know which partition is which and what is your XP. Delete the 9.04 and 9.10 partitions, the swap partition(s), all partitions ubuntu related.

Then boot again with the cd, select Install Ubuntu, and select whatever choice you want. For example Use Largest Continuous Free Space, or manual partitioning, etc.

PS. I prefer clean install as opposed to resizing because resize can still create corruption or similar. Not often but it can. If you don't mind doing clean install, the resizing is a hassle. Plus you can only expand into unpartitioned space right next to the partition and it all depends what your current layout is. You have Gparted on the ubuntu cd.

I found that gparted would "gray out" the move/resize option on NTFS partitions, e.g. my Vista C: and D: partitions.
Those partitions' properties were also hidden from my Ubuntu 9.10 installation and EVENTUALLY I decided to create a Vista side admin user with the same username and password that I use on the Ubuntu side.
That worked, I was then able to move and resize the Vista partitions, even resize grow left worked.
On re-booting the Vista side windows decided that it had to re-validate them, but that was OK.

Now, for some WEIRD reason the move/resize option in gparted is grayed out again.

Any thoughts ?

---

### Post by darkod on 2009-12-09
> **RegB said:**
> I found that gparted would "gray out" the move/resize option on NTFS partitions, e.g. my Vista C: and D: partitions.
Those partitions' properties were also hidden from my Ubuntu 9.10 installation and EVENTUALLY I decided to create a Vista side admin user with the same username and password that I use on the Ubuntu side.
That worked, I was then able to move and resize the Vista partitions, even resize grow left worked.
On re-booting the Vista side windows decided that it had to re-validate them, but that was OK.

Now, for some WEIRD reason the move/resize option in gparted is grayed out again.

Any thoughts ?

First thing about handling partitions in Gparted is that they can't be mounted (have the keys symbol next to them in the list). That's why if handling ubuntu partitions you have to start as LiveCD and not the ubuntu install (you can't unmount root while ubuntu is working). If any partition has the keys symbol it needs to be unmounted first.

I have resized ntfs with Gparted so I don't think ntfs is an issue.

Also, whether the option will be available sometimes depends on the layout on the disk, what partition you already have there, sizes, etc. If you attach a screenshot of Gparted it would be nice to see your layout and what would you like to achieve.

PS. The Gparted on the LiveCD has built-in ntfs support while Gparted installed later in ubuntu installation has to have the ntfsprogs package added.
sudo apt-get install ntfsprogs

Maybe that was the problem.

---

### Post by RegB on 2009-12-09
Thanks,
I have been trying to reproduce it, re-read your post SEVERAL TIMES, etc.
I finally broke down and installed ntfsprogs and Ta DAHH !!!

No point in taking screen shots now, but the first and most obvious sign of change was that the little warning triangles had gone from those partitions.

I really DO think that I was able to resize partitions using the GParted installed just after the 9.10 install - after a re-boot too.

Anyway, installing ntfsprogs seems to have done it and I thank you AGAIN !

---

