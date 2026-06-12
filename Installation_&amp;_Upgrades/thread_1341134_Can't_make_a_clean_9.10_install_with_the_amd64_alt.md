---
title: "Can't make a clean 9.10 install with the amd64 alternate-CD"
date: 2009-11-29
forum: Installation &amp; Upgrades
---

### Post by viking_maniac on 2009-11-29
Last night I tried to install Ubuntu 9.10 with the amd64 alternate install-CD; and I should also mention that I also setup a full system encryption with LUKS using encrypted LVM. I've done this before with the 32-bit edition, and then it worked fine. Now I got this error message after I did the partitioning and came somewhat into the copying of files from the CD-ROM with a CD-R disk:
 
```
Please insert the disc labeled: 'Ubuntu 9.10 _Karmic Koala_ - Release amd64 (some number) in the drive '/cdrom/' and press enter.
```
 
Then everything froze and I couldn't go back, forward or even open the tray. The computer didn't freeze, but the installer came to a definite stop. It's very strange! :/
 
Here's how I setup the partitions:
```
 
#1 Primary /boot (100mb) SDA1
#2 Logical Encrypted LVM SDA5
-- #1 /(root)

```
 
The md5 check-sum of the iso was fine after I downloaded from my favorite and fastest Linux server on the Ubuntu's official mirror list: ubuntu.uib.no (the university of Bergen in Norway). I also burned the iso with verify=on, and the verify went fine too.
 
I did a quick search in the forums though and found a similar problem from a year back:
[http://ubuntuforums.org/showthread.php?t=967922](http://ubuntuforums.org/showthread.php?t=967922)
So I'm definitely not the only one with this problem, and it seems to be still here.
 
I'm re-downloading both the 32-bit and 64-bit alternate as we speak, and I'll try both again now. In the meanwhile, I hope you guys have some advices here. Thanks! :)

---

### Post by mikeac72 on 2009-11-29
Try using the LiveCD.  Install it from there.

---

### Post by viking_maniac on 2009-11-29
> **mikeac72 said:**
> Try using the LiveCD. Install it from there.
 
The problem is that you can't setup an encrypted file system with the LiveCD.
 
----
 
Okay; now something really strange just happened! Like I wrote in the original post, I've already installed the 32-bit Ubuntu 9.10 alternate-CD with system encryption earlier, with success. Now I tried to do the same thing, because I thought this problem was related to the 64-bit edition, but now it suddenly didn't work! So what's new on my system since then? Nothing, actually, except for now I was using CD-R disks, and it didn't work. When it worked, I was using DVD-R disks. I don't know why this happens, since the CD-R disks was burned in only 24x speed and with verify=on; and all where successful. But it appears that the CD-R disks that I've been using lately aren't working well.
 
I don't have anymore disks to test right now, so I'll buy some new DVD-R disks tomorrow and try the 64-bit edition again then. That will be an exciting moment! I'll update the status of this issue as soon as possible, for those of you who are interested in the development.
 
[COLOR=gray]I can add that the CD-R disks works well on the LiveCD; for some strange reason totally unknown to my logical thinking.[/COLOR] :confused:

---

### Post by viking_maniac on 2009-11-30
Hi again,

Today I tried to install with a new DVD-R disk, and finally it worked! :)

I'm not 100% sure what went wrong, but I think this is an issue related to the CD-R disks that I used. 
If you ever encounter this problem, try to burn the iso-image to a DVD-R disk and try again. On my Nec DVD-drive, TDK and Verbatim 4.7GB DVD-R disks work!

Now I'm running Ubuntu 9.10 64-bit with system encryption installed from the alternate install-CD. Hooray! :D

---

