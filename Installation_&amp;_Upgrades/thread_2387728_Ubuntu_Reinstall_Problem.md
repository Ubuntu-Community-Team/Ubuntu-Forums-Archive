---
title: "Ubuntu Reinstall Problem"
date: 2018-03-22
forum: Installation &amp; Upgrades
---

### Post by arianhf on 2018-03-22
hi, 
I upgraded from 16.04 to 17.10 but there were some problems, so I decided to reinstall 17.10 from USB. 
I follow some guides which said no data loss would occur if I followed them. I follow those guides and there is no data missing but my home folder has changed! and I don't know what to do.

before my partitions used to look like this:
[ATTACH=CONFIG]279052[/ATTACH]

and now they look like this:
[ATTACH=CONFIG]279053[/ATTACH]

so the /boot /tmp /var and /home are no longer there! and there is just a / and other drives are showing up like mounted drives.

Is there anyway to fix this without data loss?

---

### Post by Impavidus on 2018-03-23
There are many ways to fix this without data loss. Some are easy, some are fast, some are dirty.

In your other thread ([https://ubuntuforums.org/showthread.php?t=2387654](https://ubuntuforums.org/showthread.php?t=2387654)) we wrote that your /var partition was full and suggested not to use a /var partition at all (and no /tmp or /boot either). Now you made the old /var partition bigger and reinstalled without using it...

When you reinstalled using the something else option, there was a window where you could choose which partition to use where. There you should have selected your old /home partition (/dev/sda8, but the number changes when you delete any of sda5, sda6 or sda7), set its mountpoint to /home and made sure it was not marked for formatting. Also you should have deleted sda6 and sda7 and expanded sda5 to reclaim that space. sda1, your old /boot partition, is a bit useless too, but as it's on the other side of the swap partition it's a bit harder to reclaim and as it's only 0.1% of your hard drive, reclaiming isn't really worth the effort.

You can repair things somewhat without reinstalling. Assuming you haven't done anything you want to keep since reinstalling and assuming your username and userID haven't changed (I suggest you check that), you can modify your /etc/fstab to mount your old /home partition at /home (use the UUID), unmount everything you mounted somewhere in /media and run```
sudo mv /home /home-old && sudo mkdir /home && sudo mount -a
```That should give you your old /home back. If everything is fine, you can delete /home-old. But that still leaves you with an unused sda6 and sda7.

If anything is unclear, ask first, or you may damage your system to the extend that you can no longer login. Even that can be fixed, but it won't be easy.

---

