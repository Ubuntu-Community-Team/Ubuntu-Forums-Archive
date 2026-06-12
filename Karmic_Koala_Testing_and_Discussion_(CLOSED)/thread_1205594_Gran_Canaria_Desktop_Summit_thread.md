---
title: "Gran Canaria Desktop Summit thread"
date: 2009-07-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by castrojo on 2009-07-06
Hi guys,

I am in Gran Canaria attending the GNOME/KDE summit. I don't have much time so I will just dump a URL. We have GNOME-shell available in a PPA:

[https://launchpad.net/~ubuntu-desktop/+archive/ppa](https://launchpad.net/~ubuntu-desktop/+archive/ppa)

Add that and then you can just run "gnome-shell" and you'll get it in a Xephyr session, if you want to replace your whole desktop do "gnome-shell --replace"

I am attending sessions and am around, if you have burning questions about anything please put it in this thread and I will do my best to answer. (Internet access is bad so please bear with me if I disappear)

EDIT: I'm putting this in the Karmic forum because that's where all the stuff that's being discussed is currently being packaged.

---

### Post by gnomeuser on 2009-07-06
I do hope you enjoy Aaron' presentation tomorrow on Banshee and Desktop 2.0, bring us back more presents please.

---

### Post by yelo3 on 2009-07-06
about gnome-shell and the PPA: it does not run, because Cogl 0.9 is missing.
What is Cogl 0.9? I couldn't find it in ubuntu packages

---

### Post by artir on 2009-07-06
cogl is a part of clutter

---

### Post by celticbhoy on 2009-07-06
I get message saying Xephyer is missing.

---

### Post by castrojo on 2009-07-06
You need to install xserver-xephyr

---

### Post by zekopeko on 2009-07-06
> **gnomeuser said:**
> I do hope you enjoy Aaron' presentation tomorrow on Banshee and Desktop 2.0, bring us back more presents please.

i can't wait to see what Cubano is all about. are there any screenshots floating around?

---

### Post by Merk42 on 2009-07-06
Can you bring a giant sign that reads "No Sidebar for GNOME Shell"?

Seriously though, with that PPA does that mean I don't have to rebuild it, and it just updates through update manager?

---

### Post by celticbhoy on 2009-07-06
Getting this :-


gary@Testing:~$ sudo apt-get install xserver-xypher
[sudo] password for gary: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xserver-xypher
gary@Testing:~$

---

### Post by pferraro on 2009-07-06
> **celticbhoy said:**
> Getting this :-


gary@Testing:~$ sudo apt-get install xserver-xypher
[sudo] password for gary: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xserver-xypher
gary@Testing:~$

Check your spelling...
xserver-xephyr

---

### Post by zekopeko on 2009-07-06
> **celticbhoy said:**
> Getting this :-


gary@Testing:~$ sudo apt-get install xserver-xypher
[sudo] password for gary: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xserver-xypher
gary@Testing:~$

do re-read what you've written. or at least copy/paste it. or use synaptic.

---

### Post by celticbhoy on 2009-07-06
oooooops.

---

### Post by gnomeuser on 2009-07-06
yeah this fails to launch  xserver-xephyr or natively.

---

### Post by morryis on 2009-07-06
It doesn't work for me, when running _gnome-shell_ I get:
```

xauth:  creating new authority file /tmp/gnome-shell.0sEfUr/database
[dix] Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
[config/dbus] couldn't take over org.x.config: org.freedesktop.DBus.Error.AccessDenied (Connection ":1.118" is not allowed to own the service "org.x.config.display82" due to security policies in the configuration file)
unrecognised device identifier!
(EE) config/hal: NewInputDeviceRequest failed (2)
unrecognised device identifier!
(EE) config/hal: NewInputDeviceRequest failed (2)
unrecognised device identifier!
(EE) config/hal: NewInputDeviceRequest failed (2)
unrecognised device identifier!
(EE) config/hal: NewInputDeviceRequest failed (2)
unrecognised device identifier!
(EE) config/hal: NewInputDeviceRequest failed (2)
    JS ERROR: !!!   Exception was: Error: Requiring Meta, version none: Typelib file for namespace 'Cogl', version '0.9' not found
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = 'gjs_throw'
    JS ERROR: !!!     stack = 'Error("Requiring Meta, version none: Typelib file for namespace 'Cogl', version '0.9' not found")@:0
("Requiring Meta, version none: Typelib file for namespace 'Cogl', version '0.9' not found")@gjs_throw:0
@/usr/share/gnome-shell/js/ui/main.js:8
'
    JS ERROR: !!!     message = 'Requiring Meta, version none: Typelib file for namespace 'Cogl', version '0.9' not found'
    JS ERROR: !!!   Exception was: Error: Requiring Meta, version none: Typelib file for namespace 'Cogl', version '0.9' not found
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = 'gjs_throw'
    JS ERROR: !!!     stack = 'Error("Requiring Meta, version none: Typelib file for namespace 'Cogl', version '0.9' not found")@:0
("Requiring Meta, version none: Typelib file for namespace 'Cogl', version '0.9' not found")@gjs_throw:0
@/usr/share/gnome-shell/js/ui/main.js:8
'
    JS ERROR: !!!     message = 'Requiring Meta, version none: Typelib file for namespace 'Cogl', version '0.9' not found'
Fenstermanager-Warnung:Log level 32: Execution of main.js threw exception: Error: Requiring Meta, version none: Typelib file for namespace 'Cogl', version '0.9' not found

```

---

### Post by soapytheclown on 2009-07-06
> **morryis said:**
> It doesn't work for me, when running _gnome-shell_ I get:
```

xauth:  creating new authority file /tmp/gnome-shell.0sEfUr/database
[dix] Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
[config/dbus] couldn't take over org.x.config: org.freedesktop.DBus.Error.AccessDenied (Connection ":1.118" is not allowed to own the service "org.x.config.display82" due to security policies in the configuration file)
unrecognised device identifier!
(EE) config/hal: NewInputDeviceRequest failed (2)
unrecognised device identifier!
(EE) config/hal: NewInputDeviceRequest failed (2)
unrecognised device identifier!
(EE) config/hal: NewInputDeviceRequest failed (2)
unrecognised device identifier!
(EE) config/hal: NewInputDeviceRequest failed (2)
unrecognised device identifier!
(EE) config/hal: NewInputDeviceRequest failed (2)
    JS ERROR: !!!   Exception was: Error: Requiring Meta, version none: Typelib file for namespace 'Cogl', version '0.9' not found
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = 'gjs_throw'
    JS ERROR: !!!     stack = 'Error("Requiring Meta, version none: Typelib file for namespace 'Cogl', version '0.9' not found")@:0
("Requiring Meta, version none: Typelib file for namespace 'Cogl', version '0.9' not found")@gjs_throw:0
@/usr/share/gnome-shell/js/ui/main.js:8
'
    JS ERROR: !!!     message = 'Requiring Meta, version none: Typelib file for namespace 'Cogl', version '0.9' not found'
    JS ERROR: !!!   Exception was: Error: Requiring Meta, version none: Typelib file for namespace 'Cogl', version '0.9' not found
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = 'gjs_throw'
    JS ERROR: !!!     stack = 'Error("Requiring Meta, version none: Typelib file for namespace 'Cogl', version '0.9' not found")@:0
("Requiring Meta, version none: Typelib file for namespace 'Cogl', version '0.9' not found")@gjs_throw:0
@/usr/share/gnome-shell/js/ui/main.js:8
'
    JS ERROR: !!!     message = 'Requiring Meta, version none: Typelib file for namespace 'Cogl', version '0.9' not found'
Fenstermanager-Warnung:Log level 32: Execution of main.js threw exception: Error: Requiring Meta, version none: Typelib file for namespace 'Cogl', version '0.9' not found

```

same errors for me

---

### Post by castrojo on 2009-07-06
Can someone please file bugs, I don't have time to help you guys debug, but I can help point resources at bugs. If you file them please post here.

---

### Post by autocrosser on 2009-07-06
OK--Whiprush---here's your first one.....

[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/396340](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/396340)

The shell won't run full-screen on my system--have been building the shell for the last few months, so I know all depends are met & I just did a shell build yesterday that works very well..

The error looks to be a simple one----here's the term output:

```
dean@linux:~/Desktop$ gnome-shell --replace
Window manager warning: "" found in configuration database is not a valid value for keybinding "run_command_11"
Window manager warning: Log level 16: Could not load library [/usr/lib/mutter/plugins/libgnome-shell.so (libmozjs.so: cannot open shared object file: No such file or directory)]
Window manager warning: Log level 8: failed to load plugins

```

---

### Post by yanns on 2009-07-07
Another bug report:
[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/396440](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/396440)

```
 JS IMPORT: Module 'main' left an exception set
    JS ERROR: !!!   Exception was: Error: Requiring Meta, version none: Typelib file for namespace 'Cogl', version '0.9' not found
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = 'gjs_throw'
    JS ERROR: !!!     stack = 'Error("Requiring Meta, version none: Typelib file for namespace 'Cogl', version '0.9' not found")@:0
("Requiring Meta, version none: Typelib file for namespace 'Cogl', version '0.9' not found")@gjs_throw:0
@/usr/share/gnome-shell/js/ui/main.js:8
```

---

### Post by MadsRH on 2009-07-09
> **zekopeko said:**
> i can't wait to see what Cubano is all about. are there any screenshots floating around?

+1

Any screenshots/videos?

[http://github.com/abock/cubano/tree/master](http://github.com/abock/cubano/tree/master)

---

### Post by Marat89 on 2009-07-09
Just read about the Banshee/Cubano talk of Aaron at GCDS on Monday.
Any chance to watch it on video, or some screenshots about the new features and the new UI Cubano?
Building Cubano is atm too hard due to cutting edge dependencies.

---

### Post by gnomeuser on 2009-07-09
> **whiprush said:**
> Can someone please file bugs, I don't have time to help you guys debug, but I can help point resources at bugs. If you file them please post here.

[Why bother](https://bugs.launchpad.net/bugs/396542) when you close bugs in your packaging as invalid.

---

### Post by autocrosser on 2009-07-09
Whiprush--Sebastien Bacher has been running around & calling the bugs "invalid"--could you talk to him about this?  [https://launchpad.net/~seb128](https://launchpad.net/~seb128)

---

### Post by autocrosser on 2009-07-09
> **gnomeuser said:**
> [Why bother]("https://bugs.launchpad.net/bugs/396542") when you close bugs in your packaging as invalid.

I also PM'd Whiprush about this--Sebastien marked my bug as invalid also....

---

### Post by zekopeko on 2009-07-09
the problem is that the ppa's don't have their own instance of launchpads bugs. i think this will be fixed soonish.

So from a tehnical point of view seb was correct to mark the bug as invalid.

---

### Post by autocrosser on 2009-07-09
I understand that---but Whiprush asked us to post bugs to Launchpad--I did so in good faith & don't really like my hand slapped.........

---

### Post by zekopeko on 2009-07-09
> **autocrosser said:**
> I understand that---but Whiprush asked us to post bugs to Launchpad--I did so in good faith & don't really like my hand slapped.........

then don't stick it in strange shell's ;)

but really why don't you just build it from source?

---

### Post by castrojo on 2009-07-09
> **zekopeko said:**
> the problem is that the ppa's don't have their own instance of launchpads bugs. i think this will be fixed soonish.

Just talked to him and this is indeed the case. Unfortunately putting PPA bugs under "ubuntu" isn't a good idea.

If it's obvious the bug isn't a packaging problem it should go upstream and unfortunately we'll have to work around the packaging bugs until it goes into ubuntu proper.

Sorry for the confusion everyone.

---

### Post by plun on 2009-07-09
It works nevertheless after installing the missing package.

gnome-shell --replace


But the "da--ed" lower panel....:-\"

---

### Post by autocrosser on 2009-07-09
> **zekopeko said:**
> then don't stick it in strange shell's ;)

but really why don't you just build it from source?

I've been building from source for the last few months--thought that I could do good on two fronts with a .deb install---my bad..........


but "strange" shells are more fun........:)

---

### Post by autocrosser on 2009-07-09
The whole point of my bug report was that the build from source was working well & the install from .deb would not start with gnome-shell  --replace....sounds like a package problem to me......

---

### Post by Merk42 on 2009-07-10
So have the issues with the ppa been fixed or am I just better off building from source like I have been?

I'd love to have the most 'up to date' version of the shell to test (though mostly to just complain about the sidebar)

---

### Post by plun on 2009-07-11
From the bug report earlier discussed:

> 
_Sebastien Bacher_ wrote on 2009-07-09: (permalink)

you need to install **libclutter-0.9-dev** to fix this issue


So the ppa works just fine with that package installed.

```
gnome-shell --replace
```

Log out and in again for the old Gnome UI

;)

