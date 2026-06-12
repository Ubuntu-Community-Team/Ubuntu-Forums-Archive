---
title: "Can't start docky"
date: 2010-03-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by slymi2005 on 2010-03-28
When I try and start docky I get the following:

```
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () [0x00000] 
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () [0x00000] 
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () [0x00000] 
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () [0x00000] 
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () [0x00000] 
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () [0x00000] 
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () [0x00000] 
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () [0x00000] 
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () [0x00000] 
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () [0x00000] 
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () [0x00000] 
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () [0x00000] 
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () [0x00000] 
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () [0x00000] 
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () [0x00000] 
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () [0x00000] 
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () [0x00000] 
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () [0x00000] 
  at Mono.Addins.Serialization.BinaryXmlReader.Skip () [0x00000] 
ERROR: Unexpected error in setup process
System.Exception: System.NullReferenceException: Object reference not set to an instance of an object
  at Mono.Addins.Database.AddinDatabase.InternalScanFolders (IProgressStatus monitor, Mono.Addins.Database.AddinScanResult scanResult) [0x00000] 
  at Mono.Addins.Database.AddinDatabase.ScanFolders (IProgressStatus monitor, Mono.Addins.Database.AddinScanResult scanResult) [0x00000] 
ERROR: Add-in scan operation failed
Stack overflow in unmanaged: IP: 0x558a80, fault addr: 0x7ffff0736ff0
ERROR: The add-in database could not be updated. It may be due to file corruption. Try running the setup repair utility

Unhandled Exception: System.InvalidOperationException: Extension node not found in path: /Docky/ItemProvider
  at Mono.Addins.ExtensionContext.GetExtensionObjects (System.String path, System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 
  at Mono.Addins.ExtensionContext.GetExtensionObjects (System.String path) [0x00000] 
  at Mono.Addins.AddinManager.GetExtensionObjects (System.String path) [0x00000] 
  at Docky.PluginManager.get_ItemProviders () [0x00000] 
  at Docky.Interface.DockPreferences.<BuildItemProviders>m__7 (System.String s) [0x00000] 
  at System.Linq.Enumerable.Any[String] (IEnumerable`1 source, System.Func`2 predicate) [0x00000] 
  at Docky.Interface.DockPreferences.BuildItemProviders () [0x00000] 
  at Docky.Interface.DockPreferences..ctor (System.String dockName) [0x00000] 
  at Docky.DockController.CreateDocks () [0x00000] 
  at Docky.DockController.Initialize () [0x00000] 
  at Docky.Docky.Main (System.String[] args) [0x00000
```

The first line repeats a bunch of times and I am not sure what it says before that. Any help would be greatly appreciated.

---

### Post by slymi2005 on 2010-03-28
I found this thread:

[http://ubuntuforums.org/showthread.php?t=1407444](http://ubuntuforums.org/showthread.php?t=1407444)

Their issue just got fixed by itself and it also had something to do with mono.

I'm still having the same issue though.

---

### Post by slymi2005 on 2010-03-28
bump

---

### Post by slymi2005 on 2010-03-31
bump

---

### Post by mamers.sdtb on 2010-04-05
same issue and error messages here..
can't start docky

---

### Post by richtard on 2010-04-16
I got the same errors as you.
This worked for me. Hope it helps

in terminal type

> killall docky

then in nautilus, or whichever filemanager you use,  navigate to

/home/USER/.local/share

and delete the docky folder

restart docky.

I'm guessing some settings got messed up and deleting the docky folder resets to default versions.

Cheers
Rich

---

### Post by winchendonsprings on 2010-04-25
Thanks. this worked for me. and it didn't mess with any of my settings either

---

