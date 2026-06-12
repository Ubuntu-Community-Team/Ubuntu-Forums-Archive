---
title: "virtualbox and intrepid"
date: 2008-07-02
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by MemoryDump on 2008-07-02
decided to try and test alpha1 using the latest virtualbox running on my hardy install.
got it installed (finally) but I keep on getting these kernel error messages when I boot it up. (attached screenshot)
I was getting them too when I was booting off the image too, however restarting the install a few times finally enabled me to continue with the install.


happy testing :D
-MD

---

### Post by philinux on 2008-07-02
Yep had this, just rebooted a couple times, seems to sort itself out. Or a trip into recovery seems to work too.

---

### Post by MemoryDump on 2008-07-02
I've rebooted a few times now and I'm not getting pass this error :(
VB is working properly as I have XP and Fedora9 running as seperate vb's.

edit: 10th times the charm.. finally got it to boot up!

---

### Post by spamzilla on 2008-07-02
I had the same problem a week ago. Remember to make regular snapshots just incase of breakage :D

---

### Post by Shazaam on 2008-07-02
I have a similar problem. See here.....
[http://ubuntuforums.org/showthread.php?t=846927](http://ubuntuforums.org/showthread.php?t=846927)

---

### Post by mitchellcipriano on 2008-07-03
I was having similar problems, but I increased the video buffer from the default 8MB to 32MB and it booted and installed.

---

### Post by simosx on 2008-08-31
Apparently it is a random error (regarding interrupts), so booting a few times you can get lucky and continue. Once in Intrepid, it's good to save the state of the VM, to avoid the tricky booting process.

---

