---
title: "Synaptic and Virtual Box"
date: 2007-03-06
forum: Installation &amp; Upgrades
---

### Post by tbuhler on 2007-03-06
After attempting to install Virtual Box on Ubuntu Edgy Eft, it froze, so I just shut down Linux.

When I restarted to try my hand at VB again, Synaptic told me that it couldn't find a VB package, and wouldn't show me any packages. So, I redownloaded VB, but Edgy told me that the package was corrupt. So I downloaded again. Same thing.

After redownloading about 3-4 times, I gave up. There is a physical problem with Synaptic. Being a relative n00b to the non-graphical Ubuntu experience, can anyone give me some pointers to fix my Package Manager?

EDIT: found problem.

---

### Post by MontanaMax on 2007-03-20
What was the solution to your problem? I've run into the same problem and haven't been able to find the fix yet.

Thanks,

---

### Post by Jon &quot;Yogi&quot; on 2007-04-05
I had a similar problem (same effect, just running feisty instead of edgy). Look at the thread [here]("http://ubuntuforums.org/showthread.php?t=398709") for some more info, or [here]("http://jhcore.com/2007/03/25/vista-on-ubuntu-using-virtualbox/") for where I got most of the info below.

Let me know if it works or not. Good luck!

Try this. From the command line, type in (at your home folder, or anywhere else you want to put this): ```
mkdir ~/install_files 
``` and ```
cd ~/install_files
```   Now  type in ```
wget http://www.virtualbox.org/download/1.3.8/VirtualBox_1.3.8_Ubuntu_edgy_i386.deb
``` Now type  ```
sudo dpkg -i VirtualBox_1.3.8_Ubuntu_edgy_i386.deb
```It should install, asking you a few questions. If it didn't install correctly (didn't for me), don't worry about that just yet. The bigger concern is making apt work again. After doing that, try to run and apt update to see if everything is working (and if it is, press Ctrl-C to stop the process: ```
sudo aptitude update
```Now you can worry with setting up Virtualbox with a working apt :).

---

### Post by jbumgar on 2007-04-08
I get this message:  E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

How do I correct it and proceed with the install?

---

