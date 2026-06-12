---
title: "lightdm / gdm broken after upgrade to 13.04"
date: 2013-04-30
forum: Installation &amp; Upgrades
---

### Post by HRH_H_Crab on 2013-04-30
I have upgraded to 13.04 (do-release-upgrade) and none of my greeters work.
Lightdm was giving just a black screen.
I've made the following edit:

```
[SeatDefaults]
user-session=ubuntu
#greeter-session=unity-greeter
greeter-session=lightdm-gtk-greeter
```

And now it displays the classic Ubuntu peach and purple background swirls and an X shaped cursor which tracks the mouse.
If I stop it (/etc/init.d/lightdm stop) and then start gdm (/etc/init.d/gdm start) I get the same display.

Otherwise these greeter screens are entirely featureless. No text entry fields, no buttons or widgets.

I have an ATI card with open source drivers.

My preference would be classic gnome, but I'll be "happy" to use Unity at the moment. Anything really...

Can anyone assist?

---

### Post by jsally on 2013-05-01
I have a similar problem. I posted Bug 1174950 to launchpad about this.

---

