---
title: "System hangs after getting abi-3.16.0-62-generic kernel"
date: 2016-02-24
forum: Installation &amp; Upgrades
---

### Post by matthewk2 on 2016-02-24
I have been running 14.04 on a VM (vmware player 7.1.3 build-3206955) on my Windows notebook for a long time now.  Yesterday I got some updates that included the new abi-3.16.0-62-generic kernel.  Last night my Windows machine rebooted for updates.  Yea, the joys of Windows..  So my VM was closed.  Today when I went to restart the VM that has been working flawlessly for the past year, it was hanging after trying to start strongswan.  After booting up in single user mode and making it so it would not want to start strongswan, it started hanging after trying to start the vmware tools.  On a hunch I rebooted into the old kernel and poof, it came right up, happy as a clam.  

I did some reading and tried an update, and a dist-upgrade.  I got a bunch of packages, but the abi-3.16.0-62-generic kernel still causes my system to hang when starting services.  BTW, I do not think that the strongswan service is where it is stopping.  It appears to be after that, but that is the last line I get on the screen.

Any thoughts are appreciated.

---

### Post by mail29 on 2016-02-25
Hi,

you are not alone :) I have the same problems on two vm's (VMware Workstation 12 Pro 12.1.0 build-3272444) . I also tried to upgrade the kernel to 3.19 and 4.2 but both have the same results. :(
Whats the best way so find the error and a solution? What logs should I use?

I think it could be related to Bug Report 1548587 [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1548587](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1548587)

---

### Post by matthewk2 on 2016-02-25
Thank you for the reply!  I had read that if you had anything with third party kernel modules that they would need to be recompiled, but that would be automatic unless you deleted the generic kernel files.  If someone knows more about this feel free to chime in now (smile).  I do know that I had accumulated a lot of old kernels and a while back I cleaned out all of them except the one that I was using (which I had been using for a while so I had faith in it..) and the one that came with the system when I first installed it.  I was under the impression that the only kernels that I wiped were versions between those two, so I should have been safe, but I really don't know 100%.

The good news is my system is still up and going strong on the abi-3.16.0-60-generic kernel.

Thank you for letting me know I am not alone.  Please follow up if you find a solution and I will do the same!

---

### Post by matthewk2 on 2016-02-27
This is weird.  I got another kernel update.  As far as I can tell this is the same 3.16.0-62 but my system came right up under it.  It looks like the initrd.img-3.16.0-62-generic was rebuilt as it has a later timestamp.  Anyway things seem happy once again. Hopefully yours will be happy now too.

---

