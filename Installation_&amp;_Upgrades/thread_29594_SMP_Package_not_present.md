---
title: "SMP Package not present"
date: 2005-04-25
forum: Installation &amp; Upgrades
---

### Post by grouchomc on 2005-04-25
I have ubuntu installed on a Dell Precision 410, with dual PII450s.  The device manager shows the 2 processors in BIOS.  In searching through the forums, I tried to run:
sudo apt-get install linux-image-386-smp
but got error:
E: Couldn't find package linux-image-386-smp
If I open Synaptic and perform a search on smp, this smp kernel is not shown among the result.  Is there a way for me to download the package so that it will show up correctly?

Thanks!

---

### Post by alastair on 2005-04-25
There should be :

linux-image-2.6.10-5-686-smp

etc.

what's available : apt-cache search linux-image
what do I have : dpkg -l "*linux-image*"

---

### Post by grouchomc on 2005-04-25
Here's what I get.

thanks!

||/ Name           Version        Description
+++-==============-==============-============================================
un  linux-image    <none>         (no description available)
un  linux-image-2. <none>         (no description available)
ii  linux-image-2. 2.6.10-34      Linux kernel image for version 2.6.10 on 386
ii  linux-image-38 2.6.10-7       Linux kernel image on 386.

---

### Post by Levander on 2005-04-25
The meta package name for the 686 smp kernel is linux-image-686-smp, I believe it's more ypical to install the kernel meta-package than the specific kernel version package.  If you install the meta-package, when they update the kernel version for their 686-smp kernel, you get the new kernel.  If you install the specific kernel version package, the kernel doesn't get updated.

---

### Post by grouchomc on 2005-04-25
So, to clarify, the metpackage I installed from the install CD did not have the smp package included, but it should be included at the next update, and I can install it then?

---

### Post by Levander on 2005-04-25
Did the Pentium 386 cpu support smp?  I'm not sure it did.  

Anyway, a 686 is a Pentium II, which is what you've got.  What the 686 means is that it was compiled with compiler flags that optimize it for features that were first available in that processor.  So, the optimizations work on all subsequent processors as well.

Why would you want a 386 kernel when you've got a 686 chip?  If you're going through the trouble of installing a kernel anyway?

---

### Post by grouchomc on 2005-04-26
The default download of the install CD is i386; I was not given a choice (that I recall) to install a 686 kernal.  I've added the internet sources to /etc/apt/sources.list as listed in:
[http://www.ubuntuguide.org/temp/#extrarepositories](http://www.ubuntuguide.org/temp/#extrarepositories)
And ran the update, but still get:
root@lar:/home/user #  sudo apt-get install linux-686 Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-686
root@lar:/home/user # sudo apt-get install linux-image-686-smp
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-image-686-smp

Thanks!

---

### Post by Levander on 2005-04-26
Well, you got the right link into the ubuntuguide for what you're trying to do.  But, I think something's wrong with your configuration of apt.  I would double check your sources.list.  Although, possibly there are other things you would have to configure with apt, but you probably wouldn't have to. I never have.

The linux-686 and linux-686-smp packages are in those online repositories.  I don't know if they are on the CDROM or not.  You've got to look at your apt configuration.

Also, in an earlier post I called the 686 smp kernel package by the wrong name, which apparently you tried to use.  The correct name is linux-686-smp.  Sorry, my mistake.  However, if you didn't find linux-686, you're probably not gonna find linux-686-smp either.

Try posting your sources.list here.  I'll look at it and see if I can find anything.  It's late here though, it might be tomorrowbefore I can.  Also, if you do post it, make sure to use the "code" tags feature of this forum.  In the editor to create new posts, it's a # icon just above text box that you edit in. You are supposed to have the sources.list text inside the tags.

---

