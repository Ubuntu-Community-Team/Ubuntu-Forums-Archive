---
title: "Update problem"
date: 2015-10-08
forum: Installation &amp; Upgrades
---

### Post by albaniaguard on 2015-10-08
Hi
my laptom take an update and now i can start my laptop only with recovery mode,whit privious version of "linux imagine generic" what i can do now?

---

### Post by grahammechanical on 2015-10-08
You continue loading Ubuntu by going to Advanced Options for Ubuntu and selecting that earlier Linux kernel until another kernel update replaces the broken one. That is one option and I have had to use that option myself in the past. This is why these earlier Linux kernels are not removed when the kernel is updated.

Another option is to go use Addtional Drivers and either use the open source video driver or experiment with another of the proprietary video drivers. It might be best to avoid using the "updates" version and to use the "tested" version.

You do not say what version of Ubuntu you are using. For all I know you could be using one of the other members of the Ubuntu famaily such as Xubuntu. So, it is not possible to give detailed instructions because they could be inaccurate. You have not told us the hardware specification of your machine and that information could be important.

Do you have the Proposed Repository enabled? Having the Proposed repository enabled will bring in updates that need testing and which could break the system.

You do not describe what happens when you try to load Ubuntu in the normal way. Therefore, we can only guess at the problem and guess as to the solution.

Regards.

---

### Post by albaniaguard on 2015-10-08
im use ubuntu 14.04 and when i start my laptop normaly hi show only the wallpeaper photo and nothing other. im try to white for 10 minutes and more and again nothing,and leater i have try with recovery mode.

---

### Post by howefield on 2015-10-08
Perhaps you got caught out with a bad kernel update that has affected many forum members, can you boot into the previously working kernel ?

---

### Post by albaniaguard on 2015-10-08
only with recovery mode,i dont know how to do in difrent way :(

---

### Post by howefield on 2015-10-08
> **albaniaguard said:**
> only with recovery mode,i dont know how to do in difrent way :(

At the grub screen (if you do not get a grub screen, pressing and holding the shift key while powering on should bring it up) select Advanced Options and select the second to newest kernel version.

If it is the kernel update that caused the issue, seems that the fix has been released so updating once the update hits your repositories should sort you out.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1503655](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1503655)

---

### Post by albaniaguard on 2015-10-08
when i start my laptop i forcet turn off pushing the power button and leater i go in advancet options of ubuntu and go in recovery mode,and i chose an difent version of kernel and my laptop work ok,but if i turn it off and i try to start again is the same thing. maby is an way to uninstall this last update?

---

### Post by howefield on 2015-10-08
> **albaniaguard said:**
> when i start my laptop i forcet turn off pushing the power button and leater i go in advancet options of ubuntu and go in recovery mode,and i chose an difent version of kernel and my laptop work ok,

That's good, at least you can get into a working kernel.

> but if i turn it off and i try to start again is the same thing. maby is an way to uninstall this last update?

Yes, you will need to select the previous kernel each time you boot until you update to the fixed package, (which shouldn't be very long) unless you remove the newer kernel with something like...

```
sudo apt-get purge linux-image-x.x.x-xx-generic
```  

Replacing x with the actual version numbers.

I'd advise just holding off until the update come through :)

---

### Post by albaniaguard on 2015-10-08
it works thankyou :)  but when i can take the new update? or is better to dont install this version of karnel?

---

### Post by howefield on 2015-10-09
> **albaniaguard said:**
> it works thankyou :)  but when i can take the new update? or is better to dont install this version of karnel?

You choice, but just waiting for a few days before updating again should be ok. Watch for kernel version number greater than the one you removed.

---

