---
title: "freezing problems after upgrade from 10.04 to 10.10"
date: 2010-11-23
forum: Installation &amp; Upgrades
---

### Post by bg123 on 2010-11-23
Upgraded from 10.04 to 10.10. Applications freeze intermittently but release with Esc. Movie players acts up with interrupted play as well as fast forward and sound and visual sync. Skype relays interrupted sound intermittently. Problem gives impression of poor RAM performance but problem immediately after upgrade leaves doubt.

---

### Post by sikander3786 on 2010-11-23
Can you please post some more details regarding your hardware specs i.e, RAM, graphics card, cpu etc.

Also, do you notice any specific application running while the freeze happens or it is just random?

And did you enable compiz?

---

### Post by bg123 on 2010-11-24
Applications freeze without pattern or preference. All applications tend to freeze, Open Office more when I use the slide bar. With regard the hardware spec, I feel stupid to say I cannot locate the details with Ubuntu, Windows was not a problem. Unfortunately I am not dug into Ubuntu/Linux yet, but in time.....

---

### Post by sikander3786 on 2010-11-24
> **bg123 said:**
> Applications freeze without pattern or preference. All applications tend to freeze, Open Office more when I use the slide bar. With regard the hardware spec, I feel stupid to say I cannot locate the details with Ubuntu, Windows was not a problem. Unfortunately I am not dug into Ubuntu/Linux yet, but in time.....
Go to Applications > Accessories > Terminal and post the output of

```
lspci | grep VGA
```

and

```
free
```

Thanks.

---

### Post by bg123 on 2010-11-24
VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)

             total       used       free     shared    buffers     cached
Mem:        986520     922920      63600          0      63132     583768
-/+ buffers/cache:     276020     710500
Swap:      2890748          0    2890748


Thank you, I will try to remember. I suppose Ubuntu will soon provide easier routes for the not so well informed.

And I did not enable compiz, can you please eleborate. 
Again, thank you for taking the time to help out

---

### Post by sikander3786 on 2010-11-24
Ok. Please post the output of

```
cat /etc/X11/xorg.conf
```

and also attach the Xorg.0.log file found under /var/log.

You should remember that solving some freeze problems are not easy as we don't know what is causing those freezes. We'll have to go step by step, so, be patient!

Thanks.

---

### Post by bg123 on 2010-11-25
cat: /etc/X11/xorg.conf: No such file or directory

Thanks

---

### Post by bg123 on 2010-11-25
[COLOR=Blue][I]and also attach the Xorg.0.log file found under /var/log.
[/I][/COLOR]
Gives me Upload Errors  "invalid file"

Tried both new and old file

---

### Post by sikander3786 on 2010-11-25
Ok before doing anything else, try reconfiguring your graphics by,

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Reboot and see if there seems to be any improvement.

---

### Post by bg123 on 2010-11-25
Movie player and VLC seems to be sorted. Thank you.
Although both refuse some DVD's, reason unclear, but let that be a problem for another day.

Freezing a lot less frequent, clear improvement. Will test Skype tomorrow and let you know.

Again, thank you.

(Considered reloading, do not know if that is possible, but it does not seem to be a solution in any case?)

---

### Post by sikander3786 on 2010-11-25
You are Welcome :-)

Lets see how your PC behaves now...

> (Considered reloading, do not know if that is possible, but it does not seem to be a solution in any case?)

Are you talking about a re-install?

And yes, that DVD play back issue needs to go to another thread ;-)

---

### Post by bg123 on 2010-11-26
Skype also still messy, distorted and broken sound

---

### Post by bg123 on 2010-11-26
Yes, re-install was on my mind but it seems not to be the solution?

---

### Post by bg123 on 2010-11-27
Installed fixes for video player which solved that issue, then after last Ubuntu update, 12 hours ago, no more freezing. Skype is clear and crisp. Problem seems to be solved.

Thank you for the time and effort.

---

### Post by sikander3786 on 2010-11-27
You are Welcome :-)

Glad to know that remaining issues have been sorted by the updates.

Happy Ubuntu-ing!

---

