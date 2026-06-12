---
title: "X-Server Problems"
date: 2007-02-09
forum: Installation &amp; Upgrades
---

### Post by Mencius on 2007-02-09
I Installed Ubuntu V5.10 on my PC and when the installation was complete an error came up saying the X-Server wasn't configured correctly. I looked through the forums and found the command to Manually set up the X Server, I got to the part where you pick the Colour in bits for your moniter but then that comes up the command line pops up below it so I cant pick any of the options.

My Hardware:

Core 2 Duo E6600
2 Gigs Ram
Nvidia 7950 GT
250 Gig hard Drive ( 10 Gig Linux Partition)


When I look at the error for the X Server it says the fatal error is no Moniter detected, My moniter is connect through a DVI/VGA adapter.

Is my graphics drivers the problem?

Any help would be appreciated.

---

### Post by Theimon on 2007-02-09
Did you install the nVidia drivers?
```
sudo aptitude install nvidia-glx
```

After that installation you may have to do the following again:
```
sudo dpkg-reconfigure xserver-xorg
```

And maybe, seeing the hardware you're using, why not try Ubuntu 6.06 or 6.10? It has better hardware support out of the box than 5.10.

---

