---
title: "Installing on non-PAE cpu notebook"
date: 2014-11-21
forum: Installation &amp; Upgrades
---

### Post by ken42 on 2014-11-21
I have Sony Vaio VGN-s150 which is non-PAE cpu notebook, I downloaded 32bit version of lubuntu 14.10 desktop i386 from the download page of lubuntu. But when I try to install or even try it without install I get error saying "Kernel requires features not present on the CPU PAE
Unable to boot - please use a kernel appropriate for your CPU"
I even tried minimal install with the same error.


so how can I install 32 bit version when my notebook don't support PAE?
or do I have to download older version of lubuntu? if so then which one do I need to download?

my notebook spec [http://www.pcmag.com/article2/0,2817,1636324,00.asp](http://www.pcmag.com/article2/0,2817,1636324,00.asp)

---

### Post by plucky on 2014-11-21
> **ken42 said:**
> I have Sony Vaio VGN-s150 which is non-PAE cpu notebook, I downloaded 32bit version of lubuntu 14.10 desktop i386 from the download page of lubuntu. But when I try to install or even try it without install I get error saying "Kernel requires features not present on the CPU PAE
Unable to boot - please use a kernel appropriate for your CPU"
I even tried minimal install with the same error.


so how can I install 32 bit version when my notebook don't support PAE?
or do I have to download older version of lubuntu? if so then which one do I need to download?

my notebook spec [http://www.pcmag.com/article2/0,2817,1636324,00.asp](http://www.pcmag.com/article2/0,2817,1636324,00.asp)

[Forcepae](https://help.ubuntu.com/community/PAE)

See if this works for you.

You might also consider running Lubuntu 14.04 Long Term Support instead of 14.10 which is only supported for 9 months.

Good Luck

---

### Post by ken42 on 2014-11-21
thanks for the forcepae command information
its installing it now

---

