---
title: "Grub loading error"
date: 2009-12-16
forum: Installation &amp; Upgrades
---

### Post by jsimonetti on 2009-12-16
I recently **attempted** to dual-boot my mac OSX notebook with ubuntu.  After running the install it restarted into OSX.  I Tried using the startup disk utility and switch to linux and instead it brought me to a grub rescue prompt.  I restarted back into OSX and removed my linux partitions, however my Linux Swap partition would not delete.  After restarting to try and reinstall i was presented with the same grub rescue prompt, restarting and trying to boot into osx now gives me the same prompt.  an ls commands shows me my hd partitions, however i cannot "cd" into them like a normal directory.  Im pretty confused so any help would be most appreciated.  Thank you

Jsimonetti

---

### Post by jsimonetti on 2009-12-16
Any Ideas?

---

### Post by jsimonetti on 2009-12-16
I have managed to restore mac by holding option and starting up.  It shows the linux partition, and the mac partition and the mac partition loads fine.  Any Ideas why ubuntu did not install properly?

---

### Post by darkod on 2009-12-17
I'm not familiar how it works on Mac, but when dual boot with windows the first step is to shrink the windows partition which is usually taking the whole hdd. Then instead of installing ubuntu right away, you need to start windows few times to make sure it's happy with the shrink. Only then boot with the ubuntu cd and start the install process. Tell it to use the fre space you created (Use Largest Available Free space) or create partitions manually.
The process should be somewhat similar.

---

