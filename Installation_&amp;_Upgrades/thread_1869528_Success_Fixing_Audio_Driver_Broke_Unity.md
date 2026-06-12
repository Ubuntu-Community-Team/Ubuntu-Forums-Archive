---
title: "Success Fixing Audio Driver Broke Unity"
date: 2011-10-25
forum: Installation &amp; Upgrades
---

### Post by ProntoAnthony on 2011-10-25
I've been scouring this forum for ideas and suggestions. The latest one being [https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

I was trying to follow the instructions and ended up removing several repository sources in the Other Software Category. Unfortunately I cannot tell you which ones of my repositories I removed. Synaptic Package Manager | File | History doesn't list them either.

However now when I log into Unity I never get to anything other than my wallpaper background. I can do a Control-T and bring terminal up. So I logged out and tried Unity 2D.

When I login to Unity 2D it comes up fine, but most importantly my Audio Driver is found (I see it in Sound Settings) and the PC now will play audio that I can hear!

The audio driver remains in Gnome, too.

So how do I fix my system to re-install Unity 3D? When I go into Synaptic Package Manager and do a Quick Filter on Unity and then right-click on unity, the option for Mark For Reinstallation is greyed out.

In fact the Mark For Reinstallation is greyed out of all packages.

In terminal I do a:

Unity --replace

The result is shows a Compiz bug:

anthony@anthony-Dimension-E521:~$ unity --replace
unity-panel-service: no process found
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Skipping upgrade com.canonical.unity.unity.01.upgrade
Skipping upgrade com.canonical.unity.unity.02.upgrade
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
compiz (core) - Warn: Value type is not yet set
compiz (core) - Warn: Value type is not yet set
Initializing mousepoll options...done
Initializing vpswitch options...done
Initializing animation options...done
Initializing snap options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing move options...done
Initializing place options...done
Initializing grid options...done
Initializing gnomecompat options...done
Initializing wall options...done
Initializing ezoom options...done
Initializing workarounds options...done
Initializing staticswitcher options...done
Initializing resize options...done
Initializing fade options...done
Initializing scale options...done
Initializing session options...done
Starting unity-window-decorator
Setting Update "shadow_radius"
Setting Update "shadow_opacity"
Setting Update "shadow_x_offset"
Setting Update "shadow_y_offset"
Setting Update "border_width"
compiz (core) - Warn: unhandled ConfigureNotify on 0x2200127!
compiz (core) - Warn: this should never happen. you shouldprobably file a bug about this.



I'm out of ideas at the moment. Any help would be appreciated.

---

### Post by raja.genupula on 2011-10-26
are you sure that in ccsm unity box checked ? 

have you tried 

unity --reset

if above things are not worked then try to remove it with purge and install again.

sudo apt-get remove --purge <pkg name>

then install it again .

all the best,

---

### Post by ProntoAnthony on 2011-10-26
Raja,

Thanks, but remember, I can't seem to install anything. Here is a record of what I tried:

anthony@anthony-Dimension-E521:~$ sudo apt-get remove --purge unity
[sudo] password for anthony: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  unity*
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
After this operation, 2,527 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 173145 files and directories currently installed.)
Removing unity ...
Processing triggers for man-db ...
anthony@anthony-Dimension-E521:~$ sudo apt-get install  unity
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package unity is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  unity-common unity-services

E: Package 'unity' has no installation candidate
anthony@anthony-Dimension-E521:~$ sudo apt-get install  unity-common unity-services
Reading package lists... Done
Building dependency tree       
Reading state information... Done
unity-services is already the newest version.
unity-services set to manually installed.
unity-common is already the newest version.
The following packages were automatically installed and are no longer required:
  libunity-misc4 indicator-power libbamf3-0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
anthony@anthony-Dimension-E521:~$ 


-----------------


I'm going to get my laptop and see about adding the repositories it has that my desktop does not. That should do it.

---

### Post by ProntoAnthony on 2011-10-26
Nothing like some heart-stopping excitement in the morning!

I'll spare the details, but I managed to copy over the /etc/apt/sources.list file to my desktop.

I then entered into terminal:

apt-get update
apt-get upgrade

then I went into synaptic package manager just to check that I could add packages from the program utility again and installed unity.

Then the moment of truth: I logged out of Unity 2D and tried logging into Unity.

No change. It wouldn't come up! So I went into Unity 2D and then went into CompizConfig Manager and noticed the Unity Plug-in wasn't checked. Of course not, I thought. I just loaded it. 

Once I checked it I am able to log in to Unity, plus I have my sound. 

Yippee!

---

### Post by raja.genupula on 2011-10-26
yeah! again ccsm in the action.

Enjoy The Ubuntu.

---

