---
title: "can't add irqpoll in 10.04 lucid therefore USB ports dont work"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by umabatata on 2010-05-08
I installed Lucid earlier today (took about 4 hours as karmic wouldn't write the cd so had to use wifes Mac OS)
In the 2 previous releases of ubuntu I have had to add irqpoll to the boot line in order for my USB ports to work. I dont understand why this works but it does.
With the new "noninteractive" boot I can't work out how to add irqpoll to the boot sequence. Any help?

thanks

---

### Post by Catharsis on 2010-05-08
Edit your GRUB file:
```
gksudo gedit /etc/default/grub
```

Find this line:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
And add "irqpoll" to it so it reads:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash irqpoll"

```

Save and exit, and then update GRUB:
```
sudo update-grub
```

---

### Post by umabatata on 2010-05-08
Brilliant. Thanks
Should have figured that out myself. I looked at that line and thought it was the right one but didn't want to mess up the boot as then I'd be stuffed. 

Thanks again.

---

