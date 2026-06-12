---
title: "Need some help with Dual Booting"
date: 2010-09-04
forum: Installation &amp; Upgrades
---

### Post by Beastlicker on 2010-09-04
Hey all. I just have some questions and would like some help setting this up.

I had two hard drives in my system, a 500 gb one that is my primary, and a 160 gb one that is my secondary.

I want to have Ubuntu on my primary, and Windows 7 on my secondary. When I go to do this, Windows 7 puts an extra partition on the primary hard drive. I think it has something to do with booting it, although I am not completely sure.

Is there any way to avoid this, or to just put the extra "boot" partition on the secondary hard drive instead of the primary?

All help is appreciated. Thanks!

---

### Post by dino99 on 2010-09-04
w7 is known to take decision itself and dont agree with user change(s), so be carefull, why not let it on 1st hdd as he wants and install ubuntu elsewhere ?

boot with partedmagic and follow this little help if you want to install ubuntu:

prepare your hdd first:

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by sikander3786 on 2010-09-04
Not difficult to accomplish with 2 hard drives. Install Ubuntu onto the 500GB 1st HDD and after that disconnect it (mean pull off the power cable of the HDD). Install Windows 7 on the 160GB 2nd HDD, reconnect the 1st HDD, boot into Ubuntu and run

```

sudo update-grub

```

And it should pick up Windows 7 from the 2nd HDD and add it to the GRUB menu.

---

