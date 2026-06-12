---
title: "xserver-xorg is broken..."
date: 2006-09-23
forum: Installation &amp; Upgrades
---

### Post by ar3nbe on 2006-09-23
Before you start flaming me, i have searched, and tried various solutions that were posted, but none of them have worked :(.

I am running Ubuntu 6.06 with xserver version 10.4. I have updated to the latest Kernel, and since then, i have had the error message of "Failed to start xserver, bla bla bla). 

I then tried to reconfigure it, with the error message of "xserver-xorg is broken or not fully installed). Prior to the latest update, all was working fine.

I am totally lost, any help would be greatly appreciated. Thankyou in advance :)

---

### Post by tseliot on 2006-09-23
Do you use the Nvidia or the ATI driver?

---

### Post by ar3nbe on 2006-09-23
Nvidia, Graph cards is a mx440

---

### Post by tseliot on 2006-09-23
> **ar3nbe said:**
> Nvidia, Graph cards is a mx440

Read this:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#WHAT_HAPPENS_IF_YOU_CHANGE_YOUR_KERNEL_OR_IF_YOUR_KERNEL_IS_UPDATED](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#WHAT_HAPPENS_IF_YOU_CHANGE_YOUR_KERNEL_OR_IF_YOUR_KERNEL_IS_UPDATED)

---

### Post by K.Mandla on 2006-09-23
As a side note, I use a 440 Go in my laptop, and it needs the nvidia-glx-legacy driver. I get the BSOD when I try to use the nvidia-glx driver.

Curiously, I use a straight 440 in my desktop, and it uses the nvidia-glx driver.

Any chance you could flip-flop drivers?

---

### Post by recon69 on 2006-09-23
You might want to read this 

[http://ubuntuforums.org/showthread.php?t=257459](http://ubuntuforums.org/showthread.php?t=257459)

Could have somthing to do with it.

---

### Post by ar3nbe on 2006-09-24
Still no luck :(. Perhaps uninstalling, and reinstalling xserver may fix the problem ? If so, what are the commands, lol

---

