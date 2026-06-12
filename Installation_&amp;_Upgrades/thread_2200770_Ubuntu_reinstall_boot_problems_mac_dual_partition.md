---
title: "Ubuntu reinstall boot problems mac dual partition"
date: 2014-01-21
forum: Installation &amp; Upgrades
---

### Post by cdahl7 on 2014-01-21
I was in the process of installing mac os on my computer with ubuntu when I accidentally clicked to update nividia driver and its screwed everything up. I re-inserted my live cd to try and just start over, but then I messed something else up and wasn't get grub or anything. I ran boot repair and now I am getting grub menu again, but I have tried to re-install from live cd, but ubuntu won't load after installation is complete. Obviously, the built in clear and reinstall in the live cd is not getting rid of everything. I have no data on this computer and have no problem starting from scratch, but I need help to do this as the live-cd built in reinstall is not cutting it.
Thank you,
-Chris

---

### Post by tfrue on 2014-01-21
Re-run the boot repair but instead of choosing repair, click the one that says make a boot-info and paste the url here. Please and thank you!

Chris

---

### Post by cdahl7 on 2014-01-21
[http://paste.ubuntu.com/6794838/](http://paste.ubuntu.com/6794838/)

---

### Post by tfrue on 2014-01-22
So how do you want the partition table laid out? Do you want Ubuntu and Mac OS on the same HDD, then manually mount the /home and other directories in the 1000GB drive? What is your plan? 

What I plan to say to you is that we should format both of the drives, use whichever drive as the main drive for grub and base installs for the other OSs and try re-installing

---

### Post by tfrue on 2014-01-22
Your partition tables are a bit out of whack, and it looks like you tried to install Mac OS to the 30GB drive. So you have Ubuntu on one drive, and Mac on the other while the Mac drive doesn't contain a valid boot loader and there is no partition table on the 1000GB drive. So that is why I say format and start over.

---

### Post by QIII on 2014-01-22
Hello!

Would you please give us the full specs of the machine?  In particular, is this an Apple product?

Thanks.

---

### Post by cdahl7 on 2014-01-23
The plan was to run both Ubuntu and Mac on the same 60 gb SSD for quick boot up, and then use the 1 TB for data for both. I was in the process of installing mac with Unibeast , but realized that it was not recognizing hard drive formatting so I went back to Ubuntu to try some hard drive formatting and that is when I hit the "update nvidia drivers" link which caused black screens of death. Please advise on complete wipe/re-format method.

---

### Post by QIII on 2014-01-23
Since you are using Unibeast, I can only assume you are in Hackintosh territory.  Since that is a violation of Apple's EULA/TOS and we don't condone such violations on the Forums, this thread is closed.

---

