---
title: "gstreamer 1.19.1 with ubuntu 20.04 / 18.04"
date: 2021-06-08
forum: Installation &amp; Upgrades
---

### Post by researchboy on 2021-06-08
By default the gstreamer version in ubuntu 20.04 is 1.16 and for 18.04 is 1.14.
What i need to use is the latest gstreamer functionalities with  of ubuntu.

What i have tried in both versions.

1) Removed gstreamer using "apt purge *gstreamer*
Issue : this will remove the default displlay driver gdm3
2) Builded the gstreamer version 1.19.1 and installed 
3) Installed back gdm3 

After restart the display is stuck in black flickering screen.
Seems like a display manager issue, how to resolve this.

Let me if there is anything i did wrong.
Kindly ask if you need any more details.

Thankyou

---

### Post by MAFoElffen on 2021-06-10
Well first, basically, you removed gdm3, which is not a display driver, but nor is gstreamer.

GDM3 is the default "Display Manager"... which in Unix and Linux lingo, basically means that is the Graphical Logon Manager before it switches over to the Graphical Desktop Theme. If you uninstall that piece then you have to manually login and start the XServer to get graphics on the desktop.(again, I say "Manually")

The layers go: the Linux Core, a Graphical Login Manager (optional), XServer, a Desktop Theme, Application Plugin Helpers, Applications. Alsa and GStreamer are in that Application Plugin Helpers layer.

Now to recover from what you have done, look in my signature line and follow the link to my Graphics Resolution Sticky. Go to the second post and find the link to my instruction on how to temporarily boot into a text console. From there install "GDM3" so you can get back to where you were.
```

sudo install gdm3

```
After you get recovered to there, or have problems recovering, post back and we'll go from there.

---

