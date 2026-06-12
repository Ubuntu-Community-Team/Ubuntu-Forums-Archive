---
title: "Boot into recovery mode and turn on networking?"
date: 2016-07-04
forum: Installation &amp; Upgrades
---

### Post by UserJB on 2016-07-04
Is it possible to boot into recovery mode and turn on networking so that I can install packages with apt-get?  If so, how can I turn on networking from recovery mode?

So far, I can boot into recovery mode, and I'm trying to run apt-get update or apt-get upgrade or even install the nvidia drivers, but networking is off so that doesn't work.

---

### Post by ajgreeny on 2016-07-04
Do you have a connection problem when booting normally into the normal desktop, or is this just a recovery-mode problem, and if so, why are you needing recovery-mode?

If you can not get a connection in normal boots tell us more about your hardware and whether wifi or cable ethernet connection.

---

### Post by UserJB on 2016-07-04
The problem I'm having is that when I boot Ubuntu 16.04, the display is broken: icons are flashing, and I can't do anything.

I was looking at recovery mode because I wanted to get at a command-line so I could install a new display driver.

I was able to solve this in another way: by typing ALT+CTRL+F1: that got me to a login prompt.

---

### Post by steeldriver on 2016-07-04
Is there no longer a "root shell with networking" in the boot menu? As seen here [http://askubuntu.com/a/95268/178692](http://askubuntu.com/a/95268/178692)

---

### Post by grahammechanical on 2016-07-04
Recovery mode has an option called Network - Enable networking. It will use the information in network manager to make a connection to the router. It will also put the file system (Ubuntu partition) in read/write mode and then come back to the recovery menu where we can select Root - drop to root shell prompt.

And with the file system in read/write mode we can make changes to the system such as purging and installing proprietary video drivers. To come out of root shell prompt type "exit" and press enter. Then, when back at the recovery menu select "resume."

At this point the video drivers have not been loaded. They have been by-passed. So, expect the system to be using a fall back open source video driver called llvmpipe with a lower screen resolution. It takes a restart to load the standard open source video driver or an installed proprietary video driver and run Ubuntu with the optimum screen resolution.

Regards.

---

### Post by kansasnoob on 2016-07-04
> **steeldriver said:**
> Is there no longer a "root shell with networking" in the boot menu? As seen here [http://askubuntu.com/a/95268/178692](http://askubuntu.com/a/95268/178692)

The devs blew that up a long time ago.

---

### Post by ajgreeny on 2016-07-05
Great! 

Assuming this really is solved for you please mark as SOLVED from the Thread Tools menu up-top. It is a great help to users searching the forum.

---

