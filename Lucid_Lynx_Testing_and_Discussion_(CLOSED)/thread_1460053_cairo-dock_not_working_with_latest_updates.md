---
title: "cairo-dock not working with latest updates"
date: 2010-04-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by riseringseeker on 2010-04-22
I have been playing around with cairo-dock.  I had it working pretty well until this mornings updates.  Now it refuses to run, saying:

"No plug-ins were found." and "Since there is almost no meaning in running the dock without them, the application will quit now."  I've purged and re-installed (from the "standard" repos), but still no dice.

Running it from a terminal gives a slew of errors as follows:

```
============================================================================ 
	Cairo-Dock version: 2.1.3-10-lucid
	Compiled date:  Apr 22 2010 01:10:48
	Running with OpenGL: 1
 ============================================================================

warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:373)  
  this module ('/usr/lib/cairo-dock/libcd-motion_blur.so') was compiled with Cairo-Dock v2.1.3-6, but Cairo-Dock is in v2.1.3-10-lucid
  It will be ignored
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:373)  
  this module ('/usr/lib/cairo-dock/libcd-weblets.so') was compiled with Cairo-Dock v2.1.3-6, but Cairo-Dock is in v2.1.3-10-lucid
  It will be ignored
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:373)  
  this module ('/usr/lib/cairo-dock/libcd-clock.so') was compiled with Cairo-Dock v2.1.3-6, but Cairo-Dock is in v2.1.3-10-lucid
  It will be ignored
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:373)  
  this module ('/usr/lib/cairo-dock/libcd-systray.so') was compiled with Cairo-Dock v2.1.3-6, but Cairo-Dock is in v2.1.3-10-lucid
  It will be ignored
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:373)  
  this module ('/usr/lib/cairo-dock/libcd-AlsaMixer.so') was compiled with Cairo-Dock v2.1.3-6, but Cairo-Dock is in v2.1.3-10-lucid
  It will be ignored
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:373)  
  this module ('/usr/lib/cairo-dock/libcd-shortcuts.so') was compiled with Cairo-Dock v2.1.3-6, but Cairo-Dock is in v2.1.3-10-lucid
  It will be ignored
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:373)  
  this module ('/usr/lib/cairo-dock/libcd-logout.so') was compiled with Cairo-Dock v2.1.3-6, but Cairo-Dock is in v2.1.3-10-lucid
  It will be ignored
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:373)  
  this module ('/usr/lib/cairo-dock/libcd-terminal.so') was compiled with Cairo-Dock v2.1.3-6, but Cairo-Dock is in v2.1.3-10-lucid
  It will be ignored
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:373)  
  this module ('/usr/lib/cairo-dock/libcd-rendering.so') was compiled with Cairo-Dock v2.1.3-6, but Cairo-Dock is in v2.1.3-10-lucid
  It will be ignored
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:373)  
  this module ('/usr/lib/cairo-dock/libcd-keyboard-indicator.so') was compiled with Cairo-Dock v2.1.3-6, but Cairo-Dock is in v2.1.3-10-lucid
  It will be ignored
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:373)  
  this module ('/usr/lib/cairo-dock/libcd-netspeed.so') was compiled with Cairo-Dock v2.1.3-6, but Cairo-Dock is in v2.1.3-10-lucid
  It will be ignored
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:373)  
  this module ('/usr/lib/cairo-dock/libcd-showDesktop.so') was compiled with Cairo-Dock v2.1.3-6, but Cairo-Dock is in v2.1.3-10-lucid
  It will be ignored
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:373)  
  this module ('/usr/lib/cairo-dock/libcd-Cairo-Penguin.so') was compiled with Cairo-Dock v2.1.3-6, but Cairo-Dock is in v2.1.3-10-lucid
  It will be ignored
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:373)  
  this module ('/usr/lib/cairo-dock/libcd-powermanager.so') was compiled with Cairo-Dock v2.1.3-6, but Cairo-Dock is in v2.1.3-10-lucid
  It will be ignored
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:373)  
  this module ('/usr/lib/cairo-dock/libcd-stack.so') was compiled with Cairo-Dock v2.1.3-6, but Cairo-Dock is in v2.1.3-10-lucid
  It will be ignored
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:373)  
  this module ('/usr/lib/cairo-dock/libcd-desklet-rendering.so') was compiled with Cairo-Dock v2.1.3-6, but Cairo-Dock is in v2.1.3-10-lucid
  It will be ignored
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:373)  
  this module ('/usr/lib/cairo-dock/libcd-Dbus.so') was compiled with Cairo-Dock v2.1.3-6, but Cairo-Dock is in v2.1.3-10-lucid
  It will be ignored
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:373)  
  this module ('/usr/lib/cairo-dock/libcd-RSSreader.so') was compiled with Cairo-Dock v2.1.3-6, but Cairo-Dock is in v2.1.3-10-lucid
  It will be ignored
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:373)  
  this module ('/usr/lib/cairo-dock/libcd-icon-effect.so') was compiled with Cairo-Dock v2.1.3-6, but Cairo-Dock is in v2.1.3-10-lucid
  It will be ignored
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:373)  
  this module ('/usr/lib/cairo-dock/libcd-show_mouse.so') was compiled with Cairo-Dock v2.1.3-6, but Cairo-Dock is in v2.1.3-10-lucid
  It will be ignored
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:373)  
  this module ('/usr/lib/cairo-dock/libcd-quick-browser.so') was compiled with Cairo-Dock v2.1.3-6, but Cairo-Dock is in v2.1.3-10-lucid
  It will be ignored
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:373)  
  this module ('/usr/lib/cairo-dock/libcd-slider.so') was compiled with Cairo-Dock v2.1.3-6, but Cairo-Dock is in v2.1.3-10-lucid
  It will be ignored
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:373)  
  this module ('/usr/lib/cairo-dock/libcd-weather.so') was compiled with Cairo-Dock v2.1.3-6, but Cairo-Dock is in v2.1.3-10-lucid
  It will be ignored
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:373)  
  this module ('/usr/lib/cairo-dock/libcd-System-Monitor.so') was compiled with Cairo-Dock v2.1.3-6, but Cairo-Dock is in v2.1.3-10-lucid
  It will be ignored
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:373)  
  this module ('/usr/lib/cairo-dock/libcd-tomboy.so') was compiled with Cairo-Dock v2.1.3-6, but Cairo-Dock is in v2.1.3-10-lucid
  It will be ignored
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:373)  
  while opening module '/usr/lib/cairo-dock/libcd_xfce-integration.so' : (libthunar-vfs-1.so.2: cannot open shared object file: No such file or directory)
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:373)  
  this module ('/usr/lib/cairo-dock/libcd-mail.so') was compiled with Cairo-Dock v2.1.3-6, but Cairo-Dock is in v2.1.3-10-lucid
  It will be ignored
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:373)  
  this module ('/usr/lib/cairo-dock/libcd-dnd2share.so') was compiled with Cairo-Dock v2.1.3-6, but Cairo-Dock is in v2.1.3-10-lucid
  It will be ignored
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:373)  
  this module ('/usr/lib/cairo-dock/libcd_gnome-integration.so') was compiled with Cairo-Dock v2.1.3-6, but Cairo-Dock is in v2.1.3-10-lucid
  It will be ignored
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:373)  
  this module ('/usr/lib/cairo-dock/libcd-dustbin.so') was compiled with Cairo-Dock v2.1.3-6, but Cairo-Dock is in v2.1.3-10-lucid
  It will be ignored
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:373)  
  this module ('/usr/lib/cairo-dock/libcd-Animated-icons.so') was compiled with Cairo-Dock v2.1.3-6, but Cairo-Dock is in v2.1.3-10-lucid
  It will be ignored
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:373)  
  this module ('/usr/lib/cairo-dock/libcd-switcher.so') was compiled with Cairo-Dock v2.1.3-6, but Cairo-Dock is in v2.1.3-10-lucid
  It will be ignored
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:373)  
  this module ('/usr/lib/cairo-dock/libcd-musicPlayer.so') was compiled with Cairo-Dock v2.1.3-6, but Cairo-Dock is in v2.1.3-10-lucid
  It will be ignored
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:373)  
  this module ('/usr/lib/cairo-dock/libcd-illusion.so') was compiled with Cairo-Dock v2.1.3-6, but Cairo-Dock is in v2.1.3-10-lucid
  It will be ignored
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:373)  
  this module ('/usr/lib/cairo-dock/libcd-Clipper.so') was compiled with Cairo-Dock v2.1.3-6, but Cairo-Dock is in v2.1.3-10-lucid
  It will be ignored
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:373)  
  this module ('/usr/lib/cairo-dock/libcd-Toons.so') was compiled with Cairo-Dock v2.1.3-6, but Cairo-Dock is in v2.1.3-10-lucid
  It will be ignored
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:373)  
  this module ('/usr/lib/cairo-dock/libcd-drop_indicator.so') was compiled with Cairo-Dock v2.1.3-6, but Cairo-Dock is in v2.1.3-10-lucid
  It will be ignored
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:373)  
  this module ('/usr/lib/cairo-dock/libcd-wifi.so') was compiled with Cairo-Dock v2.1.3-6, but Cairo-Dock is in v2.1.3-10-lucid
  It will be ignored
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:373)  
  this module ('/usr/lib/cairo-dock/libcd-GMenu.so') was compiled with Cairo-Dock v2.1.3-6, but Cairo-Dock is in v2.1.3-10-lucid
  It will be ignored
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:373)  
  this module ('/usr/lib/cairo-dock/libcd-Xgamma.so') was compiled with Cairo-Dock v2.1.3-6, but Cairo-Dock is in v2.1.3-10-lucid
  It will be ignored
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:373)  
  this module ('/usr/lib/cairo-dock/libcd-dialog-rendering.so') was compiled with Cairo-Dock v2.1.3-6, but Cairo-Dock is in v2.1.3-10-lucid
  It will be ignored
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:373)  
  this module ('/usr/lib/cairo-dock/libcd-compiz-icon.so') was compiled with Cairo-Dock v2.1.3-6, but Cairo-Dock is in v2.1.3-10-lucid
  It will be ignored
OpenGL config summary :
 - bNonPowerOfTwoAvailable : 1
 - bPBufferAvailable : 1
 - direct rendering : 1
 - bTextureFromPixmapAvailable : 1
 - GLX version : 1.4
 - OpenGL version: 1.4 Mesa 7.7.1
 - OpenGL vendor: Tungsten Graphics, Inc
 - OpenGL renderer: Mesa DRI Intel(R) 945GM GEM 20091221 2009Q4 

activating pbuffer, usually buggy drivers will crash here ... ok, they are fine enough.
separateur necessaire
cairo_dock_create_surface_from_image_simple: assertion `cImageFile != NULL' failed
cairo_dock_create_surface_from_image_simple: assertion `cImageFile != NULL' failed
debut de boucle bloquante ...
 -> action !
fin de boucle bloquante -> 0

```

---

### Post by Cavsfan on 2010-04-22
Wish I could help! I got the updates through terminal and everything went fine.

---

### Post by RatSAT on 2010-04-22
Same for me, seems we updated cairo before the package for the plugins was ready. Just do another update now and it's fixed.

---

### Post by polki@mac.com on 2010-04-22
I'm fully updated and cairo-dock still complains. It might be because I'm using a Swedish server to update from. I'll wait till tomorrow :-)

---

### Post by barisurum on 2010-04-22
New update fixes the update :D

---

### Post by dasunsrule32 on 2010-04-22
I am still having issues with this, anyone have a fix for this? I fully removed, and purged my apt cache and reinstalled, same issue. Thanks!

---

### Post by dasunsrule32 on 2010-04-22
I submitted a bug for it, you can see it [here]("https://bugs.launchpad.net/ubuntu/+source/cairo-dock-plug-ins/+bug/568552").

---

### Post by polki@mac.com on 2010-04-23
I updated today and all is well, when it comes to cairo-dock at least, in Sweden. :-)

---

