---
title: "gnumeric bug"
date: 2014-06-05
forum: Installation &amp; Upgrades
---

### Post by Azzurra on 2014-06-05
Hi Ubuntu community!!!

I have recently ungraded my Ubuntu to 14.04 and I must use gnumeric for my work, since Libreoffice spreadsheet is not very confortable. With the upgraded version of Ubuntu, I have a problem that does not allow me to work properly. When I build a graph, the graph options window is very small and I cannot see all the options without using the scrollbar. This is very annoing for working and it takes times to prepare a graph.
Does someone have the same problem?
If this bug has not been fixed, could anyone suggest me a spredsheet programm instead of gnumeric and libreoffice?

Thank you all!!!

Azzurra

---

### Post by Elfy on 2014-06-05
See where the mouse pointer is in the screenshot - you should see somewhere on your's to drag the bottom part of the customise dialogue down.

If that is not what you mean then can you do a screenshot to describe what your problem is.

---

### Post by Azzurra on 2014-06-05
Thanks Elfy!!
That is the point...I do not see the "three sall bars" wher the mouse pointer is in your screenshot. As a result, the bottom part of the screenshot is very very small in my case. What do you think it depends on?

---

### Post by Elfy on 2014-06-05
I've just checked in 14.04 - the resize handle is there in the version I've got there too.

Can you check which version you have, also what themes are you using - I'll check again if it's not default greybird.

---

### Post by Azzurra on 2014-06-05
The gnumeric version I have is 1.12.9.
As reagrds themes...what do you mean? I do not know where to look at! What is "greybird"?

---

### Post by Elfy on 2014-06-05
Also please check in your .config folder for a gnumeric entry.

That said it appears to be a bug, screenshot in there seems to be the same, they upgraded as well - [https://bugs.launchpad.net/ubuntu/+source/gnumeric/+bug/1314393](https://bugs.launchpad.net/ubuntu/+source/gnumeric/+bug/1314393)

Mark yourself as affected too - [https://bugs.launchpad.net/ubuntu/+source/gnumeric/+bug/1314393/+affectsmetoo](https://bugs.launchpad.net/ubuntu/+source/gnumeric/+bug/1314393/+affectsmetoo)

Try purging and reinstalling gnumeric

```
sudo apt-get purge gnumeric && sudo apt-get install gnumeric
```

Forget the theme :)

---

### Post by monkeybrain20122 on 2014-06-05
> **Elfy said:**
> Run ```
xfce4-appearance-settings
``` in a terminal, what theme does is say it's using.


OP doesn't appear to be using Xubuntu.

---

### Post by Elfy on 2014-06-05
> **monkeybrain20122 said:**
> OP doesn't appear to be using Xubuntu.

Thanks missed that.

---

### Post by Azzurra on 2014-06-05
1) the answer is: Ambience
2) there is not a gnumeric entry in .config

I tried to purge and re-install but nothing happend...
so do I just need to wait for the bug fixing???

---

### Post by Azzurra on 2014-06-05
or maybe i could downgrade the gnumeric version?

---

### Post by monkeybrain20122 on 2014-06-05
I added an 'affects me too' even though I don't use gnumeric. It is very bad that by keep changing cosmetic stuffs like menus and screw up people's productivity tools (it only affects Unity, it seems)

Meanwhile I don't know what you do with spreadsheet, but for data analysis and graphing you may try pspp ( pspp also has sort of a bug in Unity, in that the output window is so small that it practically becomes a dot, but this happens only on first launch, if you drag open the window after that subsequent output windows become normal) 

