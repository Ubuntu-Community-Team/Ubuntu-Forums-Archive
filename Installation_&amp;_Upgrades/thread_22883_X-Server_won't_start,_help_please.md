---
title: "X-Server won't start, help please"
date: 2005-03-30
forum: Installation &amp; Upgrades
---

### Post by mbh on 2005-03-30
I have managed to get Ubuntu 4.1 up and running on my Thinkpad T41 - using ATI drivers in 1450x10xx mode - something both Redhat and SUSE failed to do.

After installing and running Ethereal including the supporting libraries, i experienced a crash.

Now, after a re-boot, I get a message that X-server did not start. It tells me there appear to be a copy of x-server running on display 0 and I am given the option to start a fresh copy or restart the existing copy. Both options fail.

Going to console 0, running the command "startx", I get a message that the server is already active for display 0 - and if it's not, please remove /tmp/.X0-lock and start again.

Removing the lock file and runnning "startx" starts X-server succesfully. After start, I get the following error message:

Error activating XKB configuration.
Probably internal X server problem
X server version data:
The XFree86 Project, inc
40300001
You are using XFree 4.3.0
...

After accepting the message, the system appear to run OK.

Re-booting returns me to the initial error message however. 

Not wanting to go through the lock removal  procedure at each re-boot, I a looking for help. I have done a re-install of the x-server core and a reconfig of the display but this did not help.


Thanks in advance

Michael

---

