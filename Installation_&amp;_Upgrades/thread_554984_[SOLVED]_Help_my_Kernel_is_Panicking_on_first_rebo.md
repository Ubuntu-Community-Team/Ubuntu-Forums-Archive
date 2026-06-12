---
title: "[SOLVED] Help my Kernel is Panicking on first reboot after install!"
date: 2007-09-19
forum: Installation &amp; Upgrades
---

### Post by mrjoeyman on 2007-09-19
First boot without disk after install says:

"[1.16987] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block (0,0) [1.169722]"

Feisty, ver 7xx

please advise

---

### Post by rusher81572 on 2007-09-19
I had this problem with ubuntu on so many machines. I await a response. You are not alone brother.

---

### Post by themadhippy on 2007-09-19
i had the same error but fixed it with the help from here
[http://ubuntuforums.org/showthread.php?t=430529&highlight=ernel+panic+-not+syncing%3A+VFS%3A+Unable+to+mount+root+fs+on+unknown-block]("http://ubuntuforums.org/showthread.php?t=430529&highlight=ernel+panic+-not+syncing%3A+VFS%3A+Unable+to+mount+root+fs+on+unknown-block")
the magic comand that cured all was 
```
sudo update-initramfs -u
```

---

### Post by mrjoeyman on 2007-09-19
how can i get to a point to where I can execute that command?  I put in the live cd and got to the command line and entered the command it seemed to be re-loading or rebuilding the kernel, but when I rebooted it forgot all of that because it probable doesnt remember (save) whatever it did. Any advice on how to get to the command line? I think Ive tried everything I know of...........

---

