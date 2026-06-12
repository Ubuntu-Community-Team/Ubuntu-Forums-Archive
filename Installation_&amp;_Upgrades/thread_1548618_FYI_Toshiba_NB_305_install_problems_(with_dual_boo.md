---
title: "FYI: Toshiba NB 305 install problems (with dual boot)"
date: 2010-08-08
forum: Installation &amp; Upgrades
---

### Post by greenwom on 2010-08-08
I've installed Ubuntu on a lot of computers, this one is a pain.
Recently threw a copy of netbook remix on this NB-305, here's what I did.

With windows 7 and the latest netbook remix 

defrag the hard drive in windows.
pop in a live usb stick with netbook remix.
run the install (letting the installer do the dual boot partitioning)

Reboot - select windows.  Let windows 7 repair itself.  it takes a while.
for those who have done this in the past.  It looks different then the XP repair blue screen your used to.

Upon reboot you'll see that the new ubuntu install drops to a busybox terminal due grub not seeing the hard drive and using UUID.

it looks something like this:```
"Gave up waiting for root device."

It also give the error "Missing modules (cat /proc/modules; ls /dev"

And Finally it says:
ALERT: /dev/disk/by-uuid/90eoad56....11d9 does not exist. Dropping to shell!"
```

The fix to this is going into the BIOS and changing the sata controller mode from AHCI to COMPATIBILITY ( [credit here]("http://ubuntuforums.org/showthread.php?t=1467481") )

This for some reason then breaks Windows 7 again.  Again let it repair itself.  This time it takes even longer.

In the end you should have a dual boot system.  
Out of the box I know wifi works and usually all I check :) 

Hope that helps someone.

I had tried editing grub and it's config files, this didn't work.  
Also for some reason the BIOS change and the NTFS resize just don't make Windows 7 happy on this laptop.  I had to run the restore from grub in the end to fix the windows 7 install.

In the end I like the laptop.  If it was mine I'd drop the windows partition all together.

---

### Post by naveen chakravarthy on 2010-09-22
hi,
I have the aame netbook...and I ve tried loading UBUNTU on a separate partition 3 times so far with no luckso far.I hope ur solution works.
Thanks any ways.

> **greenwom said:**
> I've installed Ubuntu on a lot of computers, this one is a pain.
Recently threw a copy of netbook remix on this NB-305, here's what I did.

With windows 7 and the latest netbook remix 

defrag the hard drive in windows.
pop in a live usb stick with netbook remix.
run the install (letting the installer do the dual boot partitioning)

Reboot - select windows.  Let windows 7 repair itself.  it takes a while.
for those who have done this in the past.  It looks different then the XP repair blue screen your used to.

Upon reboot you'll see that the new ubuntu install drops to a busybox terminal due grub not seeing the hard drive and using UUID.

it looks something like this:```
"Gave up waiting for root device."

It also give the error "Missing modules (cat /proc/modules; ls /dev"

And Finally it says:
ALERT: /dev/disk/by-uuid/90eoad56....11d9 does not exist. Dropping to shell!"
```The fix to this is going into the BIOS and changing the sata controller mode from AHCI to COMPATIBILITY ( [credit here]("http://ubuntuforums.org/showthread.php?t=1467481") )

This for some reason then breaks Windows 7 again.  Again let it repair itself.  This time it takes even longer.

In the end you should have a dual boot system.  
Out of the box I know wifi works and usually all I check :) 

Hope that helps someone.

I had tried editing grub and it's config files, this didn't work.  
Also for some reason the BIOS change and the NTFS resize just don't make Windows 7 happy on this laptop.  I had to run the restore from grub in the end to fix the windows 7 install.

In the end I like the laptop.  If it was mine I'd drop the windows partition all together.

---

