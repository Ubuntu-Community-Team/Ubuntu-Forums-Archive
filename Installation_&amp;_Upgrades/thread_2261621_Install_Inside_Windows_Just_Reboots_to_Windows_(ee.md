---
title: "Install Inside Windows Just Reboots to Windows (eeePC)"
date: 2015-01-20
forum: Installation &amp; Upgrades
---

### Post by b0ng0 on 2015-01-20
I previously had Ubuntu 12.04 installed on my eeePC 905F via Wubi. Decided to uninstall it and put the latest Lubuntu on instead.

I've booted into Live Environment via USB and it all works fine. I go through the install steps and choose "Install Inside Windows". I am running Windows 7 Starter.

I then get the Lubuntu splash screen for a few seconds and the computer reboots and starts loading Windows.

I've tried this several times and it just does the same thing every time. Any suggestions as to how to solve this?

---

### Post by tokyobadger on 2015-01-20
[wubi is no longer officially supported](http://ubuntuforums.org/showthread.php?t=2229766) so I don't think you'll have much luck resolving this - standard install time

---

### Post by b0ng0 on 2015-01-20
Sorry, I had previously used Wubi but then uninstalled it/Ubuntu.

I am now trying to install Lubuntu the standard way (via Live USB), but I am selecting the "Install Alongside Windows" option.

So I don't think Wubi is the issue here (unless this install option is powered by Wubi?)

---

### Post by tokyobadger on 2015-01-20
> **b0ng0 said:**
> I previously had Ubuntu 12.04 installed on my eeePC 905F via Wubi. Decided to uninstall it and put the latest Lubuntu on instead.

I've booted into Live Environment via USB and it all works fine. I go through the install steps and choose "Install Inside Windows". I am running Windows 7 Starter.

I then get the Lubuntu splash screen for a few seconds and the computer reboots and starts loading Windows.

I've tried this several times and it just does the same thing every time. Any suggestions as to how to solve this?
It sounded like you were trying wubi again. If you're choosing alongside instead of inside Windows then it's a different situation.

I'd suggest providing a partition table if you can as well as the exact steps you have taken so far.

Is it the Lubuntu splash screen you see (plymouth) or the Grub bootloader?

If Win7 is on there and has the whole disk and there are no linux installations on there then as I recall you will have to resize and partition from within Win7 with it's own tools - plenty of tutorials here ans elsewhere on the web for that.

Having done that, a better option than install alongside might be to choose the "something different" option at installation menu - again most tutorials/guides will cover this.

---

### Post by Mark Phelps on 2015-01-20
Heed TokyoBadger's advice and be sure to use Windows Disk Management tool to do any resizing of Windows filesystems. IF you use the Ubuntu installer to do this (using the slider), you risk corrupting the Windows filesystem and rendering it unbootable -- which will make it really hard to fix.

After you shrink down the Windows filesystem partition, you will need to use the "Something Else" option to create and format the proper partitions for the Ubuntu installation.

---

### Post by hakuna_matata on 2015-01-20
> **b0ng0 said:**
> I go through the install steps and choose "Install Inside Windows". I am running Windows 7 Starter.

I then get the Lubuntu splash screen for a few seconds and the computer reboots and starts loading Windows.

IMHO [here]("http://askubuntu.com/questions/69481/why-dont-i-have-the-option-install-ubuntu-alongside-with-them") is your issue and [your solution]("http://askubuntu.com/a/272036"). Good luck.

---

