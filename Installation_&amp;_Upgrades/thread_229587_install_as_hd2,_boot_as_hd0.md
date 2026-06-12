---
title: "install as hd2, boot as hd0?"
date: 2006-08-04
forum: Installation &amp; Upgrades
---

### Post by skeetly on 2006-08-04
I am trying to install Xubuntu on an old IBM Thinkpad with a PCMCIA cd drive.  I think there is no way to boot from this cd, so this is what I did...

I installed the thinkpad harddrive in one of my desktop machines which could boot from cd, and installed Xubuntu on the thinkpad drive as hd2.  The drive was not partitioned, so I accepted the defaults for partitioning and Grub installation.  When I installed the harddrive back in the thinkpad, grub came up and of course it would not start the kernel.  So I used the Grub edit mode to change boot options from root hd2 to root hd0, and and removed "quiet" from the kernel load line.  On boot, the kernel loads and filesystem load scripts begin to run.  It hangs on "waiting for filesystem".  What should I do?  Is there some other scripts which I can edit to resolve this?  I am able to put the harddrive back into the desktop and run Xubuntu repair mode to get a shell.  I haven't used vim for years but feel that I can cope.  I have some familiarity with unix command-line work.

Thanks for any suggestions.

---

