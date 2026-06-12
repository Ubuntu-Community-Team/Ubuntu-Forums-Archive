---
title: "Wolfenstein ET"
date: 2006-10-14
forum: Installation &amp; Upgrades
---

### Post by Sambie on 2006-10-14
After downloading and installing ET sucessfully (well almost) I manage to open up the application but notice that while the game was loading up that the sounds are some how disabled or not seen.. Is their anyway for me to fix this?

---

### Post by factotum218 on 2006-11-03
i have the same issue no sound, really slow (unusable), not full screen. Even with the nvidia-glx and all that installed its completely fubared.

---

### Post by wijet on 2006-11-03
I have this same problem when in background run kaffeine or amarok(even music doesn't play). Just shutdown audio players,

---

### Post by jdaviespa on 2007-05-01
i am expereanceing these issues as well, i downloaded "et-linux-2.60.x86.run" i had to run a chmod + command in the terminal before it would execute the code and install, even now i have to run a +set r_allowSoftware GL 1 command inorder to get the program to run but there is no sound and the program is unusable slow, realy realy, realy, slowwwwww......

---

### Post by Sumtn on 2007-05-01
yes it is going very slow for me aswell..... i was wondering if there was a code the will replace the libGL to my nvidia Card

---

### Post by Danwright on 2007-06-01
> **factotum218 said:**
> i have the same issue no sound, really slow (unusable), not full screen. Even with the nvidia-glx and all that installed its completely fubared.

i managed to fix the sound issue but still cannot get full screen, it goes into full screen mode but 1/4 of the screen is black.

to fix the sound try this:

```
sudo -s
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
Exit
```

then exit all music players and programs, and load ET again

```
killall esd
et
```

this worked for my sound, if anyone as any suggestions about the full screen mode i would like to hear them.

---

