---
title: "Bad DVD? AMD 64 DVD - corrupt w/ correkt md5"
date: 2006-04-02
forum: Installation &amp; Upgrades
---

### Post by dacovale on 2006-04-02
I've downloaded the DVD-iso for AMD64 and have burnt it (twice).
Both DVDs fail to install a working ubuntu system.
The iso have the correkt md5sum (from the checksums on the server)
yet the disc doesn't work. I've acctually even downloaded the image twice through bittorent, to see if the first download was corrupt despite of the md5sum.

Since one of the DVDs doesn't hang before it's in the final stages, I tried to install a server install, and I think I have a working server install, (but I can't install regular, then it freezes).
Is there some way to check if my system is healthy? or do I need to trust to luck?

As long as it's healthy, my only problem is how I'll get gnome up and running.

What do I type to download a good, working copy, and what do I type to install it?

or,

If it's not healthy, is it possible to install from a 5.04 x86 CD (from shipit, it works but has its own problems since it's x86), and somehow upgrade from there to an working 64-bit 5.10 system w/out too much hassle?

would appreciate any help I can get. I like what I've seen of ubuntu, w/ the exception of my small install problem on my own computer. 








I'd be really glad if someone could help me sort this out.

---

### Post by Bartender on 2006-04-02
If you've got the time to try again, maybe it'd be a good idea to d/l and burn a LiveCD and see if your PC will run off of that.  Might tell you more about whether it's an incompatibility with your hardware or not.

---

### Post by dacovale on 2006-04-03
I know that there's no hardware problems.
I had a working install of ubunto (from the x86 hoary CD I mentioned).
Unfortunately, since I've got a AMD64, all didn't work as it was supposed to. 
the system clock ran about twice as fast as it should have done. Through a search in these forums, I got to know that the problem was because of my AMD64 and that I really should use the AMD64 version instead of the x86 one.

My problem is that the download seems to be wacked, no matter how often I try.

---

### Post by dacovale on 2006-04-03
Unfortunately, I have discovered that my server install wasn't flawless iether. For some reason, there's a problem with the locales. (I'm a swede).

Twice during boot, I see the following errormessages:
> locale: Cannot set LC_CTYPE to default locale. No such file or directory.
locale: Cannot set LC_MESSAGES to default locale. No such file or directory.
locale: Cannot set LC_ALL to default locale. No such file or directory.

---

### Post by dacovale on 2006-04-05
Ok, I'll have another go at this little problem...

I have a new but not so fancy system with an AMD64 and two harddrives (one 200GB and one 120GB).

On my main drive (the 200GB) I have 3 partitions, one 127GB NTFS (Windows XP) as primary partition and two ~30GB FAT32 partitions.

On the other drive, I want ubuntu. There's already a heap of failed installs on my secondary drive, and nothing worth keeping.

Now, since I seem to be unable to properly burn the DVD (I don't have any blank CDs at home), how would I do to install from the iso or the network.

I have read 

[http://www.ubuntuforums.org/showthread.php?p=143583](http://www.ubuntuforums.org/showthread.php?p=143583)
[https://wiki.ubuntu.com/InstallUbuntuWithoutRemoveableMedia](https://wiki.ubuntu.com/InstallUbuntuWithoutRemoveableMedia)
[https://wiki.ubuntu.com/Installation/FromWindows](https://wiki.ubuntu.com/Installation/FromWindows)
[https://wiki.ubuntu.com/Installation/LocalNet](https://wiki.ubuntu.com/Installation/LocalNet)
[https://wiki.ubuntu.com/Installation/WindowsServerNetboot](https://wiki.ubuntu.com/Installation/WindowsServerNetboot)
[https://wiki.ubuntu.com/InstallationUbuntuFromWindows](https://wiki.ubuntu.com/InstallationUbuntuFromWindows)
[https://wiki.ubuntu.com/InstallerForWindows](https://wiki.ubuntu.com/InstallerForWindows)
[http://marc.herbert.free.fr/linux/win2linstall.html#ubuntu](http://marc.herbert.free.fr/linux/win2linstall.html#ubuntu)
[http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/doc/manual/en/ch04s04.html](http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/doc/manual/en/ch04s04.html)

and some others, but I can't get it to work on my machine.
When I follow the instructions and use my primary (NTFS) partition, the kernel panics.
If i try to use the FAT partitions, I get all kinds of exotic failures from XP at boot.

Could someone walk me through how to get Ubuntu installed on my machine?


Or, if this aproach is too stupid/complicated/wrong/dangerous, could someone tell me how to transform a working x86 install (from pressed 5.04 CDs) into a 5.10 AMD64 install?

---

### Post by dacovale on 2006-04-07
please, can someone help me with this? I'd like to get Ubuntu installed.

---

### Post by Panhead Bill on 2006-04-08
Do a memtest, try the liveCD, borrow another CD/ROM, change Video cards.

That is what it took for my Spare parts PC; one stick of ram was flaky, the Live CD pointed out that my Plextor DVD/R/W wasn't compatible with the live or install process, and when I finally had a useable CD/ROM, the old AGP video board was also not compatible.

After all that my first install CD worked, I just updated and installed the K7 core this evening and I'm on to more discoveries . . .

---

