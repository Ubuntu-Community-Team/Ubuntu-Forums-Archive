---
title: "Problem mounting, Code 13 (I wonder what that might be!)"
date: 2010-07-29
forum: Installation &amp; Upgrades
---

### Post by Albatrossed on 2010-07-29
Hi Everybody,

I am a new, very happy Ubuntu user, on my laptop (for the last couple of months, actually), and on my desktop since yesterday. 

Every time I had a minor problem, I checked this forum for an answer, and I was able to solve every single one of them, although I'm very, very far from being an expert. This time I couldn't find any threads related to my current situation.  

I'm having a problem with one of my partitions after installing 10.04 on a desktop that already has Windows XP. I'm getting the following message when I try to explore it:

"Unable to mount E_NTFS

Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 6).
Failed to mount '/dev/sda6': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details".

I installed Gparted, and this is how it looks:

[IMG]file:///tmp/moz-screenshot.png[/IMG]
[IMG]file:///tmp/moz-screenshot-1.png[/IMG]

Actually, many smaller partitions have been created since I installed Ubuntu: I would be happy with just three: C, D and E... but I guess that's a different problem.

Thanks a lot!
All help will be appreciated!

---

### Post by chopinhauer on 2010-07-29
> **Albatrossed said:**
> 
Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 6).
Failed to mount '/dev/sda6': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware.


Your filesystem may be corrupted, check it under Windows.

---

### Post by Albatrossed on 2010-07-29
Well, I did, and things just started working!

On startup, Windows did a checkdisk on that unit, and now it seems to be working just right, both in windows and Ubuntu.

Thanks a lot!

---

