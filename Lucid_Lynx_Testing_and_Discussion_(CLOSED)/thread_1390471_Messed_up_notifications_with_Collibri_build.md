---
title: "Messed up notifications with Collibri build"
date: 2010-01-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by DeadSuperHero on 2010-01-25
I recently noticed that KDE SC 4.4 for Kubuntu seemed to lack Ayatana-style notifications, so you can imagine how I jumped at the chance to build them with the Colibri package.

Everything built just fine, and the notifications seemed to use the Plasma theme I was using at the time. The control module never showed up for Collibri after building it, so I couldn't position the notifications where I wanted them to be. Long story short, I got tired of KDE, uninstalled everything, and went back to Gnome. However, now all of my notifications still have the Plasma theme in the notifications. The screenshot below demonstrates the problem.

How do I fix the Ayatana notifications to have their default look? Do I need to reinstall the package, or do I need to get gedit out and do some good old fashioned file configuring?

---

### Post by koso on 2010-01-25
Have you deleted all files, which vere installed into system after colibri installation? Especialy .desktop file, and .service file.

This is probably name of service file:
org.freedesktop.Notifications.service

It should be locatedd in /usr/share/dbus-1/services/

---

### Post by raycosm on 2010-01-25
I risk thread hijacking, but how did you ever get it to compiled? I'm on KDE 4.4 RC2 and every time I try to compile, I get this

```
ryan@ryan-laptop:~/Downloads/colibri-0.1.0$ cmake -DCMAKE_INSTALL_PREFIX=/usr /home/ryan/Downloads/colibri-0.1.0/
-- The C compiler identification is GNU
-- The CXX compiler identification is unknown
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was not found.   Please set CMAKE_CXX_COMPILER to a valid compiler path or name.
CMake Error at /usr/share/cmake-2.6/Modules/FindKDE4.cmake:84 (MESSAGE):
  ERROR: cmake/modules/FindKDE4Internal.cmake not found in
  /home/ryan/.kde/share/apps;/usr/share/kubuntu-default-settings/kde4-profile/default/share/apps;/usr/share/kde4/apps
Call Stack (most recent call first):
  CMakeLists.txt:13 (find_package)


CMake Warning (dev) in CMakeLists.txt:
  No cmake_minimum_required command is present.  A line of code such as

    cmake_minimum_required(VERSION 2.6)

  should be added at the top of the file.  The version specified may be lower
  if you wish to support older CMake versions for this project.  For more
  information run "cmake --help-policy CMP0000".
This warning is for project developers.  Use -Wno-dev to suppress it.

-- Configuring incomplete, errors occurred!

```

Do you mind telling me the steps on how you managed to compile it? I don't really know what I'm doing.

---

### Post by DeadSuperHero on 2010-01-25
You probably need a C++ compiler. Also, it can't hurt to try kdelibs5.

---

### Post by DeadSuperHero on 2010-01-25
I checked the path, as well as the org.freedesktop.Notifications.service file, but I can't find anything pertaining to Collibri.

That said, I got rid of my lingering .kde file, and the style of the notifications reverted back to Oxygen. So I'm a step further, but I still have no idea what to do next.

---

### Post by Eclipse. on 2010-01-25
Mind sharing the theme details of the screenshot? :)

Thanks

---

### Post by DeadSuperHero on 2010-01-25
> **Eclipse. said:**
> Mind sharing the theme details of the screenshot? :)

Thanks

Er, it's just New Wave 0.8.0 with a space background, and Humanity icons.

I'm still having no luck with getting the notifications to change back to their original form. Would reinstalling the notify-osd package possibly fix it?

Edit:

I tried removing some KDE libraries that were still sitting around (kdelibs5, kdebase-runtime-bin, etc.), and now all Notify-OSD is rendering is the text of the notification, nothing else. How to fix this...hmmm...

I've included another screenshot for details. Peculiar indeed.

---

### Post by koso on 2010-01-26
Colibri Build-Depends: debhelper (>= 7), cmake, kdelibs5-dev (>=  4:4.3.85), x11proto-xext-dev


And the notification problem. Maybe gnome has its own service while, which was overriden by colibri. Try to reinstal whole desktop. Or try to search for that service file in packages. Also I woud look, if there is running proces "colibri", I dont know exactly the name, but in KDE, after first colibri notification, this process was started ... those notification look like colibri, only without theme so that is becase you removed KDE4 libraries, which can rendere it.

---

### Post by DeadSuperHero on 2010-01-26
After a quick update and a restart, notify-osd doesn't work at all. When I try a and put in 

> notify-send "Test"

I end up getting output like this:

> libnotify-Message: GetServerInformation call failed: Launch helper exited with unknown return code 127
libnotify-Message: Error getting spec version


Confusing, to say the least!

---

### Post by DeadSuperHero on 2010-01-26
Finally fixed the problem by building the latest release on Launchpad from source. Works great now.

---

