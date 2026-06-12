---
title: "Mono updates"
date: 2009-06-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by descendent87 on 2009-06-24
Have had 15 updates for mono held back for the last day or so, at the moment its
```
The following packages have been kept back:
  libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-data2.0-cil
  libmono-getoptions2.0-cil libmono-posix2.0-cil libmono-security2.0-cil
  libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil
  libmono-system-web2.0-cil libmono-system2.0-cil libmono2.0-cil mono-2.0-gac
  mono-gac mono-runtime update-manager-core
0 upgraded, 0 newly installed, 0 to remove and 16 not upgraded.
```
If I try dist-upgrade I get the following:
```
The following packages will be REMOVED
  mono-2.0-runtime mono-common mono-jit ubuntu-desktop update-manager
  update-notifier
The following packages will be upgraded:
  libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-data2.0-cil
  libmono-getoptions2.0-cil libmono-posix2.0-cil libmono-security2.0-cil
  libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil
  libmono-system-web2.0-cil libmono-system2.0-cil libmono2.0-cil mono-2.0-gac
  mono-gac mono-runtime update-manager-core
16 upgraded, 0 newly installed, 6 to remove and 0 not upgraded.
Need to get 6250kB of archives.
After this operation, 1286kB disk space will be freed.

```
ubuntu-desktop, update-manager and update-notifier are from the update-manager-core upgrade.
Is it safe to remove the mono bits it wants to or is there still new stuff needed before it's safe to upgrade?
Also no mono apps will open at the moment (banshee, tomboy) is this known or should I file a bug report?

```
ben@ubuntu-desktop:~$ banshee

Unhandled Exception: System.Exception: Unable to open the session message bus. ---> System.TypeInitializationException: An exception was thrown by the type initializer for Mono.Unix.Native.Syscall ---> System.DllNotFoundException: libMonoPosixHelper.so
  at (wrapper managed-to-native) Mono.Unix.Native.Syscall:_L_ctermid ()
  at Mono.Unix.Native.Syscall..cctor () [0x00000] 
  --- End of inner exception stack trace ---
  at Mono.Unix.UnixStream..ctor (Int32 fileDescriptor, Boolean ownsHandle) [0x00000] 
  at Mono.Unix.UnixStream..ctor (Int32 fileDescriptor) [0x00000] 
  at (wrapper remoting-invoke-with-check) Mono.Unix.UnixStream:.ctor (int)
  at NDesk.DBus.Transports.UnixNativeTransport.Open (System.String path, Boolean abstract) [0x00000] 
  at NDesk.DBus.Transports.UnixTransport.Open (NDesk.DBus.AddressEntry entry) [0x00000] 
  at NDesk.DBus.Transports.Transport.Create (NDesk.DBus.AddressEntry entry) [0x00000] 
  at NDesk.DBus.Connection.OpenPrivate (System.String address) [0x00000] 
  at NDesk.DBus.Connection..ctor (System.String address) [0x00000] 
  at NDesk.DBus.Bus..ctor (System.String address) [0x00000] 
  at NDesk.DBus.Bus.Open (System.String address) [0x00000] 
  at NDesk.DBus.Bus.get_Session () [0x00000] 
  --- End of inner exception stack trace ---
  at NDesk.DBus.Bus.get_Session () [0x00000] 
  at Banshee.ServiceStack.DBusConnection.get_ApplicationInstanceAlreadyRunning () [0x00000] 
  at Booter.Booter.Main () [0x00000]
```
```
ben@ubuntu-desktop:~$ tomboy

Unhandled Exception: System.TypeInitializationException: An exception was thrown by the type initializer for Mono.Unix.Native.Stdlib ---> System.DllNotFoundException: libMonoPosixHelper.so
  at (wrapper managed-to-native) Mono.Unix.Native.Stdlib:GetDefaultSignal ()
  at Mono.Unix.Native.Stdlib..cctor () [0x00000] 
  --- End of inner exception stack trace ---
  at Mono.Unix.UnixMarshal.AllocHeap (Int64 size) [0x00000] 
  at Mono.Unix.UnixMarshal.StringToHeap (System.String s, Int32 index, Int32 count, System.Text.Encoding encoding) [0x00000] 
  at Mono.Unix.UnixMarshal.StringToHeap (System.String s, System.Text.Encoding encoding) [0x00000] 
  at Mono.Unix.UnixMarshal.StringToHeap (System.String s) [0x00000] 
  at Mono.Unix.Catalog.MarshalStrings (System.String s1, System.IntPtr& p1, System.String s2, System.IntPtr& p2, System.String s3, System.IntPtr& p3) [0x00000] 
  at Mono.Unix.Catalog.Init (System.String package, System.String localedir) [0x00000] 
  at Tomboy.Tomboy.Main (System.String[] args) [0x00000] 

Unhandled Exception: System.TypeInitializationException: An exception was thrown by the type initializer for Mono.Unix.Native.Stdlib ---> System.DllNotFoundException: libMonoPosixHelper.so
  at (wrapper managed-to-native) Mono.Unix.Native.Stdlib:GetDefaultSignal ()
  at Mono.Unix.Native.Stdlib..cctor () [0x00000] 
  --- End of inner exception stack trace ---
  at Mono.Unix.UnixMarshal.AllocHeap (Int64 size) [0x00000] 
  at Mono.Unix.UnixMarshal.StringToHeap (System.String s, Int32 index, Int32 count, System.Text.Encoding encoding) [0x00000] 
  at Mono.Unix.UnixMarshal.StringToHeap (System.String s, System.Text.Encoding encoding) [0x00000] 
  at Mono.Unix.UnixMarshal.StringToHeap (System.String s) [0x00000] 
  at Mono.Unix.Catalog.MarshalStrings (System.String s1, System.IntPtr& p1, System.String s2, System.IntPtr& p2, System.String s3, System.IntPtr& p3) [0x00000] 
  at Mono.Unix.Catalog.Init (System.String package, System.String localedir) [0x00000] 
  at Tomboy.Tomboy.Main (System.String[] args) [0x00000]
```

