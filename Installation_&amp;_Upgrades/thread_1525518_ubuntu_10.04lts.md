---
title: "ubuntu 10.04lts"
date: 2010-07-06
forum: Installation &amp; Upgrades
---

### Post by cjmonaco on 2010-07-06
I have downloaded it and when i try to update or get other software for it ,it comes up with error saying that i have to configure and run this and that and i still get the errors in the package and so on how can i fix this 

this is 1 thing 
Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

i did this and then i got this 

dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem
i did that and i then got this 

dpkg: parse error, in file '/var/lib/dpkg/updates/0072' near line 0:
 EOF during value of field `4.7' (missing final newline)

how do i fix this 
all help would be great full

---

### Post by mörgæs on 2010-07-07
You need to be as specific as possible. Noone can help you based on this description.

[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by jdysinger on 2010-07-07
To configure the upgrade go to Administration -> Software Sources
In the Ubuntu Software Tab checkmark:
-Canonical-support Open Source software (main)
-Community-maintained Open source software (universe)
-Proprietary Drivers for devices (restricted). 
 
In the Download from: click the up/down arrow, and select either Main server, server for the United states, or "Other" and press the "Select Best Server" button.
 
If that doesn't do anything (or that's what you meant by "do this and that", make sure your internet connection is working.

---

