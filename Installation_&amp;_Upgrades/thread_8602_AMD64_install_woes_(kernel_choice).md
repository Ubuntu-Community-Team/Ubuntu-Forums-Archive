---
title: "AMD64 install woes (kernel choice)"
date: 2004-12-19
forum: Installation &amp; Upgrades
---

### Post by Dylanby on 2004-12-19
Past:
Last week I put together a new system based off of the MSI Neo2 Platinum mb & AMD64+ 3200.

I tried to install the x86 version from the shippit cd's but they wouldn't even start. I then downloaded the AMD64 iso (verified the md5 sum) & installed Ubuntu into a dual boot setup. The install partition(s) were logical partitions.

I wasn't sure about the onboard nics so I installed one I knew worked in Linux (an Intell Pro100/M). The installer had set my monitor's horizontal & vertical scan ranges wrong leaving me with "no screens". I was able to fix this using "dpkg-reconfigure xserver-xfree86".

Present:
Due to problems with "that other OS" I'm now giving Linux my entire hard drive & have blown away everything. Having verified that the onboard nics work in Linux I took out the Intell (to allow for better cooling for my vid card).

So now I'm trying to install onto the same hardware (minus one nic), into primary partitions (vs logical), using the same cd that worked last week...no dice.

I've tried different install options & they all end the same. Last week the installer gave me a choice of three kernels & I chose the "linux-amd64" & the install continued. Now I only have the "linux-amd64-generic" kernel to chose from which doesn't work (I can't remember the 3rd kernel that I was offered).

Anyways...I'm off to try a net install (too impatient to wait for a reply), but obviously the installer could use a little more resiliency for us noobs.

Posted via live-cd.

---

### Post by gkhewitt on 2004-12-19
[QUOTE=Dylanby]
I've tried different install options & they all end the same.
[/QUOTE]

Please elaborate... how do they all end..?

Posting any error messages would be helpful in helping us help you! When the error occurs during install (assuming its during install) you can cycle through the different terminals, tty2 tty3 tty4 etc by using CTRL + F2, F3, F4 etc
HTH

---

