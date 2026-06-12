---
title: "Cannot upgrade from 9.04 to 9.10"
date: 2010-12-07
forum: Installation &amp; Upgrades
---

### Post by teddiebeer on 2010-12-07
I'm not sure if there is a similar problem to mine somewhere. I am still on 9.04. On all my machines an option to upgrade to 9.10 is available and I have done them. On the one machine I have a problem. The update manager does NOT offer me an upgrade to 9.10. 

I have tried everything I know but still... bump.

I have downloaded an ISO for 10.04 but when I use that disk to boot up the machine from scratch, it runs for a while then stops and then just sits there and nothing happens. I have in fact left the machine for more than 1 hour and still nothing.

Something else, I inserted the 10.04 disk whilst the machine was on 9.04. Suddenly if I try any update/upgrade the machine asks me for the 10.04 disk.

Is there no way I can at least get the machine to upgrade to 9.10. I am weary to attempt an upgrade to 10.04 or 10.10 as I think my machine might be a little small on the RAM side of things.

Any help or ideas.:popcorn:

---

### Post by sikander3786 on 2010-12-08
> 
Something else, I inserted the 10.04 disk whilst the machine was on 9.04. Suddenly if I try any update/upgrade the machine asks me for the 10.04 disk.

That suggests as if your CD-ROM has been added as a software source. Go to System > Administration > Software Sources > Other Software Tab and disable the CD-ROM there. Then try these commands from Applications > Accessories > Terminal and post the output if un-successful.

```
sudo apt-get update && sudo apt-get upgrade
```

```
sudo do-release-upgrade
```

[https://help.ubuntu.com/community/KarmicUpgrades](https://help.ubuntu.com/community/KarmicUpgrades)

Good Luck!

---

