---
title: "ATi Xpress Drivers 1150 Performance in Jaunty"
date: 2009-03-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by etherealeclipse on 2009-03-30
From reading it up I can see xorg 1.6 won't(?) have fglrx support for my card, ATI Technologies Inc **RS482** [Radeon Xpress 200M]. Thats fine but the open-source drivers should work with xorg 1.6 judging from the _[Ubuntu 9.04 Technical Overview]("http://www.ubuntu.com/testing/jaunty/beta#X.Org%20server%201.6")_, but they don't have half the performance I had in intrepid when I used them for a while. the mine problem is I'm getting more X crashes now for example holding the 'super key' + 'tab' for a while so the windows scroll rapidly always crashes X in about a second of doing so. Any way to boost performance? I know its the beta but still.
Any help is most appreciated Thanks.

EDIT: 'Side Quest' - How do I stop the system beep its rather annoying when restarting or shutting down.

---

### Post by kacperpl1 on 2009-04-12
Any updated info about this problem so far? I have the same card in my notebook and i can't find the fix for this piece of crap known as fglrx.
Is there any chance to install older driver from binary? When i try doing this i have "Error: ./default_policy.sh does not support version".

---

### Post by MALEADt on 2009-04-13
> **kacperpl1 said:**
> Is there any chance to install older driver from binary? When i try doing this i have "Error: ./default_policy.sh does not support version".

No, there is definitely not. The driver doesn't support the X server. End of line. Have fun repairing your X server if you persist on installing it.

About the scroll performance, check your Xorg.log if EXA is working.

About the sound problem, add this to /etc/modprobe/blacklist
```
# No PC spreaker
blacklist pcspkr
```
You might have to replace pcspkr with snd_spkr (check lsmod to see which of both is loaded right now), I'm working on Intrepid right now so I can't check it.

---

### Post by sergks on 2009-04-13
Have exactly the same problem:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/347569](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/347569)

---

