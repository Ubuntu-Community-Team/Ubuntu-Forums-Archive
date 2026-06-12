---
title: "Help installing Wine"
date: 2010-06-16
forum: Installation &amp; Upgrades
---

### Post by Admiral1234 on 2010-06-16
I am running Ubuntu Desktop 10.04 booting from a usb driver. I don't know if that is the problem, but i want to be sure everything works before i permenantly switch to ubuntu. When I try to install Wine, it gives me this error message 'Can not install 'wine' (E:Unable to correct problems, you have held broken packages.)'. And when I try to get it on software center, it tells me wine isn't available for my computer.

---

### Post by leorolla on 2010-06-17
Can you open a terminal and run
```
sudo apt-get update
sudo apt-get upgrade

```and copy-paste here the outputs?

---

### Post by Chame_Wizard on 2010-06-17
You're running Lucid Lynx from a USB driver,it can give problems.

---

### Post by Admiral1234 on 2010-06-17
> **Chame_Wizard said:**
> You're running Lucid Lynx from a USB driver,it can give problems.

If I install Ubuntu from a CD, will I be able to install wine?

---

### Post by Chame_Wizard on 2010-06-17
> **Admiral1234 said:**
> If I install Ubuntu from a CD, will I be able to install wine?

You wan to try something?

---

### Post by gadolinio on 2010-06-17
> **Admiral1234 said:**
> I am running Ubuntu Desktop 10.04 booting from a usb driver. I don't know if that is the problem, but i want to be sure everything works before i permenantly switch to ubuntu. When I try to install Wine, it gives me this error message 'Can not install 'wine' (E:Unable to correct problems, you have held broken packages.)'. And when I try to get it on software center, it tells me wine isn't available for my computer.

That "broken packages" thing sounds to me like a specific problem that took place in your current system/session. Have you tried shuting down the computer and then booting again with the usb in? 
I've never had a problem with wine, although I don't remember ever trying to instal it from a liveCD or liveUSB. Don't know whether a full install can be necessary.

---

