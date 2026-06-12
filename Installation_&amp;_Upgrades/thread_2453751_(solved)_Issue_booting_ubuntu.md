---
title: "(solved) Issue booting ubuntu"
date: 2020-11-16
forum: Installation &amp; Upgrades
---

### Post by pedia on 2020-11-16
Hi guys 

I did some updates yesterday (don't actually know which one) all went fine afterwards.  I switched off my computer for the night and in the morning I could not boot in. A white "-" was flickering at the top left corner. 

So I decided to change from mintlinux to Ubuntu.
I mounted the last Ubuntu onto an USB key I erased my disk and install Ubuntu. All went fine as well. A message advices me to restart and unmount my USB key but when I switched it off again an error appears : "defeat boot device missing or boot failed. Insert recovery media and hit any key. Then select boot manager to choose a new boot device or to boot recovery media"

In the boot manager I cannot choose anything but a "yes" .

 I'm quiet a newbie with Linux and I feel unprepared to fix that. I would greatly appreciate some helps here. 

In case you need additional datas about my computer : 
It's an Acer spin sp513-51
Cpu : Intel core i5 7200 cpu 2.5ghz
Had model name : micron 1100
8go ram

---

### Post by CelticWarrior on 2020-11-16
Welcome.

Please check UEFI settings > Boot before anything else. Chances are you need to explicitly select "Ubuntu" as the boot priority.

---

### Post by oldfred on 2020-11-16
Acer typically needs UEFI update, if SSD, SSD update & a "trust" setting in UEFI to change UEFI boot entry of "unknown" to "Ubuntu" or whatever you name it.

Older but issue same.
Acer Spin 5 Ubuntu 17.04 Needs Acer password & trust
[https://askubuntu.com/questions/908854/installed-ubuntu-17-04-and-now-cant-boot-at-all-failed-to-open-efi-boot-grubx/909238#909238](https://askubuntu.com/questions/908854/installed-ubuntu-17-04-and-now-cant-boot-at-all-failed-to-open-efi-boot-grubx/909238#909238)

Acer Very latest UEFI/BIOS works, downgrade not required if no trust screens, you must now upgrade:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)
Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)

One of several with more details on trust:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[http://ubuntuforums.org/showthread.php?t=2291335](http://ubuntuforums.org/showthread.php?t=2291335)

---

### Post by pedia on 2020-11-16
I added grub.fi as trusted UEFi files. And it worked. Thanks guys

---

