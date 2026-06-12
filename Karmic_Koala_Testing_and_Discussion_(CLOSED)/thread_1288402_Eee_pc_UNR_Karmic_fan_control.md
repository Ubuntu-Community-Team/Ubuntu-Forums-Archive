---
title: "Eee pc UNR Karmic fan control"
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by santaslittlehelper on 2009-10-11
I just installed UNR karmic on a eee-pc 900. 
I could give you a ”rant” about how great it looks and feels, because it really does, but I will spear you for now, lets just say that I am very happy with UNR.

I know it's still beta, which leads me to my problem. 
The CPU fan is at a 100% RPM all the time which is noisy.

There is a bug report on eee-applet which is not working at all...
Eee-control are not karmic ready as of yet...I think...
Eeepc-acpi-utilities seems discontinued...

Do anyone know of a way to bring the fan down somehow?

---

### Post by joee92 on 2009-10-11
I had the same problem with my eee 1000 and karmic ubuntu desktop (not UNR).  Here's what I do to control the fan manually:

```
sudo -i
echo 1 >/sys/devices/platform/eeepc/hwmon/hwmon1/pwm1_enable
echo 100 >/sys/devices/platform/eeepc/hwmon/hwmon1/pwm1
```

It looks like the useful range for pwm1 is 0-255.  [COLOR="Red"]NOTE: Running your fan too slow may cook your hardware, so do it at your own risk![/COLOR]

---

### Post by sgosnell on 2009-10-11
You're going to spear me?  With which spear?

---

### Post by santaslittlehelper on 2009-10-12
> **joee92 said:**
> I had the same problem with my eee 1000 and karmic ubuntu desktop (not UNR).  Here's what I do to control the fan manually:

```
sudo -i
echo 1 >/sys/devices/platform/eeepc/hwmon/hwmon1/pwm1_enable
echo 100 >/sys/devices/platform/eeepc/hwmon/hwmon1/pwm1
```

It looks like the useful range for pwm1 is 0-255.  [COLOR="Red"]NOTE: Running your fan too slow may cook your hardware, so do it at your own risk![/COLOR]
Thank you :)
> **sgosnell said:**
> You're going to spear me?  With which spear?
anD g1 :D my English could be better, you made me look it up, so thanks to you too.

---

