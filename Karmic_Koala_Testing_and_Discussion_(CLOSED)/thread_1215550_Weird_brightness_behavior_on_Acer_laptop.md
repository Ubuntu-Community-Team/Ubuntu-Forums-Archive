---
title: "Weird brightness behavior on Acer laptop"
date: 2009-07-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rodrigocastrillon on 2009-07-17
Hello everyone.

I'll post this here before creating a new bug on Launchpad, maybe it can be fixed somehow.

This is what I'm experiencing:

- If brightnes = 0:
1. I press "Fn + >" and brightness increase one step;
2. Press "Fn + >" again and another step is increased;
3. Press "Fn + >" again, but this time 2 steps are increased;
4. "Fn + >" increases another 2 steps;
5. "Fn + >" increases another 2 steps;
6. "Fn + >" increases another 1 step and maximum brightness is reached;

- If brightness = 10:
  Same situation happens, but backwards.

- If increasing but decreasing before reach 10:
1. I press "Fn + >" and brightness increase one or two steps;
2. Press "Fn + <" and brightness decrease one step, as expected, BUT brightness notification popup shows that the brightness is **increasing**;
   This also happens backwards.

I have Karmic with ALL updates installed (until now) and I'm running on latest kernel. My laptop is an Acer 5315-2940.

Is there any other information that I can provide to help to get this fixed?

---

### Post by Rackstar on 2009-07-18
I had similar strange behaviour with versions < 9.10 with my Acer Aspire laptop. Didn't test it on karmic

---

### Post by rodrigocastrillon on 2009-07-18
Please run your tests in Karmic, so I can open a bug report... Then Canonical can fix it, so you'll get a perfect operating system when you install Karmic Final :D
Oh, and in order to help other Acer users too :)

Best regards!

---

### Post by taavikko on 2009-07-18
> **rodrigocastrillon said:**
> Please run your tests in Karmic, so I can open a bug report... 

You don't need confirmation on other users to report a bug, please do so immediately so it might eventually be fixed.

---

