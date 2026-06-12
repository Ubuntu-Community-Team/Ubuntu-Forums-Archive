---
title: "loading screen hangs"
date: 2008-10-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by magicmanfk on 2008-10-05
about half the time, when I boot up ubuntu, the loading screen with the word "ubuntu" and the loading bar freezes about 2 and a fourth bars in and doesn't start again. If I force a shutdown and try again it usually works, but the error still occurs about half of the time. Any suggestions?

Thanks
Franklin

---

### Post by autocrosser on 2008-10-05
The first thing you need to do is edit your menu.list & put "nosplash" instead of "quiet splash" at the end of the kernel line you are using. That way you can watch the load & see where it stops, or if that "fixes" your problem. There are a couple of bugs with usplash currently & that will check for them. If you still have a load "hang", you will be able to see what is causing it.

In any case, that is the first step.....

---

### Post by magicmanfk on 2008-10-05
ok, so I tried it and it hung on the line:

"iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels"

So, I assume that this is some sort of problem loading my intel wireless card...

---

### Post by wgrant on 2008-10-05
> **magicmanfk said:**
> ok, so I tried it and it hung on the line:

"iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels"

So, I assume that this is some sort of problem loading my intel wireless card...

[File a bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+filebug"), with details of your hardware and the boot log (ideally for both successful and failed boots).

---

