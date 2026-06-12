---
title: "Problems with Installing Ubuntu"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by king EZi on 2008-05-02
I'm using a x86 system and i tried installing Ubuntu 7.10 from a live cd but it loads up and drops me to a shell, and from there i dont really know what to do. Please help.

---

### Post by Eirikizer on 2008-05-02
I've experienced the same problems, but for me, an installation with Wubi from Windows works. I know it's not the same, but it's ok. Try an install with the alternative CD, perhaps that will help ;)

---

### Post by mlentink on 2008-05-02
> **king EZi said:**
> I'm using a x86 system and i tried installing Ubuntu 7.10 from a live cd but it loads up and drops me to a shell, and from there i dont really know what to do. Please help.

Could you specify what sort of system you're using? Like what processor, graphics card and how much memory?

---

### Post by Neobuntu on 2008-05-02
I can only guess that X just didn't start. The good news is, you're install is just about completed. Perhaps you have a special video card and/or monitor resolution. Try...> sudo dpkg-reconfigure xserver-xorg...and just try the defaults. you can also do a...> lspci...and see what video card model you have. Then Google it and how others got it going with the new release.

Also, I've seen whole systems destabilized, just for having the computers BIOS **shared video** settings too low. 

It may seem stupid but as you find the road block, in the end, you'll probably note that it is simply strange hardware. When things don't install; trouble free, it's like a board in our eye. I understand. In comparison, it's just a spec. I've had most systems install Kubuntu far faster and with far more finish, than any other system. Great rewards, come with a little initial setup.

Please let us know how it goes.

---

### Post by king EZi on 2008-05-30
Thanks guys, i got Ubuntu 8.04 (HARDY HERON) and it worked fine, im quite happy.

---

### Post by Bubba64 on 2008-05-30
All right one more happy user.

---

