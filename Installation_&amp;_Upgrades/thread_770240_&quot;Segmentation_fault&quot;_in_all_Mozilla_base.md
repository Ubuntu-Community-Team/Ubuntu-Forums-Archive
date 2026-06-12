---
title: "&quot;Segmentation fault&quot; in all Mozilla based browsers after Hardy upgrade"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by endre on 2008-04-27
As explained by the title, both Firefox and Flock crashes almost immediately after book.

Flock crashes almost immediately without me doing anything more than just starting it up, Firefox crashes as soon as I try to navigate from my startpage. 

Launching them by "sudo" does not help. 

Do I need to delete/reset all the profiles?

Thanks!

---

### Post by LaRoza on 2008-04-27
Start it in the terminal to see what errors you get.

---

### Post by endre on 2008-04-27
In Firefox, after running it from terminal, with sudo (freezes during startup otherwise) I get the following.

** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
GCJ PLUGIN: thread 0x805e0e0: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x805e0e0: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x805e0e0: NP_GetValue
GCJ PLUGIN: thread 0x805e0e0: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x805e0e0: NP_GetValue return
GCJ PLUGIN: thread 0x805e0e0: NP_GetValue
GCJ PLUGIN: thread 0x805e0e0: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x805e0e0: NP_GetValue return

(firefox:10217): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:10217): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:10217): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:10217): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:10217): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:10217): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:10217): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:10217): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:10217): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:10217): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:10217): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:10217): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Segmentation fault

And it crashes.

In Flock, also running by the way of sudo, I don't get any output until it crashes and all it says is: segmentation fault.

---

### Post by FredB on 2008-04-27
Try removing your current java plugin... Just a guess, of course ;)

---

### Post by kerry_s on 2008-04-27
why are you running your browser as root(sudo)?
that is most likely the cause of the problems, try removing your ~/.mozilla folder, you will lose all your settings, everything will be fresh. don't use sudo to run a browser!

**mv ~/.mozilla ~/mozilla.old**

you might have to use sudo, if root has taken control

**sudo mv ~/.mozilla ~/mozilla.old**

---

### Post by Mandibela on 2008-10-02
> **kerry_s said:**
> why are you running your browser as root(sudo)?
that is most likely the cause of the problems, try removing your ~/.mozilla folder, you will lose all your settings, everything will be fresh. don't use sudo to run a browser!

**mv ~/.mozilla ~/mozilla.old**

you might have to use sudo, if root has taken control

**sudo mv ~/.mozilla ~/mozilla.old**

You should read the first message before you post. Using sudo was not the problem.

---

### Post by Mandibela on 2008-10-02
```
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

(firefox:15976): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:15976): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:15976): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:15976): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:15976): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Segmentation fault

```

Happens to me mostly when sufring sites with flash content... Any ideas?

Hardy w/ 2.6.24-19-generic, AMD X2 (scaling), and just a few extensions with firefox 3.0.3. I use the NVIDIA driver 173.14.12.

---

### Post by peakshysteria on 2008-10-02
Start Firefox in [**safemode**]("http://kb.mozillazine.org/Safe_mode#Linux") to see if the problem is still there. But since you have been running FF with sudo things might be broken already. As mentioned above you should never run FF with sudo. Might have gone from bad to worse.

Could it be some addons that are causing the problems? Could you list the addons you have installed? ([**infolister**]("https://addons.mozilla.org/en-US/firefox/addon/447") can help you with this).

Have you tried to uninstall FF and reinstall it? This should still leave your profile intact. If it doesn't help remove Firefox completely and reinstall it.

Also see: [**[COLOR="Red"]Standard diagnostic - Firefox[/COLOR]**]("http://kb.mozillazine.org/Standard_diagnostic_-_Firefox"), [**[COLOR="Red"]Firefox crashes[/COLOR]**]("http://kb.mozillazine.org/Firefox_crashes"), **[COLOR="Red"][Problematic extensions]("http://kb.mozillazine.org/Problematic_extensions")[/COLOR]**.

---

### Post by Mandibela on 2008-10-02
I got these, but firefox did not crash! So, these may not be related to the Segmentation fault at all.

** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

(firefox:17212): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:17212): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:17212): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:17212): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:17212): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:17212): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:17212): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:17212): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:17212): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed


I can't reproduce the Segmentation fault by certain steps or using a certain webpage. It just happens.. And most of the time with youtube or the like.

---

