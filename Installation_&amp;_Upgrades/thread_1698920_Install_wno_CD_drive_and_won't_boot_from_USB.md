---
title: "Install w/no CD drive and won't boot from USB"
date: 2011-03-02
forum: Installation &amp; Upgrades
---

### Post by BigGreyhound on 2011-03-02
I want to know if/how I can copy a verified Live CD to an external HDD and then install that HDD in another computer in order to do a full install?  I have an old Toshiba laptop with a dead CD drive and the &quot;no legacy&quot; BIOS (should be called &quot;no access&quot;) that cannot boot from USB.  I'm wondering if I can either copy the live CD to that HDD (external) then install that drive in the laptop and use it to do a full install, or if I can do a full install to the external and install it to the laptop and have it work?   IOW, is there any way to get Ubuntu to detect a new environment and reconfigure itself?

---

### Post by swapnilnarendra on 2011-03-03
As far as the installation from external media goes, I think it needs to be booted up. So unless you boot your laptop from your external HDD, I guess it would be pretty much difficult to accomplish what you are trying to do. But I guess it is possible to install Ubuntu in your HDD and then to boot your laptop with it.

You can install it in the HDD and can boot your laptop with it but what next ? I am not sure if your laptop is going to reconfigure its old HDD via your new one. You would still have to install Ubuntu using some media (CD Rom/USB). So my suggestion is to look for an external CD Rom. Then burn a CD/DVD and then to boot your laptop using that Live CD and go for a full install.

---

### Post by BigGreyhound on 2011-03-03
Thank you for replying.
The laptop can't boot from an external CD since it's BIOS is fixed and inaccessible. This was a very bad idea Toshiba had a decade ago and put into an otherwise solid laptop.

That's why I was wondering if Ubuntu might be installed to it's HDD from another computer via an external enclosure and then install the HDD back into the laptop.

---

### Post by oldfred on 2011-03-03
Yes, you can install from another computer and it should work. The biggest issue is usually video drivers, so do not install any proprietary drivers.

---

### Post by BigGreyhound on 2011-03-03
Very cool. Thanks for the reply. We will try it tonight and report back on the outcome.

---

### Post by BigGreyhound on 2011-03-06
No luck so far. Got a few ideas, I have yet to try...

---

### Post by Mark Phelps on 2011-03-07
> **BigGreyhound said:**
> No luck so far...

Not very informative ...

Is the problem that it does not boot when the HDD is installed to the PC?  If so, my guess would be that when you installed Ubuntu to the HDD, it installed GRUB to an existing internal HDD.  Thus, you would NOT have GRUB on the HDD -- which you need to boot.

Usually, you just stick in an Ubuntu CD and restore GRUB from that, but since your PC doesn't have a CD drive, you would have to do this from an Ubuntu Live USB.

---