---

### Post by Mazza558 on 2009-07-11
Added the repo, added the key, updated, updated again, and I get this:

> james@james-desktop:~$ sudo apt-get install gnome-shell
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gnome-shell
james@james-desktop:~$ 



---

### Post by morryis on 2009-07-11
According to the Gnome-Shell mailing list, there are some problems with the proprietary nvidia driver ([link]("http://mail.gnome.org/archives/gnome-shell-list/2009-July/msg00041.html")). I still get the following error when running gnome-shell:
```
xauth:  creating new authority file /tmp/gnome-shell.SQ7lJe/database
[dix] Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
[config/dbus] couldn't take over org.x.config: org.freedesktop.DBus.Error.AccessDenied (Connection ":1.69" is not allowed to own the service "org.x.config.display87" due to security policies in the configuration file)
unrecognised device identifier!
(EE) config/hal: NewInputDeviceRequest failed (2)
unrecognised device identifier!
(EE) config/hal: NewInputDeviceRequest failed (2)
unrecognised device identifier!
(EE) config/hal: NewInputDeviceRequest failed (2)
unrecognised device identifier!
(EE) config/hal: NewInputDeviceRequest failed (2)
unrecognised device identifier!
(EE) config/hal: NewInputDeviceRequest failed (2)
      JS LOG: Loading tweener.js
      JS LOG: Loading tweenlist.js
      JS LOG: Done loading tweenlist.js
      JS LOG: Done loading tweener.js
      JS LOG: Loading equations.js
      JS LOG: Done loading equations.js
Fehler in Fenstermanager:Unexpected X error: GLXUnsupportedPrivateRequest serial 1266 error_code 162 request_code 150 minor_code 16)

```
Only a black window with gnome-eyes, terminal and xserver-logo opens. --replace doesn't work for me, too.

---

### Post by frustphil on 2009-07-11
> **Mazza558 said:**
> Added the repo, added the key, updated, updated again, and I get this:

I guess I am not the only one lost here...

---

### Post by plun on 2009-07-11
> **Mazza558 said:**
> Added the repo, added the key, updated, updated again, and I get this:

Strange....

