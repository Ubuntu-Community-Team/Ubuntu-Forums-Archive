---
title: "nvidia + legacy + feisty (also w/envy or automatix2) = FAIL"
date: 2007-07-03
forum: Installation &amp; Upgrades
---

### Post by dj_flx on 2007-07-03
Why is it **every** time I upgrade my system it turns into a circus with this stupid Vanta/Vanta LT nvidia card and the nvidia driver? Is there some rule that every upgrade must break it?

I've been all through the forums searching all day and nothing has got it working yet - does *anyone* have nvidia legacy drivers working in 7.04?

I just don't get why something like this should break. The hardware and the driver haven't changed, why does Ubuntu keep getting changed to the effect of breaking it? ](*,)

---

### Post by linuxwizard on 2007-07-04
Look here and see if you can find something that may help you to figure it out.

[https://help.ubuntu.com/community/Latest_Nvidia_Dapper](https://help.ubuntu.com/community/Latest_Nvidia_Dapper)

---

### Post by Pumalite on 2007-07-04
This is normal. The update doesn't break anything. Every kernel update requires rebuilding the modules necessary for the driver to work. I don't use legacy ot envy or automatix. I just use propietary drivers ( you can't beat them), I keep it in /home/<username> and I'm used to reinstall after every kernel update. It takes 30 seconds. Logic indicates that it should be so. For this, you need kernel-headers matching your kernel, make, automake, autoconf and latest gcc ( I think you can get all this with 'apt-get install build-essential' in your terminal).

---

### Post by alan_new on 2007-07-05
> **dj_flx said:**
> Why is it **every** time I upgrade my system it turns into a circus with this stupid Vanta/Vanta LT nvidia card and the nvidia driver? Is there some rule that every upgrade must break it?

I've been all through the forums searching all day and nothing has got it working yet - does *anyone* have nvidia legacy drivers working in 7.04?

Try with this: [http://blog.shevin.info/2007/04/dont-panic-if-you-broke-graphic-in.html](http://blog.shevin.info/2007/04/dont-panic-if-you-broke-graphic-in.html).

---

