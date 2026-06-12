---
title: "How to upgrade kernel to a new version?"
date: 2007-06-16
forum: Installation &amp; Upgrades
---

### Post by Arrive on 2007-06-16
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117314](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117314) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi there, 

I have encountered the infamous "kinit: no resume image" found problem after I upgrade from Edgy to Feisty last night. 

From [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117314](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117314) I get linked to [http://www.ubuntu.com/usn/usn-470-1](http://www.ubuntu.com/usn/usn-470-1), which states:

> The problem can be corrected by upgrading your system to the following package versions: 
Ubuntu 7.04: 
linux-image-2.6.20-16-386 2.6.20-16.29 
linux-image-2.6.20-16-generic 2.6.20-16.29 
linux-image-2.6.20-16-hppa32 2.6.20-16.29
linux-image-2.6.20-16-hppa64 2.6.20-16.29
linux-image-2.6.20-16-itanium 2.6.20-16.29 
linux-image-2.6.20-16-lowlatency 2.6.20-16.29 
linux-image-2.6.20-16-mckinley 2.6.20-16.29 
linux-image-2.6.20-16-powerpc 2.6.20-16.29 
linux-image-2.6.20-16-powerpc-smp 2.6.20-16.29 linux-image-2.6.20-16-powerpc64-smp 2.6.20-16.29 
linux-image-2.6.20-16-server 2.6.20-16.29 
linux-image-2.6.20-16-server-bigiron 2.6.20-16.29 
linux-image-2.6.20-16-sparc64 2.6.20-16.29 
linux-image-2.6.20-16-sparc64-smp 2.6.20-16.29 

After a standard system upgrade you need to reboot your computer to effect the necessary changes. 

However, when I do 
> sudo apt-get install linux-image-2.6.20-16-generic,
it tells me that "the newest version is already installed", but when I use "dpkg -l" to check, it shows that the version is still "2.6.20-16.[COLOR="Red"]28[/COLOR]", so how do I specify to let apt-get to install the 2.6.20-16.[COLOR="Blue"]29[/COLOR] kernel for me?

Thanks in advance!

---

