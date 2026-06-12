---
title: "Compile MonoDevelop 1.0 RC1?"
date: 2008-02-25
forum: Installation &amp; Upgrades
---

### Post by putte30 on 2008-02-25
Does anyone know how to successfully compile MonoDevelop 1.0 RC1? Found some .dev packets, but was unsuccessfully with them. Any help would be appreciated.

---

### Post by Partyboi2 on 2008-02-25
I had no success in compiling it, I found that installing the deb package was easier and successful. Not sure where you got stuck. But this is how I installed it.
```
sudo apt-get install mono-devel build-essential mono-gmcs libmono-dev libpango1.0-dev libgtk2.0-dev libgtksourceview2.0-cil libgecko2.0-cil monodoc libmono-system-runtime2.0-cil libmono-cairo2.0-cil gettext
```then downloaded mono-addins-0.3_0.3-1_i386.deb    
```
wget http://dl4u.savefile.com/ae0f912f6cf96e172148bbecc7f6da6b/mono-addins-0.3_0.3-1_i386.deb
```and monodevelop_0.19-1_i386.deb
  ```
wget http://dl5u.savefile.com/7e41026ab1890e88c4f8f510144e6cb4/monodevelop_0.19-1_i386.deb
```then install the mono-addins first
```
sudo dpkg -i mono-addins-0.3_0.3-1_i386.deb
```then install monodevelop
```
sudo dpkg -i monodevelop_0.19-1_i386.deb
``` If you get a message about unmet dependecies try
```
sudo apt-get -f install
``` then to start type
```
monodevelop
```

---

### Post by putte30 on 2008-02-25
Won't start...

Following error message was thrown when i try to start monodevelop.


**An exception was thrown by the type initializer for MonoDevelop.Core.Gui.Services.**

System.TypeInitializationException: An exception was thrown by the type initializer for MonoDevelop.Core.Gui.Services ---> System.InvalidOperationException: Extension node not found in path: /MonoDevelop/Core/PlatformService
  at Mono.Addins.ExtensionContext.GetExtensionObjects (System.String path, System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 
  at Mono.Addins.ExtensionContext.GetExtensionObjects (System.String path) [0x00000] 
  at Mono.Addins.AddinManager.GetExtensionObjects (System.String path) [0x00000] 
  at MonoDevelop.Core.Gui.Services..cctor () [0x00000] --- End of inner exception stack trace ---

  at <0x00000> <unknown method>
  at MonoDevelop.Ide.Gui.IdeApp.Initialize (IProgressMonitor monitor) [0x00000] 
  at MonoDevelop.Ide.Gui.IdeStartup.Run (System.String[] args) [0x00000]


Also :

libpango1.0-0 (= 1.18.2-0ubuntu1) but 1.18.3-0ubuntu1 will be installed....

---

### Post by JC Denton on 2008-03-08
A Similar exception was thrown when I attempted running 0.19 too.. Any solutions, anyone?



**System.TypeInitializationException: An exception was thrown by the type initializer for MonoDevelop.Core.Gui.Services ---> System.InvalidOperationException: Extension node not found in path: /MonoDevelop/Core/PlatformService**
  at Mono.Addins.ExtensionContext.GetExtensionObjects (System.String path, System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 
  at Mono.Addins.ExtensionContext.GetExtensionObjects (System.String path) [0x00000] 
  at Mono.Addins.AddinManager.GetExtensionObjects (System.String path) [0x00000] 
  at MonoDevelop.Core.Gui.Services..cctor () [0x00000] --- End of inner exception stack trace ---

  at <0x00000> <unknown method>
  at MonoDevelop.Ide.Gui.IdeApp.Initialize (IProgressMonitor monitor) [0x00000] 
  at MonoDevelop.Ide.Gui.IdeStartup.Run (System.String[] args) [0x00000]

---

### Post by reverseblade on 2008-03-09
Yes it works here. You need to compile lot of things from source. gtk-sharp, gnome-sharp, gtksourceview2, xsp2, mono-doc , mono-addins, gktsourceview-0.x, gtkmozembed.

When I have time I can post a more through guide

---

### Post by JC Denton on 2008-03-11
> **reverseblade said:**
> Yes it works here. You need to compile lot of things from source. gtk-sharp, gnome-sharp, gtksourceview2, xsp2, mono-doc , mono-addins, gktsourceview-0.x, gtkmozembed.

When I have time I can post a more through guide
That would be great b/c just about everything else fails (installing from source, turning rpm's into deb's and trying to install deb's I've found online)

---

### Post by rickatnight11 on 2008-03-18
[http://ubuntuforums.org/showthread.php?t=725402&highlight=configure%3A+error%3A+mcs&page=2](http://ubuntuforums.org/showthread.php?t=725402&highlight=configure%3A+error%3A+mcs&page=2)

---

