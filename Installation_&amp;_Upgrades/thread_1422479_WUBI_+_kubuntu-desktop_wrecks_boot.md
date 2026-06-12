---
title: "WUBI + kubuntu-desktop wrecks boot"
date: 2010-03-05
forum: Installation &amp; Upgrades
---

### Post by spoxox on 2010-03-05
On my MS Vista 64bit machine, I installed Ubuntu through WUBI (some time in 2010) and was happily booting one or the other as needed. Then I added kubuntu-desktop (using Synaptic).

Now, when I reboot, the Windows Boot Manager still offers Vista and Ubuntu as boot options. But Ubuntu, rather than boot, goes to a grub shell. 

I found a GrubHowto that includes "Manual boot into a Linux OS" - but it seems to suggest that clean Karmic installs use Grub2 and the Howto instructions apply only to Grub. I don't know if the WUBI install was Karmic or something older. I don't know anything about using grub manually.

And I don't know how to get my (k)ubuntu back!

Thanks for your help.

---

### Post by spoxox on 2010-03-05
Appears solved.

Can't find reference now, but solution (working so far) was to replace c:\wubildr per Agostino Russo @ launchpad.net discussing similar problem.

---

