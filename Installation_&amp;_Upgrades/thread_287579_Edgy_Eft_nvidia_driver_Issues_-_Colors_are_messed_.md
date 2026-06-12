---
title: "Edgy Eft nvidia driver Issues - Colors are messed up"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by cpradio on 2006-10-28
I recently upgraded to Edgy Eft with a lot of hassle, but I finally worked my way around every problem to come up with a list of others.  However, I will only focus on one for now and might bring up the others later.

The nvidia driver shipped with Edgy Eft sucks.  It completely renders the primary monitor (when doing twinview at least) wrong.  In fact, it acts like its loading the primary monitor with the depth of 16 or below, as specific sections are discolored ([Tall Trees Wallpaper](http://www.kde-look.org/content/show.php?content=35488))

I tested this by loading the Dapper Drake Live CD and booting it up, loaded my wallpaper on the Live CD and it showed the colors just fine on my Primary Monitor.  Also, when I was running Edgy Eft, the wallpaper colors were again just fine.

I plan on tickering with other nvidia drivers later on, but its nearing Midnight (though I just realized we fall back an hour - so really its still and hour from midnight) here and I need some sleep.

Is anyone else noticing this problem?

---

### Post by cpradio on 2006-10-28
Odd thing just happened.  I ran sudo nvidia-settings in the terminal and the colors got corrected, I am not sure why yet, but that was very interesting.

Matt

---

### Post by rvdrijst on 2006-10-31
Hi Matt,

Same problem here: the upgrade introduced numerous problems, including the colors getting messed up. Your solution of sudo nvidia-settings seems to do the trick and in fact I have seen the problem disappear mysteriously before. 

However, every time I reboot, the colors are messed up again. So if you find a solution that fixes this problem once and for all, I'll be glad to hear it! And of course, I will post a solution if I find one.

-Robin

---

### Post by rvdrijst on 2006-11-29
Hi,

I still haven't found a proper solution to the 'colors-messed-up' problem but the easiest workaround seems to press ctrl+alt+backspace on every boot, it gets rid of the weird colors.

Also, these threads seem to be on the same (or very similar) problems:

[http://ubuntuforums.org/showthread.php?t=289116](http://ubuntuforums.org/showthread.php?t=289116)
[http://www.ubuntuforums.org/showthread.php?t=293364](http://www.ubuntuforums.org/showthread.php?t=293364)

the latter is a duplicate from a Kubuntu forum:
[http://kubuntuforums.net/forums/index.php?topic=10686.0](http://kubuntuforums.net/forums/index.php?topic=10686.0)

and these guys posted this as a bug on
[https://launchpad.net/distros/ubuntu/+bug/71094](https://launchpad.net/distros/ubuntu/+bug/71094)

So, has anyone a better solution than the ctrl+alt+backspace on reboot? It's very tricky to actually show the problem in a screenshot, because the issue is non-existent in the screenshot!

Thanks in advance for a definite solution,

-Robin

---

