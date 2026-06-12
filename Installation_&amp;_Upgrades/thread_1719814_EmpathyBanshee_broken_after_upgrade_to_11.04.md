---
title: "Empathy/Banshee broken after upgrade to 11.04"
date: 2011-04-02
forum: Installation &amp; Upgrades
---

### Post by sn0w75 on 2011-04-02
I recently upgraded to Ubuntu 11.04 beta from 10.10. While I'm very happy with the new Unity interface, two of my most used programs, Empathy and Banshee, broke in one way or another after the upgrade.

Empathy was crashing and/or the contact list window was disappearing as soon as it appeared. After fiddling around for a few hours, I was able to get Empathy to work by installing it from the PPA (as well as adding the gnome3 ppa to my repositories to fix some dependency issues with the PPA version of empathy).
While it now runs just fine without crashing, two features of Empathy are still broken:
-The PPA version of empathy seems to have ABSOLUTELY no theming; the beautiful ubuntu adium theme is now replaced with some default ugly theme for me. And for the life of me I can't seem to get it to see the ubuntu adium theme located in /usr/share/adium or wherever.
-The PPA version of empathy doesn't seem to work with the Ubuntu messaging menu (which might be problematic, since that's the only place where you can see that you got a message from someone that's not in your contact list?) >.>"


Banshee appeared to be fine initially (although I didn't launch it, it appeared on the Unity bar). However, at some point it disappeared from the Unity bar (drawing my attention to it), and launching it by clicking the Unity icon and typing its name didn't seem to do anything (although it did show up).

Running it in a terminal gave this output:
> sn0w75@PowerSpec:~$ banshee
[Info  09:46:16.956] Running Banshee 1.9.6: [Ubuntu Natty (development branch) 44d9b6f (linux-gnu, i686) @ 2011-03-28 17:39:30 UTC]
Exception has been thrown by the target of an invocation.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.DllNotFoundException: libgtk-x11-2.0.so.0
  at (wrapper managed-to-native) Gtk.Application:gtk_init (int&,intptr&)
  at Gtk.Application.Init () [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient.InitializeGtk () [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient.Initialize (Boolean registerCommonServices) [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient..ctor (Boolean initializeDefault, System.String defaultIconName) [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient..ctor () [0x00000] in <filename unknown>:0 
  at Nereid.Client..ctor () [0x00000] in <filename unknown>:0 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] in <filename unknown>:0 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] in <filename unknown>:0 
  at System.Activator.CreateInstance (System.Type type) [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient.Startup () [0x00000] in <filename unknown>:0 
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00000] in <filename unknown>:0 

Unhandled Exception: System.DllNotFoundException: libgtk-x11-2.0.so.0
  at (wrapper managed-to-native) Gtk.Application:gtk_init (int&,intptr&)
  at Gtk.Application.Init () [0x00000] in <filename unknown>:0 
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient.Startup[Client] () [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient.Startup[Client] (System.String[] args) [0x00000] in <filename unknown>:0 
  at Nereid.Client.Main (System.String[] args) [0x00000] in <filename unknown>:0 
  at (wrapper managed-to-native) System.AppDomain:ExecuteAssembly (System.Reflection.Assembly,string[])
  at System.AppDomain.ExecuteAssemblyInternal (System.Reflection.Assembly a, System.String[] args) [0x00000] in <filename unknown>:0 
  at System.AppDomain.ExecuteAssembly (System.String assemblyFile, System.Security.Policy.Evidence assemblySecurity, System.String[] args) [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) System.AppDomain:ExecuteAssembly (string,System.Security.Policy.Evidence,string[])
  at System.AppDomain.ExecuteAssembly (System.String assemblyFile) [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) System.AppDomain:ExecuteAssembly (string)
  at Booter.Booter.BootClient (System.String clientName) [0x00000] in <filename unknown>:0 
  at Booter.Booter.Main () [0x00000] in <filename unknown>:0 
It seems to be a pretty straightforward issue to me- banshee can't find the dll library file libgtk-x11-2.0.so.0. However, a 'libgtk-x11' doesn't seem to exist in the default ubuntu repositories, which has me completely confused. I'm using banshee from the default repositories; shouldn't the default repository have all of these dependencies covered?

In my opinion, priority on this issue goes to banshee; Empathy is at least functional at this point for me. Thanks in advance to any help. ^.^

UPDATE 2: The theming issue is due to installing packages from the gnome3 repository. >.>" But if I un-install all the gnome3 repository packages and go back to the default, empathy will crash and stuff again. >.>" Any suggestions as far as what to do?

UPDATE 3: after a huge giant mess, I managed to fix everything. Not sure exactly how I fixed empathy in the end (although I need to mention that in the end I went back to the ubuntu repostiory empathy). Banshee has a bug ([https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/717850](https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/717850)) that will cause it not to run if libGL.so.1 and libGL.so.1.2 (leftover files from a fglrx installation???) are in /usr/lib. Removing them solves the problem.

---

### Post by nutznboltz on 2011-05-21
> Empathy was crashing and/or the contact list window was disappearing as soon as it appeared.

Yeah, the contact list closes under certain circumstances and can only be re-opened by restarting Empathy.

> after a huge giant mess
Yeah, don't mix Gnome 2 and Gnome 3 unless you really know what you are doing.

> Not sure exactly how I fixed empathy in the end (although I need to mention that in the end I went back to the ubuntu repository empathy). 
Do you mean that the contact list window no longer closes?

---

### Post by nutznboltz on 2011-05-21
I've been scraping ubuntuforums and launchpad for bug reports about Empathy on Natty with respect to the contact list window closing mysteriously.

I found this:

[https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/784938](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/784938)

"empathy contact list glides to the right every time it is closed and reopened"

Is it possible that the contact window is not closing but moving off the screen?

UPDATE: Alt-tab doesn't show the contact window.

---

