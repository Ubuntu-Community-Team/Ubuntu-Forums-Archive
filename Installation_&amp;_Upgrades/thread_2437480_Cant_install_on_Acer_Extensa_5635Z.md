---
title: "Cant install on Acer Extensa 5635Z"
date: 2020-02-24
forum: Installation &amp; Upgrades
---

### Post by hanswurst98 on 2020-02-24
Hi everbody

As a Linux newbie, I try to install Ubuntu 19.10 on an Acer Extensa 5635Z.

Win7 is working fine, thats why I think it is an Ubuntu issue.

I prepared an USB boot stick with Universal USB Installer and I can boot into Ubuntu.

However, as soon as it gets to anything WiFi related, the system freezes.

Just the same when I try to fully install Ubuntu. When it gets to the step of using an internet connection the install routine freezes, regardless of opting for "connect" or "skip".

The WiFi adaptor is an Atheros AR5B93.

Please let me know if you need any further information.

Thanks

p.s. For the sake of completenes, I also tried lubuntu facing the same issue

---

### Post by EuclideanCoffee on 2020-02-24
Have you tried using Ethernet to install the operating system?

---

### Post by hanswurst98 on 2020-02-25
> **EuclideanCoffee said:**
> ... using Ethernet ...

I cant imagine how to do this since the installation routine suggests to use the "Qualcomm Atheros AR928X" and doesnt give me any other option.

As I said, shortly after it freezes even if I decided to skip the "connection" part.

---

### Post by mörgæs on 2020-02-25
For this hardware it's better to stick to Lubuntu.

Does the computer have a hardware switch for disabling wifi access?

---

### Post by EuclideanCoffee on 2020-02-25
Even without wifi, you can still install Ubuntu. If you skip the connection part, it's likely unrelated to wifi. Perhaps your BIOS settings may be wrong for Ubuntu. I cannot say for sure as I do not have access to your device.

---

### Post by hanswurst98 on 2020-02-26
Thanks everybody.

It seems the issue was caused by v19.10 since 18.04.4 is up and running now.

As a newbie I am going to have lots of further questions.

But for now, thanks again.

---

### Post by CelticWarrior on 2020-02-27
> **hanswurst98 said:**
> I cant imagine how to do this since the installation routine suggests to use the "Qualcomm Atheros AR928X" and doesnt give me any other option.

As I said, shortly after it freezes even if I decided to skip the "connection" part.

A litle late to the party but something wasn't yet mentioned in the thread regarding this specific post.

The installer always tries to get an internet connection and use any network device natively supported. Ethernet will be the default choice if it has a cable connected and it's up and running, otherwise it will try WiFi, if present and already supported. This should be the case for the Atheros WiFi you have, the cabled connection not offered because there isn't one at the moment?

Anyway,
glad to know you're satisfied with 18.04. However +1 to the suggestion about using Lubuntu. It's a 10 years old laptop withed limited RAM and poor graphics compared to more modern machines. So, there are advantages in using an Ubuntu flavor with a lighter desktop environment instead of the standard distro because it requires much less resources and it's snappier in old computers. Lubuntu is a good choice but, going outside of the Ubuntu family, AntiX has been recommended for such computers, it's even lighter than Lubuntu.

---

### Post by hanswurst98 on 2020-02-27
> **CelticWarrior said:**
>  ... Lubuntu is a good choice but ... AntiX has been recommended for such computers ... 

That's pretty much what almost everybody is recommending and it's highly appreciated. Thanks!

I am going to keep the current installation, however, since bionic beaver is the coolest name ever :biggrin:

You need to know that the machine will be in use quarterly or monthly, so I am not too concerned about snappiness.

Plus, superstition or not, I believe in never touch a running system.

---

### Post by mörgæs on 2020-02-27
> **hanswurst98 said:**
> I believe in never touch a running system.
I hope that you up*date* it every time you turn it on but there is no need to up*grade* from the beaver as long as it is supported.

Antix is indeed a good candidate for very old computers but I don't consider ten years age very old. Many suitable distros are available if you want to experiment.

---

### Post by CelticWarrior on 2020-02-27
> **mörgæs said:**
> I hope that you up*date* it every time you turn it on but there is no need to up*grade* from the beaver as long as it is supported.

Antix is indeed a good candidate for very old computers but I don't consider ten years age very old. Many suitable distros are available if you want to experiment.

Age doesn't tell the whole story: [https://www.notebookcheck.info/Acer-Extensa-5635Z.19816.0.html](https://www.notebookcheck.info/Acer-Extensa-5635Z.19816.0.html)

---

