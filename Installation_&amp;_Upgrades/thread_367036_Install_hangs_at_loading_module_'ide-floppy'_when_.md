---
title: "Install hangs at loading module 'ide-floppy' when detecting hardware."
date: 2007-02-21
forum: Installation &amp; Upgrades
---

### Post by lovitts on 2007-02-21
I'm a noobie to Ubuntu - trying my first install.  I'm using the alternate CD, and everything progresses ok until detecting hardware, when the install hangs at "loading module 'ide-floppy'"
This problem happens in both text and command line install.
Can anyone please help point me in the right direction?

Thanks in advance!

---

### Post by rsambuca on 2007-02-21
At the opening menu screen, prior to selecting install, add "ide=nodma" as a boot option.  If I recall, I think it is F6 to enter the boot options, and then and the above line before the "--" at the end of the line (don't forget to leave a space before the dashes).  Then see if it will work.

---

### Post by lovitts on 2007-02-21
Thank you for your reply.  I tried adding ide-nodma just before the -- in the boot options (with a space before --).   Still the same problem...installation hangs while detecting hardware at 85%, loading module 'ide-floppy' for 'Linux IDE floppy'...

other ideas?

---

### Post by L337reap0r on 2007-02-22
I'm having a similar problem myself. I've been running Ubuntu since Breezy, and I've done a full reinstall every time. I am currently running the live system while trying to install Edgy, and everything seems to have hung at 90%. The installation is currently on "Loading module 'usb-storage' for 'USB storage' ..." and it hasn't moved in about a half hour or so. I can still use everything, nothing has locked up, but the installation has stopped advancing. Dapper installs and runs fine, and I have done the md5 checksum on the Edgy iso as well as the CD self-test in boot.

I've found several threads stating problems like this, but no one seems to really have an answer that has been verified to work. I intend on trying the console installation and the alternate CD next.

---

### Post by rsambuca on 2007-02-22
Sorry guys, out of ideas on this one.

---

### Post by sokam on 2008-03-11
I had the same prob when I install 7.10 on a computer with Seagate ST320413A (20gb) harddrive but didn't have any problem with Seagate ST38410A (8.4gb).  The only thing I changed was the harddrive.  Is this a harddrive related issue?

---

### Post by blitzkin on 2008-03-28
is there any solution for this issue? i cant install ubuntu server version :(

---

### Post by blitzkin on 2008-03-28
anyone please? previous installed is the desktop version and is working fine. when i downloaded the server version it hangs in 86%

---

### Post by F1 Systems on 2008-07-17
The exact same problem attempting to install to a Seagate 20GB hard drive. 

Using another drive solved the problem. My drive was a 20GB Seagate U Series 5 ST320413A. 

Seems this might even be old news. Searching for linux and Seagate U Series gets a number of sad stories.

Mine, however, works fine with its Western Digital 20GB drive.

---

