---
title: "Clean install or upgrade?"
date: 2014-04-12
forum: Installation &amp; Upgrades
---

### Post by modig-lars on 2014-04-12
Hi,

I have had some issues with Ubuntu lately. Everything works more or less fine, but I always after log in get this system error pop up. Tried to looked into it but it seams like it's different things all the time. 

I had an issue with Grub (I guess) so my computer wouldn't boot up before, but I was able to log in via an old kernel and from that one I upgraded to a new Ubuntu release, therefore I'm now running 12.10. But next week I  was planning to go for next LTS 14.04. So what do you think I should do. Is it enough with just upgrade or should I do a complete new install? And in case I do a complete new install what to do with my Home. Should I copy all my hidden files also, or will they maybe mess up everything?

I looked in the gParted and noted that I didn't have any mount point to Home so I guess that I need to erase everything and start from the beginning (I have my complete home backed up on my NAS) if I want to do a clean install.

Another thing is that I also added quite a lot of "software sources" that I do not know what they do. Is it possible in an easy way to find out? For example, this one I can understand is for wine ([http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu)), but this is a bit harder...([http://ppa.launchpad.net/nemh/gambas3/ubuntu](http://ppa.launchpad.net/nemh/gambas3/ubuntu)).

Thanks,

Lars

---

### Post by mörgæs on 2014-04-12
Please see the link in my signature.

---

### Post by Warren Hill on 2014-04-12
> **mörgæs said:**
> Please see the link in my signature.

+1 

Before any major change to your system backup.  Since you are already having some problems I'd definitely recommend a clean install and restore your personal files from the backup.

But test it first from a live USB or DVD to make sure all the hardware works as expected.

---

### Post by modig-lars on 2014-05-04
OK finally done...

Everything went perfect tested first on a laptop before doing on my desktop. Good idea but sadly my laptop could only install the 32 bit version so I still got some issue with the 64 bit version on my desktop. It took a while to get the BankID working, and installing the webapp Linkedin froze the complete computer, so I uninstalled that again...

But the boot time is rapidly fast strangely the loggin time feels longer? And it sometimes take long time before you can open nautilus, don’t know if that is due to I auto mount my NAS at bootup in fstab.

BR,

Lars

---