---

### Post by xebian on 2009-06-24
Didn't you hear there is a big debate as to include or NOt moNO?
:P

---

### Post by descendent87 on 2009-06-24
yes I've seen the many threads with all the pointless arguments about mono (IMO if people don't want it, remove it) but it doesn't really answer my original question does it :P

---

### Post by Martey on 2009-06-24
You should wait until all of the Mono packages can be upgraded before upgrading. If you upgrade some of the libraries, but not others (which is what will happen if you end up removing mono-jit and other not-yet-upgraded packages that conflict with upgraded ones), Mono programs will not work.

---

### Post by taavikko on 2009-06-24
AFAIK, "mono-2.0-runtime & mono-jit" can be removed, since mono-runtime replaces mono-2*-runtime, and is dependent of jit.

---

### Post by directhex on 2009-06-24
> **taavikko said:**
> AFAIK, "mono-2.0-runtime & mono-jit" can be removed, since mono-runtime replaces mono-2*-runtime, and is dependent of jit.

Yeppers.

"held back" is NORMAL when using "upgrade" rather than "dist-upgrade". "upgrade" will never remove packages (or install new packages), it will only change the version of installed packages. If a "dist-upgrade" shows packages held back, then THAT's a bug, as it means there is some unresolvable situation in the upgrade (i.e. apt cannot work out what to add or remove to fix the situation). In this instance, you can see that a couple of packages are being removed, and some others installed. That's perfectly normal behaviour when a dependency tree changes.

The update-manager thing? That's someone else's problem. Go shout at them.

---

### Post by zika on 2009-06-24
> **directhex said:**
> Yeppers.

"held back" is NORMAL when using "upgrade" rather than "dist-upgrade". "upgrade" will never remove packages (or install new packages), it will only change the version of installed packages. If a "dist-upgrade" shows packages held back, then THAT's a bug, as it means there is some unresolvable situation in the upgrade (i.e. apt cannot work out what to add or remove to fix the situation). In this instance, you can see that a couple of packages are being removed, and some others installed. That's perfectly normal behaviour when a dependency tree changes.

The update-manager thing? That's someone else's problem. Go shout at them.Thank You for encouragement to use aptitude full-upgrade. It solved Mono "problem" and I will not try to shout at anybody about update-manager, I'll just wait ... :)

---

### Post by descendent87 on 2009-06-24
just did an upgrade and update manager wen't through fine, seems the dependency problems were finally sorted

> **directhex said:**
> Yeppers.

"held back" is NORMAL when using "upgrade" rather than "dist-upgrade". "upgrade" will never remove packages (or install new packages), it will only change the version of installed packages. If a "dist-upgrade" shows packages held back, then THAT's a bug, as it means there is some unresolvable situation in the upgrade (i.e. apt cannot work out what to add or remove to fix the situation). In this instance, you can see that a couple of packages are being removed, and some others installed. That's perfectly normal behaviour when a dependency tree changes.

thanks for explaining, just wanted to check before I caused bigger problems

---

