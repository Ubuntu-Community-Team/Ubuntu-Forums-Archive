---
title: "Still 10.10, but show 11.04???"
date: 2011-04-06
forum: Installation &amp; Upgrades
---

### Post by tybo42 on 2011-04-06
Hello, something weird happened recently, not sure exactly when... I've never been willing to upgrade my ubuntu from 10.10 to 11.04 (I actually didn't even know about the upgrade until that happened), but now when I click system>"about ubuntu", it says I'm running 11.04, even though the desktop is exactly the same as it was before, which makes me pretty certain that I haven't upgraded at all... I don't know what happened, but I'm afraid it causes some conflicts, particularly with compiz which stopped working pretty much at the same time. Any idea how I could tell ubuntu that it is still in 10.10? Otherwise I guess I'll have to upgrade to avoid any conflicts...

Thanks for you help in advance!

---

### Post by irv on 2011-04-06
Do you have "Ubuntu Tweak" install? If you do you could go to "System" "Computer Details". and See what shows up there.

---

### Post by tybo42 on 2011-04-06
Thanks for the reply. I just installed Tweak and restarted my computer but I cannot find "system""computer details"... when I run "sysinfo" in the terminal I can see all the info except the "system". Here is what I get from the terminal:

sysinfo in terminal, then click on "system" 

GConf.NoSuchKeyException: Key '/apps/sysinfo/initial_animation' not found in GConf
  at GConf.Client.Get (System.String key) [0x00000] in <filename unknown>:0 
  at Sysinfo.Sysinfo.UpdateFromGConf () [0x00000] in <filename unknown>:0 
GConf.NoSuchKeyException: Key '/apps/sysinfo/window_width' not found in GConf
  at GConf.Client.Get (System.String key) [0x00000] in <filename unknown>:0 
  at Sysinfo.Sysinfo..ctor (System.String[] args) [0x00000] in <filename unknown>:0 
GConf.NoSuchKeyException: Key '/apps/sysinfo/section_start' not found in GConf
  at GConf.Client.Get (System.String key) [0x00000] in <filename unknown>:0 
  at Sysinfo.Sysinfo..ctor (System.String[] args) [0x00000] in <filename unknown>:0 
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
thibault@thibault-L635:~$ sysinfo
GConf.NoSuchKeyException: Key '/apps/sysinfo/window_width' not found in GConf
  at GConf.Client.Get (System.String key) [0x00000] in <filename unknown>:0 
  at Sysinfo.Sysinfo..ctor (System.String[] args) [0x00000] in <filename unknown>:0 
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

I guess i have a problem right here! Any idea?

Thanks for your help

---

### Post by tybo42 on 2011-04-06
oups sorry I copy/pasted twice the stuff...

here si only one.


thibault@thibault-L635:~$ sysinfo
GConf.NoSuchKeyException: Key '/apps/sysinfo/window_width' not found in GConf
  at GConf.Client.Get (System.String key) [0x00000] in <filename unknown>:0 
  at Sysinfo.Sysinfo..ctor (System.String[] args) [0x00000] in <filename unknown>:0 
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
thibault@thibault-L635:~$ sysinfo
GConf.NoSuchKeyException: Key '/apps/sysinfo/window_width' not found in GConf
  at GConf.Client.Get (System.String key) [0x00000] in <filename unknown>:0 
  at Sysinfo.Sysinfo..ctor (System.String[] args) [0x00000] in <filename unknown>:0

---

### Post by tybo42 on 2011-04-06
Ok I should I've checked before but it's a reported bug... I don't think it has something to do my system. How can I use tweak? Thanks.

---

### Post by tgm4883 on 2011-04-06
Open a terminal. What is the output of these two commands

```
lsb_release -a
```

```
cat /etc/apt/sources.list
```

---

### Post by tybo42 on 2011-04-06
thibault@thibault-L635:~$ lsb_release -a
LSB Version:	core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 10.10
Release:	10.10
Codename:	maverick


thibault@thibault-L635:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu-Netbook 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://mirror.peer1.net/ubuntu/](http://mirror.peer1.net/ubuntu/) maverick main restricted multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirror.peer1.net/ubuntu/](http://mirror.peer1.net/ubuntu/) maverick-updates main restricted multiverse

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://mirror.peer1.net/ubuntu/](http://mirror.peer1.net/ubuntu/) maverick universe
deb [http://mirror.peer1.net/ubuntu/](http://mirror.peer1.net/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://mirror.peer1.net/ubuntu/](http://mirror.peer1.net/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

deb [http://mirror.peer1.net/ubuntu/](http://mirror.peer1.net/ubuntu/) maverick-proposed restricted main universe multiverse

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security restricted main universe multiverse
# deb [http://ppa.launchpad.net/compiz/ppa/ubuntu](http://ppa.launchpad.net/compiz/ppa/ubuntu) maverick main
# deb-src [http://ppa.launchpad.net/compiz/ppa/ubuntu](http://ppa.launchpad.net/compiz/ppa/ubuntu) maverick main

So I guess I'm still running 10.10... why is "about ubuntu" saying I'm 11.04 then?...

---

### Post by irv on 2011-04-06
[attach]188293[/attach]

[attach]188294[/attach]

---

### Post by tybo42 on 2011-04-06
ok, I did 

sudo add-apt-repository ppa:tualatrix/ppa

sudo apt-get update

sudo apt-get install ubuntu-tweak


Now I get (see attached)

Do you think it means there is no problem?...

---

### Post by tgm4883 on 2011-04-06
> **tybo42 said:**
> ok, I did 

sudo add-apt-repository ppa:tualatrix/ppa

sudo apt-get update

sudo apt-get install ubuntu-tweak


Now I get (see attached)

Do you think it means there is no problem?...

You are still on 10.10. I've seen others with the same issue you have for past releases.

:EDIT:

As an added note, there was no reason to install Ubuntu tweak to find this information.

---

### Post by tybo42 on 2011-04-06
Ok thanks very much. I guess I'm gonna have to find another reason why Compiz stopped working then... but it's gonna be for another thread! Solved.

---

### Post by irv on 2011-04-06
I find that compiz quits once in a while. When this happens I do this.
Press Alt +F2 bring up a run application box, just type in the following:
```
metacity --replace &
```
then do it again and type in:
```
compiz --replace &
```
I think I had to do this las week and compiz started working again.

---

