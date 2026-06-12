---
title: "Login fails after executing &quot;vncserver -geometry 1024x768&quot;"
date: 2013-03-13
forum: Installation &amp; Upgrades
---

### Post by vestport on 2013-03-13
Hello group,  Here is my situation. I have tried installing Ubuntu Desktop 12.10 and 12.04.2 with DRBL. I go through all the configs and DRBL/Clonezilla works great. Now rather than having to be on the console to update/install software etc I would like to just use a vnc like tightvncserver so that I can vnc in from whatever client or other computer.   I do an "apt-get install tightvncserver" and no issues installing on either install (12.10 or 12.04.2) however once I do a  vncserver -geometry 1024x768 I can no longer login after a reboot.  The only way I can get back in as a regular or sudo user is to go into recovery mode then   "mount -rw -o remount /"  then give another user sudo privs. Even if I delete the user that could not get in after reboot and or "apt-get remove tightvncserver" the same thing happens. That user is trash even after I remove tightvncserver, delete & recreate the user. It appears just the fact that I have executed the "vncserver -geometyr" command that it writes to some other files that screw up login. I have no idea what is going on here. I have DRBL going on CentOS with vnc and no issues. Is this a bug in Ubuntu or is there another vnc server that I can try that is less problematic? Does anyone have a work around? I have installed and re-installed and messed with this countless times and no joy.    Please help!     Art

---

