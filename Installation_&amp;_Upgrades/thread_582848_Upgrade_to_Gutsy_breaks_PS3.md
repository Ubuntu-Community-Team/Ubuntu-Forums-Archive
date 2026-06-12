---
title: "Upgrade to Gutsy breaks PS3"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by IMOC on 2007-10-20
I attempted to update my PS3 Ubuntu installation from 7.04 to 7.10 using the graphical update manager and the installation itself ran through with no problems.

However whenever the system tries to boot into 7.10 it hangs with the following on the screen:


Loading kernel with initrd...success.
Booting system...
_


I can still boot into the game OS so the system is not completely broken.
Is there any way of recovering from this?  Does 7.10 work on the PS3?

Thanks,
Chris

---

### Post by shador on 2007-10-20
Maybe it's better to do a clean install on the PS3?

---

### Post by IMOC on 2007-10-20
> **shador said:**
> Maybe it's better to do a clean install on the PS3?

Looking into doing a clean install I found this bug:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/120295]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/120295")

This bug basically says the live CD install has what looks to be the same bug as I am seeing.  It's a little disappointing that the update manager allowed he PS3 to update to a known broken image.

Cheers,
Chris

---

### Post by shador on 2007-10-20
And the alternate CD then?

---

### Post by Spankmaster79 on 2007-10-20
I tried the alternate cd and it ends up with the same errors.

Also installing in with "install" ends up in a kernel error message while installing the kernel.

If you choose "expert mode" you get asked for the following kernels:

> 
linux-cell
linux-image-cell
linux-image-2.6.22-14-cell
none 


the first two fail, the third works but then after the install has finished a reboot doesn't work.

Shutting down the PS3 (really switching off and on again) I get the kboot promt and type "boot" or what would be the command????

It hangs at the same messages IMOC reported.....

---

### Post by oddroot on 2007-10-20
i think your installs might be working, just X (the gui) is not booting properly. I was running 7.04 and upgraded to 7.10. The gui wouldn't book, but hitting alt+ctrl+f1 to get to a login terminal did, and I was able to fight my way back to a properly working gui again.

Usually at the boot prompt you can type linux to boot ubuntu.

---

