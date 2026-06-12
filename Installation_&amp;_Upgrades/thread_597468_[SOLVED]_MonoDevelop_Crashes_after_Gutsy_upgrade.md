---
title: "[SOLVED] MonoDevelop Crashes after Gutsy upgrade"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by rdoolen on 2007-10-30
I haven't been able to got Mondevelop to work since I upgraded to Gutsy. I tried the version in the Gutsy repos as well as installing from source. I can't get anything to work.

For the purpose of this post, I wanted to start from a clean slate; so, I uninstalled all packages in Synaptic that begin with the letters “mono.” This also resulted in lots of lib* packages being removable; so I uninstalled them as well. It also resulted in the uninstallation of F-spot and tomboy. After everything was uninstalled, I reinstalled F-spot and Tomboy, because I want them. After that, I removed all residual configurations of the left over mono packages and deleted the Monodevelop and Stetic folders from the ~/.config directory. 

Then I entered
```
sudo apt-get install mono mono-gmcs mono-gac mono-utils monodevelop monodoc-browser monodevelop-nunit monodevelop-versioncontrol
```
and everything seemed to go fine.


If I run monodevelop from the command line I get the following:

(MonoDevelop:26833): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
2633 [-1226867824] INFO MonoDevelop.Core.ILoggingService (null) - Initializing service: MonoDevelop.Core.PropertyService
2735 [-1226867824] INFO MonoDevelop.Core.ILoggingService (null) - Initializing service: MonoDevelop.Core.SystemAssemblyService
4391 [-1226867824] INFO MonoDevelop.Core.ILoggingService (null) - Initializing service: MonoDevelop.Projects.Documentation.IDocumentationService


Then when I try to open a project , monodevelop crashes and I get:


Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.NullReferenceException: A null value was found where an object instance was required.
  at MonoDevelop.Ide.Gui.ProjectOperations.RestoreCombinePreferences (System.Object data) [0x00000]   at MonoDevelop.Ide.Gui.ProjectOperations+<>c__CompilerGenerated39.<>c__AnonymousMethod40 (System.Object +19, System.EventArgs +20) [0x00000] 
  at (wrapper delegate-invoke) system.MulticastDelegate:invoke_void_object_EventArgs (object,System.EventArgs)
  at Gtk.Application+InvokeCB.Invoke () [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_bool ()
  at GLib.Timeout+TimeoutProxy.Handler () [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException ()
   at GLib.Timeout+TimeoutProxy.Handler ()
   at GLib.Timeout+TimeoutProxy.Handler ()
   at Gtk.Application.gtk_main ()
   at Gtk.Application.gtk_main ()
   at Gtk.Application.Run ()
   at MonoDevelop.Ide.Gui.IdeApp.Run ()
   at MonoDevelop.Ide.Gui.IdeStartup.Run ()
   at MonoDevelop.Core.ApplicationService.StartApplication ()
   at MonoDevelop.Startup.SharpDevelopMain.Main ()

Can anyone help me get this running?

---

### Post by rdoolen on 2007-10-31
bump

---

### Post by cwmoser on 2007-11-02
I am experiencing the same thing -- MonoDevelop crashes with Gutsy.

I have a project that worked fine in MonoDevelop v0.15 under Feisty but crashes MonoDevelop IDE under Gutsy.  

I have tried MonoDevelop v0.16 and v0.15 and both result in crash. when I click on MainWindow.cs

I would think the reason is the differences between Feisty and Gutsy.
Something in Gutsy is the issue.
Any ideas why Gutsy is doing this?

Thanks

Carl

---

### Post by rdoolen on 2007-11-03
I have worked on this alot. I can't get it to work. I have installed 0.14, 0.15 and 0.16 at different times. I have tried from the repos, from getdeb and from source.  I tried an installer I found. Nothing works. I even tried a different computer. 

Things  crash at different places, but the error is always a GTK# exception of some sort. From my reading this may be a GTK# bug. I am not really sure where to turn.

This is very disappointing, I was in the middle of a project and this killed it.

---

### Post by motters on 2007-11-04
I've also had very much the same experience.  I've tried versions 0.14, 0.15, 0.16 compiled from source and the binaries version from GetDeb.  They all seem to suffer from the same problem.  

I have existing projects created using MonoDevelop (0.15 on feisty) and when I try to open a GTK# project and view a form I get an immediate crash.  Also if I try creating a new project, then go to the form designer and add a menu then try to save it also crashes.  The problem is entirely repeatable.

This has been quite annoying because it's effectively preventing me from doing C# development.

I suspect that the problem may be something to do with the GTK libraries - possibly some version incompatibility - but this is really just a guess.

---

### Post by rdoolen on 2007-11-06
Success!

Basically, I installed 0.17. 

For details see:
[http://ubuntuforums.org/showthread.php?t=597841](http://ubuntuforums.org/showthread.php?t=597841)

---

