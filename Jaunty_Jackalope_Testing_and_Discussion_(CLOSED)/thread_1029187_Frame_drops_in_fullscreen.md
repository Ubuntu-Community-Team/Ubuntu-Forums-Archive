---
title: "Frame drops in fullscreen"
date: 2009-01-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Bou on 2009-01-03
Hi,

Quick question here. I would like to know if you're also getting these huge frame drops while watching videos on totem in fullscreen mode. They are so annoying.

---

### Post by LordVeovis on 2009-01-03
What kind of videos?

I have very low fps when watching flash, but always have.. :(

---

### Post by Bou on 2009-01-04
Any kind actually. The bigger the resolution, the more noticeable the problem.

I'm on Intrepid right now and the difference is enormous. Videos are fluid here, jumpy on Jaunty.

---

### Post by danf_1979 on 2009-01-04
It looks like a video driver issue to me.

1. What video card do you have?
2. Post the contents of /etc/X11/xorg.conf
3. Post the contents of /var/log/Xorg.0.log
4. Post the contents of this command: LIBGL_DEBUG=verbose glxinfo

---

