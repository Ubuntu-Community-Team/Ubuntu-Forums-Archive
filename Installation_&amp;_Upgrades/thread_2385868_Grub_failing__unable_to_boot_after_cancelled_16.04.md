---
title: "Grub failing / unable to boot after cancelled 16.04 downgrade from 17.10"
date: 2018-02-26
forum: Installation &amp; Upgrades
---

### Post by timlai77 on 2018-02-26
I made a mistake, resulting in my inability to boot or read my data from my /home directory.   Ideally, I would like to fix GRUB so that I can boot.   But failing that, I would just like to pull all my data off of /home/timlai    
Scenario:
In an attempt to resolve an issue with login loop (nvidia drivers), I upgraded my system to 17.10 (from 16.04.3).    The upgrade seemed to complete without error, but the login loop was worse, because the login loop continued even after removing the nvidia drivers.
Since 17.10 was not working at all, I then attempted (unwisely) to revert back to 16.04.3 by using my USB drive with ISO image.    I went through the installation process, and clicked next to verify that I wanted to install 16.04, only realizing a moment after clicking that I would lose all my data (which was not true with the upgrade to 17.10).    I cancelled the installation on the "choose your timezone/geography" screen. 
Upon rebooting, I found myself on the "GRUB Rescue" prompt.   I was able to determine that my Ubuntu installation is on /dev/sda7, and recovered to the point that I was able to reach the GRUB prompt.  However, attempts to load the linux kernel result in "error: invalid magic number". 
I then tried "Boot repair", as described here: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows).    This process failed, as well, generating the following report:
[http://paste.ubuntu.com/p/P7jZfvnK9n/](http://paste.ubuntu.com/p/P7jZfvnK9n/)

Can someone help?    Thanks in advance!

---

### Post by timlai77 on 2018-02-26
Upon further examination and work, I have found that the 16.04.3 install was very efficient and quickly destroyed the data in my /home directory.   I was able to unlock the directory using encryptfs-recover-private, but my files were almost all gone.
   So, I suspect the GRUB and boot are fairly irreparable as well.   Thanks to the community in any case.

---

### Post by oldfred on 2018-02-26
Whenever you have separate /home or multiple drives you need to use the Something Else install option.
With auto install options you have little or no control over what the installer does. 
If you just want / & have unallocated space the installer works. But when it starts auto resizing or overwriting other partitions you have no control.

It looks like you still have sda5 as a Linux partition that is not mounted via fstab as /home.
And the installer would not have done anything to that partition. But if /home was really inside / on sda7 then it would have overwritten it.

---

