---
title: "upgrade to 10.4 monitor sleep on log in"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by maldron on 2010-05-06
I upgraded to 10.4 today and right after I select my choice in grub it seems to start for a split second on an ubuntu start screen then the screen goes black the monitor says it can't detect a signal and sleep mode kicks in. I can go to recovery mode and choose gauranteed graphic mode or whatever you call it and get in. I did that and have tried to find updates but it says my system is up to date. So I'm not really sure what to do next. I have an "ati saphire" graphic card if that helps...I'm pretty sure this has something to do with it. I can't remember how to find out the exact info from within ubuntu for it though. Id on't see a display adapter like phrase under "system" anywhwere.

---

### Post by Catharsis on 2010-05-07
Try adding "nomodeset" to the kernel parameters.

1) Hold down SHIFT while booting to get into GRUB.

2) Highlight your kernel and hit 'e'.

3) Arrow down to the part with "quiet splash" and replace that text with "nomodeset".

4) Ctrl+x to boot.

---

### Post by gabyong on 2010-05-07
i am having almost the same problem after upgrading thru update manager. Monitor screen run into black after showing ubuntu icon dot screen in 2 seconds, not even shown the login page. i had to hard reset my system and had been doing it so many times. afraid this may damage my hard disk. i am on Dell Inspiron 700m.

---

### Post by gabyong on 2010-05-07
> **Catharsis said:**
> Try adding "nomodeset" to the kernel parameters.

1) Hold down SHIFT while booting to get into GRUB.

2) Highlight your kernel and hit 'e'.

3) Arrow down to the part with "quiet splash" and replace that text with "nomodeset".

4) Ctrl+x to boot.


I had just followed your advices but still didn't work. Had also try to replace with "i915.modeset=0", "i915 modeset=1" or xforcevesa noapic noapci nosplash irqpoll".

Any other ways to solve it. Thanks!

---

### Post by garvinrick4 on 2010-05-07
So plymouth is starting but we do not know about ureadahead or mountall? Here are mine that work see if yours looks the same installed and version. I believe you said you can get to grub. If cannot get to grub, we have to reinstall grub2. 

rick@rick-laptop:~$ aptitude show ureadahead
Package: ureadahead
State: installed
Automatically installed: no
Version: 0.100.0-4.1
Priority: important
Section: admin
Maintainer: Scott James Remnant <scott@ubuntu.com>
Uncompressed Size: 156k
Depends: e2fslibs (>= 1.41.0), libblkid1 (>= 2.15~rc2-1ubuntu1), libc6 (>= 2.4),
         libnih1 (>= 1.0.0), upstart (>= 0.6.0)
Conflicts: readahead
Replaces: readahead
Provides: readahead
Description: Read required files in advance
 über-readahead is used during boot to read files in advance of when they are
 needed such that they are already in the page cache, improving boot
 performance. 
 
 Its data files are regenerated on the first boot after install, and either
 monthly thereafter or when packages with init scripts or configs are installed
 or updated. 
 
 ureadahead requires a kernel patch included in the Ubuntu kernel.

rick@rick-laptop:~$ aptitude show mountall
Package: mountall
State: installed
Automatically installed: no
Version: 2.14
Priority: required
Section: admin
Maintainer: Scott James Remnant <scott@ubuntu.com>
Uncompressed Size: 238k
Depends: makedev, udev, plymouth, coreutils (>= 7.1), libc6 (>= 2.9),
         libdbus-1-3 (>= 1.2.16), libnih-dbus1 (>= 1.0.0), libnih1 (>= 1.0.0),
         libplymouth2 (>= 0.8.1-3), libudev0 (>= 151-5)
Breaks: policycoreutils (< 2.0.69-2ubuntu4), usplash (< 0.5.47)
Replaces: upstart (< 0.6.3-2)
Description: filesystem mounting tool
 mountall mounts filesystems when the underlying block devices are ready, or
 when network interfaces come up, checking the filesystems first.

These are the 3 packages that are suppose to start in order. I believe it is your graphic drivers so plymouth starts, ureadahead and the mountall and it makes a successful boot. Lets start here to make sure we got the right packages doing their thing.

---

### Post by maldron on 2010-05-07
I did as you suggested Catharsis and it worked perfectly. Although I must have made some type of silly mistake because when I go to reboot after it loaded successfuly to see if it would do so again the "quiet splash" was still in the kernel line and I have to retype nomodeset every time. Is there a way to add that perfemently to the line?

edited:
I just found a post explaining that I needed to update my grub because I didn't hold down left shift correctly. It seems to be staying in Nomodeset now. Thanks for the help Catharsis!

---

