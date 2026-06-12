---
title: "DPKG Errors after update to 9.04"
date: 2009-12-19
forum: Installation &amp; Upgrades
---

### Post by IceRayn on 2009-12-19
I used Update Manager to update my system, and, other then this, it went great.

Now, when installing anything through apt, I get this filling my terminal:

Setting up xulrunner-1.9 (1.9.0.16+nobinonly-0ubuntu0.9.04.1) ...
dpkg: error processing xulrunner-1.9 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of yelp:
 yelp depends on xulrunner-1.9 (>= 1.9~rc1); however:
  Package xulrunner-1.9 is not configured yet.
dpkg: error processing yelp (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-user-guide:
 gnome-user-guide depends on yelp; however:
  Package yelp is not configured yet.
dpkg: error processing gnome-user-guide (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-docs:
 ubuntu-docs depends on gnome-user-guide; however:
  Package gnome-user-guide is not configured yet.
 ubuntu-docs depends on yelp; however:
  Package yelp is not configured yet.
dpkg: error processing ubuntu-docs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xulruNo apport report written because the error message indicates its a followup error from a previous failure.
  No apport report written because the error message indicates its a followup error from a previous failure.
                            No apport report written because MaxReports is reached already
          No apport report written because MaxReports is reached already
                                                                        No apport report written because MaxReports is reached already
                                                      No apport report written because MaxReports is reached already
                                    No apport report written because MaxReports is reached already
                  No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            No apport report written because MaxReports is reached already
                          nner-1.9-gnome-support:
 xulrunner-1.9-gnome-support depends on xulrunner-1.9 (= 1.9.0.16+nobinonly-0ubuntu0.9.04.1); however:
  Package xulrunner-1.9 is not configured yet.
dpkg: error processing xulrunner-1.9-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of epiphany-gecko:
 epiphany-gecko depends on xulrunner-1.9 (>= 1.9~rc2-3); however:
  Package xulrunner-1.9 is not configured yet.
 epiphany-gecko depends on xulrunner-1.9-gnome-support; however:
  Package xulrunner-1.9-gnome-support is not configured yet.
dpkg: error processing epiphany-gecko (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of epiphany-browser:
 epiphany-browser depends on epiphany-gecko | epiphany-webkit; however:
  Package epiphany-gecko is not configured yet.
  Package epiphany-webkit is not installed.
dpkg: error processing epiphany-browser (--configure):
 dependency problems - leaving uNo apport report written because MaxReports is reached already
              nconfigured
dpkg: dependency problems prevent configuration of epiphany-extensions:
 epiphany-extensions depends on epiphany-gecko (>= 2.25); however:
  Package epiphany-gecko is not configured yet.
dpkg: error processing epiphany-extensions (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-3.0:
 firefox-3.0 depends on xulrunner-1.9 (>= 1.9.0.1); however:
  Package xulrunner-1.9 is not configured yet.
dpkg: error processing firefox-3.0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-3.0-branding:
 firefox-3.0-branding depends on firefox-3.0 (= 3.0.16+nobinonly-0ubuntu0.9.04.1); however:
  Package firefox-3.0 is not configured yet.
dpkg: error processing firefox-3.0-branding (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox:
 firefox depends on firefox-3.0; however:
  Package firefox-3.0 is not configured yet.
 firefox depends on firefox-3.0-branding; however:
  Package firefox-3.0-branding is not configured yet.
dpkg: error processing firefox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-3.0-gnome-support:
 firefox-3.0-gnome-support depends on firefox-3.0 (= 3.0.16+nobinonly-0ubuntu0.9.04.1); however:
  Package firefox-3.0 is not configured yet.
 firefox-3.0-gnome-support depends on xulrunner-1.9-gnome-support (>= 1.9~b4~); however:
  Package xulrunner-1.9-gnome-support is not configured yet.
dpkg: error processing firefox-3.0-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on firefox-3.0-gnome-support; however:
  Package firefox-3.0-gnome-support is not configured yet.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-user-guide-en:
 gnome-user-guide-en depends on gnome-user-guide (= 2.26.0+svn20090323ubuntu5); however:
  Package gnome-user-guide is not configured yet.
 gnome-user-guide-en depends on yelp; however:
  Package yelp is not configured yet.
dpkg: error processing gnome-user-guide-en (--configure):
 dependency problems - leaving unconfigured
Setting up python-opengl (3.0.0~b6-3) ...
No apport report written because MaxReports is reached already
                                                              pycentral: pycentral pkginstall: Not overwriting local files:
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/GL/ARB/depth_buffer_float.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/GL/ARB/draw_instanced.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/GL/ARB/framebuffer_object.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/GL/ARB/framebuffer_sRGB.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/GL/ARB/geometry_shader4.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/GL/ARB/half_float_vertex.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/GL/ARB/instanced_arrays.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/GL/ARB/map_buffer_range.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/GL/ARB/texture_buffer_object.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/GL/ARB/texture_compression_rgtc.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/GL/ARB/texture_rg.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/GL/ARB/vertex_array_object.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/GL/EXT/transform_feedback.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/GL/MESAX/__init__.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/GL/MESAX/texture_stack.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/GL/NV/conditional_render.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/GL/NV/present_video.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/GL/VERSION/GL_3_0.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/arrays/vbo.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/lazywrapper.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/plugins.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/raw/GL/ARB/depth_buffer_float.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/raw/GL/ARB/draw_instanced.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/raw/GL/ARB/framebuffer_object.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/raw/GL/ARB/framebuffer_sRGB.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/raw/GL/ARB/geometry_shader4.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/raw/GL/ARB/half_float_vertex.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/raw/GL/ARB/instanced_arrays.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/raw/GL/ARB/map_buffer_range.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/raw/GL/ARB/texture_buffer_object.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/raw/GL/ARB/texture_compression_rgtc.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/raw/GL/ARB/texture_rg.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/raw/GL/ARB/vertex_array_object.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/raw/GL/EXT/transform_feedback.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/raw/GL/NV/conditional_render.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/raw/GL/NV/present_video.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/raw/GL/VERSION/GL_3_0.py not found.
pycentral pkginstall: Not overwriting local files:
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/GL/ARB/depth_buffer_float.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/GL/ARB/draw_instanced.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/GL/ARB/framebuffer_object.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/GL/ARB/framebuffer_sRGB.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/GL/ARB/geometry_shader4.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/GL/ARB/half_float_vertex.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/GL/ARB/instanced_arrays.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/GL/ARB/map_buffer_range.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/GL/ARB/texture_buffer_object.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/GL/ARB/texture_compression_rgtc.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/GL/ARB/texture_rg.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/GL/ARB/vertex_array_object.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/GL/EXT/transform_feedback.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/GL/MESAX/__init__.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/GL/MESAX/texture_stack.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/GL/NV/conditional_render.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/GL/NV/present_video.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/GL/VERSION/GL_3_0.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/arrays/vbo.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/lazywrapper.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/plugins.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/raw/GL/ARB/depth_buffer_float.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/raw/GL/ARB/draw_instanced.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/raw/GL/ARB/framebuffer_object.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/raw/GL/ARB/framebuffer_sRGB.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/raw/GL/ARB/geometry_shader4.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/raw/GL/ARB/half_float_vertex.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/raw/GL/ARB/instanced_arrays.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/raw/GL/ARB/map_buffer_range.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/raw/GL/ARB/texture_buffer_object.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/raw/GL/ARB/texture_compression_rgtc.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/raw/GL/ARB/texture_rg.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/raw/GL/ARB/vertex_array_object.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/raw/GL/EXT/transform_feedback.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/raw/GL/NV/conditional_render.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/raw/GL/NV/present_video.py not found.
   dpkg: /usr/lib/python2.5/site-packages/OpenGL/raw/GL/VERSION/GL_3_0.py not found.
dpkg: error processing python-opengl (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of sun-java6-plugin:
 sun-java6-plugin depends on firefox | firefox-2 | iceweasel | mozilla-firefox | iceape-browser | mozilla-browser | epiphany-gecko | epiphany-webkit | epiphany-browser | galeon | midbrowser | moblin-web-browser | xulrunner | xulrunner-1.9; however:
  Package firefox is not configured yet.
  Package firefox-2 is not installed.
  Package iceweasel is not installed.
  Package mozilla-firefox is not installed.
  Package iceape-browser is not installed.
  Package mozilla-browser is not installed.
  Package epiphany-gecko is not configured yet.
  Package epiphany-webkit is not installed.
  Package epiphany-browser is not configured yet.
  Package galeon is not installed.
  Package midbrowser is not installed.
  Package moblin-web-browser is not installed.
  Package xulrunner is not installed.
  Package xulrunner-1.No apport report written because MaxReports is reached already
    No apport report written because MaxReports is reached already
                                                                  No apport report written because MaxReports is reached already
                                                No apport report written because MaxReports is reached already
                              No apport report written because MaxReports is reached already
            9 is not configured yet.
dpkg: error processing sun-java6-plugin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of epiphany-browser-dbg:
 epiphany-browser-dbg depends on epiphany-gecko (= 2.26.1-0ubuntu1) | epiphany-webkit (= 2.26.1-0ubuntu1); however:
  Package epiphany-gecko is not configured yet.
  Package epiphany-webkit is not installed.
dpkg: error processing epiphany-browser-dbg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-dbg:
 gnome-dbg depends on epiphany-browser-dbg; however:
  Package epiphany-browser-dbg is not configured yet.
dpkg: error processing gnome-dbg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubufox:
 ubufox depends on firefox | abrowser | firefox-3.0 | firefox-2; however:
  Package firefox is not configured yet.
  Package abrowser is not installed.
  Package firefox-3.0 is not configured yet.
  Package firefox-2 is not installed.
dpkg: error processing ubufox (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xulrunner-1.9
 yelp
 gnome-user-guide
 ubuntu-docs
 xulrunner-1.9-gnome-support
 epiphany-gecko
 epiphany-browser
 epiphany-extensions
 firefox-3.0
 firefox-3.0-branding
 firefox
 firefox-3.0-gnome-support
 firefox-gnome-support
 gnome-user-guide-en
 python-opengl
 sun-java6-plugin
 epiphany-browser-dbg
 gnome-dbg
 ubufox
E: Sub-process /usr/bin/dpkg returned an error code (1)

To summarize, xulrunner through ubufox aren't able to be upgraded.

Can anyone help me with this? I've done sudo apt-get clean && sudo apt-get dist-upgrade in addition to many other commands trying to get this to work.

Thanks,
IceRayn

---

### Post by HappyFeet on 2009-12-19
try
```
sudo dpkg --configure -a && sudo apt-get install -f
```

---

