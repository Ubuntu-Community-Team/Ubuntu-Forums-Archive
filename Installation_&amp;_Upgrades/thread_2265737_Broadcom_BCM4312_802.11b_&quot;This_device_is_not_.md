---
title: "Broadcom BCM4312 802.11/b &quot;This device is not working&quot;"
date: 2015-02-17
forum: Installation &amp; Upgrades
---

### Post by wesleydepratt on 2015-02-17
I have searched the internet far and wide for a solution to my problem,but my driver won't connect to wireless or Ethernet ( i plugged in a network cable i know works) and everyone's solutions are using internet to download b-43. I am running 64-bit Ubuntu 14.10 on a Dell latitude E6400.Any ideas???

---

### Post by MAFoElffen on 2015-02-17
If you research it (use the simulate switch on apt-get on that laptop), it will do a dry run and tell you what other packages it will need for the depends.

Download the deb packages from another computer to a USB thumb drive. Use that USB drive to install manaully on your puter.

What I know about that one is that the B43 driver doesn't always work on those old dell's. Sometimes I've had to use the windows driver with wrapper. Just giving you a heads ups about that other possibility.

But if not connecting on wired, on a known good connection, you may have other problems going on along side that... That should work regardless whether wireless is or is not.

Please post the results of 
```

sudo lshw -n -c network
ifconfig

```

---

### Post by wesleydepratt on 2015-02-17
i did have other problems! static ip was set as manual, so the additional driver couldnt update,disabling the ethernet and wifi.it was the perfect storm of problems.thanks for the feedback!

---

