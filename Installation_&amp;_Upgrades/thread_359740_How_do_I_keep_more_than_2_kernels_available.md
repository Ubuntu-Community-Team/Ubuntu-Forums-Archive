---
title: "How do I keep more than 2 kernels available?"
date: 2007-02-12
forum: Installation &amp; Upgrades
---

### Post by lojic on 2007-02-12
Being able to boot into 2.6.17-10 after the recent kernel update has saved my behind, but I'm concerned that the next kernel update will bump -10 off and I'll be left with -11 and -12.

Does anyone know what I can do to keep -10 around until I can verify that -12 isn't as bad as -11?  Is there a configuration setting to keep N kernels?

Thanks!

---

### Post by Rui Pais on 2007-02-12
Hi, 
I'm not sure but i think that kernel updates do not remove old ones (like it happen with 10->11)

But in any case you can make a backup copy of the debs of that specific version, from /var/cache/apt/archives/:
linux-image-2.6.17-10-generic....deb
linux-headers-2.6.17-10....deb

and if needed:
linux-restricted-modules-2.6.17-10-generic....deb 

Or you can download the debs from: [http://packages.ubuntu.com](http://packages.ubuntu.com).

---

### Post by lojic on 2007-02-12
> **Rui Pais said:**
> Hi, 
I'm not sure but i think that kernel updates do not remove old ones (like it happen with 10->11)

But in any case you can make a backup copy of the debs of that specific version, from /var/cache/apt/archives/:
linux-image-2.6.17-10-generic....deb
linux-headers-2.6.17-10....deb

and if needed:
linux-restricted-modules-2.6.17-10-generic....deb 

Or you can download the debs from: [http://packages.ubuntu.com](http://packages.ubuntu.com).
Thanks. I guess I assumed that it only kept 2 since I only had 2, but maybe the -11 upgrade was the only one I've had since installing 6.10.  The -10 kernel is already gone from /var/cache/apt/archives, but I did see it on the web page you provided - the oldest one I saw was -10.

---

### Post by confused57 on 2007-02-12
There's an option in your /boot/grub/menu.lst for how many kernel entries allowed(default is all):

```
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all
```

---

### Post by lojic on 2007-02-12
> **confused57 said:**
> There's an option in your /boot/grub/menu.lst for how many kernel entries allowed(default is all):

```
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all
```
Thanks, but doesn't that just limit how many are displayed in the grub menu? I was referring to keeping them in the system, not just the boot menu. However, it appears from the previous poster that Ubuntu won't remove any kernels, so I shouldn't be concerned about losing the -10 kernel from a later update.

---

### Post by confused57 on 2007-02-12
Unless you delete your older kernels through synaptic, they're still on your system...you shouldn't have to worry about them being automatically deleted.

---

### Post by lojic on 2007-02-12
> **confused57 said:**
> Unless you delete your older kernels through synaptic, they're still on your system...you shouldn't have to worry about them being automatically deleted.
Ok, then I guess this is the first kernel update for 6.10 since I've never deleted a kernel and I only have -10 and -11. I wonder why people are discussing so many kernel upgrades - maybe the other versions of Ubuntu have more.

---

### Post by confused57 on 2007-02-12
> **lojic said:**
> Ok, then I guess this is the first kernel update for 6.10 since I've never deleted a kernel and I only have -10 and -11. I wonder why people are discussing so many kernel upgrades - maybe the other versions of Ubuntu have more.

It's good to keep a couple of older kernel around, just in case there's a problem booting to the newer ones.

You can open Synaptic Package Manager, click on "Search", enter **linux-image**, this will show the kernels installed on your system...I have a Dapper install that I upgraded from Breezy, which I installed over a year ago...there's still 3 Breezy kernels listed in SPM, as well as 3 or 4 Dapper kernels.   I really need to get around to uninstalling the Breezy kernels.

There's always the possiblity of problems with updates to the xserver or kernel, there's been a couple of instances of this with both...it's probably prudent to wait a day or 2 if you're notified there's an update for either.

---

### Post by lojic on 2007-02-12
> ...it's probably prudent to wait a day or 2 if you're notified there's an update for either.

Just out of curiosity, how does this help? I think it's unlikely that there will be another kernel update to fix the problems anytime soon, so installing 2.6.17-11 now or waiting a week and then installing it will have the same effect, won't it?

I think most people are concentrating on the broken-dependency issue that the Ubuntu folks solved (at least temporarily), but the problems caused by the new kernel itself won't change in a few days I don't think.

So, in my case, even if I waited, I would have still needed to know to install the restricted modules on one machine and do some complicated blacklisting of wireless modules on another machine. I don't think any amount of waiting will change that :(

This is the first kernel update I've had since installing 6.10, so I presume it may be quite a while before another kernel (-12) comes along.

---

### Post by confused57 on 2007-02-12
> **lojic said:**
> Just out of curiosity, how does this help? I think it's unlikely that there will be another kernel update to fix the problems anytime soon, so installing 2.6.17-11 now or waiting a week and then installing it will have the same effect, won't it?

I think most people are concentrating on the broken-dependency issue that the Ubuntu folks solved (at least temporarily), but the problems caused by the new kernel itself won't change in a few days I don't think.

So, in my case, even if I waited, I would have still needed to know to install the restricted modules on one machine and do some complicated blacklisting of wireless modules on another machine. I don't think any amount of waiting will change that :(

This is the first kernel update I've had since installing 6.10, so I presume it may be quite a while before another kernel (-12) comes along.

It helps, because you will know if other people are having issues with the updates, what the issues are, if it was a matter of the update being released with problems(such as unmet dependencies), that will be corrected by the Ubuntu developers...that you should be able to follow  threads specifically addressing the issues and solutions that other people have found or if you need to wait for the corrected release...doesn't happen very often, but it does happen.

By the way, how are things at RTP?  Haven't been down that way in eons...as a grad student, I attended a couple of ASM meetings at Burroughs-Wellcome & Becton-Dickenson and have an ex-bride who was from Raleigh...nice area.

---

### Post by bissej on 2008-05-31
Hi,
I'm confused---is it still the case that only 2 kernels are kept? I just upgraded to 2.6.22-14-generic on a AMD64, and it caused a bunch of problems. I changed my menu.1st to boot from 2.6.20-16-generic, and it seems to work okay again. But I'd like to keep more than 2 kernels around, so I'll have 2.6.20-16-generic (the working one) when a new one comes out.

Looking in Synaptic Package Manager and /lib/modules, it seems that I only have these two kernels. Do I still have more around? If not, can I set it to keep more?

thanks!

---

