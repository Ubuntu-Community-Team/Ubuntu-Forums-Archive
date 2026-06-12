---
title: "Meerkat won't display itself in SysInfo"
date: 2010-10-15
forum: Installation &amp; Upgrades
---

### Post by grikdog on 2010-10-15
After installing Meerkat, some windows close (and take their apps along with them into oblivion ;-)  E.g., when I run Applications -> System Tools -> Sysinfo, selecting the FIRST MENU OPTION, i.e., System, causes the app to close suddenly.

There are other small examples, in Firefox, e.g., but I'm not compiling a dossier here.

Aside from the butt-ugly Ubuntu font, there don't seem to be (m)any major issues.  Well, EXCEPT THAT MY WALLPAPERS have vanished, but I'm sure Q.A. knew that would happen, right?

---

### Post by SteveDee on 2010-10-16
Yes, I get that with Sysinfo.
If I launch sysinfo from a terminal, I get this when it crashes & closes:-
```

Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.NullReferenceException: Object reference not set to an instance of an object
  at Sysinfo.SystemInfo.Xorg () [0x00000] in <filename unknown>:0 
  at Sysinfo.Sysinfo.on_notebook1_switch_page (System.Object o, Gtk.SwitchPageArgs e) [0x00000] in <filename unknown>:0 
  at Gtk.Notebook.SwitchPageSignalCallback (IntPtr arg0, IntPtr arg1, UInt32 arg2, IntPtr gch) [0x00000] in <filename unknown>:0 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at Gtk.Notebook.SwitchPageSignalCallback(IntPtr arg0, IntPtr arg1, UInt32 arg2, IntPtr gch)
   at Gtk.Notebook.gtk_notebook_set_current_page(IntPtr , Int32 )
   at Gtk.Notebook.set_CurrentPage(Int32 value)
   at Sysinfo.Sysinfo.on_treeview1_cursor_changed(System.Object o, System.EventArgs e)
   at System.Reflection.MonoMethod.InternalInvoke(System.Object , System.Object[] , System.Exception ByRef )
   at System.Reflection.MonoMethod.Invoke(System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
   at System.Reflection.MethodBase.Invoke(System.Object obj, System.Object[] parameters)
   at System.Delegate.DynamicInvokeImpl(System.Object[] args)
   at System.MulticastDelegate.DynamicInvokeImpl(System.Object[] args)
   at System.Delegate.DynamicInvoke(System.Object[] args)
   at GLib.Signal.ClosureInvokedCB(System.Object o, GLib.ClosureInvokedArgs args)
   at GLib.SignalClosure.Invoke(GLib.ClosureInvokedArgs args)
   at GLib.SignalClosure.MarshalCallback(IntPtr raw_closure, IntPtr return_val, UInt32 n_param_vals, IntPtr param_values, IntPtr invocation_hint, IntPtr marshal_data)
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Sysinfo.Sysinfo..ctor(System.String[] args)
   at Sysinfo.Sysinfo.Main(System.String[] args)

```

---

### Post by Ronok on 2010-10-26
Hi
another --> **"Sysinfo" Crashes when clicking "System"** 

**Ubuntu 10.10**
Linux 2.6.35-22-generic #35
**Sysinfo 0.7**

There are at least 2 Bug Reports over at launchpad
[URL="https://bugs.launchpad.net/ubuntu/+source/sysinfo/+bug/596727"]
https://bugs.launchpad.net/ubuntu/+source/sysinfo/+bug/596727[/URL]

[https://bugs.launchpad.net/ubuntu/+source/sysinfo/+bug/659542]("https://bugs.launchpad.net/ubuntu/+source/sysinfo/+bug/659542")

Where to go from here ?
[URL="http://www.gongkuo.com/linuxcli.htm"]**Thanks**
Ronok[/URL]

from running in **Terminal**
```

anotheruse@another:~$
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.NullReferenceException: Object reference not set to an instance of an object
  at Sysinfo.SystemInfo.Xorg () [0x00000] in <filename unknown>:0 
  at Sysinfo.Sysinfo.on_notebook1_switch_page (System.Object o, Gtk.SwitchPageArgs e) [0x00000] in <filename unknown>:0 
  at Gtk.Notebook.SwitchPageSignalCallback (IntPtr arg0, IntPtr arg1, UInt32 arg2, IntPtr gch) [0x00000] in <filename unknown>:0 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at Gtk.Notebook.SwitchPageSignalCallback(IntPtr arg0, IntPtr arg1, UInt32 arg2, IntPtr gch)
   at Gtk.Notebook.gtk_notebook_set_current_page(IntPtr , Int32 )
   at Gtk.Notebook.set_CurrentPage(Int32 value)
   at Sysinfo.Sysinfo.on_treeview1_cursor_changed(System.Object o, System.EventArgs e)
   at System.Reflection.MonoMethod.InternalInvoke(System.Object , System.Object[] , System.Exception ByRef )
   at System.Reflection.MonoMethod.Invoke(System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
   at System.Reflection.MethodBase.Invoke(System.Object obj, System.Object[] parameters)
   at System.Delegate.DynamicInvokeImpl(System.Object[] args)
   at System.MulticastDelegate.DynamicInvokeImpl(System.Object[] args)
   at System.Delegate.DynamicInvoke(System.Object[] args)
   at GLib.Signal.ClosureInvokedCB(System.Object o, GLib.ClosureInvokedArgs args)
   at GLib.SignalClosure.Invoke(GLib.ClosureInvokedArgs args)
   at GLib.SignalClosure.MarshalCallback(IntPtr raw_closure, IntPtr return_val, UInt32 n_param_vals, IntPtr param_values, IntPtr invocation_hint, IntPtr marshal_data)
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Sysinfo.Sysinfo..ctor(System.String[] args)
   at Sysinfo.Sysinfo.Main(System.String[] args)
```

---

### Post by SteveDee on 2010-10-26
> **Ronok said:**
> 

...Where to go from here ?...


...install "hardinfo"

---

