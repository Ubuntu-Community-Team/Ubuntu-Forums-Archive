---
title: "Resume Upgrade broken by SSH disconnection?"
date: 2010-04-17
forum: Installation &amp; Upgrades
---

### Post by smitty825 on 2010-04-17
I started an upgrade last night (from Jaunty to Karmic) using a "do-release-upgrade" command on a remote server via ssh.  However, this morning, I discovered that the ssh connection between my machine and my server was broken.  

I can see that the do-release-upgrade process is still running (well, a giant /usr/bin/dpkg is in the process list) and waiting for a response.

Is there any way I can take control of that session from my current session?

---

### Post by smitty825 on 2010-04-17
Oh, yea, the installer said it was going to create an SSHd instance running on port 9004.  However, using netstat, I do not see that instance created...

---

### Post by smitty825 on 2010-04-17
To get this sorted out I had to do the following:

1)  Reboot the system. 

2)  Observe the reboot fail (My hosting provider provides a way to ssh into my system via a serial console)  (It failed with the string "init: ureadahead main process (986) terminated with status 5" and only mounted the filesystems as "read only"

3)  I used the "hit escape to get into the debug console" and mounted the filesystem as read/write (mount -o remount,rw /)

4)  (I'm root at this point) so I typed "dpkg --configure -a" to continue where I left off

5)  I exited out of the console and allowed the boot sequence to complete.

6)  I performed an "aptitude -f dist-upgrade" 

Everything seemed to work after that.

***Note: To ensure that everything is working, I am performing an upgrade to the beta of lucid using the do-release-upgrade, so I don't know how well my suggestions above will work over the long term.  If my update fails, I'll update this again...

---

