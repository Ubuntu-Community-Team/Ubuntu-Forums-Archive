---
title: "Broken X - nvidia.ko?"
date: 2008-01-06
forum: Installation &amp; Upgrades
---

### Post by codesplice on 2008-01-06
Hey all,
Running Mint 3.1 on an hp dv6700 notebook.  Pretty fresh install, and everything for the most part worked well.  Once I installed the necessary updates, though, I've been having trouble getting xserver to launch at bootup.

Included in the updates was a kernel update - 2.6.20-15 to 2.6.20-16.  Since then, I get a message on bootup that X could not find "/lib/modules/2.6.20-16-generic/volatile/nvidia.ko".  which makes sense, because there IS no such file.  There's one in "/lib/modules/2.6.20-15-generic/nvidia/nvidia.ko", so I used the console to create a symbolic link (via sudo) from where it's looking to where it is.  Run startx, and everything loads as normal.  Until I reboot - then I get the same message.  Look in the 2.6.20-16-generic/volatile directory, and my symbolic link is gone :-/  Recreate it, everything works.

How can I make the link "stick"?  Or am I going about this problem all wrong?

Thanks

---

### Post by codesplice on 2008-01-06
I'm an idiot.  I had completely forgotten that the nvidia driver needed to be reinstalled through Envy after each kernel upgrade. 

Oopsy!

Just reinstalled it, and I'm gonna reboot in a  minute to see if it's fixed.

---

### Post by codesplice on 2008-01-06
Yep.  Reinstalling through Envy fixed the issue.  Hooray!

---

