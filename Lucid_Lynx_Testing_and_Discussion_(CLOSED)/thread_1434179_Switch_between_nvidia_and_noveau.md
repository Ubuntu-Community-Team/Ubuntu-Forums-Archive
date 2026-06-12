---
title: "Switch between nvidia and noveau"
date: 2010-03-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Ancanus on 2010-03-19
Hello.

It is to my understanding that you cannot have both the nvidia (proprietary) and the noveau (free) video drivers at the same time, because the noveau one enables some kernel setting that allows resolution detection while nvidia does not. However, I'm also aware that we now have an alternative system that does enables many video drivers to be installed at the same time.

So my question is, in **update-alternatives --config gl_conf** is it correct to assume that
/usr/lib/nvidia-current/ld.so.conf  is the *nvidia* driver and
/usr/lib/mesa/ld.so.conf is the *noveau* one?

And switching between them is as easy as just changing the alternative? I ask because I really want to keep tabs on noveau, but the rendering on launchpad is so slow that I need to fall back to nvidia.

Thanks.

---

