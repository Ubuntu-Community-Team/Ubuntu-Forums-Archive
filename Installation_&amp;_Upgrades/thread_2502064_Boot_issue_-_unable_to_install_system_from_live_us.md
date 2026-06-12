---
title: "Boot issue - unable to install system from live usb"
date: 2024-10-31
forum: Installation &amp; Upgrades
---

### Post by moronkatia on 2024-10-31
Hi!
I recently installed Ubuntu 24 but was having certain issues, so I decided to reinstall Ubuntu 22 through live usb. I chose the option erase all partitions, but the installation gave an error (something about cd/did being damaged or dirty). 
Then, I got this: "Error Minimal BASH like line editing is supported", and have been trying to fix it. I was able to get the usb live running, installed boot-repair and got the following boot-info summary:
[http://paste.ubuntu.com/p/tMQn6XCMrq/](http://paste.ubuntu.com/p/tMQn6XCMrq/)
What I didn't get when running boot-repair was the repair option; just the boot-info.
I really someone can help me out. &#128591;&#127995;&#128591;&#127995;&#128591;&#127995;I've been using ubuntu for a while, but my knowledge about computers is pretty basic.
Thanks!

---

### Post by tea for one on 2024-10-31
Unfortunately, the installation failed.
Have a look at line 126 of the report
0% of the system partition is occupied.

I suggest that you make a new USB and test it for 60 minutes before trying the installation.

---

### Post by ne29914 on 2024-10-31
I've had similar issues.
Solution was fully formating the USB thumb drive to FAT32 on a Windows machine before burning the .iso image onto it. Takes half an hour, though.
Previous installs leave spurious partitions on the drive, it seems.

---

