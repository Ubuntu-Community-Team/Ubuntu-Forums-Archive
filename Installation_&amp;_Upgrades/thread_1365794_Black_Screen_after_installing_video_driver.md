---
title: "Black Screen after installing video driver"
date: 2009-12-27
forum: Installation &amp; Upgrades
---

### Post by van1017 on 2009-12-27
Hello all,

I'm completely new here. In fact, I will freely admit that this is my first day trying to use any operating system (for personal use) other than a variation of Windows. Because of this, my knowledge of Ubuntu is practically nonexistent. So please, be patient with me and if you could explain things in as simple of a manner as possible, I would be grateful...

Anyway, here's my situation. I just got a new computer a few days ago, and I wanted to try out Ubuntu on it. I used the Wubi installer and everything seemed to go alright. Then I tried to enhance the visual effects. I selected the normal effects and it said that I needed to download a different driver. I did so, restarted as it told me to do, and then my screen went black on the next start-up screen. Mind you, I could still log in, but I had to do so without actually seeing anything. So, it still works, I just can't see squat.

I did a fresh install and tried to do the same thing again, and got the same result. I tried it a third time, and alas, same thing. So now I'm here, asking for help...

Thanks in advance for any help that any of you can give me...

---

### Post by van1017 on 2009-12-28
I don't know what the policy on "bumping" is around here, but I guess I'll give it a go.

My situation hasn't really changed, either...

---

### Post by MelDJ on 2009-12-28
what graphics card do you have?

---

### Post by van1017 on 2009-12-28
NVIDIA® GeForce® G210M GPU (256MB VRAM)

---

### Post by MelDJ on 2009-12-28
have you tried installing the drivers available from the nvidia site? [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

---

### Post by beany1 on 2009-12-28
i did a google and found same problem in a dif thread.. [http://ubuntuforums.org/showthread.php?p=8556793#post8556793]("http://ubuntuforums.org/showthread.php?p=8556793#post8556793")
they seemed to solve it by making a custom x11 file..
from info on here
[http://www.nvnews.net/vbulletin/showpost.php?p=2118873&postcount=22]("http://www.nvnews.net/vbulletin/showpost.php?p=2118873&postcount=22")
problem with the driver not detecting the EID or something lolz, but if you follow it others have had success!

---

### Post by van1017 on 2009-12-28
> **MelDJ said:**
> have you tried installing the drivers available from the nvidia site? [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

My drivers seem to be up to date.

However, I did make an unusual discovery. I hooked up my external monitor and tried booting up, and to my surprise, I could see everything... Just only on the external monitor. Furthermore, I was able to set the graphics to the highest setting. 

So I guess my problem has changed a bit. Do you know what could be happening and how I can get this to work on my laptop without the external monitor?

(And feel free to make me feel like an idiot if the answer is simple)

---

### Post by beany1 on 2009-12-28
yeah its caus theres some problem with the driver, so when you install the nvidia ones it cant pick up your laptop screens EDID which makes it work, if you get this info from windows and change your X11 file itl apparo work following the links i gave

---

### Post by van1017 on 2009-12-28
> **beany1 said:**
> yeah its caus theres some problem with the driver, so when you install the nvidia ones it cant pick up your laptop screens EDID which makes it work, if you get this info from windows and change your X11 file itl apparo work following the links i gave

Ok, I read through the steps that I apparently have to take to get it working, and they kind of went over my head (I'm extremely new at this). So, I'm going to continue to fool around with Ubuntu on my external monitor for a while until I feel more comfortable with it before I attempt the fix. 

If at that time, it doesn't work, I'll post again in this thread. And thank you very much for the help...

---

