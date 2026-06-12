---
title: "i855gm graphics from 9.10 to 10.04.1 LTS"
date: 2010-11-01
forum: Installation &amp; Upgrades
---

### Post by Slash621 on 2010-11-01
I'm thinking of upgrading from 9.10 to 10.04.1 LTS to have the support during the rest of my bachelors degree.  I'm trying to keep my old Acer 290LMi alive as a note taking and basic office machine.

I want to move to the LTS version in order to keep updated in terms of security and with the latest software, but the last couple times I've installed 10.04.1 I have had graphics problems.

I know of the general linux 855gm problems, but I wanted to see if 10.04.1 LTS had those taken care of in the short term.  

I've also seen Glasen's ISO for Lucid LTS and the live CD still had the same problems I had during my install yesterday as I did with the normal 10.04 (without the .01 LTS at the end) almost 6 months ago.

Is there any easy way of doing this? I am intimidated slightly by all the command line stuff I'm seeing in the Lucidi855gm wiki is telling me to do.

---

### Post by Rubi1200 on 2010-11-02
There is absolutely no reason to feel intimidated by the commands that need to be run.

Four commands and your machine with i855gm will run just fine; I have tested this workaround and have had no problems with it.

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

Run the commands separately in this order:
```
sudo add-apt-repository ppa:glasen/intel-driver
```

```
sudo apt-get update && sudo apt-get upgrade
```

Reboot

```
sudo add-apt-repository ppa:glasen/855gm-fix
```

```
sudo apt-get update && sudo apt-get install dkms 855gm-fix-dkms
```

Make sure you keep the machine updated with the Glasen PPA updates and you should be good to go.

I hope this convinces you to upgrade to 10.04

---

### Post by Slash621 on 2011-01-11
I know this is gravedigging, but given..

[https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus)

..

should I just go straight to 10.10 and see what happens?

---

### Post by Rubi1200 on 2011-01-11
The same fix for 10.04 applies to 10.10, but with one difference; Compiz (desktop effects) won't work on 10.10. If that doesn't bother you, then sure go ahead and use 10.10.

I have tested the fix on 10.10 and it works great.

Stefan Glasenhardt, who packaged the fix, told me that he _hopes_ all these issues with Intel i8xxx chipsets will be resolved in 11.04.

---

### Post by davidmohammed on 2011-01-11
rubi1200 - did you try the [Brian Roger]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/541511/comments/427")s fix? - this worked brilliantly for me in lucid - compiz effects also worked as well.  Glasenhardt fix still gave me occasional lockups - Brians does not.

---

### Post by Slash621 on 2011-01-11
Im not sure I really care about the effects.  I just want the most recent security updates and the ability to run open office and take notes at school....

Also, using just software I can still watch youtube, just maybe not fullscreen.  Not a big deal.

---

### Post by Rubi1200 on 2011-01-12
> **davidmohammed said:**
> rubi1200 - did you try the [Brian Roger]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/541511/comments/427")s fix? - this worked brilliantly for me in lucid - compiz effects also worked as well.  Glasenhardt fix still gave me occasional lockups - Brians does not.

No, I haven't. Thanks for the link; will definitely check it out at some point.

---