```
plun@plun:~$ sudo apt-get install gnome-shell

Reading package lists... Done
Building dependency tree       
Reading state information... Done

The following extra packages will be installed:
  gjs gobject-introspection gobject-introspection-repository libclutter-0.8-0
  libclutter-0.9-0 libgirepository1 libmutter0 mutter mutter-common
  python-giscanner
The following NEW packages will be installed:
  gjs gnome-shell gobject-introspection gobject-introspection-repository
  libclutter-0.8-0 libclutter-0.9-0 libgirepository1 libmutter0 mutter
  mutter-common python-giscanner
0 upgraded, 11 newly installed, 0 to remove and 1 not upgraded.
Need to get 4691kB of archives.
After this operation, 23.0MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://archive.ubuntu.com karmic/universe libgirepository1 0.6.3-0ubuntu1 [56.4kB]
Get:2 http://ppa.launchpad.net karmic/main gjs 0.3-0ubuntu1 [159kB]
Get:3 http://archive.ubuntu.com karmic/universe python-giscanner 0.6.3-0ubuntu1 [169kB]
Get:4 http://ppa.launchpad.net karmic/main mutter-common 2.27.0~git090630-0ubuntu3 [1836kB]
Get:5 http://archive.ubuntu.com karmic/universe gobject-introspection 0.6.3-0ubuntu1 [55.4kB]
Get:6 http://archive.ubuntu.com karmic/universe libclutter-0.8-0 0.8.8-0ubuntu1 [278kB]
Get:7 http://archive.ubuntu.com karmic/universe gobject-introspection-repository 0.6.4~git20090630-0ubuntu1 [986kB]
Get:8 http://archive.ubuntu.com karmic/universe libclutter-0.9-0 0.9.4-0ubuntu3 [376kB]
Get:9 http://ppa.launchpad.net karmic/main libmutter0 2.27.0~git090630-0ubuntu3 [292kB]
Get:10 http://ppa.launchpad.net karmic/main mutter 2.27.0~git090630-0ubuntu3 [308kB]
Get:11 http://ppa.launchpad.net karmic/main gnome-shell 0.0.1~git20090702-0ubuntu0.1 [174kB]
Fetched 4691kB in 4s (1126kB/s)
Selecting previously deselected package libgirepository1.
(Reading database ... 452286 files and directories currently installed.)
Unpacking libgirepository1 (from .../libgirepository1_0.6.3-0ubuntu1_amd64.deb) ...
Selecting previously deselected package python-giscanner.
Unpacking python-giscanner (from .../python-giscanner_0.6.3-0ubuntu1_amd64.deb) ...
Selecting previously deselected package gobject-introspection.
Unpacking gobject-introspection (from .../gobject-introspection_0.6.3-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libclutter-0.8-0.
Unpacking libclutter-0.8-0 (from .../libclutter-0.8-0_0.8.8-0ubuntu1_amd64.deb) ...
Selecting previously deselected package gobject-introspection-repository.
Unpacking gobject-introspection-repository (from .../gobject-introspection-repository_0.6.4~git20090630-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libclutter-0.9-0.
Unpacking libclutter-0.9-0 (from .../libclutter-0.9-0_0.9.4-0ubuntu3_amd64.deb) ...
Selecting previously deselected package gjs.
Unpacking gjs (from .../gjs_0.3-0ubuntu1_amd64.deb) ...
Selecting previously deselected package mutter-common.
Unpacking mutter-common (from .../mutter-common_2.27.0~git090630-0ubuntu3_all.deb) ...
Selecting previously deselected package libmutter0.
Unpacking libmutter0 (from .../libmutter0_2.27.0~git090630-0ubuntu3_amd64.deb) ...
Selecting previously deselected package mutter.
Unpacking mutter (from .../mutter_2.27.0~git090630-0ubuntu3_amd64.deb) ...
Selecting previously deselected package gnome-shell.
Unpacking gnome-shell (from .../gnome-shell_0.0.1~git20090702-0ubuntu0.1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Setting up libgirepository1 (0.6.3-0ubuntu1) ...

Setting up python-giscanner (0.6.3-0ubuntu1) ...

Setting up gobject-introspection (0.6.3-0ubuntu1) ...
Setting up libclutter-0.8-0 (0.8.8-0ubuntu1) ...

Setting up gobject-introspection-repository (0.6.4~git20090630-0ubuntu1) ...

Setting up libclutter-0.9-0 (0.9.4-0ubuntu3) ...

Setting up gjs (0.3-0ubuntu1) ...

Setting up mutter-common (2.27.0~git090630-0ubuntu3) ...

Setting up libmutter0 (2.27.0~git090630-0ubuntu3) ...

Setting up mutter (2.27.0~git090630-0ubuntu3) ...

Setting up gnome-shell (0.0.1~git20090702-0ubuntu0.1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

```

:confused:

---

### Post by plun on 2009-07-11
> **morryis said:**
> According to the Gnome-Shell mailing list, there are some problems with the proprietary nvidia driver 

I just installed it on my desktop with a nVidia graphic card.

Compiz must be replaced first

```
metacity --replace
```

and then

```
gnome-shell --replace

```

---

### Post by autocrosser on 2009-07-11
Yes--I have both versions working now--the .deb is already looking dated compared to the current build---so I will keep both, but continue to do bug reports on the build......

It's interesting that I had libclutter0.9-dev installed & the .deb version wouldn't start until I also installed libclutter0.8-dev...........

And as for nVidia cards--I'm using a SLI-nVidia 9500GT set without problems....

---

### Post by plun on 2009-07-11
> **autocrosser said:**
> Yes--I have both versions working now--the .deb is already looking dated compared to the current build---so I will keep both, but continue to do bug reports on the build......

It's interesting that I had libclutter0.9-dev installed & the .deb version wouldn't start until I also installed libclutter0.8-dev...........


Well, its strange with my desktop with nVidia graphic, it works sometimes.

With my laptop, X300/ATI it always works

Going to install libclutter08-dev also.....;)

Another good idea is maybe to enable Ctrl-Alt-Backspace for X-restart or Ctrl-Alt-F1 and a sudo /etc/init.d/gdm restart):P

---

### Post by autocrosser on 2009-07-11
I did find out something interesting today---while you are in shell--open a term & do gnome-panel --replace  you can start your normal session panel over the top of the shells panel (I only use a bottom panel--modded similar to OSX dock)--looks kind'a strange, but I get my normal functions that way....

---

### Post by Marat89 on 2009-07-11
hey any idea how to get the talk videos from the summit?

---

### Post by Mazza558 on 2009-07-11
> **plun said:**
> Strange....

