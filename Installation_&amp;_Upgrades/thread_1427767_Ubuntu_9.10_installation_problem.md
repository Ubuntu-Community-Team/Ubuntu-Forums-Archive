---
title: "Ubuntu 9.10 installation problem"
date: 2010-03-11
forum: Installation &amp; Upgrades
---

### Post by Lijnk on 2010-03-11
Recently, I tried upgrading Ubuntu 9.04 to 9.10 using a Live CD, however every time it stops at 74% for about 10-15 min and returns this error:

[errno 30] read-only file system: '/target/boot/vmlinuz-2.6.31-14-generic'

It said the cause was usually from a bad hard drive, so I used Boot and Nuke to zero-wipe the drive. I also tried switching the partition type to Ext3, however both Live CDs for 9.04 and 9.10 returned an error stating it couldn't be done, so I was stuck with Ext4.

I reinstalled 9.04 and it works as well as before I tried the upgrade. I'm also fairly new to Ubuntu (installed 9.04 sometime in February), so there's still a lot for me to learn.

---

### Post by dusdus on 2010-03-12
When exactly do you get the error message?
If you get the message while booting the LiveCD, it probably has nothing to do with your harddisk, but most likely your LiveCD. Have you checked the CD for errors?

---

### Post by Lijnk on 2010-03-12
I'll try that since there's actually a few things that point to that as well. I'll edit this space with what happened.

The integrity of the disc was good, but I was fairly sure it wasn't, so I downloaded another .iso file and this time, I checked the hash. The first time, there was a read/write error, so I downloaded it again, but used a different mirror. The hash worked, I've burned it to the disc using the slowest speed. Integrity of the disc passed.

Now I'll see if the install works (on a separate partition).

---

### Post by Lijnk on 2010-03-13
Got a different error:

The installer encountered an error copying files to the hard disk:

[Errno 30] Read-only file system

This is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.

The disc didn't look dirty, but I cleaned it anyways. I can't burn at a lower speed and I'm very sure the lens aren't dirty. Hard drive is under a year old and the environment is definitely cool.

I'll try the install again to see if it was a fluke.

Not sure what happened, but during the install the entire screen went to a terminal except the text cursor isn't blinking and I can see my mouse. Also, the caps lock light is blinking.

---

### Post by Lijnk on 2010-03-15
I'm going to download the alternate iso and install tomorrow to see if there's a difference. I'm still open to any solutions/ideas anyone might have.

---

### Post by Lijnk on 2010-03-15
I think the problem may be with the wireless card driver since the terminal will return an error with "b43" in it and the only other time I've seen "b43" was when I needed to enable my wireless card in 9.04.

How would I disable/remove the wireless adapter driver before 9.10 installs in a Live USB? (I use a Broadcom in case that helps)

---

### Post by Lijnk on 2010-03-16
I went back to trying the Live CD again (I'm starting to doubt the wireless packages have anything to do with the problem), but I still got the Errno 30 again (at 50% or 51%). I did find a couple threads that seemed to find that it was a conflict with the hard disk and the DVD.

[http://ubuntuforums.org/showthread.php?t=1311565](http://ubuntuforums.org/showthread.php?t=1311565)
[http://ubuntuforums.org/showthread.php?t=749447](http://ubuntuforums.org/showthread.php?t=749447)

Since I can't hook the hard drive up somewhere else and I can't switch DVD drives, is there something I could do to stop this conflict? Any other suggestions would be great since I'm at a brick wall right now :(

---

### Post by Lijnk on 2010-03-16
Still looking for an answer.

---

