---
title: "Adding ram after install - any kernel changes?"
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by stream303 on 2008-05-03
I'm not a kernel guy, and I have been wondering about something:

Let's say that I have installed Ubuntu with only 256 mb of memory, and after a good install, I later upgrade the ram to 1gb.

Normally, I know to change the size of my swap file to be in accordance with this new amount of ram, but my question isn't about the swap file size - it is about the default kernel configuration files.

During installation, does the Ubuntu installer make certain configurations for the kernel based upon what amount of ram it sees at first, and does it later detect any additional ram after the fact and change any aspects of the kernel automatically?

Or is it the case that even though everything seems to work ok with 1gb ram, the kernel configurations are still stuck at what I first used to install with, ie 256mb ram?  (it's not the amount, but any kernel configuration files that I'm wondering about)

I don't know what files to look at to see if the kernel is aware of the additional memory, other than just the fact that there is now more to use, which I verify with *free -m* on the commandline.

Any pointers would be great!

---

### Post by Herman on 2008-05-03
Well in my computers that I have here I just whack in another stick of RAM and power up and boot and away I go.
I don't think there's anything special to do.
The BIOS should detect the RAM during P.O.S.T., and as far as I know, the kernel will just automatically use whatever RAM is there.
I have one old computer that I installed Ubuntu in when I only had 64 MB of RAM, and now I have 256 + 127 MB in it and it's working a lot better. I didn't do anything complicated at all.

Regards, Herman :)

---

### Post by stream303 on 2008-05-03
Thanks Herman - yeah, the systems always seem to like the additional ram for sure, but I was thinking along kernel sysctls and the like.

For instance, if I do a:

```
sudo sysctl -a | sort | less
```

I see all sorts of kernel parameters, and wonder if the system is still using old values based on my original ram, or if these values are being automatically changed, like max-threads etc?

Maybe I should have paid more attention to this during install prior to adding ram. :)

---

