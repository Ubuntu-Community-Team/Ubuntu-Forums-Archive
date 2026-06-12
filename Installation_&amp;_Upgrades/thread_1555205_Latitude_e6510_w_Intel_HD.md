---
title: "Latitude e6510 w/ Intel HD"
date: 2010-08-17
forum: Installation &amp; Upgrades
---

### Post by acroporas on 2010-08-17
Can anyone help me install ubuntu on a Dell Latitude e6510 with Intel HD Graphics.  The live cd boots (can hear the welcome jingle) but the screen is blank.

---

### Post by acroporas on 2010-08-18
Bump

---

### Post by spcwingo on 2010-08-18
When booting from the live CD at the bottom there should be something to the effect of "other options".  It'll say what button to press to access it (I think it's F6).  After pressing the appropriate button at the end of the text enter this:

```
i915.modeset=1
```

If that doesn't work you can try:

```
i915.modeset=0
```

If that doesn't work either you could finally try:

```
xforcevesa
```

Let me know if this will at least get you video output...If so I'll help you get it installed and make that setting stick after installation.  :)

---

### Post by acroporas on 2010-08-18
Nope, none of those fix the problem.

It is closer though.  Before the screen would go black immediately after selecting "Try Ubuntu", with any of those options the screen would stay purple for a while, not going black until just moments before the desktop loaded.

---

### Post by spcwingo on 2010-08-18
The only other thing that I could think of to try is the 10.10 (Maverick Meerkat) Alpha release.  The ISO can be downloaded here:

[http://cdimage.ubuntu.com/cdimage/releases/maverick/alpha-3/]("http://cdimage.ubuntu.com/cdimage/releases/maverick/alpha-3/")

---

### Post by rioatca on 2010-08-19
On same boat :)

DELL Latitude E6510 with NV GEFORCE 310M :(

---

### Post by acroporas on 2010-08-19
10.10 does not do any better...

> **spcwingo said:**
> The only other thing that I could think of to try is the 10.10 (Maverick Meerkat) Alpha release.  The ISO can be downloaded here:

[http://cdimage.ubuntu.com/cdimage/releases/maverick/alpha-3/]("http://cdimage.ubuntu.com/cdimage/releases/maverick/alpha-3/")

---

### Post by spcwingo on 2010-08-19
> **rioatca said:**
> On same boat :)

DELL Latitude E6510 with NV GEFORCE 310M :(

Have you tried the:

```
xforcevesa
```

as above?

> **acroporas said:**
> 10.10 does not do any better...

I am at a loss at what to try next...those extra kernel parameters have worked on every Intel video chipset that I have tried so far (at least the ones that just output a black screen before).

I don't normally recommend older releases but, have you tried Hardy (8.04)?  Hardy has bang-up Intel video support.

---

### Post by rioatca on 2010-08-20
back to 9.0.4
it works

---

### Post by sambarluc on 2010-08-20
I have exactly the same problem, I can only use the low graphics mode if I add both options in grup i915.modesetsomething=0 AND xforcevesa.
Good luck

---

### Post by acroporas on 2010-08-20
10.10 - No screen output.
10.04 - No screen output.
9.10 - Screen works, but crashes IMMEDIATELY
9.04 - Neither the wired or wireless network works. Compiz does not work.

---

### Post by acroporas on 2010-08-20
> **sambarluc said:**
> I have exactly the same problem, I can only use the low graphics mode if I add both options in grup i915.modesetsomething=0 AND xforcevesa.
Good luck

This does work. I added "i915.modeset=0 xforcevesa"  and the live CD will boot.  No compiz :(  but better than nothing...

---

### Post by dfhoughton on 2010-09-23
I struggled with this for most of a day. Here are some tips I discovered in my struggles:
[LIST]
[*]You need to press shift, not escape, to get the GRUB menu with GRUB 2.
[*]The BIOS, I find, is a little flaky. If you press shift too soon it will throw a rod and die. Wait for the underscore cursor to appear. But don't wait too long! (See next point.)
[*]Getting the GRUB menu is like blowing up the Death Star. You have a small window of opportunity and you can't use instruments. You have to use the force to find that window. Holding shift doesn't work. Press the shift key manically and you are likely to get the menu.
[/LIST]

---

### Post by FredWst on 2010-10-06
Hello,

With Maverick RC, no need modeset and xforcevesa.
Just a little trick to make work with drm.
I boot my system until ear sound, i have black screen.
Just connect a LCD to VGA and remove it, and everything will be OK.
It's working on both 32 and 64 bits OS

Have someone fixe this ?

Fred

---

