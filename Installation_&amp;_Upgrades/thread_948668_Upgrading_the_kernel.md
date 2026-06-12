---
title: "Upgrading the kernel"
date: 2008-10-15
forum: Installation &amp; Upgrades
---

### Post by Idefix82 on 2008-10-15
I am so new to Ubuntu that I haven't had to upgrade the kernel before. Here are some questions about upgrading it via the update manager:

Will the new kernel automatically load the modules that I use now for, say, Ethernet and WiFi?
If not, suppose I keep the old kernel and add it as an option in GRUB (the upadte manager will automatically offer me this option, right?). When I boot into the old kernel, will the old modules be loaded?

So to get more specific, firstly I am using ndiswrapper for wireless and that's working well. I don't want to break it with some potentially buggy proprietary driver. Secondly, I had to blacklist the r8169 driver for ethernet which came with the kernel and had to install the proprietary r8168. Will these changes be reversed and will I have to repeat this procedure again if the default driver turns out to be as buggy as the one I had to remove?

Just want to know whether upgrading is a one minute thing this time just as usual or whether I should do it when I actually have time to sort out any mess that can occur.

Thanks in advance!

---

### Post by ww711 on 2008-10-15
> **Idefix82 said:**
> 

Just want to know whether upgrading is a one minute thing this time just as usual or whether I should do it when I actually have time to sort out any mess that can occur.



Probably the latter would be the better option.

---

### Post by howefield on 2008-10-15
Definately the latter, I'd guess that most people have few issues but from the posts in these forums today, it seems that many people have had issues with kernel updating breaking something.

---

