---
title: "VMWare: Install kernel headers failed"
date: 2011-08-28
forum: Installation &amp; Upgrades
---

### Post by ritchie-w on 2011-08-28
Hi,

I try to install the kernel header of 2.6.35-30-generic,
but there are no longer in the reposit.

Where can i get these header files, because i need them to get the vmware player to (recompiling).

Thanks for help
R.

---

### Post by MAFoElffen on 2011-08-28
> **ritchie-w said:**
> Hi,

I try to install the kernel header of 2.6.35-30-generic,
but there are no longer in the reposit.

Where can i get these header files, because i need them to get the vmware player to (recompiling).

Thanks for help
R.
Have you checked here?
[v2.6.35.3-maverick/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.35.3-maverick/")

---

### Post by ritchie-w on 2011-08-29
Hi,

it does not work.

See picture

The other kernel did not fit the installation conditions.

Thanks for help

R.

---

### Post by MAFoElffen on 2011-08-29
> **ritchie-w said:**
> Hi,

it does not work.

The other kernel did not fit the installation conditions.

R.2 Suggestions:

First Suggestion:
```

[I]sudo apt-get install linux-headers-'uname -r'
[/I]
```Would try to install header files for a running kernel version.  

Second Suggestion:
If still not found and not available... maybe you should upgrade your kernel to one that is supported.

Edit-- You haven't mentioned the Ubuntu Release you were working from... But I had another idea.  If you went into synaptic, you could turn on backports and see if you could find it(?)

---

### Post by ritchie-w on 2011-08-29
Hi,

I already tried this, and I get the message, that this kernel version is no longer in the reposit.

I already try to upgrade to the actual (at least higher kernel), but since I have to upgrade my mainboard because of damaged grafic onboard card, the kernel is crashing during the start up and rebooting the system. 
No chance to install or analyse anything (with my knowlege of linux).

I still waiting for a little help to solve this item. See thread:

[http://ubuntuforums.org/showthread.php?t=1828728](http://ubuntuforums.org/showthread.php?t=1828728)

Thanks for help

Edit: I am using 64Bit kUbuntu 11.04 and 32Bit kUbuntu 11.04

R.

---

### Post by MAFoElffen on 2011-08-30
> **ritchie-w said:**
> Hi,

I already tried this, and I get the message, that this kernel version is no longer in the reposit.

I already try to upgrade to the actual (at least higher kernel), but since I have to upgrade my mainboard because of damaged grafic onboard card, the kernel is crashing during the start up and rebooting the system. 
No chance to install or analyse anything (with my knowlege of linux).

I still waiting for a little help to solve this item. See thread:

[http://ubuntuforums.org/showthread.php?t=1828728](http://ubuntuforums.org/showthread.php?t=1828728)

Thanks for help

Edit: I am using 64Bit kUbuntu 11.04 and 32Bit kUbuntu 11.04

R.
Seems that you found your answer.  IMHO- I doubt that you are going to be able to solve this problem until you solve the original problem that you just linked to...

The key is your "SandyBridge Chipset."  I'm thinking, since the kernel you are using does not have available header files, you are pretty much screwed with that as a deadend. So, if it were me, I'd be trying to get another kernel working that does have header files available... Make sense?

Unfortunatley, I haven't had much luck gettign Sandy Bridge Graphics running on Ubuntu pasted the basic (first) chipset.  As I remember, the Sandy Bridge is another hybred switched graphics chipsets, where X see's the first chipset and has problems seeing past it to the second chipset.  I helped someone get it going with 11.04 about 34 months ago, but we got it going with the first (the lower res) of the 2 chipsets.

Ubuntu 10.10 said the Sandy Bridge was supported and certified, but I haven't see that for 11.04.

I'll try to jump over to your other thread and help out there.

---

