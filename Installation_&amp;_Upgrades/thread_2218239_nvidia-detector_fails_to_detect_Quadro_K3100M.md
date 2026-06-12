---
title: "nvidia-detector fails to detect Quadro K3100M"
date: 2014-04-20
forum: Installation &amp; Upgrades
---

### Post by The Dragon Master on 2014-04-20
I've a new HP Zbook with an Nvidia Quadro K3100M graphics card

nvidia-detector returns "none"

lspci | grep VGA returns
01:00.0 VGA compatible controller: NVIDIA Corporation GK104GLM [Quadro K3100M]

I've tried all of the first 3 methods listed here [http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html](http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html)

Google shows up some bug reports of this nature for older cards - should I post one?

---

### Post by The Dragon Master on 2014-04-20
any one have any ideas?

---

### Post by ivan-janes on 2014-04-20
On my notebook with nvidia hybrid graphics card nvidia-detector returns none but everything works ok (including 3D acceleration). 
I have hybrid graphics card with nvidia-331-updates drivers from official repository and nvidia-prime package.

---

### Post by The Dragon Master on 2014-04-20
Thanks Ivan-Janes for your reply here and on a related thread ([http://ubuntuforums.org/showthread.php?t=2218218](http://ubuntuforums.org/showthread.php?t=2218218))

I don't know if the quadro is hybrid or not, but purging bumblebee and installing nvidia-331-updates and nvidia-prime has solved the crazy low-low-low resolution problem at least.
Although nvidia-detector still returns "none" the resolution is good and things appear to work at least at a basic level. 

What would be a good benchmark test to check that the quadro is really running optimally (once I'm back from a 4 day mountain hike far away from computers that is)?

---

### Post by ivan-janes on 2014-04-21
For changing the settings of your nvidia graphics card you can use nvidia-settings utility.

You can try glmark2 package for testing OpenGL perfomance.

On my notebook I have following results for glmark2:

```
=======================================================
    glmark2 2012.08
=======================================================
    OpenGL Information
    GL_VENDOR:     NVIDIA Corporation
    GL_RENDERER:   GeForce GT 720M/PCIe/SSE2
    GL_VERSION:    4.4.0 NVIDIA 331.38
=======================================================
[build] use-vbo=false: FPS: 1265 FrameTime: 0.791 ms
[build] use-vbo=true: FPS: 1599 FrameTime: 0.625 ms
[texture] texture-filter=nearest: FPS: 1187 FrameTime: 0.842 ms
[texture] texture-filter=linear: FPS: 1176 FrameTime: 0.850 ms
[texture] texture-filter=mipmap: FPS: 1283 FrameTime: 0.779 ms
[shading] shading=gouraud: FPS: 1078 FrameTime: 0.928 ms
[shading] shading=blinn-phong-inf: FPS: 1099 FrameTime: 0.910 ms
[shading] shading=phong: FPS: 1048 FrameTime: 0.954 ms
[bump] bump-render=high-poly: FPS: 855 FrameTime: 1.170 ms
[bump] bump-render=normals: FPS: 1608 FrameTime: 0.622 ms
[bump] bump-render=height: FPS: 1523 FrameTime: 0.657 ms
[effect2d] kernel=0,1,0;1,-4,1;0,1,0;: FPS: 853 FrameTime: 1.172 ms
[effect2d] kernel=1,1,1,1,1;1,1,1,1,1;1,1,1,1,1;: FPS: 584 FrameTime: 1.712 ms
[pulsar] light=false:quads=5:texture=false: FPS: 1315 FrameTime: 0.760 ms
[desktop] blur-radius=5:effect=blur:passes=1:separable=true:windows=4: FPS: 420 FrameTime: 2.381 ms
[desktop] effect=shadow:windows=4: FPS: 561 FrameTime: 1.783 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 504 FrameTime: 1.984 ms
[buffer] columns=200:interleave=false:update-dispersion=0.9:update-fraction=0.5:update-method=subdata: FPS: 656 FrameTime: 1.524 ms
[buffer] columns=200:interleave=true:update-dispersion=0.9:update-fraction=0.5:update-method=map: FPS: 547 FrameTime: 1.828 ms
[ideas] speed=duration: FPS: 1117 FrameTime: 0.895 ms
[jellyfish] <default>: FPS: 656 FrameTime: 1.524 ms
[terrain] <default>: FPS: 84 FrameTime: 11.905 ms
[conditionals] fragment-steps=0:vertex-steps=0: FPS: 1033 FrameTime: 0.968 ms
[conditionals] fragment-steps=5:vertex-steps=0: FPS: 986 FrameTime: 1.014 ms
[conditionals] fragment-steps=0:vertex-steps=5: FPS: 1007 FrameTime: 0.993 ms
[function] fragment-complexity=low:fragment-steps=5: FPS: 1010 FrameTime: 0.990 ms
[function] fragment-complexity=medium:fragment-steps=5: FPS: 1003 FrameTime: 0.997 ms
[loop] fragment-loop=false:fragment-steps=5:vertex-steps=5: FPS: 1016 FrameTime: 0.984 ms
[loop] fragment-steps=5:fragment-uniform=false:vertex-steps=5: FPS: 1015 FrameTime: 0.985 ms
[loop] fragment-steps=5:fragment-uniform=true:vertex-steps=5: FPS: 925 FrameTime: 1.081 ms
=======================================================
                                  glmark2 Score: 967 
=======================================================
```

---

