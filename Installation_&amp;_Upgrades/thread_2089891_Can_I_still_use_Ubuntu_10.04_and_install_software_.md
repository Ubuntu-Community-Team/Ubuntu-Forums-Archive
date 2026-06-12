---
title: "Can I still use Ubuntu 10.04 and install software on it using software center"
date: 2012-11-30
forum: Installation &amp; Upgrades
---

### Post by silvercats on 2012-11-30
Last time I tried to do that, It said this version(10.xx)is not supported any more and get a new version. It wasn't Ubuntu 10.04 as I remember, it was just 10. The question is, if I install 10.04 LTS on my virtual machine , can I install software ? and it is still supported? I can't use new Ubuntu on my Vmachine because it gets slow. currently using Kubuntu 11 which is still slow so I really need Ubuntu 10 something. 

thanks

---

### Post by howefield on 2012-11-30
Desktop 10.04 is supported till next April, which isn't that far away.

So yes, you could use and install software. Any reason for not using a different flavour of 12.04, eg Xubuntu ?

---

### Post by sudodus on 2012-11-30
Ubuntu 10.04 has long time support until April 2013, so there is still half a year to go, until security and other updates will stop.

It works and is very stable now, but the hardware detection for new hardware is not as good as that of new versions.

---

### Post by Cavsfan on 2012-11-30
I love Lucid 10.04 LTS 64 bit! I am going to ride it up until April 2013 before upgrading to Precise 12.04 LTS.
The version that you would download now is 10.04.4 which is very stable.
I prefer LTS versions for my main Ubuntu.

Ubuntu Software Center works great although I use **sudo apt-get install <package(s)> **most of the time.

I never use update manager on any Ubuntu.
For all of my updates I use a script called **ud** and to get upgrades **ud2** entered in terminal.

Someone in this forum showed me this: **gedit ~/.bashrc** in terminal and paste this toward the bottom where you see aliases.

```
# update aliases
alias ud='sudo apt-get update && sudo apt-get upgrade && sudo apt-get clean'
alias ud2='sudo apt-get dist-upgrade'
```

You have to logout and back in for it to take effect.

**ud2** will get things that are being held back like a new kernel install and can be entered right after **ud**.
Update Manager can mess you up sometimes. A friend calls it Update Mangler. :D

---

### Post by silvercats on 2012-11-30
yes There is a reason I want t use 10. My Virtual machine gets slow if I install newer versions. Sometimes that taskbar to the left doesn't show up, so can't access anything like file explorer,browser,terminal etc..

---

### Post by silvercats on 2012-11-30
so after April,can't I use it anymore? I will have to download a newer version? or only the updates stop. Last time I tried 10.xx, It didn't allow me to install a software at least. Always go the message saying download the newer Ubuntu.

---

### Post by Sef on 2012-12-01
> so after April,can't I use it anymore? I will have to download a newer version? or only the updates stop.

The last one is correct: only the updates stop. However, it is not advised to use a distro where the updates have been stopped because holes and flaws do not get fixed.

---

### Post by zombifier25 on 2012-12-01
> **silvercats said:**
> yes There is a reason I want t use 10. My Virtual machine gets slow if I install newer versions. Sometimes that taskbar to the left doesn't show up, so can't access anything like file explorer,browser,terminal etc..

Then try some of the lighter variants, such as Xubuntu or Lubuntu.

---

### Post by silvercats on 2012-12-01
> **zombifier25 said:**
> Then try some of the lighter variants, such as Xubuntu or Lubuntu.

thanks. will try

---

