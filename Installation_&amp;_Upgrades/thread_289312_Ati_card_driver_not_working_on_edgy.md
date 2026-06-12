---
title: "Ati card driver not working on edgy"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by g3k0 on 2006-10-30
I tried installing the ati proprietary driver for edgy (which previously worked for me on dapper, crashed when updated, and fresh installed edgy) and notice the following problems

$ glxinfo | grep render
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: Mesa GLX Indirect

$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

I am very new to linux and do not know what to do to fix this.  I followed this guide to get it to work on dapper, but it wont work for edgy =(
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

Thanks for any help
g3k0

---

### Post by mwolfe on 2006-10-30
whoops, looks like you followed the wrong tutorial. The one you followed was for dapper, and although its almost the same there are a few subtle differences.

here:
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)


follow that tutorial instead..

---

### Post by mwolfe on 2006-10-30
And for general installation howto's in edgy, use this:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

---

### Post by kvonb on 2006-10-30
Unfortunately I have a 9200SE card which does NOT work fully under Edgy.

I tried several install methods, the best being the ccwiki one.

The official Ubuntu driver v28.8 works, and I get 3d, but Google Earth doesn't work with that version.

I would suspect that other things won't work either, such as OpenOffice.

I then tried to use the ATI proprietary 8.27.10 driver (which I know solves the Google Earth and OO problem), but unfortunately it only has the Dapper drivers included.

I will now try to install the ATI proprietary 8.27.10 driver for Dapper in Edgy.

If it doesn't work, I think it's time to switch back to Dapper.

---

### Post by g3k0 on 2006-10-31
It worked! =)  Thanks for showing me the correct guide.  I guess what threw me off is the one that I was using originally had an edgy section.

Now everything works for me on edgy =)
Thanks again
~g3k0

By the way, how do the people who write those come up with that stuff and learn what the commands do?

---

