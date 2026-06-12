---
title: "Cairo dock plug ins installation problem."
date: 2012-06-20
forum: Installation &amp; Upgrades
---

### Post by sbshaikh on 2012-06-20
I have installed cairo dock in my laptop by following instructions as follows-

```
sudo add-apt-repository ppa:cairo-dock-team/ppa
sudo apt-get update
sudo apt-get install cairo-dock cairo-dock-plug-ins
```


[COLOR=black][COLOR=Red]_1) Accordingly it shown laptop is installed but it is not properly working and shown following problem-_[/COLOR][/COLOR]

No plug-in were found.
Plug-ins provide most of the functionnalities of Cairo-Dock (annimations, applets, views, etc).
See [http://glx-dock.org](http://glx-dock.org) for more information.
Since there is almost no meaning in running the dock without them the application will quit now.
 
2) [COLOR=Red]_My laptop's terminal has the following input. I have reproduce the same with some deleted portion of messages hereunder -_[/COLOR]

```
ubuntu@ubuntu-linux:~/Desktop$ cairo-dock -c -o
Code:
(cairo-dock:9969): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1971:11: Not using units is deprecated. Assuming 'px'.

(cairo-dock:9969): Gtk-WARNING **: Failed to parse /usr/share/themes/mac-os-lion-theme-v2/gtk-3.0/settings.ini: Key file
 contains line '/* ' which is not a key-value pair, group, or comment
warning :  (/build/buildd/cairo-dock-3.0.0.1/src/gldit/cairo-dock-opengl.c:cairo_dock_initialize_opengl_backend:209)
  couldn't find an appropriate visual, trying to get one without Stencil buffer
(it may cause some little deterioration in the rendering) ...

 ============================================================================
    Cairo-Dock version : 3.0.2
    Compiled date      : Jun 15 2012 17:21:08
    Built with GTK     : 3.4
    Running with OpenGL: 1
 ============================================================================

warning :  (/build/buildd/cairo-dock-3.0.0.1/src/gldit/cairo-dock-module-manager.c:cairo_dock_load_module:167)
  this module ('/usr/lib/i386-linux-gnu/cairo-dock/libcd-Messaging-Menu.so') was compiled with Cairo-Dock v3.0.2, but Cairo-Dock is in v3.0.0
  It will be ignored
warning :  (/build/buildd/cairo-dock-3.0.0.1/src/gldit/cairo-dock-module-manager.c:cairo_dock_load_module:167)  
  this module ('/usr/lib/i386-linux-gnu/cairo-dock/libcd-musicPlayer.so') was compiled with Cairo-Dock v3.0.2, but Cairo-Dock is in v3.0.0
  It will be ignored
warning :  (/build/buildd/cairo-dock-3.0.0.1/src/gldit/cairo-dock-module-manager.c:cairo_dock_load_module:167)  
  this module ('/usr/lib/i386-linux-gnu/cairo-dock/libcd-dustbin.so') was compiled with Cairo-Dock v3.0.2, but Cairo-Dock is in v3.0.0
  It will be ignored
warning :  (/build/buildd/cairo-dock-3.0.0.1/src/gldit/cairo-dock-module-manager.c:cairo_dock_load_module:167)  
  this module ('/usr/lib/i386-linux-gnu/cairo-dock/libcd-tomboy.so') was compiled with Cairo-Dock v3.0.2, but Cairo-Dock is in v3.0.0
  It will be ignored
warning :  (/build/buildd/cairo-dock-3.0.0.1/src/gldit/cairo-dock-module-manager.c:cairo_dock_load_module:167)  
  this module ('/usr/lib/i386-linux-gnu/cairo-dock/libcd-logout.so') was compiled with Cairo-Dock v3.0.2, but Cairo-Dock is in v3.0.0
  It will be ignored
warning :  (/build/buildd/cairo-dock-3.0.0.1/src/gldit/cairo-dock-module-manager.c:cairo_dock_load_module:167)  
  this module ('/usr/lib/i386-linux-gnu/cairo-dock/libcd-dnd2share.so') was compiled with Cairo-Dock v3.0.2, but Cairo-Dock is in v3.0.0
  It will be ignored
warning :  (/build/buildd/cairo-dock-3.0.0.1/src/gldit/cairo-dock-module-manager.c:cairo_dock_load_module:167)  
  this module ('/usr/lib/i386-linux-gnu/cairo-dock/libcd-dialog-rendering.so') was compiled with Cairo-Dock v3.0.2, but Cairo-Dock is in v3.0.0
  It will be ignored
warning :  (/build/buildd/cairo-dock-3.0.0.1/src/gldit/cairo-dock-module-manager.c:cairo_dock_load_module:167)  
  this module ('/usr/lib/i386-linux-gnu/cairo-dock/libcd-rendering.so') was compiled with Cairo-Dock v3.0.2, but Cairo-Dock is in v3.0.0
  It will be ignored
warning :  (/build/buildd/cairo-dock-3.0.0.1/src/gldit/cairo-dock-module-manager.c:cairo_dock_load_module:167)  
  this module ('/usr/lib/i386-linux-gnu/cairo-dock/libcd-Toons.so') was compiled with Cairo-Dock v3.0.2, but Cairo-Dock is in v3.0.0
  It will be ignored
warning :  (/build/buildd/cairo-dock-3.0.0.1/src/gldit/cairo-dock-module-manager.c:cairo_dock_load_module:167)  
  this module ('/usr/lib/i386-linux-gnu/cairo-dock/libcd-Recent-Events.so') was compiled 
warning :  (/build/buildd/cairo-dock-3.0.0.1/src/gldit/cairo-dock-module-manager.c:cairo_dock_load_module:167)  
  warning :  (/build/buildd/cairo-dock-3.0.0.1/src/gldit/cairo-dock-module-manager.c:cairo_dock_load_module:167)  
  this module ('/usr/lib/i386-linux-gnu/cairo-dock/libcd-powermanager.so') was compiled with Cairo-Dock v3.0.2, but Cairo-Dock is in v3.0.0
  It will be ignored
warning :  (/build/buildd/cairo-dock-3.0.0.1/src/gldit/cairo-dock-module-manager.c:cairo_dock_load_module:167)  
  this module ('/usr/lib/i386-linux-gnu/cairo-dock/libcd-quick-browser.so') was compiled with Cairo-Dock v3.0.2, but Cairo-Dock is in v3.0.0
  It will be ignored
warning :  (/build/buildd/cairo-dock-3.0.0.1/src/gldit/cairo-dock-module-manager.c:cairo_dock_load_module:167)  
  this module ('/usr/lib/i386-linux-gnu/cairo-dock/libcd-mail.so') was compiled with Cairo-Dock v3.0.2, but Cairo-Dock is in v3.0.0
  It will be ignored
warning :  (/build/buildd/cairo-dock-3.0.0.1/src/gldit/cairo-dock-module-manager.c:cairo_dock_load_module:167)  
  this module ('/usr/lib/i386-linux-gnu/cairo-dock/libcd-system-monitor.so') was compiled with Cairo-Dock v3.0.2, but Cairo-Dock is in v3.0.0
  It will be ignored
warning :  (/build/buildd/cairo-dock-3.0.0.1/src/gldit/cairo-dock-module-manager.c:cairo_dock_load_module:167)  
  this module ('/usr/lib/i386-linux-gnu/cairo-dock/libcd-showDesktop.so') was compiled with Cairo-Dock v3.0.2, but Cairo-Dock is in v3.0.0
  It will be ignored
warning :  (/build/buildd/cairo-dock-3.0.0.1/src/gldit/cairo-dock-module-manager.c:cairo_dock_load_module:167)  
  this module ('/usr/lib/i386-linux-gnu/cairo-dock/libcd-switcher.so') was compiled with Cairo-Dock v3.0.2, but Cairo-Dock is in v3.0.0
  It will be ignored
warning :  (/build/buildd/cairo-dock-3.0.0.1/src/gldit/cairo-dock-module-manager.c:cairo_dock_load_module:167)  
  this module ('/usr/lib/i386-linux-gnu/cairo-dock/libcd-Clipper.so') was compiled with Cairo-Dock v3.0.2, but Cairo-Dock is in v3.0.0
  It will be ignored
warning :  (/build/buildd/cairo-dock-3.0.0.1/src/gldit/cairo-dock-module-manager.c:cairo_dock_load_module:167)  
  this module ('/usr/lib/i386-linux-gnu/cairo-dock/libcd-systray.so') was compiled with Cairo-Dock v3.0.2, but Cairo-Dock is in v3.0.0
  It will be ignored
warning :  (/build/buildd/cairo-dock-3.0.0.1/src/gldit/cairo-dock-module-manager.c:cairo_dock_load_module:167)  
  this module ('/usr/lib/i386-linux-gnu/cairo-dock/libcd-Folders.so') was compiled with Cairo-Dock v3.0.2, but Cairo-Dock is in v3.0.0
  It will be ignored
warning :  (/build/buildd/cairo-dock-3.0.0.1/src/gldit/cairo-dock-module-manager.c:cairo_dock_load_module:167)  
  this module ('/usr/lib/i386-linux-gnu/cairo-dock/libcd-wifi.so') was compiled with Cairo-Dock v3.0.2, but Cairo-Dock is in v3.0.0
  It will be ignored
warning :  (/build/buildd/cairo-dock-3.0.0.1/src/gldit/cairo-dock-module-manager.c:cairo_dock_load_module:167)  
  this module ('/usr/lib/i386-linux-gnu/cairo-dock/libcd-AlsaMixer.so') was compiled with Cairo-Dock v3.0.2, but Cairo-Dock is in v3.0.0
  It will be ignored
warning :  (/build/buildd/cairo-dock-3.0.0.1/src/gldit/cairo-dock-module-manager.c:cairo_dock_load_module:167)  
  this module ('/usr/lib/i386-linux-gnu/cairo-dock/libcd_gnome-integration.so') was compiled with Cairo-Dock v3.0.2, but Cairo-Dock is in v3.0.0
  It will be ignored
warning :  (/build/buildd/cairo-dock-3.0.0.1/src/gldit/cairo-dock-module-manager.c:cairo_dock_load_module:167)  
  this module ('/usr/lib/i386-linux-gnu/cairo-dock/libcd-weblets.so') was compiled with Cairo-Dock v3.0.2, but Cairo-Dock is in v3.0.0
  It will be ignored
warning :  (/build/buildd/cairo-dock-3.0.0.1/src/gldit/cairo-dock-module-manager.c:cairo_dock_load_module:167)  
  this module ('/usr/lib/i386-linux-gnu/cairo-dock/libcd-netspeed.so') was compiled with Cairo-Dock v3.0.2, but Cairo-Dock is in v3.0.0
  It will be ignored
```
[COLOR=red][COLOR=Red]_**Please help me to resolve the problem..**_[/COLOR][/COLOR]

---

### Post by indwic on 2012-07-02
Upgrade libgldi3 to 3.0.2-1ubuntu0~precise

```
sudo apt-get install libgldi3
```

---

### Post by sbshaikh on 2012-07-02
Thanks a lot Sir..

---

### Post by raja.genupula on 2012-07-02
Hi mark the thread as solved from thread tools  . Thank you .:)

---

