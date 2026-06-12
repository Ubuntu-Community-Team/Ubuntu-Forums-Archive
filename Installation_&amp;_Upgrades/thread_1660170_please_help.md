---
title: "please help"
date: 2011-01-05
forum: Installation &amp; Upgrades
---

### Post by Lielith on 2011-01-05
[LIST=1]
[*]I just installed 10.10 on my gateway 3040 GZ and everything went great except sound does not work. The computer says every thing is working but there is no sound. And yes I checked the usual like the mute and all that jazz. Any advice would be most appreciated!! I am new to forums and ubuntulinux so am not sure what the prefix is all about but i picked the one that seemed to fit I hope.
[/LIST]

---

### Post by dino99 on 2011-01-05
is your sound hardware well identified: system pref sound ?

with synaptic: install gnome-alsamixer and set your prefs (applications sound alsamixer)

check the system:

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by Lielith on 2011-01-06
Thanks bro!! I never thought it would be that simple!! I was geeking out like a little girl over her first when I heard the sound come on. For any one else reading you got to turn the external audio booster off in the alsa mixer after you down load it!!\\:D/

---

