---
title: "Can I upgrade from ubuntu 10.04LTS to 12.04.1 LTS directly?"
date: 2012-09-19
forum: Installation &amp; Upgrades
---

### Post by newhere_m on 2012-09-19
Is there any harm in upgrading from ubuntu 10.04 LTS to directly 12.04.1 LTS or should I first upgrade to 12.04 LTS and then to 12.04.1 LTS?

---

### Post by oldfred on 2012-09-19
The upgrade will be to 12.04.1. The only difference is that 12.04.1 includes on the CD the cumulative updates since 12.04 was released.

You need to download liveCD and test that everything still works with your system and you may need a current version liveCD to make repairs if need be.

Be sure to backup before upgrading.

---

### Post by newhere_m on 2012-09-19
Thanks for your reply. However I am a bit confused. 

Will it not work if I try from my current ubuntu 10.04 LTS:

system->administration->update manager->update 
and follow the instructions to upgrade to 12.04.1LTS?

---

### Post by DeezyFaReal on 2012-09-19
You can upgrade directly using the method you described.

---

### Post by DeezyFaReal on 2012-09-19
oldfred said to download a livecd so you can test ubuntu 12.04 on your system

In my experience this is a very helpful thing to do. You might test the new version from a cd and see that your pc can't handle the new graphics or see that the new version works better on a pc with more RAM

---

### Post by Glencore on 2012-09-20
> **DeezyFaReal said:**
> oldfred said to download a livecd so you can test ubuntu 12.04 on your system

In my experience this is a very helpful thing to do. You might test the new version from a cd and see that your pc can't handle the new graphics or see that the new version works better on a pc with more RAM

Further more the backing up suggestion is nice... just in case something goes wrong. It’s unlikely but it better to be safe than sorry &#61514;

---

### Post by nariub on 2012-09-20
I have upgraded 2 11.10's and 3 10.04 boxes to 12.04

I would suggest 
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

to freshen the 10.04 installation to the latest 10.04 version available

then 
  sudo do-release-upgrade

follow the prompts..

Word of warning though, the last one I did went sideways

[http://ubuntuforums.org/showthread.php?t=2050041](http://ubuntuforums.org/showthread.php?t=2050041)

I suggest you have a 10.04 alternative disc available before you upgrade..
mine required some nudging mid-upgrade ... had to boot into a 10.04 recovery mode and do some fixing to get the release upgrade to continue correctly.. 

she came out of it fine in the end..   backups are always a good idea..

---

