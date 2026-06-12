---
title: "64 bit on my laptop?"
date: 2014-06-22
forum: Installation &amp; Upgrades
---

### Post by RyeMan on 2014-06-22
Should I install 32 or 64 bit Ubuntu on my Toshiba Satellite 355D-s7901 laptop (actually, my 15 year old sons)?  It will be used mostly for gaming.

Here are the specs:
AMD Turion X2 RM72 (2 cpu's), 2.1 GB
2800 RAM
1400 video memory
165 MB HD

Any opinions will be greatly appreciated.

---

### Post by Bucky Ball on 2014-06-23
*Thread moved to **Installation & Upgrades**.*

64bit. I.e. the AMD64 version.

---

### Post by LastDino on 2014-06-23
Always go with the best architecture supported unless you're terribely short on RAM (Less than 1GB). Here x64 is good choice.

---

### Post by RyeMan on 2014-06-23
> **Bucky Ball said:**
> 

64bit. I.e. the AMD64 version.

The AMD64 version says "MAC". Mine is not a Mac, use it anyway?

---

### Post by LastDino on 2014-06-23
If you don't have uefi, then sure. Which is more than likely. But if you haven't downloaded yet, please stick with AMD64.

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

---

### Post by Bucky Ball on 2014-06-23
AMD64 version. I have no idea where you're downloading the Mac version. Is that what it offers you when you choose to download from here?

[http://www.ubuntu.com/download/desktop/thank-you?country=AU&version=14.04&architecture=amd64](http://www.ubuntu.com/download/desktop/thank-you?country=AU&version=14.04&architecture=amd64)

---

### Post by RyeMan on 2014-06-23
> **Bucky Ball said:**
> AMD64 version. I have no idea where you're downloading the Mac version. Is that what it offers you when you choose to download from here?

[http://www.ubuntu.com/download/desktop/thank-you?country=AU&version=14.04&architecture=amd64](http://www.ubuntu.com/download/desktop/thank-you?country=AU&version=14.04&architecture=amd64)

It's the bottom choice here:
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

I assume the choice that just says 64 bit is the one for Intel.

Just to follow up, I installed the Mac 64 one and it's working great :). Still not sure why it says Mac though...Mac is os not hardware.:confused:

BTW, thanks for all the help!

---

### Post by Bucky Ball on 2014-06-23
Well, that's good, but I have no idea why you're using the 64bit Mac image when you don't have a Mac. Why didn't you just use the regular 64bit image?

Either way, it's working so please mark the thread as solved to help others and start new threads with descriptive titles and in the appropriate forums for any further support requests. 

Good luck. 

PS: Yes, the AMD64 is what you would normally use ...

---

### Post by RyeMan on 2014-06-23
> **Bucky Ball said:**
> I have no idea why you're using the 64bit Mac image when you don't have a Mac. Why didn't you just use the regular 64bit image?

Because I assumed it was for INTEL.  I really wasn't sure which of the two 64 bit choices to use, the first one said **64 bit** and the other one said **64 bit Mac (AMD64)**...well I don't have a Mac but I do have AMD64.   It would be helpful to have some explanation on the one that just says **64 bit** (is it for Intel?)  Working fine thus far.

Thanks again

---

### Post by LastDino on 2014-06-24
Its not for just Intel, actually, the name of the file when you download the x64 only has AMD in it, and no that doesn't mean its for just AMD either. There are historical reasons for that. What you need to know is that it works on both.

Difference between MAC (AMD64) and just AMDX64/x64 wont be apparent to you as you don't have MAC or UEFI at all, it was designed to work with MAC systems UEFI as many of the people using MAC had problem installing simply AMDx64 on their systems and then Ubuntu came up with new installation image with some tweaks to incorporate with those MAC systems better. 

Some do have success using normal AMDx64 on MAC as well, but that hasn't been the common scenario.

From what I know.

---

### Post by deadflowr on 2014-06-24
> **RyeMan said:**
> Because I assumed it was for INTEL.  I really wasn't sure which of the two 64 bit choices to use, the first one said **64 bit** and the other one said **64 bit Mac (AMD64)**...well I don't have a Mac but I do have AMD64.   It would be helpful to have some explanation on the one that just says **64 bit** (is it for Intel?)  Working fine thus far.

Thanks again

All 64-bit versions of Ubuntu will be marked as AMD64.
It's a naming scheme.
It works for both intel and amd processors.

---

