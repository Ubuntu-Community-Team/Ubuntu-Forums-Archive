---
title: "ubuntu 24.10 unmount: /var/lib/snapd/seed/snaps/pc-kernel_2010.snap: target is busy."
date: 2024-10-12
forum: Installation &amp; Upgrades
---

### Post by katara on 2024-10-12
hi.

i can't install ubuntu 24.10 (trying with pendrive) because after choosed drive and third party software, the installation show a popup error and the log saYS:

[COLOR=#101010][FONT=Ubuntu]unmount: /var/lib/snapd/seed/snaps/pc-kernel_2010.snap: target is busy.


how can i solve?[/FONT][/COLOR]

---

### Post by martin87k on 2024-10-13
Hello, I had same issue on two diffent computers. Solution was NOT to connect to the internet during install, hope this helps. Cheers

---

### Post by sweatingbadwater on 2024-10-29
I'm having the same problem I think I figured it out just let me get back to you

---

### Post by sweatingbadwater on 2024-10-29
I think the problem is that the PC kernel 2010 is not there, I was trying to experiment with it and just keeps on coming up with error codes like there is a different kernel in there that you are currently running I think the one I have is 1984 and it can't unmount because it is currently using it. I think. I had tried to delete and reinstall the latest PC Colonel 2010 but it just said Eric cannot perform falling task cannot refresh kernel with change created by old snapd that is missing gadget update task.

---

### Post by sweatingbadwater on 2024-11-07
Okay, I tried a lot of different things, but then I just turned the internet on, connected it, and did the smaller install, and it worked.

---

