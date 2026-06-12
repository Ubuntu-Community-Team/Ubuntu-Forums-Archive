---
title: "boot space error on update"
date: 2012-10-13
forum: Installation &amp; Upgrades
---

### Post by janetk on 2012-10-13
I cannot install the latest update on Ubuntu 10.04 and get an error message about lack of boot space. I have tried the suggestions (empty trash and sudo apt-get clean) but I still have the error. When created my boot was 197 mb. What should I do next?

---

### Post by Wim Sturkenboom on 2012-10-13
Clean it out by removing some old kernels. Do a search on the web how to do so. One that I saw a while ago is [http://tuxtweaks.com/2009/12/remove-old-kernels-in-ubuntu/](http://tuxtweaks.com/2009/12/remove-old-kernels-in-ubuntu/)

---

### Post by efflandt on 2012-10-13
If you are still running 10.04 and have never removed old kernels, you could have more than a dozen old ones lying around doing nothing.  How many kernel versions are listed in your grub menu?

I have an old 10.04 system I do not run much and had not cleaned house lately, and it had a total of 13 kernels.  So I removed 10 of them leaving the 3 most recent.

If you do not trust a script to make sure it does it right, you can do it yourself.

Assuming you are booting the most recent kernel you do have, to find out its version in a terminal do: **uname -r**

Go to **Administration** > **Synaptic** and enter **linux** in Quick search.  Scroll through the list and any green boxes in any **linux-generic**, **linux-headers**, or **linux-image** more than several versions older than you are running as "Mark for complete removal".  When you get them all Apply.  Note that files for kernel versions are not necessarily in numerical order, and do not remove other files common to all linux versions.

For example my 10.04 is running 2.6.32-42, so I removed linux header, image or generic files from 2.6.32-39 or earlier.  Now grub only shows 3 kernels -40, -41, and -42.

---

