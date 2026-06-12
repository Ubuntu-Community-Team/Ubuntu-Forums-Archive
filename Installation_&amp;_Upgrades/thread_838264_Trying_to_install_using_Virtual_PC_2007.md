---
title: "Trying to install using Virtual PC 2007"
date: 2008-06-23
forum: Installation &amp; Upgrades
---

### Post by Haulnbones on 2008-06-23
It opens the .iso, I choose English, hit Install UBUNTU, then I get

An Unrecoverable processor error has been encountered.
The Virtual Machine will reset now.

Anyone else had a problem with installing Ubuntu on VPC2007?  

Thanks,

Bones

---

### Post by ros256 on 2008-07-22
I received the same message. However I think I downloaded the Live installer version rather than the alternate text-based installer. You probably did the same. Try it with the alternate installer.

---

### Post by Tommygib on 2008-08-28
Hi Haulnbones,
I am experiencing the same difficulty.  I have tried to install the alternate iso as you suggetsed and even get to the "loading linux kernal" screen when the by now infamous "unrecoverable error" message reappears.

I have Ubuntu dual booted onto the system with Vista and it runs fine. So I am at a loss to know why it fails to run in vpc2007.

Any other pointers would be greatly appreciated.

Tommy.

---

### Post by buck2825 on 2008-09-24
I have been having the same problems with my VPC2007 install.  I have tried all the text edits i can find and different iso.  is i tried an odd one, installed 6.06 LTS that works great.... installed the updates and then hit upgrade everything took great now for the real test.  REBOOT.  processor error, reset.  

i'm so glad i just wasted 3 hours. 

Virtual PC 2007 both with and without SP1

---

### Post by cbolwerk on 2008-09-25
I had the same problem. After searching for a long time, I came across this, which worked for me.

Add "noreplace-paravirt" to the command for installation.

---

### Post by buck2825 on 2008-09-29
OK call me a quiter if you want, but VMware is awsome USB even works 8.04.1 installed great and runs great.  no cool graphic stuff like AWN or springy windows but its still ubuntu.

---

