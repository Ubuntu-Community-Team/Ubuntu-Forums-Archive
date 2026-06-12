---
title: "Laptop doesn't boot (starts beeping)"
date: 2008-10-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by krausest on 2008-10-05
My laptop (hp hdx 9400) works fine with 8.04, but I can't boot into 8.10 (no matter what kernel) unless I add vga=3 nosplash or similar to the kernel params. Otherwise the laptop starts to beep and within a few seconds it beeps continuously such that I have to shut it down.

Anyone else having this problem (maybe something about the vbe_init failed -22 message)?
How should I write a bug report for it? I must restart the laptop so early, that no file in /var/log is written.

---

### Post by autocrosser on 2008-10-05
Interesting--sounds like a bug that I've reported quite a while ago-- [https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/235662](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/235662)

It sounds like you have a more severe version of this bug--I will get BIOS warnings sometimes so severe that I need to reboot the unit--this is not happening all the time, but enough that it is a real problem.

Try booting with "nosplash" & then downloading v86d from synaptic--see if that helps..there are no "real" fixes yet for this one--ststus has been moved to high.

---

### Post by krausest on 2008-10-08
I've filed a bug at [https://bugs.launchpad.net/bugs/279187](https://bugs.launchpad.net/bugs/279187)
Hope it's getting fixed soon.

---

### Post by MacUntu on 2008-10-08
What happens if you remove all boot parameters except "ro"?

---

### Post by krausest on 2008-10-08
Hi MacUntu, 
I hope I was clear on that issue: As soon as the splash option is removed it boots fine (I think even just removing quiet or splash is enough). It's still a regression since it worked perfectly fine on 8.04.

---

### Post by autocrosser on 2008-10-08
New information: I've "cured" my BIOS beeping problem--look at my bugreport: [https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/235662](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/235662)  & also the referenced report with my comments at the bottom..that may "fix" your problems....

---

