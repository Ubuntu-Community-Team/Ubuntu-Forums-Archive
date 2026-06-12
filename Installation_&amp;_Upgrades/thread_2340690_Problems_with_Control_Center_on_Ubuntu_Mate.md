---
title: "Problems with Control Center on Ubuntu Mate"
date: 2016-10-21
forum: Installation &amp; Upgrades
---

### Post by josep2 on 2016-10-21
I had firstly Ubuntu with Unity (in Trusty Tahr). Upon this I have installed Mate. All functions well, with the exception of the Mate Control Center, which allways crashes. If I start it thru terminal, I obtain this:

[COLOR=#333333][FONT=Ubuntu](mate-control-center:7519): Gtk-CRITICAL **: IA__gtk_widget_set_size_request: assertion 'GTK_IS_WIDGET (widget)' failed[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu](mate-control-center:7519): GLib-CRITICAL **: g_strdelimit: assertion 'string != NULL' failed[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu](mate-control-center:7519): GLib-CRITICAL **: g_strrstr: assertion 'haystack != NULL' failed[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu](mate-control-center:7519): GLib-CRITICAL **: g_ascii_strdown: assertion 'str != NULL' failed[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu](mate-control-center:7519): GLib-GObject-CRITICAL **: g_object_set_data: assertion 'G_IS_OBJECT (object)' failed

I have no idea what does it mean. I have searched intensely throug the web but without succes. Could someone have any idea for solvong this problem? 

Thanks in advance.[/FONT][/COLOR]

---

### Post by TheFu on 2016-10-21
Shot in the dark, but if the config files have conflicting entries the easiest way to see if that is it is to create a new userid, login using that new user with Mate and see how it goes. Do not login with Unity first.  If it doesn't crash, then you know it is likely the config files and can start trying to fix it.

---

### Post by josep2 on 2016-10-22
Thanks a lot for your answer! I have created a new user, but I have had the same problem in his home-space. I have even logged myself as a guest-user... but again the same problem... So, perhaps it has nothing to do with config-files, but with "something else" (...but what?) related to the prior unity-version I had... The "mate-converted" distribution works fine. But, perhaps, it would have been better to install directly Ubuntu-Mate version instead of adding the new interface...  

Unfortunately, it doesn't seem to be a lot of information about this issue in the web...

Thanks again!

---

