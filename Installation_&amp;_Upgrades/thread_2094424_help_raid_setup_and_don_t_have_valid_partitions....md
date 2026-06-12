---
title: "help raid setup and don t have valid partitions..."
date: 2012-12-13
forum: Installation &amp; Upgrades
---

### Post by Mascarade on 2012-12-13
Hi!
I try install unbuntu 12.04 alt ver..to a raid 10 array...

I make 4 partitions on /dev/sda, and 4 similar to /dev/sdb...

sda1 500 mg /boot ext4
sda5 10gb / ext4
sda6 2gb swap
sda7 50gb /home ext4

I do the same for sdb...

after, i create Raid1 on the /boot sda1/sdb1
all the other partition is on raid 0....
i set a mont point for each of them and then format and install unbuntu...(whit the kubuntu setting...)

try to install grub /dev/sda /dev/sdb....and after that, i can enter ubuntu, but nothing want to run....exept the console....i ve sean grub installing only on sdb1.....and whit fdisk, it said that all the partition are not valid partition.....but i see /dev/md0 and the other raid partition create....but not valid....? can someone help me please, i tryng this for a week now and get a bit pistoff...but im new to configure whit terminal so.... i continu learning and try, but if someone want to help me just come :)):P

---

### Post by steeldriver on 2012-12-13
I think it's normal for fdisk to report "Disk /dev/mdXX doesn't contain a valid partition table" for RAID devices (as well as for LVM volumes) - my RAIDed HTPC box does for sure

If you are booting as far as the console I don't think there's anything fundamentally wrong with your system - what "alt ver" did you install exactly? are you sure you have actually installed a full desktop / Xserver?

```
 apt-cache policy .?ubuntu-desktop
```Or maybe you have a graphics driver problem?

---

### Post by darkod on 2012-12-13
So, you can boot ubuntu, enter with your user, the desktop loads but nothing works?

Open terminal if you can, and post the output of these commands:
```
df -h
cat /proc/mdstat
```

Also, are you aware that raid0 is not redundant and if one disk dies you lose all your data? Using raid0 is not a very good idea, it is quite risky.

---

### Post by Mascarade on 2012-12-13
Wow! thanx for your reply!!

first i use the mini.iso cd it a alternate cd.....I think, i made a mistake in the : select and installation software....i choose all the 3 kubuntu setting...desktop full and two other kbuntu setting.....im not sure but everything seam fiine fine about the raid

Filesystem                                   mount point
/dev/md1       19 g .........                    /
udev              997m.......                     /dev
tmpfs                                                 /run
none                                                  /run/lock
none                                                  /run/shm
none                                                  /run/ user
/dev/md0                                            /boot
/dev/md3                                            /home

And all raid 1 (for boot) and raid 0 (/, swap, home) is active.....

For the desktop im confuse a bit.....
kubuntu active default setting
installed: 12.04oubuntu2
candidated: 12.04oubuntu2
version stable
***12.04 oubuntu2 0
addresse internet for archive.....
N: unable to locate package desktop

So it is active and nowhere..?

Yes, i can enter the login and see the image font and the bar.....but, when i right click nothing happen (she dissapear) and if i go to the software manager (the shortcut button on desktop) i see program, but nothing after.......So maybe the problem is a desktop package?  Can i reinstalll it...??....
thx :)

---

### Post by Mascarade on 2012-12-13
......just wandering...i dont need to install grub on /dev/sda if he install in /dev/sdb???
just dont care about it or...?
Thx

---

### Post by steeldriver on 2012-12-13
Sorry I don't know anything about installing grub on a RAIDed boot device - however I don't think that would affect your current (desktop) issues - booting is pretty much an all or nothing thing

I'm still not sure exactly which desktop you installed - if it was kubuntu you could try

```
sudo dpkg-reconfigure kubuntu-desktop
```DISCLAIMER: I haven't used a KDE based distro in a while - my advice may be out of date

---

### Post by darkod on 2012-12-14
Grub should work from both sda or sdb. Usually in raid1 you would install on both disks so that it can continue working if one disk fails. But since you are using raid0, it can't work if one disk fails anyway, so having grub on both disks is not really necessary.

According to what you said so far it looks like it's booting but in text mode. If it was grub issue it wouldn't boot at all.

If you used the mini CD and not the Alternate CD, maybe the desktop environment (GUI) installation failed. Also, if you used the ubuntu mini cd, I am not sure if it accepts kubuntu desktop. Maybe it's missing other basic packages.

If you want kubuntu, you should install the kubuntu mini cd.

And is there a need for the mini cd at all? Why don't you simply install Ubuntu Desktop or Kubuntu Desktop which will give you a working GUI system? With the mini cd it installs only basic core system, then you have to chase up packages. If you don't have experience with that, it's much work that you can avoid by installing the desktop cd (or alternate cd for raid support).

---

### Post by Mascarade on 2012-12-22
Ok Thank everybody!!!
I just decide to reinstall kubuntu alt cd and i just discover that i was made a mistake at the first install......Now it work great!! :p

):P

---

