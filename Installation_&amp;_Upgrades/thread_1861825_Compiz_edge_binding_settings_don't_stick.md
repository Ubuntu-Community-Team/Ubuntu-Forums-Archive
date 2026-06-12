---
title: "Compiz edge binding settings don't stick"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by clegends on 2011-10-16
Hi people, just upgraded to 11.10 on my eeepc 901 netbook. I am running from a clean install.

I am having problems with some settings in compiz retaining the changes I make after each logout, as well as after each reboot. Tweaking compiz seems very buggy... I have installed ccsm, and am having to reset the edge bindings via it for  both the  expo plugin & scale plugin.

For some years now (on Ubuntu as well as other distros) I have set the top right edge binding for the scale plugin, and the bottom right edge binding for the expo plugin. Both these plugins are activated when I move my mouse cursor to that  edge. Now, while I can activate this after each login by opening up ccsm and choosing the appropriate setting, I need to d this after *every* boot-up or login. Very tedious. Either the edge bindings won't work, they are forgotten, or the Unity launcher won't unhide when I move my mouse to the left edge of the screen. Anyone elsehad this issue? 

I'd love some help debugging this, as well as finding a workaround.Cheers.

---

### Post by VadimLopatkin on 2011-10-16
The same problem, probably because of the last upgrade.

I have a conventional PC - not an netbook.

---

### Post by markb69 on 2011-10-16
Same problem after I upgraded. I have Expo on lower left screen and Workspace switcher on bottom right. I have open compizconfig and click Commands enable/disable to get it to work. I usually have to run unity --replace after to clean up window glitches. I am going to check launchpad and see if a bug has been filed or I will put one in for you.

---

### Post by clegends on 2011-10-16
Thanks for that. Can you please post back when you file a launchpad report, with the url? I'd like to follow that. For myself, I've temporarily given up on the edge bindings, and found that Oneiric is working beautifully now. The random crashes and freezes plaguing me since install have disappeared now.

I guess that's one of the difficulties of using compiz as the windows manager; tweaking it can have dire consequences. For now I'm using the Unity Launcher to switch windows, and it works really well. Cheers.

---

### Post by Biernak on 2011-10-17
Hey,
I found the solution on launchpad:

> Just edit /apps/compiz-1/general/screen0/options/active_plugins key in gconf-editor and place expo under unityshell...

which was posted by Diego Cortassa here:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/858845]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/858845")

It solved the problem for me, I hope it will help you too.

---

### Post by clegends on 2011-10-17
Thanks for that, works almost perfectly! My scale plugin (set to top right corner) now works flawlessly on every boot,and the expo plugin (set to bottom right corner) at least works now. The problem is that when I zoom into any desktop except the default desktop the computer boots into,then I get a black flash (momentarily goes blank, flickers really). It's surprisingly distracting. Am running an eeepc 901. Anyone else have this problem?

edit: meh...am getting the shits with this. Like before, it worked for awhile, then seems to provide me with random crashes and other strange glitches. Oneiric is visually very stunning... but buggy as hell. I find this so irritating, as I've just updated my perfectly working Natty to the latest. This sucks. Have finally switched to Unity 2d. I don't mind having to tweak things, but not being *able* to tweak things defeats me. Also random crashes suck. I have a new computer coming, and am considering installing Natty on it again, with a partition setup to keep bug testing. Oneiric. This release feels very undercooked to me.

Ok, rant over. That's what I get for not being involved in testing this latest release. Will have to keep more up to speed with 12.04, and contribute more than this rant. Anyone else having problems with random crashes (system freezes, really) and general compiz/unity instability? Cheers.

---

