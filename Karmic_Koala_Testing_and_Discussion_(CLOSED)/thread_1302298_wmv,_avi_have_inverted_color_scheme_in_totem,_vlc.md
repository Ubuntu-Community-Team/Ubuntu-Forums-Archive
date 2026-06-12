---
title: "wmv, avi have inverted color scheme in totem, vlc"
date: 2009-10-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by uschxc on 2009-10-26
not sure what info i need to provide, but this still hasn't been fixed and its becoming a concern.  i've attached a screen shot for sample

i am running nvidia driver 185

---

### Post by FuturePilot on 2009-10-26
Go to Edit > Preferences > Display tab and slide the Hue slider all the way to the right. It should [s]fix[/s] workaround both. It's an old bug with the way the Nvidia driver and gstreamer handle hue.

---

### Post by uschxc on 2009-10-26
> **FuturePilot said:**
> Go to Edit > Preferences > Display tab and slide the Hue slider all the way to the right. It should [s]fix[/s] workaround both. It's an old bug with the way the Nvidia driver and gstreamer handle hue.

aftering doing that, it just made it worse, then i brought it back to 0 and it was perfect.  it seemed that the dial reported 0, i suppose it read 0 from default configuration, but was actually running much higher.

---

### Post by uschxc on 2009-10-27
> **uschxc said:**
> aftering doing that, it just made it worse, then i brought it back to 0 and it was perfect.  it seemed that the dial reported 0, i suppose it read 0 from default configuration, but was actually running much higher.

so i didn't find the solution fully.  after re-entering 0 as the Hue value the colors for the video returned to normal.  i opened another one, and i then had one video playing right and another playing with inverted colors.  i then closed both and reopened both and they were both screwed up.

i restarted and opened a .wmv, then opened nvidia-settings and the colors corrected themselves.  opened up another .wmv with nvidia-settings still open and it came back with the screwed up colors.

it seems like i need to manually set the value in xorg.conf or something

---

