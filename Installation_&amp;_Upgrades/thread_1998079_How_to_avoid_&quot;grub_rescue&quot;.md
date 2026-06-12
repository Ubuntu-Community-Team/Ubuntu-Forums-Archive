---
title: "How to avoid &quot;grub rescue&quot;?"
date: 2012-06-06
forum: Installation &amp; Upgrades
---

### Post by 3v3rgr33n on 2012-06-06
Hi

The last time I tried to partition my hard drive in Windows, my machine didn't want to boot at reboot. It only gave me the "grub rescue" screen. I managed to solve my problem through googl'ing and typing commands which 60% of, I don't understand. I just wanted a safe way to partition my hard drive. does anyone know where I can find a ".pdf" file with the steps on what on what to do when a user sees the "grub rescue" screen.

Thnx

---

### Post by dino99 on 2012-06-06
you get this issue because grub is not installed as it might (it dont find the good path)

so, boot from the livecd (liveusb) and open a terminal to install grub:

sudo grub-install /dev/sda
sudo update-grub

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by wilee-nilee on 2012-06-06
> **dino99 said:**
> you get this issue because grub is not installed as it might (it dont find the good path)

so, boot from the livecd (liveusb) and open a terminal to install grub:

sudo grub-install /dev/sda
sudo update-grub

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

Those commands from a live cd do nothing, they have to be run in a install, or in a chroot from the cd.

OP here is the grub manual.
[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

---

### Post by 3v3rgr33n on 2012-06-06
> **dino99 said:**
> 
sudo grub-install /dev/sda
sudo update-grub


Are you trying to tell me you need an internet connection just to solve that problem?

---

### Post by wilee-nilee on 2012-06-06
> **3v3rgr33n said:**
> Are you trying to tell me you need an internet connection just to solve that problem?

That information was incorrect.

A grub> rescue prompt is a generic response to grub not booting there could be any number of problems, and there is no specific link really, without knowing what the problem is.

When installing though you can use the something other option for a custom install and in that set up is a choice of where you want grub put.

---

### Post by blackbird34 on 2012-06-06
Supergrubdisk does the trick. See [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) 
I've dealt with such a case on my laptop before: i was faced with a grub>rescue and no live CD on hand, so i downloaded it and burned it from another computer. You boot from the CD and it looks for operating systems that load with GRUB (Windows, Linux), boots one of your choice, then you can repair GRUB from inside Linux with [Boot-Repair]("https://launchpad.net/boot-repair") (a GUI tool). More explanations on the [_wiki_]("http://www.supergrubdisk.org/wiki/Boot_Problems").


------------------
[Tug of war, community vs mods, we need help!! :D]("http://ubuntuforums.org/showthread.php?p=12004020&")

---

### Post by 3v3rgr33n on 2012-06-06
Thank you very much

---

### Post by blackbird34 on 2012-06-06
hope it worked for you, pass on the tip to others! :D

---