```
plun@plun:~$ sudo apt-get install gnome-shell

Reading package lists... Done
Building dependency tree       
Reading state information... Done

The following extra packages will be installed:
  gjs gobject-introspection gobject-introspection-repository libclutter-0.8-0
  libclutter-0.9-0 libgirepository1 libmutter0 mutter mutter-common
  python-giscanner
The following NEW packages will be installed:
  gjs gnome-shell gobject-introspection gobject-introspection-repository
  libclutter-0.8-0 libclutter-0.9-0 libgirepository1 libmutter0 mutter
  mutter-common python-giscanner
0 upgraded, 11 newly installed, 0 to remove and 1 not upgraded.
Need to get 4691kB of archives.
After this operation, 23.0MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://archive.ubuntu.com karmic/universe libgirepository1 0.6.3-0ubuntu1 [56.4kB]
Get:2 http://ppa.launchpad.net karmic/main gjs 0.3-0ubuntu1 [159kB]
Get:3 http://archive.ubuntu.com karmic/universe python-giscanner 0.6.3-0ubuntu1 [169kB]
Get:4 http://ppa.launchpad.net karmic/main mutter-common 2.27.0~git090630-0ubuntu3 [1836kB]
Get:5 http://archive.ubuntu.com karmic/universe gobject-introspection 0.6.3-0ubuntu1 [55.4kB]
Get:6 http://archive.ubuntu.com karmic/universe libclutter-0.8-0 0.8.8-0ubuntu1 [278kB]
Get:7 http://archive.ubuntu.com karmic/universe gobject-introspection-repository 0.6.4~git20090630-0ubuntu1 [986kB]
Get:8 http://archive.ubuntu.com karmic/universe libclutter-0.9-0 0.9.4-0ubuntu3 [376kB]
Get:9 http://ppa.launchpad.net karmic/main libmutter0 2.27.0~git090630-0ubuntu3 [292kB]
Get:10 http://ppa.launchpad.net karmic/main mutter 2.27.0~git090630-0ubuntu3 [308kB]
Get:11 http://ppa.launchpad.net karmic/main gnome-shell 0.0.1~git20090702-0ubuntu0.1 [174kB]
Fetched 4691kB in 4s (1126kB/s)
Selecting previously deselected package libgirepository1.
(Reading database ... 452286 files and directories currently installed.)
Unpacking libgirepository1 (from .../libgirepository1_0.6.3-0ubuntu1_amd64.deb) ...
Selecting previously deselected package python-giscanner.
Unpacking python-giscanner (from .../python-giscanner_0.6.3-0ubuntu1_amd64.deb) ...
Selecting previously deselected package gobject-introspection.
Unpacking gobject-introspection (from .../gobject-introspection_0.6.3-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libclutter-0.8-0.
Unpacking libclutter-0.8-0 (from .../libclutter-0.8-0_0.8.8-0ubuntu1_amd64.deb) ...
Selecting previously deselected package gobject-introspection-repository.
Unpacking gobject-introspection-repository (from .../gobject-introspection-repository_0.6.4~git20090630-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libclutter-0.9-0.
Unpacking libclutter-0.9-0 (from .../libclutter-0.9-0_0.9.4-0ubuntu3_amd64.deb) ...
Selecting previously deselected package gjs.
Unpacking gjs (from .../gjs_0.3-0ubuntu1_amd64.deb) ...
Selecting previously deselected package mutter-common.
Unpacking mutter-common (from .../mutter-common_2.27.0~git090630-0ubuntu3_all.deb) ...
Selecting previously deselected package libmutter0.
Unpacking libmutter0 (from .../libmutter0_2.27.0~git090630-0ubuntu3_amd64.deb) ...
Selecting previously deselected package mutter.
Unpacking mutter (from .../mutter_2.27.0~git090630-0ubuntu3_amd64.deb) ...
Selecting previously deselected package gnome-shell.
Unpacking gnome-shell (from .../gnome-shell_0.0.1~git20090702-0ubuntu0.1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Setting up libgirepository1 (0.6.3-0ubuntu1) ...

Setting up python-giscanner (0.6.3-0ubuntu1) ...

Setting up gobject-introspection (0.6.3-0ubuntu1) ...
Setting up libclutter-0.8-0 (0.8.8-0ubuntu1) ...

Setting up gobject-introspection-repository (0.6.4~git20090630-0ubuntu1) ...

Setting up libclutter-0.9-0 (0.9.4-0ubuntu3) ...

Setting up gjs (0.3-0ubuntu1) ...

Setting up mutter-common (2.27.0~git090630-0ubuntu3) ...

Setting up libmutter0 (2.27.0~git090630-0ubuntu3) ...

Setting up mutter (2.27.0~git090630-0ubuntu3) ...

Setting up gnome-shell (0.0.1~git20090702-0ubuntu0.1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

```

:confused:

I'm using the Jaunty repos. Maybe they're not ready yet.

---

### Post by Regenweald on 2009-07-11
This turned from a Gran Canaria thread to another shell thread :) Any actual news on Gnome/KDE improvements/inclusions ?

---

### Post by descendent87 on 2009-07-11
Tried installing this, installed everything that people have said is needed but when I do
gnome-shell --replace
I get the following:
```
ben@desktop:~$ gnome-shell --replace
      JS LOG: Loading tweener.js
      JS LOG: Loading tweenlist.js
      JS LOG: Done loading tweenlist.js
      JS LOG: Done loading tweener.js
      JS LOG: Loading equations.js
      JS LOG: Done loading equations.js

(mutter:3961): Clutter-CRITICAL **: clutter_id_pool_lookup: assertion `id < id_pool->array->len' failed

(mutter:3961): Clutter-CRITICAL **: clutter_id_pool_lookup: assertion `id < id_pool->array->len' failed
ben@desktop:~$ Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
```Any ideas?

---

### Post by 23meg on 2009-07-11
> **Regenweald said:**
> This turned from a Gran Canaria thread to another shell thread :) Any actual news on Gnome/KDE improvements/inclusions ?

Keep an eye on [Planet GNOME]("http://planet.gnome.org") and [Planet KDE]("http://planetkde.org/").

---

### Post by wayne_cat on 2009-07-11
> **Regenweald said:**
> This turned from a Gran Canaria thread to another shell thread :) Any actual news on Gnome/KDE improvements/inclusions ?

The last thing that I found was:

[http://dot.kde.org/2009/07/07/day-2-gran-canaria-desktop-summit](http://dot.kde.org/2009/07/07/day-2-gran-canaria-desktop-summit)

3 days old ... 

Gran Canaria Desktop Summit = secret society ???

---

### Post by Regenweald on 2009-07-11
> **23meg said:**
> Keep an eye on [Planet GNOME]("http://planet.gnome.org") and [Planet KDE]("http://planetkde.org/").

Thanks, I'll head over there :)

> **wayne_cat said:**
> The last thing that I found was:

[http://dot.kde.org/2009/07/07/day-2-gran-canaria-desktop-summit](http://dot.kde.org/2009/07/07/day-2-gran-canaria-desktop-summit)

3 days old ... 

Gran Canaria Desktop Summit = secret society ???

My same thoughts, I kept going to the main site but found nothing really. Other than the nokia OS switching to full QT only for development(which does not affect me anyway) I know nothing new. Guess I'll head over to the planets...

---

### Post by 23meg on 2009-07-11
> **Regenweald said:**
> Guess I'll head over to the planets...

The planets have been flooded with GCDS impressions and reports for the last week or so. 

Matt Zimmermann (Ubuntu Technical Board member and CTO) also posted his own:

[http://mdzlog.alcor.net/2009/07/09/gran-canaria-desktop-summit-2009/](http://mdzlog.alcor.net/2009/07/09/gran-canaria-desktop-summit-2009/)

---

### Post by wayne_cat on 2009-07-11
> **23meg said:**
> The planets have been flooded with GCDS impressions and reports for the last week or so. 

Matt Zimmermann (Ubuntu Technical Board member and CTO) also posted his own:

[http://mdzlog.alcor.net/2009/07/09/gran-canaria-desktop-summit-2009/](http://mdzlog.alcor.net/2009/07/09/gran-canaria-desktop-summit-2009/)

I still haven't found "the flood" on PlanetGnome ... looks a little bit like a Stallman fanblog ;)

But your link to Matt's blog ... much better ... thanks.

Well .. I think the videos will shed some light on it.

---

### Post by ronacc on 2009-07-11
a quick look at the "planets" reveals an interesting comtrast . At KDE most of the posts concern some aspect of KDE at Gnome most seem to be diatribes against RMS and making a call for "political correctness" .

---

### Post by 23meg on 2009-07-12
> **wayne_cat said:**
> I still haven't found "the flood" on PlanetGnome ... looks a little bit like a Stallman fanblog ;)

You'll need to go back a few days. Try doing a search for "gcds" or "summit" (upper right corner).

---

### Post by gnomeuser on 2009-07-15
> **zekopeko said:**
> i can't wait to see what Cubano is all about. are there any screenshots floating around?

Aaron posted some pictures, here:
[http://abock.org/2009/07/14/exciting-updates-on-the-road-to-banshee-2-0](http://abock.org/2009/07/14/exciting-updates-on-the-road-to-banshee-2-0)

But to do a vivid desktop 2.0 application justice then you really have to try it out in all it's smoothness. However a release along with it's dependencies isn't expected till sometime in august - especially problematic is the need for git versions of banshee, clutter and clutter-sharp.

---

### Post by gnomeuser on 2009-07-15
I am royally unimpressed by gnome-shell having now made it work. 

Firstly and worst, it is a solution looking for a problem. This is apparent from using it as well as reading it's design document. In the latter it starts out by assuming that workspaces are powerful but underused, with nothing substantial to back up this conclusion. The one data provided merely states how many workspaces the various distros ship with enabled. The problem with this abnormally stupidity is naturally that it assumes users actually use at least that many. The second assumption is that power users just more workspaces and that no downsides exists in working with workspaces.

However, that is not the case, most users regardless of skill in my experience, observing their workflow use only one workspace. The main problem is that people tend to lose entire windows filled with work using workspaces.

The only place workspaces actually do work is on cellphones where the screen space in constrained and every workspace is clearly defined as having a specific use. Additionally in this work situation you are rarely sitting for hours typing documents which is not the case with your average desktop. Gnome-shell doesn't provide nor is it designed with specific use case workspaces in mind instead providing generic workspaces.

Secondly it has these floating buttons on the side that take up a lot of screen space and it doesn't appear one can disable them. The activity menu isn't populated with your applications in anyway. 

It's also ugly but that is at least a problem that can go away.

Even the animations which are supposed to be a slight and subtle enhancement seem over eager especially in the cases where you add new workspaces.

It even feels slow and cumbersome rather than light and cheerful, something that really shouldn't be the case on any modern hardware. Everything seems to lag and stutter.

I doubt gnome-shell will actually solve any real problem simply based on it's false assumptions and lack of user testing during it's design phase. 

A much nicer approach to specific use case solving interface design and rethinking can definitely be found in the Moblin camp. It's speedy, it solves real problems. I am pretty sure it could be adapted to scale to a general desktop, with custom zones added for wordprocessing. The latter being probably moblins biggest weird wart is that they ship an offline mail client when more and more people switch to online versions such as gmail, but expect you to use online wordprocessors which fail horribly on the fairly meager hardware of a netbook and also require pretty much constant webaccess. Something like a crafted abiword like that found in OLPCs default distro with cloud integration would be much nicer.

---

### Post by Merk42 on 2009-07-15
> **gnomeuser said:**
> STUFF

I agree, did you post any of this on [the mailing list](http://mail.gnome.org/mailman/listinfo/gnome-shell-list)? Also, would it maybe be more relevant for you to repost this [here](http://ubuntuforums.org/showthread.php?t=1150357&page=24)

If GNOME Shell keeps going in this direction, are you going to have to change your username? :p

---

### Post by ronacc on 2009-07-15
@ gnomeuser re royally unimpressed , I agree completely .

---

### Post by wayne_cat on 2009-07-15
> **gnomeuser said:**
> facts about gnome shell ... in line with reality

Take a look at Gnome-Shell after reading the "GNOME Human Interface Guidelines".  
Gnome-Shell is an offense ... utterly absurd.

Somebody has to stop them before it's to late.

---

### Post by zekopeko on 2009-07-15
> **gnomeuser said:**
> Aaron posted some pictures, here:
[http://abock.org/2009/07/14/exciting-updates-on-the-road-to-banshee-2-0](http://abock.org/2009/07/14/exciting-updates-on-the-road-to-banshee-2-0)

But to do a vivid desktop 2.0 application justice then you really have to try it out in all it's smoothness. However a release along with it's dependencies isn't expected till sometime in august - especially problematic is the need for git versions of banshee, clutter and clutter-sharp.

i tried it. it's not that hard to compile all the dependencies. how ever i did have a problem finding the exact url for clutter-sharp.
it looks really nice but needs work.
after a poster pointed to cubano being linux's zune software 3.1 i installed it.
and was completely blown off! the user experience is amazing. navigation simple yet powerful. and everything is so smooth and pleasing to the eye. simple animations that really bring the app to life. 
and people bitch that MS can't do anything that could out-apple Apple.

i hope cubano out-zunes it's inspiration :).

---

### Post by zekopeko on 2009-07-15
> **gnomeuser said:**
> <snip>

it's sad how everybody is excited about this. it's like a mass delusion.

---

### Post by Merk42 on 2009-07-15
> **zekopeko said:**
> it's sad how everybody is excited about this. it's like a mass delusion.

So if I start a thread in the mailing list will others at least join me?

---

### Post by zekopeko on 2009-07-15
> **Merk42 said:**
> So if I start a thread in the mailing list will others at least join me?

well let's flesh-out an idea first. criticizing without a alternative isn't going to sway people. especially since (and i'm guessing) non of us have an coding knowledge.
start a new thread and a wiki page on ubuntu.com and we can start from there.

---

### Post by gnomeuser on 2009-07-15
> **Merk42 said:**
> I agree, did you post any of this on [the mailing list](http://mail.gnome.org/mailman/listinfo/gnome-shell-list)? Also, would it maybe be more relevant for you to repost this [here](http://ubuntuforums.org/showthread.php?t=1150357&page=24)


No, I believe they are already so far down this idiotic path that it is to late to stop them so why bother. I will look to Moblin and Novell (who I think are secretly planning something around Moonlight to wow us all, it's a perfect tool for them to quickly bring to fruition some very cool stuff) to bring forth the GNOME platform instead.

> 
If GNOME Shell keeps going in this direction, are you going to have to change your username? :p

While the gnome-shell really doesn't appeal to me, the rest of the GNOME platform and GNOME 3 as such do appeal to me - with the exception of writing everything in Javascript which seems idiotic, unsafe and just all around a bad idea. I understand wanting to get away from C but to go to a language where everyone purposefully ignores the standard with known security problems in the design.. does not seem like the wisest decision ever to me at least.

I suspect I can remain gnomeuser for a while, though using my real name is my preference these days, sadly David Nielsen being a common name, it is taken most places.

---

### Post by Merk42 on 2009-07-15
> **zekopeko said:**
> well let's flesh-out an idea first. criticizing without a alternative isn't going to sway people. especially since (and i'm guessing) non of us have an coding knowledge.
start a new thread and a wiki page on ubuntu.com and we can start from there.

Is making a wiki page for changes to GNOME-Shell relevant on Ubuntu's wiki?

> **gnomeuser said:**
> No, I believe they are already so far down this idiotic path that it is to late to stop them so why bother.
Ouch.

> **gnomeuser said:**
> I will look to Moblin and Novell (who I think are secretly planning something around Moonlight to wow us all, it's a perfect tool for them to quickly bring to fruition some very cool stuff) to bring forth the GNOME platform instead.

How/Why would non-GNOME devs bring for the GNOME platform?

GNOME or KDE, it's all about the environment Google is making from Chrome ;)

---

### Post by wayne_cat on 2009-07-15
this "thing around moonlight" ... is this just a thought/rumor?

Gtk+ 3  will have a lot of interesting capability characteristics:

[http://mail.gnome.org/archives/gtk-devel-list/2009-April/msg00048.html](http://mail.gnome.org/archives/gtk-devel-list/2009-April/msg00048.html)

Isn't the "good old gnome design" with eye candy and improvements from the Gtk+ version enough?

---

### Post by Regenweald on 2009-07-15
I find it to be a bit funny actually, of all the issues that the user community clamors for, I never thought that workspaces would be overhauled ;)
seriously ? who goes past 4 ? and if so, are these users in the majority ?

aside from that, the libraries ARE being cleaned up and as long as the workspaces don't get in my way and everything does not have to be so large and 'buttoney' i think it will work out. The javacript thing threw me though, what could have precipitated that choice ?

---

### Post by Merk42 on 2009-07-15
> **wayne_cat said:**
> Isn't the "good old gnome design" with eye candy and improvements from the Gtk+ version enough?

Possibly, but with the introduction of **third panel** and an emphasis on multiple desktops that **arguably very few people use**, so far GNOME-Shell isn't the "good old gnome design".

---

### Post by Reiger on 2009-07-15
> **Regenweald said:**
> I find it to be a bit funny actually, of all the issues that the user community clamors for, I never thought that workspaces would be overhauled ;)
seriously ? who goes past 4 ? and if so, are these users in the majority ?

aside from that, the libraries ARE being cleaned up and as long as the workspaces don't get in my way and everything does not have to be so large and 'buttoney' i think it will work out. The javacript thing threw me though, what could have precipitated that choice ?

Many workspaces make perfect sense for things like mobile phones were you need it simply because of the constraints of the device. But you'll also find that on those devices the workspaces are not so much "work spaces" rather than "OS navigation", a very short and direct means to an end (taking a picture, playing an mp3, calling someone else...); whereas with Gnome Shell the workspaces seem to have become a point and purpose in and of themselves, if not an &#8220;activity&#8221; in their vocabulary.

Which is where I leave: multiple workspaces are all fine and dandy, but I want to get work done rather than "managing" how I will get work done. Basically put: if I have to put time and effort into planning how I will work with my desktop today, I might as well use a vanilla Fvwm setup: at least it still has the Debian menu.

---

### Post by gnomeuser on 2009-07-15
> **Merk42 said:**
> 
How/Why would non-GNOME devs bring for the GNOME platform?


Underneath something like Moblin is very much GNOME (the platform), they put a different spin on the actual "desktop shell" but the very same libraries are in use. Just like Nokias Hildon platform is also GNOME underneath, every library is basically right out of the GNOME platfrom.. even now when they switched to QT as their toolkit (and I still have no idea why they did that, but so be it). 

GNOME is more than just what you and I use every day and we shouldn't forget that. Many people and companies take these tools in new and interesting directions, scale them down to devices where a regular GNOME desktop would fail miserable or use part of the libraries to facilitate parts of supercomputing.

I am very hopeful with regards to GNOME as a platform, I see many interesting things going on with the underlying tools and I see people using it for interesting deployments. I think that if someone goes and does something better using our platform then we should be happy. I would at least be considerably more depressed if there was a decided move to tank the platform than just this one part of the desktop.

---

### Post by Reiger on 2009-07-15
> **gnomeuser said:**
> While the gnome-shell really doesn't appeal to me, the rest of the GNOME platform and GNOME 3 as such do appeal to me - with the exception of writing everything in Javascript which seems idiotic, unsafe and just all around a bad idea. I understand wanting to get away from C but to go to a language where everyone purposefully ignores the standard with known security problems in the design.. does not seem like the wisest decision ever to me at least.

Well not so long ago there was talk of "object hardening" becoming part of the standard: basically you would at some point be able to tell JavaScript that this object was final an no more prototype-extensions could be done about it. That's not much good "right now" but there are fairly well-understood ways of avoiding one JavaScript interfering with another, the easiest way being (obviously) an URI based "permission scheme": all files are by necessity a different URI (can't have two files with the exact same location being different from each other).

---

### Post by zekopeko on 2009-07-15
> **gnomeuser said:**
> While the gnome-shell really doesn't appeal to me, the rest of the GNOME platform and GNOME 3 as such do appeal to me - with the exception of writing everything in Javascript which seems idiotic, unsafe and just all around a bad idea. I understand wanting to get away from C but to go to a language where everyone purposefully ignores the standard with known security problems in the design.. does not seem like the wisest decision ever to me at least.

I suspect I can remain gnomeuser for a while, though using my real name is my preference these days, sadly David Nielsen being a common name, it is taken most places.

I also don't know why you would want to write everything in javascript. don't they have that fancy new Vala language or good old python or even mono/moonlight?

---

### Post by gnomeuser on 2009-07-15
> **wayne_cat said:**
> this "thing around moonlight" ... is this just a thought/rumor?


Well Miguel has spoken at great length on the Herding Code podcast (in his 2 parter interview - which is very recommended listening btw.) about how Moonlight would be a good replacement eventually for GTK+ for doing desktop applications that also incorporates collaboration and reaches out into the cloud. He at that time had a wild idea to do something big like a collaborative wordprocessor using Moonlight or something similar in scope.

I also think that to really show off what Moonlight can do for Linux they would be inclined to do a fairly decent sized application with lots of bling, possibly something that blends weblication space and desktop space. I am thinking this will have it's foundation on what is quickly becoming the Banshee application platform. It's really growing to become the crown in Novells desktop set of jewels. With Banshee now handling media in picture, movie and music form it is becoming an attractive platform to build something very interesting on top of. Maybe a bigger more professionally minded F-spot type application, maybe something like iMovie.. who knows. At the very least Aaron is personally interested in doing Cubano in Moonlight at some point since it makes a great deal of sense for that job but I think we will see them build on what they have done in some way besides this.

It is all speculation but is built on seeing what they have done and what seems to excite the people who work with this every day. Moonlight is definitely going to be more that just a browser plugin, it is useful for the desktop and Novell are definitely aware of that. I think they will show us that by at least building one really impressive application to get people a hands on thing they can see and play with to really understand this whole thing. Remember that when Ximian first announced Mono back many years ago they didn't have applications to show this off, it wasn't till Tomboy got built and Banshee came along that people really saw what Mono could do for us and got as passionate about it as the hackers who did the work were. That ecosystem of excitement needs to be built around Moonlight as well, I think there is a general understanding of that lesson from Mono and it needs to happen early.

That is why I think shortly after the release of Moonlight 2 we will see Novell release the initial version of something good. It is not going to be a replacement for GNOME or Moblin, they are invested in both but it will probably augment both platforms.

I believe in exciting times ahead.

*edit*

I should mention that having a big user also serves as very good dogfooding for Moonlight development, so it wouldn't be surprising if they were working on it now. Having something that actually uses very extensive bits of that codebase really exercises it and shows your the slow paths and other weak points early on.

---

### Post by Regenweald on 2009-07-15
> **Reiger said:**
> Many workspaces make perfect sense for things like mobile phones were you need it simply because of the constraints of the device. But you'll also find that on those devices the workspaces are not so much "work spaces" rather than "OS navigation", a very short and direct means to an end (taking a picture, playing an mp3, calling someone else...); whereas with Gnome Shell the workspaces seem to have become a point and purpose in and of themselves, if not an “activity” in their vocabulary.

Which is where I leave: multiple workspaces are all fine and dandy, but I want to get work done rather than "managing" how I will get work done. Basically put: if I have to put time and effort into planning how I will work with my desktop today, I might as well use a vanilla Fvwm setup: at least it still has the Debian menu.

Have to agree. But Gnome is ploughing ahead and I'll support them till i use 3.0 final and see what's what :) I still think that the release team gave in to stupid 'community' criticism and the constant KDE comparisons and took a blind leap. The Gnome platform offers amazing functionality ease of use and **STABILITY**. I sincerely hope that 3.0 does not reverse this.

---

### Post by wayne_cat on 2009-07-15
I'm quite sure you are not talking about this:

[http://herdingcode.com/?p=114](http://herdingcode.com/?p=114)

After listening to this I started to think that Miguel is dangerous. Not that kind of "stupid dangerous" like the unofficial 
Microsoft soldier Darl McBride (FUD) .... more like "No need to kill them ... we will have to absorb them". Paying for 
codecs and downloading things from from Microsoft ... is this the future off the typical Linux applications?

edit: related to this
[http://ubuntuforums.org/showpost.php?p=7621454&postcount=70](http://ubuntuforums.org/showpost.php?p=7621454&postcount=70)

---

### Post by gnomeuser on 2009-07-15
> **wayne_cat said:**
> I'm quite sure you are not talking about this:

[http://herdingcode.com/?p=114](http://herdingcode.com/?p=114)

After listening to this I started to think that Miguel is dangerous. Not that kind of "stupid dangerous" like the unofficial 
Microsoft soldier Darl McBride (FUD) .... more like "No need to kill them ... we will have to absorb them". Paying for 
codecs and downloading things from from Microsoft ... is this the future off the typical Linux applications?

edit: related to this
[http://ubuntuforums.org/showpost.php?p=7621454&postcount=70](http://ubuntuforums.org/showpost.php?p=7621454&postcount=70)

As is explained in the interview, this is advise for users who have no other legal choice. Regardless, as a Ubuntu user you already get Moonlight compiled against ffmpeg (rumors are abound of a port to gstreamer which would be easier to support in a distro especially with packagekit helping). Like it or not the multimedia field is a minefield and Novell have to find a solution that gives users a 100% legal way to get 100% compatible support. They in addition also give the option to compile against ffmpeg, however should that be illegal in your country of residence or due to other reasons Microsoft offered to pay for your media experience. If you are afraid that this code might contain bad stuff, then all you have to do is trust the Novell programmers, who work with the source under NDA. It is not like you are being forced to run a binary straight from the dark labs over in Redmond. You have that option, you also have the option to use 100% free software.

You must understand that Miguel can't stand up and tell people that the strategy he (and by extension Novell) recommends customers is to violate the law, that would.. you know make him a criminal, and very likely get him fired as well as put in jail. He thus recommends a perfectly legal solution which is entirely gratis for you the user, Microsoft encures the cost on your behalf. (or think of it as a Microsoft hater, even if you delete it without ever using it, every time you hit download for that media pack.. you cost Microsoft money, granted the money goes to the MPEG-LA whose policies, in part, are causing the media problem in the first place. so not recommended for the thinking person).

Additionally starting with Silverlight 3 there is support for additional media formats provided they are delivered in managed code. So in Moonlight you will get 100% legal free software support for Vorbis and Dirac (I believe those two are done or nearly done now but it has been a while since I checked). This code should already be in Moonlight and should ship with Moonlight 2.

I see no problem with Miguels advice, it's the only legal way to get support for those media formats for a great number of people. I would suggest this battle be fought with the media codec people not with Miguel. They are the ones causing the root problem. The salvation might very well be that the BBC submitted Dirac (abide a subset for Dirac) as a contender to be VC-2. Making the next generation defacto standard format one we can ship legally. The future is looking brighter.. even the mp3 patents are running out soonish and we have people awakening to the benefits of open standards. This problem will be solved, for now though we need to live in the real world and work on making the dream reality in the future.

---

### Post by 23meg on 2009-07-15
> **Merk42 said:**
> Is making a wiki page for changes to GNOME-Shell relevant on Ubuntu's wiki?

It wouldn't hurt, but there's a better place (that I had pointed to a few times before); from [http://live.gnome.org/GnomeShell](http://live.gnome.org/GnomeShell):

> **Contributing User Observations**: Writeups about users interacting with their desktop today that allow us to learn how they switch between tasks and generally interact with their desktop are [here]("http://live.gnome.org/GnomeShell/UserObservationData"). You can add new write-ups based on your friends' or you own experience. General problems with desktop usage are summarized [here]("http://live.gnome.org/GnomeShell/NotesAboutDesktopUsage") and information about the default desktop set up of different distributions plus more ideas about user research is [here]("http://live.gnome.org/GnomeShell/UserResearch"). 

---

### Post by wayne_cat on 2009-07-15
> **gnomeuser said:**
> As is explained in the interview, this is advise for users who have no other legal choice.

OK .. this is something I forgot  ... a lot of people (I hope) will use Gnome (or KDE) at work.
A company can not say "we drop Windows .. Gnome/KDE and is our new enterprise desktop" without legal solutions for the things they need. Mono has the chance to be what Java never was/is ... yet another way to create applications. 

I stand corrected.

My ranting was about "I don't see a future for Gnome-Shell ... there must be something else" and I misunderstood your comment as a hint that a Mono based application could be the basic graphical user interface for Gnome 3. I don't mind that there are Mono applications in Ubuntu. If the influence from Microsoft (and people like Miguel) is getting to strong ... apt-get remove is my friend.


The relationship between Novell and Microsoft is legal and profitable for both sides. I just don't want to see their "Visions" as the visual Gnome basement. First I was interested in Gnome-Shell ... and I expected to see "the evidence that Gnome-Shell can be the new Gnome face" at the Gran Canaria Desktop Summit. Maybe the videos will give me some hope that Gnome 3 will still be my personal desktop environment. 

My harsh words about Miguel ... they where never meant to offend your idea that Mono is not an evel / bad thing and that it can be an option for creative programmers. I beg your pardon.

The videos from the Summit will tell us a little bit about the visions that will come true. Still haven't seen them ... still not available ... so I still think that Gnome-Shell is the wrong way to success. And if I'm wrong ... KDE after 6 years Gnome will not kill me.

---

### Post by zekopeko on 2009-07-15
@wayne_cat

well the point of moonlight being a user interface library is that it's easy to create rich applications with less code. so we could finally get some sweet Mac OSX-style desktop app bling. and with the (finally) stronger push with usability/interface studies going on FLOSS developers can finally start to create applications that look as slick as anything Apple can produce.

---

### Post by wayne_cat on 2009-07-15
Is Gtk+ 3.0 so far behind. :(

I saw a link to a blog about the new Gtk bling bling features here on Ubuntuforums. And I asked myself ... who will steal these ideas first ... Microsoft or Apple.

---

### Post by Regenweald on 2009-07-15
> **wayne_cat said:**
> Is Gtk+ 3.0 so far behind. :(

I saw a link to a blog about the new Gtk bling bling features here on Ubuntuforums. And I asked myself ... who will steal these ideas first ... Microsoft or Apple.

It's all about who has the programming power to implement fastest. If you lay out a bunch of great free ideas, someone is bound to agree.

On another note, Banshee is beginning to look like it will mutate into a DE. 

As per 23Meg's post, i'm going to install the shell and start shaping this 3.0 thingamerbob. Time to help out.

---

### Post by zekopeko on 2009-07-15
> **wayne_cat said:**
> Is Gtk+ 3.0 so far behind. :(

I saw a link to a blog about the new Gtk bling bling features here on Ubuntuforums. And I asked myself ... who will steal these ideas first ... Microsoft or Apple.

well considering how much Linux "steals" from Microsoft and Apple...
I think that people still have that bad aftertaste when MS is concerned although they are changing. You have to decouple your perception of MS as an evil company. 

There are many people working there that are starting to see how good open source is.
And like always it started from the bottom. the management is still mostly driven by stock prices (therefore being "evil") and such but as said they are changing.

consider that todays programmer is something like 300-600% more efficient then 10 years ago. and that is mostly thanks to open source software and better tools.

and apple is really at the forefront of UI design. 
They are mostly closed source when there UI is concerned but they build it on strong opensource foundations. they are one of the strongest supporters of FLOSS along side Google,Red Hat, Novell etc.

So sharing ideas is a good thing especially if there is code behind said idea.
As said Silverlight/Moonlight could be a good path to take for Gnome bling. But i'll wait and see what comes of it.

---

### Post by Merk42 on 2009-07-15
> **23meg said:**
> It wouldn't hurt, but there's a better place (that I had pointed to a few times before); from [http://live.gnome.org/GnomeShell](http://live.gnome.org/GnomeShell):

I've read that stuff before, had to in order to build the shell in the first place.  None of those pages seem to be about the shell so far. Like "Oh hey here's what it's like so far, what do you think?" sort of thing.

---

### Post by seeker5528 on 2009-07-15
> **gnomeuser said:**
> I am royally unimpressed by gnome-shell having now made it work. 

Firstly and worst, it is a solution looking for a problem.

Seems to me like the discussions used to start with some crap about the panel and the tray being broken, which I don't doubt. Then instead of tackling the shark head on they jumped it. 

From: [http://linux.com/news/software/applications/20788-gnome-shell-plans-outlined](http://linux.com/news/software/applications/20788-gnome-shell-plans-outlined)

> "We thought the existing desktop is a little too freeform," Taylor explains. "The GNOME panel is extraordinarily flexible and you can move things around anyway you want it--which sounds very good, but means that the panel doesn't really have any idea of what the things on the panel are. If you change screen resolutions, it can get confused."

Another guiding critique was to make navigation less ambiguous. "Right now, with GNOME, it can be confusing to find what you're doing if you have to open an application. The first question is what desktop it is on, and, if you don't have it open, you have to go to the menu to get it started. So we wanted to have one place to go to do everything.

So I guess with Gnome Shell, what you see is what you get?

That other part is not very convicing/inspiring either.

Swithching through all my desktops to find an open app takes very little time. 

If the 'Alt+Tab' invoked task switcher would show all the running tasks and lets you switch to the desired task, problem solved. 

And the task applet in the panel already gives you an option to switch between showing all tasks or only tasks from the current desktop, uhm, problem solved for quite some time it seems.

I suppose next we are going to start hearing stories about how it confuses people when they accidentally hit the scroll lock key twice then either a number 1, 2,(, 3, 4) or the up or down arrow key and their KVM switches to a different computer and plans to fix that by ignoring number and arrow keys for 8 seconds after hitting the scroll lock twice. :-s :p

Later, Seeker

---

### Post by zekopeko on 2009-07-15
> **Regenweald said:**
> It's all about who has the programming power to implement fastest. If you lay out a bunch of great free ideas, someone is bound to agree.

On another note, Banshee is beginning to look like it will mutate into a DE. 

As per 23Meg's post, i'm going to install the shell and start shaping this 3.0 thingamerbob. Time to help out.

i personally think that Banshee becoming a platform is a great addition to the Gnome framework. It's going to be easier for developers to focus on interface design then under the hood stuff.
Some really snazzy stuff could come from it.
Not to mention that it will show one of the great strengths of FLOSS.

---

### Post by zekopeko on 2009-07-15
> **seeker5528 said:**
> So I guess with Gnome Shell, what you see is what you get?

That other part is not very convicing/inspiring either.

Swithching through all my desktops to find an open app takes very little time. 

If the 'Alt+Tab' invoked task switcher would show all the running tasks and lets you switch to the desired task, problem solved. 

And the task applet in the panel already gives you an option to switch between showing all tasks or only tasks from the current desktop, uhm, problem solved for quite some time it seems.

I suppose next we are going to start hearing stories about how it confuses people when they accidentally hit the scroll lock key twice then either a number 1, 2,(, 3, 4) or the up or down arrow key and their KVM switches to a different computer and plans to fix that by ignoring number and arrow keys for 8 seconds after hitting the scroll lock twice. :-s :p

Later, Seeker

it's amazing how they took one simple element of the design and instead of fixing what's wrong (the applet placement) they created this whole new desktop shell. i haven't thought about gnome-shell much until reading the post from gnomeuser in this thread. and i have to agree with his perspective.

would it kill them to simply create/re-use gnome-do-like docky as the bottom panel and integrate it with mutter (metacity 3) so that we can get windows7-like task switching? and fix the panel.

---

### Post by wayne_cat on 2009-07-15
Well .. maybe I'm not the only person in this forum that understands german. Here is a link
to a standard.at report about the Gnome-Shell at the Gran Canaria Desktop Summit:

[http://derstandard.at/fs/1246541865421/Neue-Details-GNOME-Shell-will-den-Desktop-grundlegend-umbauen](http://derstandard.at/fs/1246541865421/Neue-Details-GNOME-Shell-will-den-Desktop-grundlegend-umbauen)

They have mentioned a paper from Jon McCann and  Jeremy Perry (redhat) ... but I was 
not able to find it ... the google results are all about Jon McCann .... a musican

---

### Post by 23meg on 2009-07-15
> **wayne_cat said:**
> 
They have mentioned a paper from Jon McCann and  Jeremy Perry (redhat) ... but I was 
not able to find it ... the google results are all about Jon McCann .... a musican

[http://www.gnome.org/~mccann/shell/design/GNOME_Shell-20090705.pdf](http://www.gnome.org/~mccann/shell/design/GNOME_Shell-20090705.pdf)

---

### Post by wayne_cat on 2009-07-15
> **23meg said:**
> [http://www.gnome.org/~mccann/shell/design/GNOME_Shell-20090705.pdf]("http://www.gnome.org/%7Emccann/shell/design/GNOME_Shell-20090705.pdf")

thank you very much ... and some mockups here:

[http://www.gnome.org/~mccann/shell/mockups/](http://www.gnome.org/~mccann/shell/mockups/)

---

### Post by Regenweald on 2009-07-15
> **wayne_cat said:**
> thank you very much ... and some mockups here:

[http://www.gnome.org/~mccann/shell/mockups/](http://www.gnome.org/~mccann/shell/mockups/)

I look at those mockups and see nothing new. Feels like the freedom of customization was finally becoming difficult for Gnome to maintain and move forward at the same time so they trimmed some fat, Locked some stuff in place and 3.0 was born. I really have to wait to see what new technology is included in the Shell, zeitgeist etc. The Birth of this new Activities terminology is quite un-necessary.

---

### Post by Merk42 on 2009-07-15
> **wayne_cat said:**
> thank you very much ... and some mockups here:

[http://www.gnome.org/~mccann/shell/mockups/](http://www.gnome.org/~mccann/shell/mockups/)

I've noticed any mockups I've seen are missing the sidebar...

---

### Post by zekopeko on 2009-07-15
> **Merk42 said:**
> I've noticed any mockups I've seen are missing the sidebar...

the sidebar is an "experiment" that probably gonna be shoved in.

---

### Post by Merk42 on 2009-07-15
> **zekopeko said:**
> the sidebar is an "experiment" that probably gonna be shoved in.

:) Hey this new shell is pretty cool so far
:P Check this out you can put stuff like a sidebar in it
:) Um, shouldn't you finish the changes to the bottom panel first?
:P Oh we will, we're just trying out a sidebar...
:) Well why give the user a third place, shouldn't you be keeping things simple?
:P We're just experimenting, want to see what users would think of a sidebar
:) Didn't Microsoft try a sidebar with Vista, which has been dropped for Windows 7?
:evil: A SIDEBAR IS A GOOD IDEA

---

### Post by wayne_cat on 2009-07-15
My suggestion ... don't have a look at Gnome-Shell until at least 10% on the visions from the 
pdf came true. They are talking about the "ideal world" and Gnome-Shell is at the moment:
[I]
from: GNOME Shell - A design for a personal integrated digital work environment[/I]

```
"Quality isn't job one. Being totally fu*king amazing is job one."
```I'm one of these persons that switches to the "Windows XP classic view menu"  and I will not 
buy a glossy screen (everybody loves them???).

On the other hand ... I'm typing this on an Apple Macbook Pro ... Mac OS 10.5 is one of the 
boot options in efi-grub ... why .... because Apple knew hot to mix a really good OS (BSD) with 
a smooth/usable/eye candy surface.

Maybe people like William Jon McCann and Jeremy Perry are the Steve Jobs and Jonathan Ive 
of the open source UI world.

Anyway ... Ubuntu will be my main aperating system ... until someone adds a facebook and a
 twitter option to grub.

---

### Post by Merk42 on 2009-07-18
> **wayne_cat said:**
> I'm one of these persons that switches to the "Windows XP classic view menu"

You're not going to like Windows 7...




So I made a [wiki for GNOME Shell](https://wiki.ubuntu.com/gnomeshell), it's pretty basic and probably 'wrong' because I have never done a wiki before.  Please feel free to change it, I just personally felt it had to be made.  I'm not liking what GNOME Shell is doing, so hopefully Canonical will make slight modifications to it when it is in its future releases of Ubuntu.

---

### Post by Regenweald on 2009-08-17
How is the ppa doing ? is it up with the latest updates ? Installing from the ppa currently.

---

