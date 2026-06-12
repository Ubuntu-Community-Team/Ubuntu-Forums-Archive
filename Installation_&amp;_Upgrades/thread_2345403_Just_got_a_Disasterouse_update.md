---
title: "Just got a Disasterouse update"
date: 2016-12-03
forum: Installation &amp; Upgrades
---

### Post by Roland_Msl on 2016-12-03
I have Ubuntu 16.04 on an Acer ES1-331-C0YK
This has a Celeon N3150 with only 6 W TDP and 4,8 W typical.

Until now, this notebook had the following fan behavior:

After system start: Fan always on
After Suspend to RAM and wake up: never a fan

I just got an update and restarted. Fan always. Usual Suspend to RAM and wake up to end fan.

But this time, it's not like usual that the fan goes silent.

It starts any time, the CPU usage goes a little bit higher.
I can not work with such a noisy machine.

Was it really the last update?
What can I do against the fan terror?

---

### Post by Dennis N on 2016-12-03
> Was it really the last update?
It would help if you could list the packages in this update.

---

### Post by Roland_Msl on 2016-12-04
How?

I have now a proof. At my Acer ES1-331-C0YK did FN arrow left right until this update not work to change screen brightness.
Now this keys work to change screen brightness

Since May 18th, the fan did not start. Even at using ffmpeg for several hours using all 4 CPU 100%

Now the fan starts at 50 degree Celsius - shown with "sensors" in terminal

There is no /etc/fancontrol

sudo pwm-config

comes with
There are no pwm-capable sensor modules installed

but
sensors
shows the temp for each of 4 CPU

---

