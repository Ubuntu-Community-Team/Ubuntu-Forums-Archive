---
title: "Install/upgrade problems"
date: 2008-02-25
forum: Installation &amp; Upgrades
---

### Post by sonshadowcat on 2008-02-25
I downloaded the latest AMD version but for some reason it does not even start up the install process. I hit the install button and the PC simply freezes up and does nothing. The i386 version however installs fine. Any ideas on that?


My other major problem is updating once I installed. It downloads all the patches but gives me an error when trying to install them. And then when I restart after the failed patching, I get nothing but a terminal which doesn't let me do anything.


Any ideas or help? Everything runs just fine if I don't try to patch and use the i386 version but I'd like to have up to date software and run the AMD version of kubuntu.

---

### Post by zvacet on 2008-02-26
If you have 64 bit processor and you can not install 64 bit version it is maybe bad download,bad burn.....

For errors type in terminal 

```
sudo apt-get update && sudo apt-get upgrade
```

and post the output with errors.

---

### Post by Carl H on 2008-02-26
A bad disc is one cause. Download and burn it again - try using the alternate install CD instead of the Live CD. I never have any problems with the alternate disc.

The terminal appearing at restart after patching sounds like a video driver problem or incorrect X config. 

What's the spec of your machine?

---

