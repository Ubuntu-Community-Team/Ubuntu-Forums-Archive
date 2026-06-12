---
title: "Upgrade could not install fglrx. Now cannot see logon or desktop."
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by skutter2k on 2010-10-10
Just finished upgrading to 10.10 from 10.04. All went well until the cleanup part where I noticed a few error messages such as not being able to install fglrx and a few other packages that flashed by too quickly to catch.

Now when I boot up I get a the boot splash screen but the 10.10 and four dots look like plain text. It then stays with a purple background but nothing else. If I type my password I can hear it log in however the display stays purple.

While I find purple calming it's very difficult to do much work!

Any help gratefully received.

It's a Dell Studio with ATI 4570 gfx.

---

### Post by mörgæs on 2010-10-10
How does it behave when booted with a live CD?

---

### Post by alphacrucis2 on 2010-10-10
> **skutter2k said:**
> Just finished upgrading to 10.10 from 10.04. All went well until the cleanup part where I noticed a few error messages such as not being able to install fglrx and a few other packages that flashed by too quickly to catch.

Now when I boot up I get a the boot splash screen but the 10.10 and four dots look like plain text. It then stays with a purple background but nothing else. If I type my password I can hear it log in however the display stays purple.

While I find purple calming it's very difficult to do much work!

Any help gratefully received.

It's a Dell Studio with ATI 4570 gfx.

Try booting in to recovery mode. Then completely remove fglrx. 

```
apt-get --purge remove fglrx
```

Note - you don't need sudo at the root recovery prompt.

Then reboot and try installing the new fglrx via the Hardware drivers menu. Before rebooting again do this:

```
sudo aticonfig --initial -f
```

---

### Post by alphacrucis2 on 2010-10-10
> **mörgæs said:**
> How does it behave when booted with a live CD?

fglrx isn't included on the live CD. That would just be using the OSS driver.

---

### Post by mörgæs on 2010-10-10
I know. I was just looking for a confirmation that everything was working well with the regular (open source) drivers.

---

### Post by skutter2k on 2010-10-11
Thanks everyone for your advice. I booted into recovery mode and noticed the option to boot into safe graphics mode. In for a penny I thought, it booted ok so I just went into drivers and enabled the proprietary ati driver. Rebooted and everything working perfectly.

Thanks again. I can get on and enjoy the latest Ubuntu offerings :-)

---

### Post by mörgæs on 2010-10-11
Good, please mark the thread 'solved'.

---

