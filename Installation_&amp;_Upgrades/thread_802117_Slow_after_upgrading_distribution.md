---
title: "Slow after upgrading distribution"
date: 2008-05-21
forum: Installation &amp; Upgrades
---

### Post by japtar10101 on 2008-05-21
I've should have asked this earlier, but oh well...
When ever I try to upgrade my, say, Feisty Fawn to Gutsy Gibbons, or Gutsy Gibbons to Hardy Heron, the operating system works more slower than simply re-imaging it.  I'm tired of burning CDs, though, and would much rather stick to "upgrading by internet" method.  Any ideas on how to make my system work more efficiently, and why it tends to slow down after upgrade?

Note:  Actually, I did find *one* reason why it acts so slowly: for some reason, upgrading causes it to use the past OS (with outdated kernal) on start-up.  Performance have significantly increased after going to System->Admin->Start-up, and then changing the OS to the latest version.
Unfortunately, I don't find this improvement to be good enough.  Could the package cache may be the reason for slow-down?

---

### Post by zvacet on 2008-05-21
How many kernels do you have installed?You don´t need more then two(latest from Hardy and Gutsy until you are sure that Hardy kernel is working wit no problems).Go to the synaptic and in search box type linux-image and delete all with lower number (as mantion before leave Gutsy and Hardy).

```
sudo update-grub
```

You can try this to see if it helps

```
sudo apt-get clean
sudo apt-get autoclean
```

---

### Post by japtar10101 on 2008-05-25
Thanks, howver, nothing significant happened.

Now that I think of it, it may just be my graphics card.  Let me see what happens if I re-install the library for my ATI Radeon-something or other graphics card.

---

