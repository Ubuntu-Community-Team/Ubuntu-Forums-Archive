---
title: "Auto Etho not working in Ubuntu 10.10"
date: 2011-01-03
forum: Installation &amp; Upgrades
---

### Post by wearyroad on 2011-01-03
Hey, I'm really really rusty when it comes to network administration, and I have a bit of a problem. I'm running Ubuntu 10.10 on Macbook Pro 2,2 hardware. It stills picks up wireless internet (but cannot connect when the networks only have one or two bars...) but the ethernet won't accept a cord. It registers that a cord has been plugged into the computer, but will not connect to the internet via it.

I'm currently running on a live CD of Ubuntu 9.04, and the ethernet cord works fine, so it's not my hardware I'm worried about. (The change in registering cords came about after I re-installed Ubuntu after I wanted to switch to pure Ubuntu rather than running a dual-boot system.) It's something to do with the networking program I have on the system. 

Does anyone know how I'd fix this?

---

### Post by sholdowa on 2011-01-03
I have no entries in interfaces for wireless or wired.

Do you have a DHCP server somewhere, or are you setting up static addressing?

---

### Post by wearyroad on 2011-01-03
I'm not entirely sure what any of those terms you just used means.

---

### Post by Geremia on 2011-02-01
> **wearyroad said:**
> Does anyone know how I'd fix this?I get the same problem, too. It's like my ethernet card isn't even on because my router's light for the port I am connected to is not on.

---

### Post by grahammechanical on 2011-02-01
I am not sure who I am giving advice to but if you right click the network manager icon and select edit connections, you will be able to edit each ethernet (wired) connection available to your machine. Make sure that they are set to be available to all users and are set to connect automatically.

Regards.

P.S. Network manager will give priority (connect first) to a wireless connection especially if it is set as default. Set an ethernet connection to default and it will get priority.

---

