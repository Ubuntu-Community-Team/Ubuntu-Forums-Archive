---
title: "Install on older machine?"
date: 2011-01-15
forum: Installation &amp; Upgrades
---

### Post by Ninesvnsicks on 2011-01-15
I just installed Ubuntu 10.10 on an older machine I had laying around it's a Pentium 3 1ghz and the install went fine but when it boots up the only thing that boots is the desktop there's no panels or anything else I'm not sure what is wrong with it.

---

### Post by garvinrick4 on 2011-01-15
Can you ctrl/alt/t and get  a terminal:
Or alt/f2

---

### Post by Ninesvnsicks on 2011-01-16
ok weird, this time it gave me a login I enter my passwd it lets me in i see the panels for 2 secs then it sends me back to login again so I login and it was working.  No idea what that's about anyways boxee wont run on it apparently so guess I'm stuck with another old comp i can't use lol.

---

### Post by Rubi1200 on 2011-01-16
Depending on the specifications, you may need to consider something 'lighter' like Xubuntu or Lubuntu.

---

### Post by TNT1 on 2011-01-16
> **Rubi1200 said:**
> Depending on the specifications, you may need to consider something 'lighter' like Xubuntu or Lubuntu.

Or something even lighter, like arch, slitaz or antiX:D

---

### Post by Ninesvnsicks on 2011-01-16
Yeah I've been trying to find some kind of jukebox software that will run but the built in video card is an old Intel 82810E so nothing I have tried so far runs.

---

### Post by TNT1 on 2011-01-16
> **Ninesvnsicks said:**
> Yeah I've been trying to find some kind of jukebox software that will run but the built in video card is an old Intel 82810E so nothing I have tried so far runs.

Try antiX or slitaz, good with old/slow hardware.

---

### Post by Rubi1200 on 2011-01-16
> **TNT1 said:**
> Try antiX or slitaz, good with old/slow hardware.
+1 to both suggestions

---

### Post by ronnielsen1 on 2011-01-16
oh come on people, it's a Pentium 3 1ghz. It should run fine. Where did you get your Ubuntu disk - Sounds like maybe a bad burn or something happened during the install. Try reinstalling with a new disk

---

### Post by Ninesvnsicks on 2011-01-16
> **ronnielsen1 said:**
> oh come on people, it's a Pentium 3 1ghz. It should run fine. Where did you get your Ubuntu disk - Sounds like maybe a bad burn or something happened during the install. Try reinstalling with a new disk

Ubuntu runs a little slow due to the video card but the main concern is Boxee (the whole reason i put ubuntu on0 doesn't run because the video card has no open gl or something.  So ubuntu is pointless on it atm.

---

### Post by LinUxaliVe on 2011-01-16
Ubuntu will run fine without (open)gl, but an app may require it...

I just installed Ubuntu 10.10 to an old PIII, 800Mhz, 512MB, using this method.

**1.** Remove the Gnome saturation of the OS: [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

If KDE is still too slow for your tastes, try something like OpenBox + Pypanel.

**2.** Remove all the excess junk: [http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

**3.** If the above two aren't enough on their own, try a different (supported) kernel: [https://wiki.ubuntu.com/RealTime](https://wiki.ubuntu.com/RealTime)

I'm posting from the machine now.

---

### Post by ronnielsen1 on 2011-01-16
> Ubuntu runs a little slow due to the video card but the main concern is Boxee (the whole reason i put ubuntu on0 doesn't run because the video card has no open gl or something. So ubuntu is pointless on it atm.Is your computer working fine EXCEPT for more graphics intensive programs? You might just need a video card driver. What video card is it? Post the output of[COLOR=Red] lspci -v[/COLOR] from a terminal

I reread your first post and I forgot about the missing panels and everything. I still think you probably need to reinstall but a video card driver can make alot of difference too

---

### Post by LinUxaliVe on 2011-01-18
Just thought I'd add that if you are using ext2, or preferably ext4, you should have them mounted with the 'noatime' option. I wouldn't use ext3 on an older PC, or even an older hard-drive.

---

