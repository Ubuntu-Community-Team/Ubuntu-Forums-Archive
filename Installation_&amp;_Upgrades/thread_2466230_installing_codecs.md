---
title: "installing codecs"
date: 2021-08-23
forum: Installation &amp; Upgrades
---

### Post by josephfg on 2021-08-23
Hi,

I tried to install the codecs with 

```
sudo apt install ubuntu-restricted-extras
```

It stopped at some point so I quit, thinking to start again.

Now it displays

```
Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 2307 (apt) . . .
```

and a seconds counter that feeds me the same line again and again.

I have kind of spotty internet service where I am.  Could that be the culprit?

Thanks for all you do.

---

### Post by tea for one on 2021-08-23
> **josephfg said:**
> Hi,

I tried to install the codecs with 

```
sudo apt install ubuntu-restricted-extras
```

It stopped at some point so I quit, thinking to start again.

During the installation of [COLOR="#0000FF"]ubuntu-restricted-extras[/COLOR], it includes another package [COLOR="#0000FF"]ttf-mscorefonts-installer[/COLOR].

[COLOR="#0000FF"]ttf-mscorefonts-installer[/COLOR] requires the user to accept the terms and conditions and I reckon that this was not visible on your display, hence it appeared to stop.

When you try to install next time and it appears to pause, press TAB on your keyboard to see if you can access the accept/decline button.

---

### Post by josephfg on 2021-08-23
> **tea for one said:**
> During the installation of [COLOR=#0000FF]ubuntu-restricted-extras[/COLOR], it includes another package [COLOR=#0000FF]ttf-mscorefonts-installer[/COLOR].

[COLOR=#0000FF]ttf-mscorefonts-installer[/COLOR] requires the user to accept the terms and conditions and I reckon that this was not visible on your display, hence it appeared to stop.

When you try to install next time and it appears to pause, press TAB on your keyboard to see if you can access the accept/decline button.

Now no matter what I do it gives the "held by process 2307" message repeatedly, once per second.  This happens when I try install again and also happens when I try purge.

What is process 2307 or how do I find out?  It seems I'm worse off now than I was before I attempted the first install.  It also gives the same message when I start with [COLOR=#0000FF]ttf-mscorefonts-installer.[/COLOR] So I can't install that either.

---

### Post by grahammechanical on 2021-08-23
When we update the System or install or remove packages certain files are locked to prevent another command or utility from intefering in the process. That is what has happen here. The system is trying again and again to run the additional commands that you have entered and it is being prevented from doing so by the locked files or program.

Have you switched off and rebooted since this happened? You might need to do that.

Regards

---

### Post by josephfg on 2021-08-23
ok I rebooted and then I hit TAB to get to the OK button.  My mistake I should have known that, but thank you, now it is installing.

---

