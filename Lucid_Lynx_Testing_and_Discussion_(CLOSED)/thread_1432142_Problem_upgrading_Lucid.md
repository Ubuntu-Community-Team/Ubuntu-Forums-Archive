---
title: "Problem upgrading Lucid"
date: 2010-03-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by medeshago on 2010-03-17
After having some troubles with audio in programs running with wine, I decided to try this ppa: [https://launchpad.net/~neil-aldur/+archive/ppa]("https://launchpad.net/~neil-aldur/+archive/ppa"). After adding it to the repositories, I haven't been able to do upgrade, this is the output:
```
$ sudo apt-get upgrade
E: dpkg se interrumpió, debe ejecutar manualmente «sudo dpkg --configure -a» para corregir el problema. 

```
And this is the output of dpkg --configure -a:
```
$ sudo dpkg --configure -a
Configurando wine1.2 (1.1.40-0ubuntu2+winepulse0.35~ppa2) ...
[Info  12:44:22.813] Docky version: 2.1.0 bzr docky r1182 ppa
[Info  12:44:22.832] Kernel version: 2.6.32.16
[Info  12:44:22.855] CLR version: 2.0.50727.1433

Unhandled Exception: System.Exception: Unable to open the session message bus. ---> System.ArgumentNullException: Argument cannot be null.
Parameter name: address
  at NDesk.DBus.Bus.Open (System.String address) [0x00000] 
  at NDesk.DBus.Bus.get_Session () [0x00000] 
  --- End of inner exception stack trace ---
  at NDesk.DBus.Bus.get_Session () [0x00000] 
  at NDesk.DBus.BusG.Init () [0x00000] 
  at Docky.Docky.Main (System.String[] args) [0x00000] 
GNOME_KEYRING_CONTROL=/tmp/keyring-NwoZEk
GNOME_KEYRING_PID=3958

** (gnome-settings-daemon:3912): WARNING **: You can only run one xsettings manager at a time; exiting

** (gnome-settings-daemon:3912): WARNING **: Unable to start xsettings manager: Could not initialize xsettings manager.
** (gnome-panel:3868): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:3868): DEBUG: Adding applet 0.
Initializing nautilus-gdu extension
[Error 12:44:29.484] [SystemService] Could not initialize dbus: Unable to open the session message bus.
** (gnome-panel:3868): DEBUG: Adding applet 1.
Unable to find a synaptics device.

** (gnome-settings-daemon:3912): WARNING **: Grab failed for some keys, another application may already have access the them.

** (gnome-settings-daemon:3912): WARNING **: Clipboard manager is already running.
** (gnome-panel:3868): DEBUG: Adding applet 2.
[Error 12:44:30.028] [NetworkService] Could not initialize Network Manager dbus: Unable to open the session message bus.
[Error 12:44:30.029] [PluginManager] Encountered error loading plugin: TargetInvocationException "Exception has been thrown by the target of an invocation."

(Do:3962): Wnck-CRITICAL **: wnck_set_client_type got called multiple times.

** (gnome-panel:3868): DEBUG: Adding applet 3.
** (gnome-panel:3868): DEBUG: Adding applet 4.
** Message: Could not connect to session manager: Could not get owner of name 'org.gnome.SessionManager': no such name

** (gnome-panel:3868): WARNING **: Could not connect to session manager: Could not get owner of name 'org.gnome.SessionManager': no such name
Error while getting object for node in path '/Do/ItemSource'.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.IO.DirectoryNotFoundException: Could not find a part of the path "/root/.mozilla/profiles.ini".
  at System.IO.FileStream..ctor (System.String path, FileMode mode, FileAccess access, FileShare share, Int32 bufferSize, Boolean anonymous, FileOptions options) [0x00000] 
  at System.IO.FileStream..ctor (System.String path, FileMode mode, FileAccess access, FileShare share) [0x00000] 
  at (wrapper remoting-invoke-with-check) System.IO.FileStream:.ctor (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare)
  at System.IO.File.OpenRead (System.String path) [0x00000] 
  at System.IO.StreamReader..ctor (System.String path, System.Text.Encoding encoding, Boolean detectEncodingFromByteOrderMarks, Int32 bufferSize) [0x00000] 
  at System.IO.StreamReader..ctor (System.String path) [0x00000] 
  at (wrapper remoting-invoke-with-check) System.IO.StreamReader:.ctor (string)
  at System.IO.File.OpenText (System.String path) [0x00000] 
  at Firefox.PlacesItemSource.FindProfilePath () [0x00000] 
  at Firefox.PlacesItemSource..ctor () [0x00000] 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  --- End of inner exception stack trace ---
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance (System.Type expectedType) [0x00000] 
  at Mono.Addins.ExtensionNode.GetChildObjects (System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 
Tomboy.NotesItemSource "Tomboy Notes" encountered an error in UpdateItems: System.TypeInitializationException: An exception was thrown by the type initializer for Tomboy.TomboyDBus ---> System.Exception: Unable to open the session message bus. ---> System.ArgumentNullException: Argument cannot be null.
Parameter name: address
  at NDesk.DBus.Bus.Open (System.String address) [0x00000] 
  at NDesk.DBus.Bus.get_Session () [0x00000] 
  --- End of inner exception stack trace ---
  at NDesk.DBus.Bus.get_Session () [0x00000] 
  at Tomboy.TomboyDBus..cctor () [0x00000] 
  --- End of inner exception stack trace ---
  at Tomboy.NotesItemSource.UpdateItems () [0x00000] 
  at Do.Universe.Safe.SafeItemSource.UpdateItems () [0x00000] .
Error while getting object for node in path '/Do/ItemSource'.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.IO.DirectoryNotFoundException: Could not find a part of the path "/root/.mozilla/profiles.ini".
  at System.IO.FileStream..ctor (System.String path, FileMode mode, FileAccess access, FileShare share, Int32 bufferSize, Boolean anonymous, FileOptions options) [0x00000] 
  at System.IO.FileStream..ctor (System.String path, FileMode mode, FileAccess access, FileShare share) [0x00000] 
  at (wrapper remoting-invoke-with-check) System.IO.FileStream:.ctor (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare)
  at System.IO.File.OpenRead (System.String path) [0x00000] 
  at System.IO.StreamReader..ctor (System.String path, System.Text.Encoding encoding, Boolean detectEncodingFromByteOrderMarks, Int32 bufferSize) [0x00000] 
  at System.IO.StreamReader..ctor (System.String path) [0x00000] 
  at (wrapper remoting-invoke-with-check) System.IO.StreamReader:.ctor (string)
  at System.IO.File.OpenText (System.String path) [0x00000] 
  at Firefox.PlacesItemSource.FindProfilePath () [0x00000] 
  at Firefox.PlacesItemSource..ctor () [0x00000] 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  --- End of inner exception stack trace ---
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance (System.Type expectedType) [0x00000] 
  at Mono.Addins.ExtensionNode.GetChildObjects (System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 
compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
Nautilus-Share-Message: Called "net usershare info" but it failed: La «red compartida» devolvió el error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No existe el fichero ó directorio
Please ask your system administrator to enable user sharing.

Conky: /home/edgardo/.conky/conkyclock: 17: no such configuration: 'border_margin'
Conky: use_spacer should have an argument of left, right, or none.  'yes' seems to be some form of 'true', so defaulting to right.
Conky: /home/edgardo/.conky/conkyrhythm: 17: no such configuration: 'border_margin'
Conky: use_spacer should have an argument of left, right, or none.  'yes' seems to be some form of 'true', so defaulting to right.
Conky: desktop window (14000aa) is subwindow of root window (15a)
Conky: window type - override
Conky: drawing to created window (0x5600001)
Conky: desktop window (14000aa) is subwindow of root window (15a)
Conky: window type - override
Conky: drawing to created window (0x5e00001)
Conky: drawing to double buffer
Conky: drawing to double buffer
```

For some strange reasons, it reloads the desktop, using the preferences in /root, and nothing else happens.

---

