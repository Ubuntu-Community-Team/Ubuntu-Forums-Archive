---
title: "Cannot start gnome-shell in an Android chroot"
date: 2013-02-20
forum: Installation &amp; Upgrades
---

### Post by kupiakos on 2013-02-20
In my Android-hosted Ubuntu 13.04 chroot, I am attempting to get gnome-shell running on Xvfb. I've handled rendering issues as far as I know, and now I'm having trouble with gnome-shell. I suspect D-Bus.

I've gotten D-Bus running in my chroot by using [this]("http://gyp.blogs.balabit.com/2011/01/using-upstart-in-a-chroot/") special python-based replacement of upstart and running /etc/init.d/rcS, /etc/init.d/rc 2 and start upstart. X starts up swimmingly. AFAIK, these are the packages I installed with apt-get:

ubuntu-desktop
gnome-shell
Xvfb
Unfortunately, I've hit a roadblock. I don't know enough about D-Bus to get gnome-shell past this error:

```

libEGL warning: GLX/ DRI2 is not supported
      JS LOG: IBus version is too old

** (gnome-screensaver:2573): WARNING **: Couldn't get presence status: The name org.gnome.SessionManager was not provided by any .service files

** (gnome-screensaver:2573): WARNING **: screensaver already running in this session

(gnome-shell:2566): Gvc-WARNING **: Failed to connect context: OK
Window manager warning: Log level 16: Could not initialize NMClient /org/freedesktop/NetworkManager: The name org.freedesktop.NetworkManager was not provided by any .service files
    JS ERROR: !!!   Exception was: Gio.DBusError: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.ConsoleKit was not provided by any .service files
    JS ERROR: !!!     message = '"GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.ConsoleKit was not provided by any .service files"'
    JS ERROR: !!!     fileName = '"/usr/share/gnome-shell/js/ui/components/polkitAgent.js"'
    JS ERROR: !!!     lineNumber = '329'
    JS ERROR: !!!     stack = '"0 anonymous()@/usr/share/gnome-shell/js/ui/components/polkitAgent.js:329
1 wrapper()@/usr/share/gjs-1.0/lang.js:204
2 anonymous("name" = ""polkitAgent"")@/usr/share/gnome-shell/js/ui/components/__init__.js:56
3 wrapper(""polkitAgent"")@/usr/share/gjs-1.0/lang.js:204
4 anonymous("name" = ""polkitAgent"", 1, [object Array])@/usr/share/gnome-shell/js/ui/components/__init__.js:22
5 anonymous()@/usr/share/gnome-shell/js/ui/components/__init__.js:21
6 wrapper()@/usr/share/gjs-1.0/lang.js:204
7 anonymous()@/usr/share/gnome-shell/js/ui/components/__init__.js:13
8 wrapper()@/usr/share/gjs-1.0/lang.js:204
9 anonymous()@/usr/share/gjs-1.0/lang.js:145
10 anonymous()@/usr/share/gjs-1.0/lang.js:239
11 start()@/usr/share/gnome-shell/js/ui/main.js:150
12 <TOP LEVEL>@<main>:1
"'
Window manager warning: Log level 32: Execution of main.js threw exception: Gio.DBusError: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.ConsoleKit was not provided by any .service files

```

I assume it's having trouble finding and executing some sort of service org.freedesktop.ConsoleKit. I assume I have some sort of configuration gone horribly awry. Are there any D-Bus gurus here that can help me?

---

### Post by MAFoElffen on 2013-02-23
I saw when this first came up and 2 days later, still see this as unanswered...

What Android device is this on? A handheld? What version and who's kernel are you chrooting from?

Since it is a gnome-screensaver error which on desktops, a lot of us remove and install xscreensaver back in it's place for a working screensaver in >= 12.04. And you are trying to get 13.04 alpha working.

gnome-screensaver just blanks and locks the screen on wakeup. A bit boring and not very colorful for a desktop... But on a handheld device, such as a phone, that behavior would be desirable as it saves on battery life.

As Xserver goes through dbus for system calls. But for Xvfb? Curious why you are using an X virtual frame buffer... a package that simulates an X server that can run on machines with no display hardware and no physical input devices? Meant to be on a headless device... I'm no doctor, but I'm suspecting that as the conflict with gnome-xserver which poles for input and affects display output, including acpi calls to a display's energy saving features...

Just a guess, but either try removing gnome-xscreensaver and substitute xscreensaver... which would also require an upstart change to autostart the daemon on Xinit. --OR-- If you truly want a full working Linux instance that you can interact with, try substituting Xvfb for a different  framebuffer driver.

The again, there might be a different package for Ubuntu phones altogether... The screen shots I've seen for those show a behavior of blank, then on wakeup, the Android styled panel with the swipe gesture tabs 2/3rds down the screen to unlock the screen.

Just my thoughts on that. 

If a handheld device, another resource with experience chrooting Ubuntu from Android devices is XDA Developers. I've been a member there for many years, so I know they have experience playing with this "there" also. That's how I know there's some different functionality chrooting from different device's flashed kernels.

If you find what has worked, I'd be interested in your solution.

---

