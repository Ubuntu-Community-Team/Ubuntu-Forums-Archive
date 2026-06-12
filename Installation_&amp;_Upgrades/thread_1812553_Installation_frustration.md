---
title: "Installation frustration"
date: 2011-07-26
forum: Installation &amp; Upgrades
---

### Post by Yoshwa on 2011-07-26
Ok, so I have been having some major issues with Ubuntu 11.04. My windows 7 installation on my hard drive (WD5000AAKS, brand new) had been acting up so I decided I was done with it for a while and would install Ubuntu instead.

So I go and download 64 bit 11.04 and make the dvd. No problem here. I booted from the dvd and installed over my windows installation. Again, no problems here. The problem came when I tried to boot; more specifically, it wouldn't. The purplish preboot screen would show up, and then the monitor would go dark and it would come back with lines of text on it that I assume were telling me bad things, but they were gone before I could read them. So I try to reboot, and it happens again. I reinstall from the same dvd, to no avail. I decide maybe this is a problem with the installation disc that i had made, and I make another one, this time with the 32 bit version instead.

I installed that, and I was actually able to boot up, and I was going through the update process, when that failed. I don't remember exactly, but it said something like "unable to apply update." So I just exit out and reboot to finish the update process. This time, it says there is something wrong with my SWAP space, something like "SWAP space failed to mount or SWAP space nonexistent." Multiple reboots do not fix this problem.

Also, i have tried reinstalling multiple times, and so far I have not actually been able to boot into any installation except the one I mentioned before.

I am at my wit's end here. Any advice would be wonderful.

---

### Post by MG&amp;TL on 2011-07-26
> **Yoshwa said:**
>  This time, it says there is something wrong with my SWAP space, something like "SWAP space failed to mount or SWAP space nonexistent." .


It sounds very like the installer did something wrong. Try burning a new cd on the lowest speed possible (cds, in my experience, boot better than DVDs).

Alternatively, if that does not work, you could try partitioning manually.
Try here for help:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Good luck!

---

### Post by Yoshwa on 2011-07-26
Thank you very much. I just installed from my old 10.04 disk (because I know it is reliable) and everything is fine and dandy, even though I really wanted to try 11.04. So there is probably definitely something wrong with both 11.04 disks I made.

---

### Post by MG&amp;TL on 2011-07-26
Most likely. You know you can 'upgrade' to 11.04?

You go to 'update manager' then from there, 'settings' bottom left, and then find the drop-down menu about releases, and set it to notify about 'normal releases' rather than LTS only. Then let it upgrade through 10.10, to 11.04.

Should work, does require a reasonable internet connection though.

---

