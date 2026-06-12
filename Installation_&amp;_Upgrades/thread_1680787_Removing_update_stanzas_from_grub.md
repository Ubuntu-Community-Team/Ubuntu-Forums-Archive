---
title: "Removing update stanzas from grub"
date: 2011-02-03
forum: Installation &amp; Upgrades
---

### Post by jabac on 2011-02-03
I have Ubuntu 10, Linux Mint 10, and Windows 7 installed on my machine.  Every time there is a kernel update, grub adds the new operating system as a new item in the boot screen, but it does not remove the old variant. The result is that more an more choices appear as bootable, but most of them will never be used.  Now, how, in grub V.2, does one remove old stanzas that one no longer needs?  It seems to me that one merely has to go to the boot directory of the particular system one is in, remove the vmlinuz, etc. for the particular kernal version no longer needed, and then run grub update.  This should give one a new cleaner screen on the next boot.  Is this right?

---

### Post by sikander3786 on 2011-02-03
Welcome to the forums :-)

It is recommended that you at least keep one older kernel so that if the newer one runs into problems, you can boot the older one and diagnose/solve the problem.

For removing Kernels, see here.

[http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)
courtesy of forum member *drs305*

---

### Post by jabac on 2011-02-04
Thanks.  I tried ubuntu-tweak.0.5.10, installing it with the debian package installer.  It found the extra kernels. It acted like it was going to do the job but never completed. I tried it several times and noticed that the program would not respond after the first use after boot. Once when I started it from a terminal, there were various error messages relating to icon images and python. So I would think that some package updates need to be made with new libraries or whatever.  Then I tried synaptic but that would not show the kernel packages right off, so I soon abandoned that and went to kpackagekit (I am running kubuntu). It was easy to bring up the installed kernel packages and instruct their removal.  That worked.  Removing the kernel-image.??? while running Ubuntu and doing update-grub took care of Mint and Win7 parts as well.  Thanks again for your answer and referrals. I appreciate them.  Problem solved.

---

