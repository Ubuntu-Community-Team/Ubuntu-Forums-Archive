---
title: "F-spot no working"
date: 2009-09-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Giwex on 2009-09-08
When I run F-spot the main window appears briefly and then crash. 
> giwex@2920z:~$ f-spot
[Info  07:29:56.342] Initializing DBus
[Info  07:29:56.483] Initializing Mono.Addins
[Info  07:29:56.677] Starting new FSpot server (f-spot 0.6.1.1)
[Info  07:29:59.202] Hack for gnome-settings-daemon engaged
lcms: Error #12288; Read error. Got 0 bytes, block should be of 128 bytes
lcms: Error #12288; Corrupted profile: '/usr/share/color/icc/ECI-RGB.V1.0.icc'
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
Cms.CmsException: Error opening ICC profile in file /usr/share/color/icc/ECI-RGB.V1.0.icc
  at Cms.Profile..ctor (System.String path) [0x00000] 
  at FSpot.ColorManagement.AddProfiles (System.String path, IDictionary`2 profs) [0x00000] 
  at FSpot.ColorManagement.get_Profiles () [0x00000] 
  at FSpot.TagSelectionWidget.IconDataFunc (Gtk.TreeViewColumn column, Gtk.CellRenderer renderer, TreeModel model, TreeIter iter) [0x00000] 
  at GtkSharp.TreeCellDataFuncWrapper.NativeCallback (IntPtr tree_column, IntPtr cell, IntPtr tree_model, IntPtr iter, IntPtr data) [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at GtkSharp.TreeCellDataFuncWrapper.NativeCallback(IntPtr tree_column, IntPtr cell, IntPtr tree_model, IntPtr iter, IntPtr data)
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at FSpot.Driver.Main(System.String[] args)
giwex@2920z:~$

Before to report it just want to be sure it's a problem also for someone else. Thanks

---

### Post by autocrosser on 2009-09-08
Hmmmm---I just updated it & it is working fine here--What are your specs?  Intel/AMD--Nvidia/ATI & etc?

I'm 32bit/Intel i7 920/nvidia all updates as of 7pm pacific time.

I just looked at my system & I do not have a /usr/share/color/icc  file--It is indicating that the file is corrupted, so I would "trash" or move the file to see if that is "really" the problem.

---

### Post by Giwex on 2009-09-09
Thanks for replying. I'll check this evening as soon as I go back home:)

---

### Post by Giwex on 2009-09-09
Ok, I deleted the entire icc folder and now F-spot is back working. I wonder what application wrote that folder :confused:

---

### Post by directhex on 2009-09-09
> **Giwex said:**
> Ok, I deleted the entire icc folder and now F-spot is back working. I wonder what application wrote that folder :confused:

icc-profiles package

Does reinstalling the package re-break F-Spot?

---

### Post by Giwex on 2009-09-09
Re-installed icc-profile. No problem at all with F-Spot.
:confused: but :)

---

