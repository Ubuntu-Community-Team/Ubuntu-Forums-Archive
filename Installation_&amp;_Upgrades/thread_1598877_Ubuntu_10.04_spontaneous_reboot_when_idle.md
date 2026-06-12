---
title: "Ubuntu 10.04 spontaneous reboot when idle"
date: 2010-10-17
forum: Installation &amp; Upgrades
---

### Post by Simon Cropper on 2010-10-17
Hi,

I have noticed today that when left idle one of my main machines with Ubuntu 10.04 on it will automatically reboot.

The sequence is as follows...
1. I start the main computer and leave so other computers can see data on Samba Shares or NFS.
2. Access computer with Windows Vista Business Laptop.
3. ~1 hour later I find the main file computer is unavailable. When investigating I find it has reboot and is hung at the BIOS password.
4. I have tried this several times and found that it does it regardless of whether anything is actually open.

Anyone have any ideas?

System of computer left idle with files...
Ubuntu Release 10.04 LTS
Kernel Linux 2.6.32-25-generic-pae
Gnome 2.30.2

**** Update ****

Continuing on with my testing I noticed that if logged on as a different user (i.e. not me) the computer did not shutdown. Consequently I surmised that the problem was a corrupt configuration file or something in my home folder. As I make complete backups of my home folder every night, I reverted to Friday's backup and the problem appears to be fixed.

I left the computer idle for the last 6 hours and it stayed on. In the previous 5 hours, prior to the restoration of the home folder, the system would have rebooted many many times.

So the problem appears to be solved. I suppose the lesson is backup and backup often!

**** end update ****

Cheers Simon

---

