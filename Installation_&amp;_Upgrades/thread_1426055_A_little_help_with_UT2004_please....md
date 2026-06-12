---
title: "A little help with UT2004 please...?"
date: 2010-03-09
forum: Installation &amp; Upgrades
---

### Post by Jiharu Ikumiya on 2010-03-09
Hi guys, I'm having some trouble with my UT2004.

I finally got it to install without problems and patched. My issue is that when I try to start a map, I get this error:
```

Assertion failed: InPos<=Size [File:../../Core/Inc/FFileManagerUnix.h] [Line: 180]

History: 

Exiting due to error
```I searched and searched all over the web, but I can't seem to find anything related to this problem. I found a couple posts about this but they're all related to server administration. I was just trying to run instant action for myself! @_@

Anyone know what this is? D:

I'm fairly new to Ubuntu 9.10 (or linux in general ^^;) so any kind of help would be greatly appreciated, thanks guys! ^_~

---

### Post by menaamism on 2010-04-12
*bumps*
 
 I seem to be having the same problem, except that the game doesn't initiate at all and exists right after the splashscreen.
 
 It's a fresh install, with the only I've changed is copied in the megapack, the most recent update, and hotlinked the libsdl-1.2.so.0 and libopenal.so to replace the original ones from UT2004.
 
 Terminal output:
 ```

 m@APC1:~$ ut2004
 Exporting CTF-BP2-Concentrate.....Successful!
 Exporting AS-BP2-SubRosa.....Successful!
 Exporting AS-BP2-Acatana.....Successful!
 Exporting DM-BP2-GoopGod.....Successful!
 Exporting AS-BP2-Jumpship.....Successful!
 Exporting AS-BP2-Thrust.....Successful!
 Exporting CTF-BP2-Pistola.....Successful!
 Assertion failed: InPos<=Size [File:../../Core/Inc/FFileManagerUnix.h] [Line: 180]
 
 History:
 
 Exiting due to error
```Log Output:```

 Log: Log file open, Mon Apr 12 13:57:30 2010
 Init: Name subsystem initialized
 Init: Version: 3369 (128.29)
 Init: Compiled: Dec 16 2005 13:23:47
 Init: Command line: 
 Init: (This is Linux patch version 3369.2)
 Init: Character set: Unicode
 Init: Base directory: /usr/local/games/ut2004/System/
 Init: Ini:UT2004.ini   UserIni:User.ini
 Init: Build label: UT2004 Build UT2004_Build_[2005-11-23_16.22]
 Init: Object subsystem initialized
 Log: Initializing OpenGLDrv...
 Log: binding libGL.so.1
 Log: Game class is 'GameInfo'
 Log: Bringing Level Entry.myLevel up for play (0) appSeconds: 7.393566...
 ScriptLog: GameInfo::InitGame : bEnableStatLogging False
 Log: Browse: NvidiaLogo.ut2?Name=Player?Class=Engine.Pawn?Character=Jakob?team=255
 Log: Collecting garbage
 Log: Purging garbage
 Log: Garbage: objects: 33847->33844; refs: 350100
 Log: Game class is 'CinematicGame'
 Log: Bringing Level NvidiaLogo.myLevel up for play (0) appSeconds: 8.477256...
 ScriptLog: GameInfo::InitGame : bEnableStatLogging False
 Log: Created and initialized a new SDL viewport.
 Log: Exporting CTF-BP2-Concentrate.....Successful!
 Warning: Missing Cubemap Cubemap AW-Cubes.Cubes.MesaEnv2
 Warning: Missing Cubemap Cubemap AW-Cubes.Cubes.MesaEnv1
 Log: Exporting AS-BP2-SubRosa.....Successful!
 Log: Exporting AS-BP2-Acatana.....Successful!
 Log: Exporting DM-BP2-GoopGod.....Successful!
 Log: Exporting AS-BP2-Jumpship.....Successful!
 Log: Exporting AS-BP2-Thrust.....Successful!
 Log: Exporting CTF-BP2-Pistola.....Successful!
 Critical: Assertion failed: InPos<=Size [File:../../Core/Inc/FFileManagerUnix.h] [Line: 180]
 Exit: Executing UObject::StaticShutdownAfterError
 Exit: Executing USDLClient::ShutdownAfterError
 Exit: Exiting.
 Log: FileManager: Reading 0 GByte 44 MByte 818 KByte 684 Bytes from HD took 8.767414 seconds (8.767414 reading, 0.000000 seeking).
 Log: FileManager: 0.000000 seconds spent with misc. duties
 Uninitialized: Name subsystem shut down
 Uninitialized: Log file closed, Mon Apr 12 13:57:43 2010
```PS: Is four weeks considered a necropost around here? *flees and takes cover* Thread was found in google. I'm not aware of any more recent threads.

EDIT1: I did a clean reinstall and ran the game without updating anything, and now it starts apart from the usual ALSA error, but maybe that can be fixed with hotlinking the native ubuntu lib.

EDIT2: Tried some stuff, putting the megapack in there seems to hurt it, but patch 3669-2 does no harm at all... Oh well, it seems i'll be stuck with manually putting in the maps and vehicles...

---

