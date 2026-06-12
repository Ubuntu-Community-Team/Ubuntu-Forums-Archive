---
title: "How to install Ubuntu safely?"
date: 2011-04-02
forum: Installation &amp; Upgrades
---

### Post by csh on 2011-04-02
I just take back my Netbook from warranty claim. The hard disk and motherboard has been replaced.

My netbook is using internal Ralink RT3090 Wireless Adapter. The module(driver) bundled with Ubuntu 10.04 and 10.10 consist of a bug that cause the whole Netbook to freeze when unloading the module. That mean, for each shut down or reboot, my Netbook will freeze. Even at the last stage of Ubuntu installation by using Wubi, my Netbook will still freeze. Every time when this happen, I have to do hard reboot (press the power button to turn off the Netbook and then turn on again). This caused the damage to my Netbook.

The bug of the module has been fixed in latest version of Wireless modules downloaded from [http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download) . However, the version bundled with Ubuntu is old version that still having the bug.

I need to reinstall Ubuntu on my Netbook. I need to use it immediately. I cannot wait until the next version of Ubuntu to be released. But, I do not want my Netbook to freeze again. I do not want my Netbook to be damaged again.

I only want to use Wubi to install Ubuntu because I do not want to do anything that affect the partitions in my hard disk. And, I do not want to run Ubuntu in virtual machine because Windows 7 itself already used a lot of memory.

So, what am I going to do to install Ubuntu safely without facing freeze? Please advice.

---

### Post by csh on 2011-04-03
bump

---

### Post by Dutch70 on 2011-04-03
Sounds like you've got it all figured out. You said the bug was fixed & that you want to do Wubi install. 

I don't think anyone can guarantee you that your laptop isn't going to freeze. However I can tell you how to avoid a hard reboot. 

To safely reboot your computer...
While holding down (Alt+SysRq) ,press the following keys in order with a slight pause between each key.
R-E-I-S-U-B
When you press the "B" key your computer should reboot. You may have to release the Alt+SysRq keys before releasing the "B" key. 

If you want to shut down without a reboot, replace the "B" with an "O".

[[COLOR="Red"]http://www.matejunkie.com/magic-sysrq-reisub/[/COLOR]]("http://www.matejunkie.com/magic-sysrq-reisub/")

---

### Post by Mark Phelps on 2011-04-04
Don't mean to dampen your enthusiasm ... but a Wubi install will end up using the same device drivers as a separate partition install.

All Wubi uses Windows for is to do the initial boot.  After that, you're running the same Ubuntu as usual.

So, given the known driver bug, there's every likelyhood that Ubuntu installed via Wubi is going to suffer the same problems.

---

