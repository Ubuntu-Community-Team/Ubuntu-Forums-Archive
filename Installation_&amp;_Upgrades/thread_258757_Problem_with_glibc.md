---
title: "Problem with glibc"
date: 2006-09-16
forum: Installation &amp; Upgrades
---

### Post by tarun86 on 2006-09-16
Hi 
Some of my applications are crashing due to some problem with glibc. how can I get rid of these errors or correct them.Will be thankful to you guys for your help O:). Anything that I should install or reinstall or remove ???

some of the common errors that I am getting are reported below:
=================================================================
tarun@Mysterio:/home/tarun$ azureus

(process:9116): Gdk-WARNING **: locale not supported by Xlib

(process:9116): Gdk-WARNING **: cannot set locale modifiers
changeLocale: *Default Language* != English (India). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (India)' (en_IN), using 'English (default)'
[B]*** glibc detected *** double free or corruption (fasttop): 0x0847b1f0 ***
Aborted[/B]
========================================================================
tarun@Mysterio:/home/tarun$ landell

(/usr/lib/landell/landell.exe:9164): Gdk-WARNING **: locale not supported by Xlib

(/usr/lib/landell/landell.exe:9164): Gdk-WARNING **: cannot set locale modifiers
[B]*** glibc detected *** double free or corruption (out): 0x08148580 ***
Aborted[/B]
=========================================================================
tarun@Mysterio:/home/tarun$ acroread

(acroread:9169): Gdk-WARNING **: locale not supported by Xlib

(acroread:9169): Gdk-WARNING **: cannot set locale modifiers

(acroread:9169): GLib-GObject-CRITICAL **: g_closure_ref: assertion `closure->ref_count > 0' failed

(acroread:9169): GLib-GObject-CRITICAL **: g_closure_invoke: assertion `closure->marshal || closure->meta_marshal' failed
***** glibc detected *** corrupted double-linked list: 0xb7043358 *****
=========================================================================

---

### Post by tarun86 on 2006-09-16
i never recieved any answer ever from this forum n prob wont ever try my luck here:confused:  . I was better with my fedora n their forums wud probably switch back to it soon :biggrin:

---

### Post by kswnsn on 2006-10-10
If you are/have run KDE, and selected a certain GTK style under the KDE control center, you will have a ~/.gtkrc-2.0 file that will prevent certain GNOME apps from running. First rename this file to see if it clears the issue, and if so, try a different theme. I was using "Glider" but changed to "Human" to correct this issue.

---

