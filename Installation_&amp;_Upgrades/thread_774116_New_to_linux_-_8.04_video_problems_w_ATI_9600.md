---
title: "New to linux - 8.04 video problems w/ ATI 9600"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by wesmoran on 2008-04-29
Hello, I just started using Ubuntu 7.10 about a month ago. I love it &  had it working perfectly on my computer (except I had sound, but it sounded terrible).

After a week of trying to update to 8.04, I finally got it to work last night. My video is extremely laggy on 8.04. I have a Radeon 9600 but the ATI driver listed as "Not in use" under System>Administration>Hardware Drivers

I no longer have a "Screens & Graphics" Option under Admin.

Can anyone point me in the right direction?

Thanks.

---

### Post by Peter09 on 2008-04-29
Well you could try in a terminal:

```
sudo apt-get instal envyng-core
```

and you may need

```
sudo apt-get install envyng-gtk
```

then run

```
envyng -t
```

that will install your ATI drivers 

PC

---

