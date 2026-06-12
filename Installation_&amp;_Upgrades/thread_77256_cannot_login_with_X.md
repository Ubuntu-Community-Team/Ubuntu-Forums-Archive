---
title: "cannot login with X"
date: 2005-10-16
forum: Installation &amp; Upgrades
---

### Post by laulau on 2005-10-16
Hello,

I upgraded from 5.04 to 5.10 using Synaptic and the 5.10 CD as a new source.
After the upgrade, when I tried to use any program, they crashed. I rebooted,
and I am presented with the usual login manager. However, I can type my
login name, but at the first char for the password, it seems the X server
crashes, restarts and I'm back at the beginning of the login-crash cycle.

The Xorg log file has no error (no line with '(EE)') and no suspect messages.
After the login-crash cycle has been run six times, I'm back in text mode, 
with a message looking like: "it seems that the x server crashed six times in the
last 90 seconds; wait two minutes before restarting it" (ha!)

I tried various magical invocations from some forum posts, like:
aptitude install deborphan ; deborphan
dpkg-reconfigure xserver-xorg
apt-get install x-window-system-core
apt-get install x-window-system          (which actually installed some progs)

  ... but I still can't login.

Once in a while, after the first crash, I get a message telling me that "the
greeter application crashed, let's try another!" (GDM, I think), but the final
result is the same.

Note that when I boot in recovery mode, and "startx" as root, I don't have
to graphically login, and I can use Gnome and any program without problem.
I only have a message "failed to init HAL" at Gnome session startup.

At this point, I'm only left with one option, given my limited knowledge
of Linux/Ubuntu things: beg for help from people that know more than 
me about Ubuntu. 

Any help would be greatly appreciated!

  --laurent

---

### Post by vasdim on 2006-02-01
Hello,

   I   have exactly the same   problem  with  laulau.The only difference is that i  made  a clean  installation.  I can  only  login  from   the  console (Alt-Ctrl-f1). The  problem  appeared  after  the Nvidia  drivers were  installed  and   after I  try to  install  some   true  type  fonts  from  windows. 

 Can  anyone  help  me? I  try  to  find   the answer  from  the  forum but  I can not   find  anything!

---

