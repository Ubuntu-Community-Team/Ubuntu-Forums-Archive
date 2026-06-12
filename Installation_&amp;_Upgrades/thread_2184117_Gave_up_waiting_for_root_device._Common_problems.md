---
title: "Gave up waiting for root device. Common problems:"
date: 2013-10-27
forum: Installation &amp; Upgrades
---

### Post by Maheriano on 2013-10-27
I upgraded my 13.04 server to 13.10 and now it won't boot, I don't know why. I did a lot of searching regarding these error messages and tried a lot of the responses but none of them worked. I can easily boot into the older kernel and it works fine, I just can't boot into the newest kernel. Not sure why. It's a RAID5 system with 3 hard drives in it and a single partition of Ubuntu 13.04. When I boot into the first kernel, I get this:

Gave up waiting for root device. Common problems:
- Root args (cat /proc/cmdline)
- Check rootdelay= (did the system wait long enough?)
- Check root= (did the system wait for the right device?)
- Missing modules. (cat /proc/modules; ls /dev)
ALERT! (/dev/disk/by-uuid/b70376fc-b05b-809b-61889b77141f does not exist. Dropping to shell!

And then it gives me BusyBox.

---

### Post by TheFu on 2013-10-27
I don't have a clue, but could your /boot partition be full?  Too many old kernels that need to be cleaned up?
```

df -h /boot
```
and```

df -i /boot
```
should tell.

---

### Post by Maheriano on 2013-10-27
Only 1% used on both. I just realized also that PHP isn't working properly on some of the pages on the server. On some of the more complicated statements like the shorthand if/else operator, it breaks. It'll just show the else portion right in the HTML, it won't execute anything. I might just try and reinstall Ubuntu.

---

### Post by Maheriano on 2013-10-27
Forget the PHP issue, that was related tot he new version not accepting "<?" as an open tag. I had to go through my web code and change them all to "<?php".
Original problem still exists.

---

### Post by Maheriano on 2014-07-12
Nearly a year later and I'm still trying to fix this, except now I'm determined it's going to get fixed. Either that or I'm going to reinstall.

I'm still getting the original error when trying to boot into a newer kernel but I can boot into one of the really old kernels just fine.

The best I could do is to take a photo of the screen the server is hooked up to. It's on a RAID5 setup and has a hardware RAID controller though I'm told I might have installed it as a software RAID, I'm not too sure if I did it correctly.

---

### Post by TheFu on 2014-07-12
Please post the output from 
* sudo parted -l
* sudo blkid
* ls /dev/md*

This will help us get information for next steps.
It would also be nice if you posted the output to the previously requested commands too.  This is a two-way street. ;)

---

### Post by Maheriano on 2014-07-12
> **TheFu said:**
> Please post the output from 
* sudo parted -l
* blkid
* ls /dev/md*

This will help us get information for next steps.
It would also be nice if you posted the output to the previously requested commands too.  This is a two-way street. ;)

For the first one I took a picture, the output was long. Please see the attachment. When I first entered the command I got this:
```
Error: Invalid argument during seek for read on /dev/sdc
retry/Ignore/Cancel?
```
Then when I type cancel I get what you see in the attached photo.

For the second one (blkid), I type it and I get nothing. I'm at the command prompt, I type it, then it just gives me the command prompt again. I tried typing it on my other desktop machine to make sure I'm doing it correctly and it gave me output there. But it gave me nothing on the server.

For the third one I got this:
```
ls: cannot access /dev/md*: No such file or directory
```
I also tried it without the * and got the same output.

Does that help? Thank you for replying, I really want to fix this as it's a production server.

---

### Post by yancek on 2014-07-16
> For the second one (blkid), I type it and I get nothing. 

That is surprising.  I'm on Ubuntu 12.04 and when I type blkid, I get the output one would expect.  You might try:  sudo blkid.
Your original error in your first post indicates it is looking for a partition with that specific UUID and can't find it for some reason so getting info from blkid would show whether it does exist.

---

### Post by Maheriano on 2014-07-17
> **yancek said:**
> That is surprising.  I'm on Ubuntu 12.04 and when I type blkid, I get the output one would expect.  You might try:  sudo blkid.
Your original error in your first post indicates it is looking for a partition with that specific UUID and can't find it for some reason so getting info from blkid would show whether it does exist.

You were right! I ran it with sudo and I get the attached output. Sorry for the photo, if it were shorter I would have manually typed it out. Thanks.

---

