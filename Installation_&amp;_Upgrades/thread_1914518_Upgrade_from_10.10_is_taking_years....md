---
title: "Upgrade from 10.10 is taking years..."
date: 2012-01-24
forum: Installation &amp; Upgrades
---

### Post by Wouter_DS on 2012-01-24
Hi,

First let me introduce myself since I'm new here on this forum. I've used this forum a few times before when searching Google when I've got issues but today I decided it was time to create an account and stop leeching :)!

So I am 18, from Belgium and a student Digital Design & Media at Howest University. Sometimes I play a game such as Counter Strike Source, Call of Duty Modern Warfare 2/Black Ops but that's it, only first person shooters and some stupid Facebook games. I'm also a bit of a geek and an Apple addict.


So yesterday I bought a VPS after using a few days ubuntu server edition on my old computer as server, now the service doesn't provide Ubuntu 11.10 only earlier versions. So I installed 10.10 and started an upgrade with the commands below.

```
sudo do-release-upgrade -d
```I started the upgrade at 01:20 PM this afternoon, it's now 19:10 pm here. So it's been upgrading for the last +- 6 hours.
My question, is this normal? Could someone give me an ETA?
Note that I didn't had anything installed on the server myself, it was a clean install.


Best regards,
WouterDS

---

### Post by Frogs Hair on 2012-01-24
Hello and welcome

That is not normal and it may be due to your ISP download rate or the mirror the upgrade is coming from . You may just have to wait it out .

If you have backed up your data I would suggest a clean installation of a newer version . Perhaps you know someone that would let you download and burn a disk .

I don't understand why you are unable to download a newer version , but I have no experience with VPS .

---

### Post by Wouter_DS on 2012-01-24
All the packages were already downloaded and installing..
It was a clean installation I was updating so didn't backed up anthing.

And I can't install a clean version of 11.10 because the VPS is located in the US (I'm from Belgium) and I don't have physically access :P.

Anyway I have canceled it and reinstalled 10.10.. Just going to use that one until the sysadmin adds the newest version to there list to install.

---

