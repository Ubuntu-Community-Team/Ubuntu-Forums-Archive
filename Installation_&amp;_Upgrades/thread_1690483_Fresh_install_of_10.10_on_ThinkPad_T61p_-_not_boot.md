---
title: "Fresh install of 10.10 on ThinkPad T61p - not booting"
date: 2011-02-18
forum: Installation &amp; Upgrades
---

### Post by r m h on 2011-02-18
So, my T61p (6459-CTO, 15.4", nVidia Quadro 570m, 8GB RAM, 320GB HDD) had been dist-upgraded since like it was new 2005/2006 (along with dd imaging from old HDD to new HDD) and it was showing it's aged pedigree.  

First, I decided to get a re-installable list of packages installed on the machine in the event I wanted to rebuild the machine to an equal state:
```
$ dpkg --get-selections | grep -v deinstall > ~/Desktop/installed_pkgs_t61p_maverick_20110215
```

Then I copied my config files and my home directory to an external HDD:
```
$ sudo mount /dev/sdb1 /320GB
$ cd ~/
$ sudo tar cf - --exclude ./.gvfs . | (cd /320GB/T61p/home/rmh && tar xBf -)
$ cd /etc
$ sudo tar cf - . | (cd /320GB/T61p/etc && tar xBf -)
```

Then using the ubuntu-10.10-desktop-amd64.iso image burned to CD, I installed a clean fresh copy of Maverick on the T61p, formatting the internal HDD in the T61p in the process.

After the install, the T61p would not boot.  It ended up on the black screen with the flashing cursor (cursing flasher?) in the upper left corner of the screen.

To fix that, here's what I did.

First, I thought the problem was the nv driver issue with the Quadro 570m, so I booted the installation disc as a Live-CD.

I downloaded boot_info_script055.sh from [http://sourceforge.net/projects/bootinfoscript/]("http://sourceforge.net/projects/bootinfoscript/")
When I ran it the RESULTS.txt file indicated that grub was not installed in the MBR of any HDD.

That's just not right.  

To resolve that issue, I installed grub to the MBR of the internal HDD.
first, I mounted the internal HDD in the laptop:
```
$ sudo mount /dev/sda1 /mnt
```

Then I installed grub to it:
```
$ sudo grub-install --root-directory=/mnt /dev/sda
```

Then I unmounted the internal HDD and rebooted:
```
$ sudo umount /mnt
$ sudo shutdown -r now
```

When the laptop restarted, it booted just fine.

I can't say if this is a bug or not, because while it had occurred each of the 3 or 4 times I installed/re-installed Maverick on this laptop over the past 3 days, I have no other fresh clean installs to compare it to.

Anyone else experience this with a fresh clean install of 10.10?

---

