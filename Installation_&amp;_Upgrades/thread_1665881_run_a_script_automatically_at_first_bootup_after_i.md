---
title: "run a script automatically at first bootup after install 10.10"
date: 2011-01-12
forum: Installation &amp; Upgrades
---

### Post by AdmiralNotorious on 2011-01-12
hello

Im attempting to make a personal customization script to run on first bootup

now i know this sounds lazy, but is there some script that runs once at the first bootup that i can stick mine into, so that i dont have to select it on first bootup?

thanx in advance

---

### Post by AdmiralNotorious on 2011-01-13
to clarify my post, i am referring to a text file on the usb-startup disk that i could edit to include my script as a final process. or maybe a directory i could place my script to get it running on first bootup

---

### Post by tommcd on 2011-01-13
You could put your script, or a symlink to your script, into the */etc/rc.local* file, right above the *exit 0* line. 
This will make the script run at the end of the bootup process, right before the desktop loads.

---

### Post by AdmiralNotorious on 2011-01-13
rc.local is a file in an finished ubuntu installation

what i want is a file on the bootable usb/cd that can be altered to include my script so that it loads only once the very first time the system loads up. 

my understanding of rc.local would be i would have to install ubuntu, alter the file and then restart to get it to activate. Or am i wrong in thinking so?

---

### Post by AdmiralNotorious on 2011-01-19
problem has not been solved

---

