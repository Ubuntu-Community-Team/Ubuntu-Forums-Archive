---
title: "Upgrade 10.04 to 10.10 Fail"
date: 2012-06-08
forum: Installation &amp; Upgrades
---

### Post by davequig on 2012-06-08
Had Ubuntu 10.04 Netbook 64bit installed. Chose to upgrade to 10.10 via update manager. Left it overnight, in the morning and Ubuntu opens in the form of Terminal/dos. Has a login which works then command line dave@dave-laptop:~$

I am a total noob and have no idea what to do here. Can anyone help?

---

### Post by raja.genupula on 2012-06-08
ok login there with your user-id and pwd and then type this .

```
sudo start lightdm
```

if its saying anything then tell us what is it .:)

---

### Post by Topsiho on 2012-06-08
I guess this upgrade failed as Ubuntu 10.10 is not supported any more: it is more than 18 months old now.

10.04 is an LTS-version, which means you CAN upgrade it to the next LTS version, which is Ubuntu 12.04. So you could try to do just that.
Ubuntu 10.04 is supported for 3 years, so until April 2013, Ubuntu 12.04 will be supported for 5 years, that is to April 2017.

However, I wonder whether you can upgrade after a failed upgrade, which would mean you'd have to do a "clean install", which means from a LiveCD.

Topsiho

---

### Post by davequig on 2012-06-08
Typed sudo start light dm
entered my password

start: Unknown job: lightdm

the reason I upgraded to 10.10 is because I read I could either install 12 or keep upgrading to 12. Seeing as I'm a noob I thought the upgrading would be an easier option.

---

### Post by Enigmapond on 2012-06-08
Yea your update failed as 10.10 has died. If your goal is to get to 12.04, you will be better off just doing a fresh install or simply wait until August for the 12.04.1 release. But I would just do a fresh install from a LiveCD/USB.

---

### Post by zombifier25 on 2012-06-08
> **raja.genupula said:**
> ok login there with your user-id and pwd and then type this .

```
sudo start lightdm
```

if its saying anything then tell us what is it .:)
There's no LightDM in 10.10 ;) only GDM

Agree with others. If you want to get 12.04, the safest way would be reinstalling from a LiveCD. But since your computer is pretty borked, I don't see you have a choice :P

---

### Post by davequig on 2012-06-08
So if i create a live CD of 12, will it boot from the cd in this state?

---

### Post by Enigmapond on 2012-06-08
Correct. Just change the BIOS to boot from the removable media and let it install. Be sure to backup anything important or move it as it will wipe the disk or partition for the install.

---

