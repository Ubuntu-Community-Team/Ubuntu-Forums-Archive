---
title: "Ubuntu install and HD space - question / issues"
date: 2010-06-25
forum: Installation &amp; Upgrades
---

### Post by gerti13 on 2010-06-25
Hello everyone,
I've installed Ubuntu from inside Windows 7, i.e. it doesn't have it's own partition. I allocated a certain amount of HD (trial space so to speak). But I'm finding out that I want to keep Ubuntu (and Windows). But there are two issues: 

1) Is there a risk that, if the "allocated" space of Ubuntu is filled, it would leak into Windows-space? If so, is there a way to either check if it's getting dangerously close OR expand this allocated space ?? (short of removing Ubuntu, shrinking Windows, and creating a new partition).

2) When I boot up the machine, in the screen in which I select the OS, I have 5 lines showing (2x(Ubuntu versions with it's accompanying "recovery" or "generic" - the word escapes me now) + 1 Windows 7). I do select the most recent Ubuntu, i.e. the greatest version number, but is there a way to remove the older versions that show there, or are they necessary to be kept??
This is happening in the machine in which Ubuntu was installed from within Windows 7 AND in another machine in which Ubuntu has its own partition

I am using Ubuntu 10.04 LTS in both machines.

Any help would be greatly appreciated.

---

### Post by darkod on 2010-06-26
1. The wubi install you made will always stay within the space you allocated. When there is low space left unused it will start reporting as if the hdd is that small and running out of space.

2. At least one older kernel version is recommended to be kept because if the newest kernel doesn't boot sometimes you can boot the other one.

Wubi was never meant for long term install, just a quick way to try. Since you like and want to keep it, I recommend to start considering moving to proper full ubuntu ASAP because you start having too much files and settings there you want to keep. Files you can copy using ext hdd but I'm not sure you will be able to transfer settings.

You will start having problems with wubi sooner or later because it wasn't meant to work long like that inside windows.

---

### Post by gerti13 on 2010-07-08
A belated thank you for the reply.

---

