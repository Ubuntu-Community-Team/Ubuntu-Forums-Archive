---
title: "Laptop with Centrino Technology - safe CPU adjustment ?"
date: 2005-07-30
forum: Installation &amp; Upgrades
---

### Post by jemt on 2005-07-30
Hi Experts.

I have been playing around with Ubuntu for the last couple of days to make it function the way I want. I'm now almost ready to install it on my brand new IBM X31 laptop with Centrino technology. But I must admit that I'm a little nervous when it comes to battery management and CPU scaling (Speed Step technology).

I can see that apt-get offers me 'cpudyn' and 'cpufreqd' as CPU frequence controllers. But are the both compatible with Pentium M (Centrino) and could a bug result in a defect CPU ? I don't want my new computer to break into fire. What do you guys use?

Also does the basic Ubuntu system (minimal installation) provide good battery management? I know from Windows that battery management tools can make the computer use less power by ie. reducing CPU frequency - but i'm not sure if this is the same as the speedstep technology. But my IBM comes with a program that makes it possible to charge the battery much faster - which means that there must be some kind of battery management. But i'm pretty sure that this could result in a bad battery if it dosn't get charged correctly. So i'm nervous that Ubuntu might damage my battery too.

Is there really anything to worry about?

 - Thanks in advance :)

---

### Post by jemt on 2005-07-30
Hm, just did a 'apt-cache search cpu' - I can see that there is a little more than just two CPU Frequency Controllers available.

---

### Post by kleeman on 2005-07-30
Don't know about the battery but the centrino cpu speedup and slow down works really well on my centrino laptop. You can watch it interactively by enabling the appropriate applet in Gnome (cpu frequency scaling monitor). One thing to watch out for is smp - the cpufreq stuff doesn't work with smp kernels.

---

### Post by kleeman on 2005-07-30
The powernowd package is in main while the others are in universe so I would try that first....

---

### Post by jemt on 2005-07-30
Don't know about the battery but the centrino cpu speedup and slow down works really well on my centrino laptop. You can watch it interactively by enabling the appropriate applet in Gnome (cpu frequency scaling monitor). One thing to watch out for is smp - the cpufreq stuff doesn't work with smp kernels.

Hi.

Thanks for your answer. I'm not running Gnome though. So I need to be sure what software to install. I have performed a Minimal/Server installation and installed xorg and Xfce4 using apt-get.

What software exactly do I need in order to get (SAFE!!) CPU scaling? I can see that apt-get offers me 'powernowd' (control cpu speed and voltage using 2.6 kernel interface). Is this the tool you use?

---

### Post by jemt on 2005-07-30
Thanks for the 'powernowd' answer :)

---

