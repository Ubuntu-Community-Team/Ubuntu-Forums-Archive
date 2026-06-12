---
title: "Removing Old Kernel Package"
date: 2005-04-19
forum: Installation &amp; Upgrades
---

### Post by Levander on 2005-04-19
Well, I'm about to upgrade from Warty to Hoary, and am worried about one thing.  I'm about to run out of space on my /boot partition, where the kernels go.  For some strange reason, when I installed Warty, I thought it was a good idea to only have 15M for my /boot partition, and now I only have like 250K left in that partition.

I currently have two kernels installed in there.  The 386 kernel, and the 686-smp kernel.  I'm running the 686-smp kernel.  So, I thought I could use remove the 386 kernel in case the upgrade wants to use more space in that partition.  

So, looking around, I figure out that I probably want to uninstall two packages.  I test uninstalling them with this command:

sudo apt-get --simulate remove linux-image-2.6-386 linux-image-2.6.8.1-3-386

However, the output of that command says that it will install the linux-image-2.6.8.1-5-386.  What the hell?  That's another kernel image!  I just want to get rid of the one I got.

I assume that the package maintainer was worried that if I uninstall one kernel, he better put another one out there so that my machine doesn't go without a kernel...

But, I installed the new kernel first, and wanted to come back and remove the old one later.

How do I get rid of the 386 kernel?

---

### Post by az on 2005-04-19
I think you should use an apt tool like synaptic or aptitude.  I think you need to have a linux-image metapackage that points to the most recent kernel in the desired architecture to ensure that you get security updates.

You would need something like linux-image-2.6-686-smp or something, instead of just linux-image-2.6.8.1-5-686-smp.

---

### Post by Levander on 2005-04-19
Looks like I've got two meta-packages, linux-386 and linux-2.6-386.  I just apt-get remove'd them both.  However, when I apt-get --simulate remove linux-image-2.6.8.1-3-386, it stills says it's going to install linux-image-2.6.8.1-5-386.

I'm looking at synaptic now to try to figure out if I can uninstall that kernel without installing a new one.

What about dpkg --purge linux-image-2.6.8.1-3-386?  Does dpkg run through all the dependency things that apt-get does? I don't see any simulate option in the dpkg man page, so I'm not sure.

---

### Post by Levander on 2005-04-19
Finally found the answer.

apt-cache show linux-image-2.6.8.1-3-386

Clearly prints out that that package contains a script to ensure that the system is not left in an unbootable state when you remove it.  I assume that is why "apt-cache --simulate remove" was saying it was going to install a more up-to-date kernel if I removed that one.

So, to get around this and remove an unused kernel package:

sudo dpkg --purge --force-remove-essential linux-image-2.6.8.1-3-386

However, at first this gave me a depency error on some restricted modules package, running these commands, in this order, got rid of that message:

sudo dpkg --remove linux-restricted-modules-386
sudo dpkg --remove linux-restricted-modules-2.6-386
sudo dpkg --remove linux-restricted-modules-2.6.8.1-3-386

Have to do it in that order, because the 1st package is a meta-package that depends on the 2nd.  You get more dependency problems if you don't do it in that order.  The same goes with the second package depending on the third.

After you remove those packages, can remove the unwanted kernel package with the command above.

---

