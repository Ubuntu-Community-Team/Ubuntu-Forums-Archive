---
title: "Update Blanks Screen Then Doesn't Boot to Desktop"
date: 2023-08-04
forum: Installation &amp; Upgrades
---

### Post by scpatl4now on 2023-08-04
I have Ubuntu 22.04 installed and went to do updates this morning.  About halfway into installing them my entire screen went blank.  I wasn't sure what to do so let it go 15 mins and then restarted.  I could only get to command prompt login.  I had to reinstall ubuntu-desktop to get back to a normal login screen.  It now is trying to get me to remove things via automatic update.  I don't think that is wise currently.  I had tried booting to previous kernel but same thing before I reinstalled the desktop.  The only options were 6.1 and 6.2 when I rebooted.  The auto update listed 5.10 to remove??  I really am not trusting the updates being pushed.  Is anyone having a similar problem?

---

### Post by solid-snail on 2023-08-04
[https://ubuntuforums.org/showthread.php?t=2489595](https://ubuntuforums.org/showthread.php?t=2489595)
probably related.
this update seems to remove gdm3 and gnome-shell, which probably explains the blank screen.

---

### Post by scpatl4now on 2023-08-04
Thanks...I do believe it is related.  I had a recent update also blank out my screen updating the kernel and Nvidia drivers (always suspect) a couple of days ago.  I was able to get back by booting to the previous kernel at which point it looked like it finished the update and I was able to boot normally.  Is anyone testing these updates they are pushing?

---

### Post by scpatl4now on 2023-08-04
Merged with another thread here
[https://ubuntuforums.org/showthread.php?t=2489595&p=14153179#post14153179](https://ubuntuforums.org/showthread.php?t=2489595&p=14153179#post14153179)

---

