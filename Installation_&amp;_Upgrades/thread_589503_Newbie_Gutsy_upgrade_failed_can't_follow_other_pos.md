---
title: "Newbie: Gutsy upgrade failed can't follow other posts advice due to ACPI issue"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by LAD29 on 2007-10-24
Hi,

I tried to run an internet upgrade to 7.10 from 7.04, however it hung soon after completing fetching the packages etc.

Having had no choice but to restart my laptop I can through grub (which shows as 7.10 and various kernels to choose from) get to a root prompt.

However, I cannot get the gui to run via startx (no errors) just partially loads until a sort of background appears and nothing else.

Anyway, having read various posts I tried to run various sudo apt-get commands at the root prompt but receive the following error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

So, following the advice of the error message and the numerous posts I've read I've tried the following several times

sudo dpkg --configure -a

Herein lies the problem:

Everything starts ok but then stops every time at:
Setting up acpid (1.0.4-5ubuntu8 )
*  Loading ACPI modules

I recall from ages back when I first installed 7.04 that I had ACPI issues when trying to start Ubuntu and somehow (I can't recall) found a fix online to resolve it.  It seems it's back in some way and I don't know how to resolve this to try and fix my 7.10 install so I can get a gui.

I've seen something about recompiling the acpi config (or words to similar effect) but I've no idea what this means or how to go about it. (I'm very much a linux/ubuntu newbie and am ultimately 'simply' trying to set up a local test webserver with apache/php/mysql).

I've also tried the following:
sudo /etc/init.d/acpid stop
sudo dpkg --configure acpid
sudo dpkg --configure -a

but when running the 2nd command exactly the same happens.

Can someone point me in the right direction of what I need to be looking at please?

For info, my laptop is a recently new Samsung Q45 with all the latest BIOS updates and drivers installed.

I'm thinking that maybe if I can conquer the ACPI issue I can get back on track with the dpkp --configure -a command, or is there a way to run the command whilst excluding the ACPI element/issue?

Cheers.

---

