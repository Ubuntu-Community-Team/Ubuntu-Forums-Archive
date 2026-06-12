---
title: "Ubuntu 20.04 freezes minutes after login"
date: 2020-09-15
forum: Installation &amp; Upgrades
---

### Post by zakos13 on 2020-09-15
Hi everyone,

I have been using Ubuntu 16.04 in the past without any issues on my desktop (dual boot with Windows 10 on separate SSD's). At point I tried upgrading to 18.04 and then my computer would freeze just a couple of minutes after login, which made me revert back to Ubuntu 16.04. Recently I decided to try a clean install of Ubuntu 20.04, but I am having the same issue. Usually 2-3 minutes after logging in, my PC just freezes and mouse and keyboard are not working. I bought a new SSD (WD 500GB) and tried to clean install on the new drive, but I am having the same issue. I read a lot of topics that it may be Nvidia related, so I tried multiple Nvidia drivers ( 340,390,440, and the open source nouveau one) but the problem persists. Since mouse and keyboard are not working, I cannot press ctrl+alt+f2 to try to debug the issue or at least find the source of the problem.

I have been a casual user of Ubuntu in the past and used it mainly for development purposes so I am not very familiar with how I can find the source of the problem. I need to sort out the issue because I need to set up Ubuntu on my desktop for work purposes and I am desperate. Any hints on what command outputs I need to post here to help reach a solution would be greatly appreciated! 

Specifications:
Motherboard: MSI 970a-g43
Processor: AMD FX-6300
Graphics Card: NVIDIA GTX 750 Ti
Memory: G.Skill PC 1333 8GB 1333 MHz DDR3

---

### Post by CelticWarrior on 2020-09-15
Welcome.

If you didn't disable Secure Boot in UEFi settings (or didn't manually signed the Nvidia drivers modules) the drivers won't load even if correctly installed. And for a GTX 750ti the 240 driver is incorrect, all the others should work fine but prefer the latest version available because your card isn't a legacy product yet although is about to be.

---

