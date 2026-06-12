---
title: "How do I boot Ubuntu over the already installed Manjaro"
date: 2015-09-20
forum: Installation &amp; Upgrades
---

### Post by shami2 on 2015-09-20
I have manjaro installed but now I want to change my OS. So when I boot from the cd, the manjaro booting takes over the cd booting (even after changing the booting sequence and clearing the cache and everything). So I deleted the entire grub of manjaro and then booted with the CD, it then showed that an OS is needed to boot. The CD and drives are functional. So please tell me how do I install a new OS in my HP Laptop? What changes should I do?

---

### Post by coffeecat on 2015-09-20
The most likely explanation is that the CD you are using is not a functional bootable CD, or that you haven't changed the boot priority in the machine's BIOS. 

What exactly did you do when you say, "after changing the booting sequence"?

What ISO did you use to create the Ubuntu CD?

How did you burn the ISO to CD? What software did you use? Did you burn as image?

By the way - I've restored the default formatting in your post. You are welcome to link to your Manjaro forum post if you really think that is necessary, but please do not obscure the link and make the whole of your post into a hyperlink with fancy BBCode formatting. Make the link clear so that people helping you know what they are following if they choose to do so. Obscured links can appear to be suspicious. Thanks.

---

### Post by shami2 on 2015-09-20
Thanks! The CD I am booting from is more than a year old so I dont remeber the details but it is functional (i.e I can see its contents) and was always bootable earlier on my laptop.

I changed the boot sequence in the bios to boot first from the CDROM (it says internal CDROM).

---

### Post by shami2 on 2015-09-20
[https://forum.manjaro.org/index.php?topic=26407.0](https://forum.manjaro.org/index.php?topic=26407.0)

---

### Post by oldfred on 2015-09-20
A CD has not been large enough for several versions of Ubuntu. You need a DVD or flash drive. I prefer flash drives as then easy to update to newer version.

Also with older versions was  a bug that erased entire drive, when using auto re-install. Best to always use Something Else install option.

Is system newer with UEFI or older BIOS only?
If UEFI, you should be two options to boot - UEFI and CSM/BIOS/Legacy in UEFI boot menu, or one time boot key, often f10 or f12.

       HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[URL="http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079"]http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079
[/URL]
 1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)

[URL="http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079"]
[/URL]

---