Edited: Not sure if it is a gnumeric bug or something to do with Unity (as Elfy's version works in Xfce), so you can grab a .deb from 13.10's repo and try install it (then pin the version in synaptic so it doesn't get upgraded), use an alternative (like PSPP) or install another DE to switch to (like lxde) when you use gnumeric

---

### Post by Elfy on 2014-06-05
> **monkeybrain20122 said:**
> I added an 'affects me too' even though I don't use gnumeric. It is very bad that people's productivity tools don't work IMO....

Edited: Not sure if it is a gnumeric bug or something to do with Unity (as Elfy's version works in Xfce), so you can grab a .deb from 13.10's repo and try install it (then pin the version in synaptic so it doesn't get upgraded), use an alternative (like PSPP) or install another DE to switch to (like lxde) when you use gnumeric

+1 to that.

The bug is gnumeric in Ubuntu - so perhaps it is an Ubuntu/Unity specific issue. Would *appear*so.

I've booted a trusty vm - but that is an Xubuntu one.

I installed the Saucy versions of both gnumeric and gnumeric-common - works ok in the VM. But whether you'd get any other issues in Ubuntu I don't know.

[http://packages.ubuntu.com/saucy/gnumeric](http://packages.ubuntu.com/saucy/gnumeric)
[http://packages.ubuntu.com/saucy/gnumeric-common](http://packages.ubuntu.com/saucy/gnumeric-common)

---

### Post by monkeybrain20122 on 2014-06-05
For alternative desktop, strikes out lxde, it seems that gnome-session-flashback would make more sense as it is more compatible with Unity and wouldn't bring in a lot of dependencies.

---

### Post by Azzurra on 2014-06-23
I followed Elfy's suggestion downgrading Gnumeric to 1.12.6. However, the same prolem persists. That is, I do think the problem is not about gnumeric but Ubuntu 14.04.
Does anyone have any ideas?
I do not know what "gnome-session-flashback" is and how it can help. Could you help me please?

Thanks

---

### Post by Dave J on 2014-07-25
Hi folks,
Any more ideas about this problem with gnumeric? I recently upgraded to Linux Mint 17 and have the exact same problem. 
I removed gnumeric 1.12.9 (default version) and installed  1.12.6 - problem remains identically. Seems like a  problem with underlying Ubuntu (Trusty in my case).
Has anyone loaded latest version (1.12.17) from gnumeric and found success? I haven't figured out how to work thru source code install there, so if that works, advice/pointers would be greatly appreciated.
Thanks in advance

---

### Post by urchinstar47 on 2014-07-28
I'm curious about this problem as I'm preparing for an upgrade to 14.04 and I need Gnumeric to run. Does the problem persist with a straigth (tiling) window manager (without DEs)?

---

### Post by m4r35n357 on 2014-07-31
Confirmed here on Xubuntu 14.04.  It's REALLY annoying, looks like I can't switch over from my Debian Wheezy machine just yet . . .
Anyone know of any timetable for a fix?

---

### Post by monkeybrain20122 on 2014-07-31
Well if you ever want it fixed you have to let the developers know by adding an "affect me too" in the bug report. But the bug affects only 3 people including myself (it doesn't really affect me, as I don't use gnumeric) Excluding myself there are more than 3 people on this page alone who claim to be affected, where are their 'affects me too"?

---

### Post by Dennis N on 2014-07-31
Reverting to gnumeric 1.10.17 solves the problem in Xubuntu 14.04 

In Xubuntu 14.04, I found the chart dialog is ok when first constructing a chart. After inserting my chart, then using properties to edit, the problem appears (same thing as shown in the image of the bug report).

In Xubuntu 12.04, this problem does not occur. 

So, in Xubuntu 14.04, I removed gnumeric, gnumeric-common, and gnumeric-doc. I downloaded the .deb files of the first two packages for version 1.10.17 and installed those with gdebi (I didn't install gnumeric-doc). gnumeric-common must be installed before gnumeric. Two additional dependencies were needed. After this, the chart dialog problem was gone. All seems ok after some brief testing.

If you do this, be sure to lock the version or you will be pestered to upgrade gnumeric.

---

### Post by vasa1 on 2014-08-01
> **urchinstar47 said:**
> I'm curious about this problem as I'm preparing for an upgrade to 14.04 and I need Gnumeric to run. Does the problem persist with a straigth (tiling) window manager (without DEs)?

Same problem with an Openbox session (stacking WM), no DE, in Lubuntu 14.04.

---

### Post by m4r35n357 on 2014-08-01
Didn't know about that; now done.

---

### Post by urchinstar47 on 2014-08-03
> **vasa1 said:**
> Same problem with an Openbox session (stacking WM), no DE, in Lubuntu 14.04.

Thanks for the report. Untill it's fixed, I'll consider 14.04 unusable.

---

### Post by bolsmanfan on 2015-05-06
> **Dennis N said:**
> Reverting to gnumeric 1.10.17 solves the problem in Xubuntu 14.04 

In Xubuntu 14.04, I found the chart dialog is ok when first constructing a chart. After inserting my chart, then using properties to edit, the problem appears (same thing as shown in the image of the bug report).

In Xubuntu 12.04, this problem does not occur. 

So, in Xubuntu 14.04, I removed gnumeric, gnumeric-common, and gnumeric-doc. I downloaded the .deb files of the first two packages for version 1.10.17 and installed those with gdebi (I didn't install gnumeric-doc). gnumeric-common must be installed before gnumeric. Two additional dependencies were needed. After this, the chart dialog problem was gone. All seems ok after some brief testing.

If you do this, be sure to lock the version or you will be pestered to upgrade gnumeric.

Thank you!
That will do for me.
It really works on Ubuntu-14.04 with Awesome.

---

