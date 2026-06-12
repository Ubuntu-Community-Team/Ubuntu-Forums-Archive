---
title: "Has anyone gotten an rt2500 working?"
date: 2009-07-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by joepotter on 2009-07-25
Has anyone gotten a wireless card based on the rt2500 chip set working under Karmic? If so, how did you do it?

I think there is some problem with the new kernel and, the drivers that are in the kernel.

---

### Post by woodbj on 2009-07-25
I just installed the driver using ndiswrapper and works fine.. the bug report [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/396417](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/396417)

---

### Post by joepotter on 2009-07-26
Thanks for the reply. I am glad to know that someone was able to make the thing work. 

I am looking to use a native linux driver however. After all, that was the reason I bought the darn thing. Back a couple of years ago, an rt2500 chip always worked with Ubuntu. Then something happened and there has been continual trouble ever since. 

By the time it gets worked out, there may not be any of the things left in service. :-)

---

### Post by psyke83 on 2009-07-26
[This]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/396417") bug probably affects you.

---

### Post by andyrogers2008 on 2009-07-26
You can either use the RC3 test kernel if you have got i386 version which Andy Whitcroft provided for me to test which are available [Here]("http://people.ubuntu.com/~apw/lp396417-karmic/")

Or try and install Kernel 2.6.30 which worked for me until this test Kernel got produced.

This bug  is still in RC4 at the moment, but hopefully it should make into Rc5/6 I hope.

---

### Post by joepotter on 2009-07-29
Thanks Andy.

I have both karmic 64 bit and karmic 32 bit on this box and could try your suggestion. But I think I'll just wait and see what happens at this point in time.

I had jaunty on the wife's computer and the rt2500 worked OK (a speed workaround was required) but then an update to the "stable" system took down the rt2500 and I had to go buy her another card. 

I am beginning to think that the rt2500 is cursed.

---

### Post by psyke83 on 2009-07-29
> **joepotter said:**
> Thanks Andy.

I have both karmic 64 bit and karmic 32 bit on this box and could try your suggestion. But I think I'll just wait and see what happens at this point in time.

I had jaunty on the wife's computer and the rt2500 worked OK (a speed workaround was required) but then an update to the "stable" system took down the rt2500 and I had to go buy her another card. 

I am beginning to think that the rt2500 is cursed.

Waiting to see if a bug resolves itself is not a good idea. That kernel that Andy linked to was created specifically to test a fix for the bug I indicated to you (which appears to be what's causing your issue), and it requires feedback on whether it solves the issue or not. 

It may fix the bug reporter's issue, but it may not fix yours (your wirelss card's PCI ID may not match, or something else that's trivial to fix).

---

### Post by joepotter on 2009-07-29
OK, I'll try that kernel and get back to you. I just hope it does not take down the Nvidia card that has been a sore spot for over a year (the 6100) but is now working in karmic.

---

### Post by psyke83 on 2009-07-29
> **joepotter said:**
> OK, I'll try that kernel and get back to you. I just hope it does not take down the Nvidia card that has been a sore spot for over a year (the 6100) but is now working in karmic.

The NVIDIA card may not work, as the restricted drivers may not work correctly with the testing kernel - but that's irrelevant. Switch to the "nv" driver temporarily and see if the wireless works with the test kernel.

If it works, you can revert to the official Karmic kernel and blacklist the rt73 driver as a temporary workaround, while you wait for the official fix.

---

### Post by joepotter on 2009-07-29
I booted into the 32 bit distro on this box. I installed the kernel and headers. I rebooted. No change. iwconfig sees the card, but I can not use it.

:-(

---

### Post by Kow on 2009-07-29
Nm

---

### Post by psyke83 on 2009-07-29
> **joepotter said:**
> I booted into the 32 bit distro on this box. I installed the kernel and headers. I rebooted. No change. iwconfig sees the card, but I can not use it.

:-(

You need to provide more information, and that bug report is the ideal place to do so.

You can try the workaround with the official kernel outlined in [comment #35]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/396417/comments/35").

---

