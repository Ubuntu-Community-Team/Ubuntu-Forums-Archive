---
title: "The player project (player / stage / gazebo)"
date: 2011-03-13
forum: Installation &amp; Upgrades
---

### Post by Morten ML on 2011-03-13
Thread copied to education and science:
[http://ubuntuforums.org/showthread.php?p=10558371#post10558371]("http://ubuntuforums.org/showthread.php?p=10558371#post10558371")
and closed here.
Hi all

I am posting my own "personal" notes on how to install gazebo player and stage here - so i can find it later. Hope this helps anybody else who wants to use these programs. I am currently using Merkat in 64 bit version...

**Installation**
adding all of the three (player/stage/gazebo) to ubuntu software center:
from this page: 
[http://playerstage.sourceforge.net/wiki/Download]("http://playerstage.sourceforge.net/wiki/Download")
read it and you get redirected to:
[https://launchpad.net/~thjc/+archive/ppa/]("https://launchpad.net/~thjc/+archive/ppa/")
Now all three programs can be found in the software center. However "player" and "stage" are called "robot-player" and "robot-stage" since other programs already have names of "player" and "stage". For "gazebo" this is not the case...
to launch player the code is therefore:
```
robot-player /usr/share/stage/worlds/simple.cfg

```

**Gazebo Problems**
```
gazebo /usr/share/gazebo/worlds/pioneer2dx.world
Gazebo multi-robot simulator, version 0.10.0

Part of the Player/Stage Project [http://playerstage.sourceforge.net].
Copyright (C) 2003 Nate Koenig, Andrew Howard, and contributors.
Released under the GNU General Public License.

[/build/buildd/gazebo-0.10.0/server/GazeboConfig.cc:124]
  Unable to find the file ~/.gazeborc. Using default paths. This may cause OGRE to fail.
terminate called after throwing an instance of 'Ogre::InvalidParametersException'
  what():  OGRE EXCEPTION(2:InvalidParametersException): Sky dome material 'Gazebo/CloudySky' not found. in SceneManager::setSkyDome at OgreSceneManager.cpp (line 1801)
Aborted

```
FIX:
create a file named ".gazeborc" in home directory. copy from this:
[http://www.mail-archive.com/playerstage-gazebo@lists.sourceforge.net/msg00851.html]("http://www.mail-archive.com/playerstage-gazebo@lists.sourceforge.net/msg00851.html")
but since ubuntu does not have the "local" folder change to:
```
<?xml version="1.0"?>
 <gazeborc>
   <gazeboPath>/usr/share/gazebo</gazeboPath>
   <gazeboPath>/home/YOUROWNNAME/share/gazebo</gazeboPath>
   <ogrePath>/usr/lib/OGRE</ogrePath>
   <gazeboPath>/home/YOUROWNNAME/lib/OGRE</gazeboPath>
   <RTTMode>PBuffer</RTTMode>
</gazeborc>
```
(Substitute YOUROWNNAME with you name on the machine)
and wow gazebo runs. You can test it using this code:
```

gazebo /usr/share/gazebo/worlds/pioneer2dx.world

```
huha!

**Stage problems**
```

robot-player /usr/share/stage/worlds/simple.cfg
Registering driver
Player v.3.0.2

* Part of the Player/Stage/Gazebo Project [http://playerstage.sourceforge.net].
* Copyright (C) 2000 - 2009 Brian Gerkey, Richard Vaughan, Andrew Howard,
* Nate Koenig, and contributors. Released under the GNU General Public License.
* Player comes with ABSOLUTELY NO WARRANTY.  This is free software, and you
* are welcome to redistribute it under certain conditions; see COPYING
* for details.

invoking player_driver_init()...
 Stage driver plugin init

 ** Stage plugin v4.0.0 **
 * Part of the Player Project [http://playerstage.sourceforge.net]
 * Copyright 2000-2009 Richard Vaughan, Brian Gerkey and contributors.
 * Released under the GNU General Public License v2.

success
 Stage plugin:  6665.simulation.0 is a Stage world
 [Loading /usr/share/stage/worlds/simple.world][Include pioneer.inc][Include map.inc][Include sick.inc]f: /usr/share/stage/worlds/simple.world
Libtool error: file not found. Can't open your plugin controller. Quitting
err: Failed to open "wander". Check that it can be found by searching the directories in your STAGEPATH environment variable, or the current directory if STAGEPATH is not set.]
 (/build/buildd/stage-4.0.0/libstage/model_load.cc LoadControllerModule)
libtool error #2

``` 
This error is caused by a some call to a "demonstration" of a plugin controller in the file "simple.world" which the file simple.cfg points too/ opens. If the line "ctrl wander" ( line 48 ) is omitted in the file simple.world it works... sort of.

EDIT: I will keep reediting this post everytime i make a new "baby step" towards the final goal of having all three running on my system. I any moderaters see a problem with this please post here.

---

### Post by Sef on 2011-04-21
Locked. [Duplicate Thread]("http://ubuntuforums.org/showthread.php?t=1706693").

---

