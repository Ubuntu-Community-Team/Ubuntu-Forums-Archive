---
title: "banshee troubles"
date: 2009-03-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by halfsane on 2009-03-18
Hey guys,

Banshee has not been running at all for me... here is the output..

 not sure what to make of it all. 

Thanks,


 also,  why doesn't amarok 2 show recently added songs in playlist? 

```

halfsane@halfsane-desktop:~/Documents$ banshee
[Info  19:13:36.235] Running Banshee 1.4.3: [Ubuntu jaunty (development branch) (linux-gnu, x86_64) @ 2009-03-15 11:05:42 UTC]
[Warn  19:13:37.506] Caught an exception - No support GNOME Settings Daemon could be reached. (in `Banshee.MultimediaKeys')
  at Banshee.MultimediaKeys.MultimediaKeysService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] 
[Warn  19:13:37.506] Extension `Banshee.MultimediaKeys.MultimediaKeysService' not started: No support GNOME Settings Daemon could be reached.

(Banshee:6405): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstcdparanoia.so': /usr/lib/libcdda_paranoia.so.0: invalid ELF header
[Warn  19:13:37.646] Caught an exception - No support GNOME Settings Daemon could be reached. (in `Banshee.MultimediaKeys')
  at Banshee.MultimediaKeys.MultimediaKeysService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] 
[Warn  19:13:37.646] Extension `Banshee.MultimediaKeys.MultimediaKeysService' not started: No support GNOME Settings Daemon could be reached.
[Info  19:13:37.647] All services are started 1.272875s
[Info  19:13:37.902] GNOME screensaver service not found
[Info  19:13:38.102] nereid Client Started

** (Banshee:6397): WARNING **: The following assembly referenced from /usr/lib/banshee-1/Extensions/Banshee.Podcasting.dll could not be loaded:
     Assembly:   taglib-sharp    (assemblyref_index=7)
     Version:    2.0.3.2
     Public Key: db62eba44689b5b0
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/banshee-1/Extensions).


** (Banshee:6397): WARNING **: Could not load file or assembly 'taglib-sharp, Version=2.0.3.2, Culture=neutral, PublicKeyToken=db62eba44689b5b0' or one of its dependencies.



```

---

### Post by directhex on 2009-03-18
It can't find taglib-sharp 2.0.3.2. This is on an up-to-date Jaunty?

---

### Post by halfsane on 2009-03-18
yes indeed!

---

### Post by halfsane on 2009-03-19
Something is up here, I try to install taglib-sharp (downloaded it from the web) 

 and i get this when i run ./configure


checking for gmcs... no
configure: error: You need mcs



im pretty sure i have that package installed... its the mono gmcs package correct?

---

### Post by Hallavej on 2009-03-20
taglib-sharp is in package libtaglib2.0-cil, and its a dependency of banshee so it should be there.
Check if the file exists:

locate taglib-sharp.dll

and if mono knows its there:

gacutil -l | grep taglib-sharp

If not, maybe simply reinstalling bashee and libtaglib2.0-cil would work.
if its there then I have no idea whats wrong. Banshee works fine here.

---

