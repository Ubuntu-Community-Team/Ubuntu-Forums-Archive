---
title: "Updating 20.04.2 LTS with 5.8 Kernel?"
date: 2021-04-15
forum: Installation &amp; Upgrades
---

### Post by robertwk on 2021-04-15
I've read that 20.04 LTS has been released with the 5.8.xxxx kernel with HWE support, but Studio 20.04.2 hasn't been updated as of yet? The current kernel that was included in my installation is 5.4.0-71-lowlatency, but the current IO chip on my motherboard isn't supported so I can't do things like monitor external fan speeds/temperatures.

I located a module on github that supports the module and the correct IO chip but was wondering first if anyone has gone this route. This seems slightly more magical than what I'm used to, so I apologize if I've posted this in the wrong place.

---

### Post by deadflowr on 2021-04-15
You can install the linux-lowlatency-hwe-20.04 package.
Then remove the linux-lowlatency package as that older one will keep installing the 5.4 kernels.

Note that the hwe version will upgrade eventually to the next kernel 5.11 (based on what Ubuntu 21.04 is gong to be using), probably around June or July, maybe August.
Then it'll upgrade to whatever the next kernel series is used in Ubuntu 21.10 sometime aroud the being of next year.

I'd run
```
sudo apt install linux-lowlatency-hwe-20.04
```
let it install, the reboot.
After reboot check that it's now running the 5.8 kernel
```
uname -r
```
if it is then remove the linux-lowlatency package,
again this will simply prevent the system from installing those pesky older 5.4 kernels.
```
sudo apt purge linux-lowlatency
```
and you can usually clear out older kernels with apt autoremove; I add the --purge flag so it fully removes the packages like
```
sudo apt autoremove --purge
```
Big Note: the autoremove command will also remove other packages marked for autoremoval. 
so look at what it output that it will remove first.
If something doesn't look good, check 'n' to abort.
You can post the output of what it says if it lists packages that you're not sure about.

On the other hand, if you're fine with whatever the autoremove outputs as listed to be removed then you can just click Y.

Hope that helps and wasn't too confusing.

---

