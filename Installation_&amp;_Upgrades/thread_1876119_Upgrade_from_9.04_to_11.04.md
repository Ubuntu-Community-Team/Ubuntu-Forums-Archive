---
title: "Upgrade from 9.04 to 11.04"
date: 2011-11-05
forum: Installation &amp; Upgrades
---

### Post by joyneo05 on 2011-11-05
Hi all,

Today I have installed Ubuntu 9.04 as this was the only Ubuntu bootable CD available with me. Now I want to upgrade it to the latest version of Ubuntu. Kindly help me as I am not getting any details in the update manager.

---

### Post by darkod on 2011-11-05
You can not upgrade directly to 11.04. You can only upgrade directly from one LTS version to the next one.

It's much better if you burn another CD with 11.04 or the latest 11.10 and install again.

Otherwise you would have to upgrade version by version and by the time you get to 11.04 (or 11.10) that will probably create too much issues and instability.

---

### Post by joyneo05 on 2011-11-05
Hi,

9.04 is also ok for me, but would like to know whether software like vlc and adobe flash players have been upgraded, because I tried to install VLC and flash player but it started giving error as command not found... :(

---

### Post by darkod on 2011-11-05
No, most of the packages in the repositories are not upgraded. The newer versions of ubuntu come with newer software but it is not updated for the older ones.

However, if you are interested in particular software, the manufacturer might have versions for ubuntu that you can download and install.

---

### Post by joyneo05 on 2011-11-05
Hi Darko,

Thanks for prompt reply. Actually I have checked in google and downloaded the ones named for it. Also I have tried to install the same through terminal by writing sudo apt-get install vlc.
But post that it is saying that command not found....

---

### Post by Kyoushuu on 2011-11-05
Try "aptitude":
```
sudo aptitude install vlc
```

---

### Post by joyneo05 on 2011-11-05
Hi all,

I have started the update manager and am now upgrading myself to 9.10. let me see what is happening. Will let you all know once it is done.

---

### Post by joyneo05 on 2011-11-06
Hi,

My upgrade is done successfully. Now I'm on 9.10. I have installed VLC also. But now the worst thing is sound is not coming from the speaker although audio output is coming from headphones.
It is a HP compaq 420 notebook series.

---

### Post by vicshrike on 2011-11-06
Good luck with your upgrade project, but you should really consider a reinstall, these old Ubuntu versions are not longer supported and even if you should succeed, the risk of getting a borked system is not only big but for sure.

---

### Post by Kyoushuu on 2011-11-06
I also recommend doing a reinstall; if you're in an old version (not Lucid LTS [10.04] or Oneiric [11.10]), other people won't be able to help you.

---

### Post by joyneo05 on 2011-11-19
Hi,

Now I am successful in upgrading to 10.04. Now I want to upgrade to 10.10 but I am not getting the upgrade option in update manager. Also My speakers are not working now, although I can listen to music through the headphone and VLC player.

I am using a HP compaq notepad (Compaq - 420). Need your help.

---

