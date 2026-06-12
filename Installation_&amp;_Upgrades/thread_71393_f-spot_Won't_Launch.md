---
title: "f-spot Won't Launch"
date: 2005-10-03
forum: Installation &amp; Upgrades
---

### Post by edm00se on 2005-10-03
I installed f-spot last week and have so far been unable to get it to launch. The output I get when I run it from terminal is below:
> eric@RabbitHole:~$ f-spot
** (/usr/lib/f-spot/f-spot.exe:8283): WARNING **: The following assembly referenced from /usr/lib/f-spot/f-spot.exe could not be loaded:
Assembly: gnome-sharp (assemblyref_index=7)
Version: 1.0.0.0
Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/f-spot).
** (/usr/lib/f-spot/f-spot.exe:8283): WARNING **: The class Gnome.Program could not be loaded, used in /usr/lib/f-spot/f-spot.exe (token 0x0100012e)
Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
All help is greatly appreciated.

---

### Post by Tinwood on 2005-10-06
[quote=edm00se]I installed f-spot last week and have so far been unable to get it to launch. The output I get when I run it from terminal is below:

All help is greatly appreciated.[/quote] 
Ah, well, you need to install mono:

(Note this is from the Beagle installation page - it worked for my copy of F-Spot : [http://www.beaglewiki.org/index.php/UbuntuInstall]("http://www.beaglewiki.org/index.php/UbuntuInstall") ):


 > First, edit your /etc/apt/sources.list file. You'll need to add an Ubuntu Backports Project mirror to your sources.list. There is a [list of mirrors]("http://backports.ubuntuforums.org/url.php") ([http://backports.ubuntuforums.org/url.php]("http://backports.ubuntuforums.org/url.php")) available.  For example, add the following line to the bottom of the file: 
 deb [http://acm.cs.umn.edu/ubp/]("http://acm.cs.umn.edu/ubp/") hoary-backports main universe multiverse restricted
Then run the following commands in a terminal: 
$ sudo apt-get update
$ sudo apt-get install libmono0 libmono-dev mono mono-devel mono-jit mono-utils \
mono-mcs mono-assemblies-arch mono-assemblies-base mono-common 
$ sudo apt-get install libdbus-cil libevolution-cil libgconf-cil libgecko-cil \
 libglade-cil libgmime-cil libgnome-cil libgnome2.0-cil libgnomevfs2-dev libgsf-cil \
libgtk-cil libgnomeui-dev libsqlite0-dev
 Hope that helps.

-- 
Alex.

---

### Post by edm00se on 2005-10-07
[QUOTE=Tinwood]Ah, well, you need to install mono:[/QUOTE]

I did have mono installed. I have since reinstalled mono and all subsidiary packages from a source build. f-spot now works, and I am quite happy to be able to upload to my flickr account with it. I was merely hoping there was something I was missing that would magically fix everything without having to do it the hard way.

---

