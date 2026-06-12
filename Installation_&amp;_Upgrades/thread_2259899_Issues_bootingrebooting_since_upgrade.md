---
title: "Issues booting/rebooting since upgrade"
date: 2015-01-07
forum: Installation &amp; Upgrades
---

### Post by walth on 2015-01-07
First I did a basic apt-get update/apt-get upgrade on 12.04 and then my computer wouldn't boot unless I used grub to go to an old version of the kernel (3.5) instead of 3.13.  Then I did do-release-upgrade -d and now it wont boot 3.16.  I have to manually enter grub and select 3.5. Even if I boot 3.5, if I do a reboot it will shutdown fine and then I don't even get the bios screen and I have to hard power off and then start up and select 3.5.

Any ideas where to look?

---

### Post by Al1000 on 2015-01-08
Have you tried updating Grub to generate a new Grub configuration file?

```
sudo update-grub
```

EDIT: You'll have to do this from a live DVD/USB

---

### Post by walth on 2015-01-08
I've done update-grub and grub-install.

I've purged grub and installed it again and did the steps above too.

Thanks for the response!

---

