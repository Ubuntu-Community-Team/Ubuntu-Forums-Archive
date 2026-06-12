---
title: "ATI X1650Pro driver not working properly on Edgy"
date: 2006-12-14
forum: Installation &amp; Upgrades
---

### Post by albler1111 on 2006-12-14
Hi,

Apologies if this is a known bug described somewhere I missed.
I followed the installation procedure from
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)
(both methods). The installation (now method 2) seems to be fine

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series Generic
OpenGL version string: 2.0.6174 (8.31.5)

$ glxinfo | grep render
direct rendering: Yes
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: Radeon X1600 Series Generic

The problems start when I scroll any window or try to move or resize them. They simply do not repaint correctly. Alas, the Xorg drivers behave properly but are painfully slow in 2560x1600.

Any insight?

---

