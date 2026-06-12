---
title: "Upgrading 14.04 to 14.04.2 to get 3.16 kernel"
date: 2015-02-22
forum: Installation &amp; Upgrades
---

### Post by geovino on 2015-02-22
How do you upgrade Ubuntu 14.04 to 14.04.2 to get the new 3.16 kernel?

---

### Post by grahammechanical on 2015-02-22
To upgrade from 14.04.1 to 14.04.2 run Software Updater as usual and then check with

```
lsb_release -a
```

Now, when I did that last week I got 14.04.2 but not the 13.16 kernel. I was expecting Software Updater to offer to install the new Hardware Enablement Stack. It did not and it still is not offering a button to click. So, I am now running

```
sudo apt-get install --install-recommends linux-generic-lts-utopic xserver-xorg-lts-utopic libgl1-mesa-glx-lts-utopic libegl1-mesa-drivers-lts-utopic
```

And that is bringing in the 3.16 kernel. To check run this

```
uname -a
```

After restarting.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Notice: The kernels in 14.04 and 14.04.1 will get security fix support up to April 2019 but the kernels in 14.04.2; 14.04.3 and 14.04.4 will only get security fix support until August 2016.

So, we have a choice. Stick with 14.04.1 for the full length of 14.04 LTS support or move onto the 14.04.2 hardware enablement stack and keep moving through 14.04.3 and 14.04.4 until we upgrade to Ubuntu 16.04.

Regards.

---

### Post by geovino on 2015-02-22
Thank you. I may stay with the 3.13 kernel since it won't make much difference in my computer use.

---

