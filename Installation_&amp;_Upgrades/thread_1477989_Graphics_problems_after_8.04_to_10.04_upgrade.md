---
title: "Graphics problems after 8.04 to 10.04 upgrade"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by MCZ_1997 on 2010-05-09
Before I upgraded, I was able to play graphics intensive games, such as BloodFrontier and OpenArena, with no problems.  After, the screen blinks from being off, to all black, to some white stripes on the upper half of the screen.

I have a Dell with an integrated video card.  There is nothing listed when I open the Hardware Drivers application.  All of the solutions I have found for integrated video cards are for 9.04.

Thanks in advance.

---

### Post by crunchfighter on 2010-05-09
Having a similar problem.  I did a failed upgrade from 9.10 (user error if you can believe it).  I then reinstalled from CD.  One successful boot.  Subsequent boots I get "graphics card not recognized..." error.  Searching for solutions now.

---

### Post by Catharsis on 2010-05-09
What exactly is your video card?
```
lspci | grep VGA
```

If you have an intel 8xx card, see:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

### Post by MCZ_1997 on 2010-05-10
When I ran the line you gave me, this is what it comes up with:
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

I can run Ubuntu fine.  Right now I'm using my system.  It's only when I run graphics heavy applications that I get the symptoms I described.  Also, I didn't use a CD or DVD, but downloaded the upgrade.

---

### Post by Catharsis on 2010-05-10
> **MCZ_1997 said:**
> When I ran the line you gave me, this is what it comes up with:
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

I can run Ubuntu fine.  Right now I'm using my system.  It's only when I run graphics heavy applications that I get the symptoms I described.  Also, I didn't use a CD or DVD, but downloaded the upgrade.

I've heard this from a couple other users too. You can try the KMS fix from that link, as well as upgrading your -intel drivers through X-Updates or using the mainline kernel (also in that link).

Edit: I just noticed you upgraded from Hardy. This could be contributing to your regression as well; you upgraded a huge number of packages, so the chances of one of them not being configured correctly is very likely.

Try reconfiguring your X server. Log into a root shell through recovery mode and run:
```
dpkg-reconfigure xserver-xorg
```
Then type "reboot" to restart the machine.

You might also want to try removing the nvidia drivers, which have been known to conflict with the intel ones after an upgrade:
```
sudo apt-get remove --purge nvidia*
```
Just make sure you check what it wants to remove before you agree.

---

