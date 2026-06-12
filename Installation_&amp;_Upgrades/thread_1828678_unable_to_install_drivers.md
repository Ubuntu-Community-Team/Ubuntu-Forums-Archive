---
title: "unable to install drivers"
date: 2011-08-19
forum: Installation &amp; Upgrades
---

### Post by bradlees on 2011-08-19
I am getting the following message when I try to install drivers that I think are necessary to run ubuntu on my laptop:

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.

What to do?

---

### Post by Bucky Ball on 2011-08-19
Have you got Ubuntu installed? Does it run from the LiveCD? If it does then you are good to go. 

Is there a specific problem here? Could you name the drivers you are trying to install? Have you tried installing them using Synaptic Package Manager?

---

### Post by Sef on 2011-08-19
> Bucky Ball: Could you name the drivers you are  trying to install? Have you tried installing them using Synaptic Package  Manager? 	

I believe they are MS fonts based on this last line:

> SystemError: E:I wasn't able to locate file for the  ttf-mscorefonts-installer package. This might mean you need to manually  fix this package.

MS fonts can be installed through Synaptic - just make sure that multiverse is enabled. 

What version of Ubuntu are you using?

---

### Post by bradlees on 2011-08-21
I am using 11.04. I've got it installed, but I think that I have a problem with my video card driver?? maybe. 

I can only boot in recovery mode on the low-res option. Everything works fine there, but if I try to boot into the regular version, all I get is the user and password screen. From there it does nothing.

My laptop has a nvidia card, g73 geforce 7600. I downloaded the linux drivers from their website, but when I try to install them on ubuntu, in recovery mode, I cannot do it. It says ubuntu can't run the file, or its not in asci or something to that effect.

---

### Post by Bucky Ball on 2011-08-21
When you're in with low-res, under system>Admin>Additional Drivers, is there one for the Nvidia?

---

### Post by bradlees on 2011-08-21
There is. I installed the recommended one, rebooted, and still no luck with getting regular ubuntu to boot. Had to go into recovery mode, low res again

says the driver is activated but not in use

---

