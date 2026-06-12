---
title: "Synaptic package manager suddenly close if used from remote desktop session"
date: 2010-11-29
forum: Installation &amp; Upgrades
---

### Post by onesim on 2010-11-29
Hi all,
has someone already experienced this failure and possibly figured out a solution?
If not, below are the details of the problem.
 
I've installed a fresh 10.10 on my acer revo 3700. I've set it up to be used with remote desktop through windows7 or another ubuntu installation (it's not a true remote desktop but a remote session with xserver).
If i start Synaptic from remote session, it suddenly close once i mark the package i want to install. But if i install it by terminal console with apt-get, installation works fine.
If i run the synaptic from the console, when the window close, a log message is returned where the main words at the beginnig are something related to libc6 and memory corruption....
 
What i can say is that if i connect the remote unit to a monitor, keyboard and mouse and access it locally, all works fine.
If i detach the monitor and try to do the same things remotely, i get the problem.
 
Looking in ubuntu forums, it seems that without monitor attached, the graphic drivers are not loaded and the graphic card is not used. So what i think is that a remote synaptic call doesn't make use of true graphic hardware of the remote machine but relay on a virtual screen that is sent to remote desktop application.
 
Another program that suffer the sudden close of the window is the gdm-system-monitor, the tab that shows graphical usage of the cpu. If used locally (on a real screen), this tool work well and smoothly, but if opened remotely, the window suddenly close.
 
Any ideas on how to make things works remotely?
Many thanks
Simone

---

### Post by onesim on 2010-11-30
Come on, anyone can help me?

---

