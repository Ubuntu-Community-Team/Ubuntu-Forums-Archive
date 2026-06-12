---
title: "deleting dual boot"
date: 2011-01-01
forum: Installation &amp; Upgrades
---

### Post by cichlidius on 2011-01-01
Hello, I would like to give ubuntu a try.  I have never used linux before and would like to try out a dual boot to see what I think.  If it doesnt work out though I would like an easy way to remove ubuntu.  Is it possible to remove ubuntu right inside windows 7?  Thanks  for any help.

---

### Post by Frogs Hair on 2011-01-01
You could try Wubi the Windows installer , which installs Ubuntu inside Windows making it easy to remove from add/remove programs.[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Downloading the ISO and running from the cd is another option for testing Ubuntu . The cd will include the Windows installer. Running from the cd may be slower , but you can see how your hardware works with Ubuntu with no commitment.

---

### Post by bcbc on 2011-01-01
That's a good way to try it. 

But there is an issue with Wubi at the moment which you need to avoid: when Update Manager prompts you, go through the whole list and uncheck grub-pc and grub-common (under the "Recommended" updates). If you update these it will stop the install from booting.

---

### Post by cichlidius on 2011-01-02
Thanks guys, I just ran it off the cd.  Decided that it just wasn't for me though.  Appreciate the help.

---

