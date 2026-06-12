---
title: "Gnome-terminal not running after upgrade from 21.10 to 22.04"
date: 2022-08-02
forum: Installation &amp; Upgrades
---

### Post by kilrah757 on 2022-08-02
I've updated a system from 21.10 to 22.04, and after that gnome-terminal won't run:

```
/usr/bin/gnome-terminal.real: error while loading shared libraries: libicuuc.so.67: cannot open shared object file: No such file or directory
```

Both libicu and gnome-terminal packages are the versions listed on packages.ubuntu.com for jammy

```
Listing... 
...
gnome-terminal-data/jammy,jammy,jammy,jammy,now 3.44.0-1ubuntu1 all [installed,automatic]
gnome-terminal/jammy,jammy,now 3.44.0-1ubuntu1 amd64 [installed]
...
libicu-dev/jammy,jammy,now 70.1-2 amd64 [installed,automatic]
libicu70/jammy,jammy,now 70.1-2 amd64 [installed,automatic]
libicu70/jammy,jammy,now 70.1-2 i386 [installed,automatic]
```

and there's no libicu67 package as expected... so why does it try to load an older version?

---

### Post by #&amp;thj^% on 2022-08-02
Show this please:
```
 cat /usr/bin/gnome-terminal
```

---

### Post by kilrah757 on 2022-08-02
Result attached, diff shows it to be the same as on a freshly installed system

[ATTACH]290799[/ATTACH]

---

### Post by #&amp;thj^% on 2022-08-02
i can confirm that here as well.
Will you show these as well:
```
**[COLOR="#FF0000"]python3 --version[/COLOR]**
Python 3.10.4
```
```

me@me-Standard-PC-Q35-ICH9-2009:~$ **[COLOR="#FF0000"]locale[/COLOR]**
LANG=en_US.UTF-8
LANGUAGE=
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
```
I've seen this in other forums upgrading to 22.04, and if your results look like mine I think it would now be safe to run:
```
dconf reset -f /org/gnome/terminal/legacy/profiles:/
```
NOTE:this will delete all of your gnome-terminal&#8217;s profiles and revert the default profile to its original settings.
I'm confused by " libicu67" this is a new finding I've not yet seen reported.
Example Mine:
```
apt-cache depends gnome-terminal
gnome-terminal
 |Depends: <default-dbus-session-bus>
    dbus-user-session:i386
    dbus-user-session
  Depends: <dbus-session-bus>
    dbus-user-session:i386
    dbus-user-session
    dbus-x11:i386
    dbus-x11
  Depends: gnome-terminal-data
  Depends: gnome-terminal-data
  Depends: gsettings-desktop-schemas
  Depends: python3
  Depends: python3-gi
  Depends: gir1.2-glib-2.0
 |Depends: dconf-gsettings-backend
  Depends: <gsettings-backend>
    dconf-gsettings-backend
  Depends: libc6
  Depends: libcairo2
  Depends: libdconf1
  Depends: libgcc-s1
  Depends: libglib2.0-0
  Depends: libgtk-3-0
  Depends: libpango-1.0-0
  Depends: libstdc++6
  Depends: libuuid1
  Depends: libvte-2.91-0
  Depends: libx11-6
  Recommends: gvfs
  Recommends: nautilus-extension-gnome-terminal
  Recommends: yelp

```
And just to be safe here, you have run these by now right?
```
sudo apt update && sudo apt full-upgrade
###and
sudo apt autoremove
```

---

### Post by kilrah757 on 2022-08-02
Python is 3.10.4

locale is

```

LANG=en_US.UTF-8LANGUAGE=
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC=fr_CH.UTF-8
LC_TIME=fr_CH.UTF-8
LC_COLLATE="en_US.UTF-8"
LC_MONETARY=fr_CH.UTF-8
LC_MESSAGES="en_US.UTF-8"
LC_PAPER=fr_CH.UTF-8
LC_NAME=fr_CH.UTF-8
LC_ADDRESS=fr_CH.UTF-8
LC_TELEPHONE=fr_CH.UTF-8
LC_MEASUREMENT=fr_CH.UTF-8
LC_IDENTIFICATION=fr_CH.UTF-8
LC_ALL=
```

Here's the deps:
```
gnome-terminal |Depends: <default-dbus-session-bus>
    dbus-user-session:i386
    dbus-user-session
  Depends: <dbus-session-bus>
    dbus-user-session:i386
    dbus-user-session
    dbus-x11:i386
    dbus-x11
  Depends: gnome-terminal-data
  Depends: gnome-terminal-data
  Depends: gsettings-desktop-schemas
  Depends: python3
  Depends: python3-gi
  Depends: gir1.2-glib-2.0
 |Depends: dconf-gsettings-backend
  Depends: <gsettings-backend>
    dconf-gsettings-backend
  Depends: libc6
  Depends: libcairo2
  Depends: libdconf1
  Depends: libgcc-s1
  Depends: libglib2.0-0
  Depends: libgtk-3-0
  Depends: libpango-1.0-0
  Depends: libstdc++6
  Depends: libuuid1
  Depends: libvte-2.91-0
  Depends: libx11-6
  Recommends: gvfs
  Recommends: nautilus-extension-gnome-terminal
  Recommends: yelp
```

> [COLOR=#000000]And just to be safe here, you have run these by now right?[/COLOR]
Yes, I do have a few packages held back by something though:

```
The following packages have been kept back:  mesa-va-drivers mesa-va-drivers:i386 python3-distupgrade
  ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk
```

I haven't run the dconf reset yet.

---

### Post by #&amp;thj^% on 2022-08-02
> **kilrah757 said:**
> Python is 3.10.4

locale is

```

LANG=en_US.UTF-8LANGUAGE=
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC=fr_CH.UTF-8
LC_TIME=fr_CH.UTF-8
LC_COLLATE="en_US.UTF-8"
LC_MONETARY=fr_CH.UTF-8
LC_MESSAGES="en_US.UTF-8"
LC_PAPER=fr_CH.UTF-8
LC_NAME=fr_CH.UTF-8
LC_ADDRESS=fr_CH.UTF-8
LC_TELEPHONE=fr_CH.UTF-8
LC_MEASUREMENT=fr_CH.UTF-8
LC_IDENTIFICATION=fr_CH.UTF-8
LC_ALL=
```

Here's the deps:
```
gnome-terminal |Depends: <default-dbus-session-bus>
    dbus-user-session:i386
    dbus-user-session
  Depends: <dbus-session-bus>
    dbus-user-session:i386
    dbus-user-session
    dbus-x11:i386
    dbus-x11
  Depends: gnome-terminal-data
  Depends: gnome-terminal-data
  Depends: gsettings-desktop-schemas
  Depends: python3
  Depends: python3-gi
  Depends: gir1.2-glib-2.0
 |Depends: dconf-gsettings-backend
  Depends: <gsettings-backend>
    dconf-gsettings-backend
  Depends: libc6
  Depends: libcairo2
  Depends: libdconf1
  Depends: libgcc-s1
  Depends: libglib2.0-0
  Depends: libgtk-3-0
  Depends: libpango-1.0-0
  Depends: libstdc++6
  Depends: libuuid1
  Depends: libvte-2.91-0
  Depends: libx11-6
  Recommends: gvfs
  Recommends: nautilus-extension-gnome-terminal
  Recommends: yelp
```


Yes, I do have a few packages held back by something though:

```
The following packages have been kept back:  mesa-va-drivers mesa-va-drivers:i386 python3-distupgrade
  ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk
```

I haven't run the dconf reset yet.

Your locale is interesting, but not a show stopper:
as for the held packages try:
```
sudo apt install mesa-va-drivers mesa-va-drivers:i386 python3-distupgrade
  ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk
```
Just to confirm it's safe to install the held packages:
```
 apt policy mesa-va-drivers mesa-va-drivers:i386 python3-distupgrade
  ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk
mesa-va-drivers:
  Installed: 22.0.5-0ubuntu0.1
  Candidate: 22.0.5-0ubuntu0.1
  Version table:
 *** 22.0.5-0ubuntu0.1 500 (phased 10%)
        500 http://archive.ubuntu.com/ubuntu jammy-updates/universe amd64 Packages
        100 /var/lib/dpkg/status
     22.0.1-1ubuntu2 500
        500 http://archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
mesa-va-drivers:i386:
  Installed: (none)
  Candidate: 22.0.5-0ubuntu0.1
  Version table:
     22.0.5-0ubuntu0.1 500 (phased 10%)
        500 http://archive.ubuntu.com/ubuntu jammy-updates/universe i386 Packages
     22.0.1-1ubuntu2 500
        500 http://archive.ubuntu.com/ubuntu jammy/universe i386 Packages
python3-distupgrade:
  Installed: 1:22.04.12
  Candidate: 1:22.04.12
  Version table:
 *** 1:22.04.12 500 (phased 0%)
        500 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu jammy-updates/main i386 Packages
        100 /var/lib/dpkg/status
     1:22.04.10 500
        500 http://archive.ubuntu.com/ubuntu jammy/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu jammy/main i386 Packages
ubuntu-release-upgrader-core: command not found
```
Some of it is held by phased updates IE:
```
apt policy ubuntu-release-upgrader-core
ubuntu-release-upgrader-core:
  Installed: 1:22.04.12
  Candidate: 1:22.04.12
  Version table:
[COLOR="#FF0000"] *** 1:22.04.12 500 (phased 0%)[/COLOR]
        500 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu jammy-updates/main i386 Packages
        100 /var/lib/dpkg/status
     1:22.04.10 500
        500 http://archive.ubuntu.com/ubuntu jammy/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu jammy/main i386 Packages

```
You should be safe to run "dconf reset"

---

### Post by kilrah757 on 2022-08-02
Could update the held back packages. 
The dconf reset however seemingly didn't help, still looking for version 67.

---

### Post by #&amp;thj^% on 2022-08-02
Can you post the whole process from running this:
```
sudo apt install --reinstall gnome-terminal
```
I need to see why " libicu67" has a strangle hold on it.

---

### Post by kilrah757 on 2022-08-02
> **1fallen said:**
> Can you post the whole process from running this:
```
sudo apt install --reinstall gnome-terminal
```
I need to see why " libicu67" has a strangle hold on it.

[COLOR=#000000]Code:
kilrah@kilrah-win-ubuntu:~$ sudo apt install --reinstall -y gnome-terminal >reinst.txt 2>&1

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.


Reading package lists...
Building dependency tree...
Reading state information...
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 1 not upgraded.
Need to get 191 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 [http://archive.ubuntu.csg.uzh.ch/ubuntu](http://archive.ubuntu.csg.uzh.ch/ubuntu) jammy/main amd64 gnome-terminal amd64 3.44.0-1ubuntu1 [191 kB]
Fetched 191 kB in 0s (2’869 kB/s)
(Reading database ... 
(Reading database ... 5%
[snip]
(Reading database ... 100%
(Reading database ... 402796 files and directories currently installed.)
Preparing to unpack .../gnome-terminal_3.44.0-1ubuntu1_amd64.deb ...
Unpacking gnome-terminal (3.44.0-1ubuntu1) over (3.44.0-1ubuntu1) ...
Setting up gnome-terminal (3.44.0-1ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu3) ...
Processing triggers for libglib2.0-0:amd64 (2.72.1-1) ...
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for mailcap (3.70+nmu1ubuntu1) ...
Processing triggers for desktop-file-utils (0.26-1ubuntu3) ...[/COLOR]
[COLOR=#000000]No change.[/COLOR]

[COLOR=#000000]I tried opening the "Language support" app, it also doesn't open, after finding it's called "gnome-language-selector" and running it from terminal I get:

```
[/COLOR]Gtk-Message: 20:20:05.298: Failed to load module "xapp-gtk3-module"

** (gnome-language-selector:10095): WARNING **: 20:20:05.345: Failed to load shared library 'libvte-2.91.so.0' referenced by the typelib: libicuuc.so.67: cannot open shared object file: No such file or directory
/usr/lib/python3/dist-packages/gi/types.py:217: Warning: cannot derive 'aptdaemon+gtk3widgets+AptTerminal' from non-derivable parent type 'void'
  _gi.type_register(cls, namespace.get('__gtype_name__'))
Traceback (most recent call last):
  File "/usr/bin/gnome-language-selector", line 5, in <module>
    from LanguageSelector.gtk.GtkLanguageSelector import GtkLanguageSelector
  File "/usr/lib/python3/dist-packages/LanguageSelector/gtk/GtkLanguageSelector.py", line 30, in <module>
    from aptdaemon.gtk3widgets import AptProgressDialog
  File "/usr/lib/python3/dist-packages/aptdaemon/gtk3widgets.py", line 392, in <module>
    class AptTerminal(Vte.Terminal):
  File "/usr/lib/python3/dist-packages/gi/types.py", line 226, in __init__
    super(GObjectMeta, cls).__init__(name, bases, dict_)
  File "/usr/lib/python3/dist-packages/gi/types.py", line 205, in __init__
    cls._type_register(cls.__dict__)
  File "/usr/lib/python3/dist-packages/gi/types.py", line 217, in _type_register
    _gi.type_register(cls, namespace.get('__gtype_name__'))
RuntimeError: could not create new GType: aptdaemon+gtk3widgets+AptTerminal (subclass of void)


[COLOR=#000000]
```
[/COLOR]

---

### Post by #&amp;thj^% on 2022-08-02
[B][COLOR="#FF0000"]EDIT: Let me save any on lookers some time and just forgo the rest of this Thread, it was a very specific problem for an OS Version
Upgrade that is now EOL
So: Tl:Dr[/COLOR][/B]
Will you please try to create another user, and login under that new account, then see if these problems are still present.
Make the new user an Admin member:Sample:
either use su or sudo. (sudo is preferred)
Create a new user named joe_blow, run: 
```
sudo adduser joe_blow
```
Make joe_blow user &#8216;sudo user&#8217; (admin) run: 
```
sudo usermod -aG sudo joe_blow
```
Verify it by running the id joe_blow command: Sample:
```
id me
uid=1000(me) gid=1000(me) groups=1000(me),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),122(lpadmin),134(lxd),135(sambashare)

```
Log in as joe_blow: su - joe_blow. Than run sudo command for verification. For example: 
```
sudo ls -l /etc/shadow
```
Along with the above, I ran across something of interest:
```
apt-cache depends libaio1  libaio-dev
libaio1
  Depends: libc6
libaio-dev
  Depends: libaio1

```
That is possibly why the call for missing lib67 
```
sudo apt install libaio1 libaio-dev
```

---

### Post by kilrah757 on 2022-08-02
New user created and verified, no help...

I did see a bunch of
```
Failed to load module "xapp-gtk3-module"
```

in the syslog, so did a 

```
sudo apt reinstall xapp
```

Those are gone now, but no change on the libicuuc... 

Here's a tail of the syslog after that...
[ATTACH]290800[/ATTACH]

---

### Post by kilrah757 on 2022-08-02
> 
Along with the above, I ran across something of interest:
```
apt-cache depends libaio1  libaio-dev
libaio1
  Depends: libc6
libaio-dev
  Depends: libaio1

```
That is possibly why the call for missing lib67 
```
sudo apt install libaio1 libaio-dev
```

libaio1 was already installed, libaio-dev installed but no change

```
testuser@kilrah-win-ubuntu:~$ sudo apt install libaio1 libaio-devReading package lists... Done
Building dependency tree... Done
Reading state information... Done
libaio1 is already the newest version (0.3.112-13build1).
libaio1 set to manually installed.
The following NEW packages will be installed:
  libaio-dev
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 21.2 kB of archives.
After this operation, 71.7 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://archive.ubuntu.csg.uzh.ch/ubuntu jammy/main amd64 libaio-dev amd64 0.3.112-13build1 [21.2 kB]
Fetched 21.2 kB in 0s (358 kB/s)
Selecting previously unselected package libaio-dev:amd64.
(Reading database ... 402999 files and directories currently installed.)
Preparing to unpack .../libaio-dev_0.3.112-13build1_amd64.deb ...
Unpacking libaio-dev:amd64 (0.3.112-13build1) ...
Setting up libaio-dev:amd64 (0.3.112-13build1) ...
Processing triggers for man-db (2.10.2-1) ...



```

---

### Post by #&amp;thj^% on 2022-08-02
Well you may have been on to something earlier when you mentioned Language Support
It maybe just this easy, To purge and re-generate your locales:
```

sudo locale-gen --purge
```

Once that&#8217;s done, try re-opening your terminal emulator.

---

### Post by kilrah757 on 2022-08-02
Had already tried a locale-gen, redid with --purge but no help, gnome-language-selector also still doesn't open :(

Also tried reinstalling libvte-2.91 with no change

---

### Post by #&amp;thj^% on 2022-08-02
I'm stumped here, I was able to sorta reproduce your problem in the terminal part only.
I played with different versions of python and that quickly broke my gnome-terminal
what I did to fix it was to add the version to the terminal via:
```
sudo nano /usr/bin/gnome-terminal
```
at the time I was using "python3.8"
So I changed "#!/usr/bin/python3" to "#!/usr/bin/python3.8"
and i was back in the terminal again, so it may be worth a shot on your end as well.
But use the current version IE:
```
#!/usr/bin/python3.10.4
```
Please at least logout or restart the current session after that change is made:
I just use this to reset: "killall -3 gnome-shell"

---

### Post by kilrah757 on 2022-08-02
OK, I don't have a symlink for python3.10.4, only 3.10 and putting that doesn't help...
3.10.4 is the only version I have on the system

---

### Post by #&amp;thj^% on 2022-08-02
> **kilrah757 said:**
> OK, I don't have a symlink for python3.10.4, only 3.10 and putting that doesn't help...
3.10.4 is the only version I have on the system

Yep that was right "python3.10" i'm growing brain dead on this one. (Typeo)
Might be worth backing-up all you need, and Invest your time productively with a new fresh clean install.
This one seems to have me beat...:o

---

### Post by mIk3_08 on 2022-08-03
> **kilrah757 said:**
> I've updated a system from 21.10 to 22.04, and after that gnome-terminal won't run:

```
/usr/bin/gnome-terminal.real: error while loading shared libraries: libicuuc.so.67: cannot open shared object file: No such file or directory
```

Both libicu and gnome-terminal packages are the versions listed on packages.ubuntu.com for jammy

```
Listing... 
...
gnome-terminal-data/jammy,jammy,jammy,jammy,now 3.44.0-1ubuntu1 all [installed,automatic]
gnome-terminal/jammy,jammy,now 3.44.0-1ubuntu1 amd64 [installed]
...
libicu-dev/jammy,jammy,now 70.1-2 amd64 [installed,automatic]
libicu70/jammy,jammy,now 70.1-2 amd64 [installed,automatic]
libicu70/jammy,jammy,now 70.1-2 i386 [installed,automatic]
```

and there's no libicu67 package as expected... so why does it try to load an older version?
You can use Xterm while fixing your gnome terminal. Maybe this may take few moments fixing your gnome terminal but when you need to run a command so you can fix your gnome terminal you can use Xterm then. Maybe this might help you then. Regards and cheers.

---

### Post by ActionParsnip on 2022-08-03
```

sudo apt-get update
sudo apt-get install libglib2.0-0

```
Source:
[https://www.codegrepper.com/code-examples/shell/ImportError%3A+libicuuc.so.67%3A+cannot+open+shared+object+file%3A+No+such+file+or+directory](https://www.codegrepper.com/code-examples/shell/ImportError%3A+libicuuc.so.67%3A+cannot+open+shared+object+file%3A+No+such+file+or+directory)

---

### Post by kilrah757 on 2022-08-03
> **ActionParsnip said:**
> ```

sudo apt-get update
sudo apt-get install libglib2.0-0

```
Source:
[https://www.codegrepper.com/code-examples/shell/ImportError%3A+libicuuc.so.67%3A+cannot+open+shared+object+file%3A+No+such+file+or+directory](https://www.codegrepper.com/code-examples/shell/ImportError%3A+libicuuc.so.67%3A+cannot+open+shared+object+file%3A+No+such+file+or+directory)

Was already installed, tried a reinstall, no change...

---

### Post by #&amp;thj^% on 2022-08-03
We just can't find the problem here, and a stock gnome-terminal will have no "debug" option, that's a pity.
One more look to find why:
```
systemctl --user status gnome-terminal-server.service

```
maybe we get lucky and find something here.

---

### Post by kilrah757 on 2022-08-03
```
gnome-terminal-server.service - GNOME Terminal Server     Loaded: loaded (/usr/lib/systemd/user/gnome-terminal-server.service; static)
     Active: inactive (dead)
```

---

### Post by #&amp;thj^% on 2022-08-03
That's all it shows??
No:
```
Aug 03 08:49:45 me-Standard-PC-Q35-ICH9-2009 systemd[1142]: Starting GNOME Termina>
Aug 03 08:49:47 me-Standard-PC-Q35-ICH9-2009 systemd[1142]: Started GNOME Terminal>
Aug 03 08:50:23 me-Standard-PC-Q35-ICH9-2009 systemd[1142]: Starting GNOME Termina>
Aug 03 08:50:23 me-Standard-PC-Q35-ICH9-2009 systemd[1142]: Started GNOME Terminal>
Aug 03 09:03:33 me-Standard-PC-Q35-ICH9-2009 systemd[1142]: gnome-terminal-server.>
Aug 03 09:03:41 me-Standard-PC-Q35-ICH9-2009 systemd[1142]: Starting GNOME Termina>
Aug 03 09:03:41 me-Standard-PC-Q35-ICH9-2009 systemd[1142]: Started GNOME Terminal>
Aug 03 09:12:21 me-Standard-PC-Q35-ICH9-2009 systemd[1142]: gnome-terminal-server.>

```
Shown?
From the terminal your using now run this:
```
gnome-terminal
```

---

### Post by kilrah757 on 2022-08-03
> **1fallen said:**
> That's all it shows??

Yup that's all, -l gives nothing more, journalctl for that unit is empty 

> **1fallen said:**
> 
From the terminal your using now run this:
```
gnome-terminal
```

The all-too familiar now :/

```
testuser@kilrah-win-ubuntu:~$ gnome-terminal>gt2.txt 2>&1

/usr/bin/gnome-terminal.real: error while loading shared libraries: libicuuc.so.67: cannot open shared object file: No such file or directory

```

---

### Post by #&amp;thj^% on 2022-08-03
> **kilrah757 said:**
> 
The all-too familiar now :/



Yep and Indeed :)
while we are trying to sort this, please try:
```
systemctl --user start --now gnome-terminal-server.service

```
This has turned into a personal challenge now. ;)
Dang it I forgot this on as well, I guess i'm hoping it will just go away LOL
```
ldconfig -p | grep libicuuc
```
It should only show this:
```
ldconfig -p | grep libicuuc
	libicuuc.so.70 (libc6,x86-64) => /lib/x86_64-linux-gnu/libicuuc.so.70
```

---

### Post by ActionParsnip on 2022-08-03
Seems to be part of the libicu-dev package. Do you have this? If you do, then  run:
```

sudo updatedb
locate libicuuc.so*

```
What is the output please?

---

### Post by #&amp;thj^% on 2022-08-03
> **ActionParsnip said:**
> Seems to be part of the libicu-dev package. Do you have this? If you do, then  run:
```

sudo updatedb
locate libicuuc.so*

```
What is the output please?

It was a good thought, but shouldn't interfere with gnome-terminal IE:
```
apt policy libicu-dev 
libicu-dev:
  Installed: (none)
  Candidate: 70.1-2
  Version table:
     70.1-2 500
        500 http://archive.ubuntu.com/ubuntu jammy/main amd64 Packages

```

---

### Post by #&amp;thj^% on 2022-08-03
Ok I found on my end this was/is the culprut>>>"libicu67"
What is libicu67

libicu67 is:    ICU is a C++ and C library that provides robust and full-featured Unicode and locale support. This package contains the runtime libraries for ICU.
the only way to remove this leftover is:
```
sudo apt install aptitude

```
let it populate, when done run this:
```
sudo aptitude -y remove libicu67
```
followed by:
```
sudo apt autoremove
```
Be careful  using aptitude beyond this though.

---

### Post by kilrah757 on 2022-08-03
> **1fallen said:**
> This has turned into a personal challenge now. ;)
:lolflag:

> **1fallen said:**
> 
```
systemctl --user start --now gnome-terminal-server.service

```

```
testuser@kilrah-win-ubuntu:~$ systemctl --user start --now gnome-terminal-server.service Job for gnome-terminal-server.service failed because the control process exited with error code.
See "systemctl --user status gnome-terminal-server.service" and "journalctl --user -xeu gnome-terminal-server.service" for details.

```
I attached the 2 logs below after that

[ATTACH]290802[/ATTACH] [ATTACH]290803[/ATTACH]

> **1fallen said:**
> 
Dang it I forgot this on as well, I guess i'm hoping it will just go away LOL
```
ldconfig -p | grep libicuuc
```
It should only show this:
```
ldconfig -p | grep libicuuc
    libicuuc.so.70 (libc6,x86-64) => /lib/x86_64-linux-gnu/libicuuc.so.70
```

```
testuser@kilrah-win-ubuntu:~$ ldconfig -p | grep libicuuc 	libicuuc.so.70 (libc6,x86-64) => /lib/x86_64-linux-gnu/libicuuc.so.70
	libicuuc.so.70 (libc6) => /lib/i386-linux-gnu/libicuuc.so.70
	libicuuc.so (libc6,x86-64) => /lib/x86_64-linux-gnu/libicuuc.so

```

---

### Post by kilrah757 on 2022-08-03
> **1fallen said:**
> 
the only way to remove this leftover is:
```
sudo apt install aptitude

```
let it populate, when done run this:
```
sudo aptitude -y remove libicu67
```
followed by:
```
sudo apt autoremove
```
Be careful  using aptitude beyond this though.
The issue is that there isn't a leftover, nothing libicu67, but *something* wants it even though there's no reason to...

```
Reading package lists...Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
Writing extended state information...
Building tag database...
Couldn't find any package whose name or description matched "libicu67"

```

---

### Post by #&amp;thj^% on 2022-08-03
It somehow got linked in the previous version 21.10, as far as I can remember the user would have had to create the link or symlink IE:
```
cat /var/lib/dpkg/info/libicu70:amd64.list
/.
/usr
/usr/lib
/usr/lib/x86_64-linux-gnu
/usr/lib/x86_64-linux-gnu/libicudata.so.70.1
/usr/lib/x86_64-linux-gnu/libicui18n.so.70.1
/usr/lib/x86_64-linux-gnu/libicuio.so.70.1
/usr/lib/x86_64-linux-gnu/libicutest.so.70.1
/usr/lib/x86_64-linux-gnu/libicutu.so.70.1
/usr/lib/x86_64-linux-gnu/libicuuc.so.70.1
/usr/share
/usr/share/doc
/usr/share/doc/libicu70
/usr/share/doc/libicu70/changelog.Debian.gz
/usr/share/doc/libicu70/copyright
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/libicu70
/usr/lib/x86_64-linux-gnu/libicudata.so.70
/usr/lib/x86_64-linux-gnu/libicui18n.so.70
/usr/lib/x86_64-linux-gnu/libicuio.so.70
/usr/lib/x86_64-linux-gnu/libicutest.so.70
/usr/lib/x86_64-linux-gnu/libicutu.so.70
/usr/lib/x86_64-linux-gnu/libicuuc.so.70

```
You may find something like it using:
```
cat /var/lib/dpkg/info/libicu67:amd64.list
```
Anything there?
if not show this:
```
cd /usr/lib/x86_64-linux-gnu/ && ls | grep libicuuc
libicuuc.so.70
libicuuc.so.70.1

```

---

### Post by kilrah757 on 2022-08-03
> **1fallen said:**
> It somehow got linked in the previous version 21.10, as far as I can remember the user would have had to create the link or symlink IE:
```
cat /var/lib/dpkg/info/libicu70:amd64.list
/.
/usr
/usr/lib
/usr/lib/x86_64-linux-gnu
/usr/lib/x86_64-linux-gnu/libicudata.so.70.1
/usr/lib/x86_64-linux-gnu/libicui18n.so.70.1
/usr/lib/x86_64-linux-gnu/libicuio.so.70.1
/usr/lib/x86_64-linux-gnu/libicutest.so.70.1
/usr/lib/x86_64-linux-gnu/libicutu.so.70.1
/usr/lib/x86_64-linux-gnu/libicuuc.so.70.1
/usr/share
/usr/share/doc
/usr/share/doc/libicu70
/usr/share/doc/libicu70/changelog.Debian.gz
/usr/share/doc/libicu70/copyright
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/libicu70
/usr/lib/x86_64-linux-gnu/libicudata.so.70
/usr/lib/x86_64-linux-gnu/libicui18n.so.70
/usr/lib/x86_64-linux-gnu/libicuio.so.70
/usr/lib/x86_64-linux-gnu/libicutest.so.70
/usr/lib/x86_64-linux-gnu/libicutu.so.70
/usr/lib/x86_64-linux-gnu/libicuuc.so.70

```
You may find something like it using:
```
cat /var/lib/dpkg/info/libicu67:amd64.list
```
Anything there?

Only .70 and -dev ones

```
testuser@kilrah-win-ubuntu:~$ cat /var/lib/dpkg/info/libicu
libicu70:amd64.list       libicu70:i386.list        libicu-dev:amd64.list
libicu70:amd64.md5sums    libicu70:i386.md5sums     libicu-dev:amd64.md5sums
libicu70:amd64.shlibs     libicu70:i386.shlibs      
libicu70:amd64.triggers   libicu70:i386.triggers    

```

> **1fallen said:**
> 
if not show this:
```
cd /usr/lib/x86_64-linux-gnu/ && ls | grep libicuuc
libicuuc.so.70
libicuuc.so.70.1

```

```
testuser@kilrah-win-ubuntu:/usr/lib/x86_64-linux-gnu$ ls |grep libicuuc
libicuuc.a
libicuuc.so
libicuuc.so.70
libicuuc.so.70.1

```

---

### Post by #&amp;thj^% on 2022-08-03
Your machine is possessed, that's my story and I'm sticking to it...;)
well again I'm down the rabbit hole:
```
sudo aptitude install -y libicu70

```
can you include that process back.
Also I'm curious if this will even be found on Jammy
```
sudo aptitude install -y libicu67
```

---

### Post by kilrah757 on 2022-08-03
> **1fallen said:**
> Your machine is possessed, that's my story and I'm sticking to it...;)
It seems so!
This install has been going since *I think* 1904, and I've tried to use it as a counter to friends who say "don't use ubuntu, it breaks way too often on release updates" but it seems they might get a win on this one eventually... :biggrin:

> **1fallen said:**
> 
well again I'm down the rabbit hole:
```
sudo aptitude install -y libicu70

```
can you include that process back.

```
testuser@kilrah-win-ubuntu:~$ sudo aptitude install -y libicu70

Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
Writing extended state information...
Building tag database...
libicu70 is already installed at the requested version (70.1-2)
libicu70 is already installed at the requested version (70.1-2)
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
Writing extended state information...
Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
Writing extended state information...
Building tag database...

```

```
testuser@kilrah-win-ubuntu:~$ sudo aptitude reinstall -y libicu70

Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
Writing extended state information...
Building tag database...
The following packages will be REINSTALLED:
  libicu70 libicu70:i386 
0 packages upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 0 not upgraded.
Need to get 21.3 MB of archives. After unpacking 0 B will be used.
Writing extended state information...
Get: 1 http://archive.ubuntu.csg.uzh.ch/ubuntu jammy/main amd64 libicu70 amd64 70.1-2 [10.6 MB]
Get: 2 http://archive.ubuntu.csg.uzh.ch/ubuntu jammy/main i386 libicu70 i386 70.1-2 [10.8 MB]
Fetched 21.3 MB in 1s (19.2 MB/s)
(Reading database ... 
(Reading database ... 100%
(Reading database ... 403311 files and directories currently installed.)
Preparing to unpack .../libicu70_70.1-2_amd64.deb ...
Unpacking libicu70:amd64 (70.1-2) over (70.1-2) ...
Preparing to unpack .../libicu70_70.1-2_i386.deb ...
Unpacking libicu70:i386 (70.1-2) over (70.1-2) ...
Setting up libicu70:amd64 (70.1-2) ...
Setting up libicu70:i386 (70.1-2) ...
Processing triggers for libc-bin (2.35-0ubuntu3.1) ...
Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
Writing extended state information...
Building tag database...
```

> **1fallen said:**
> 
Also I'm curious if this will even be found on Jammy
```
sudo aptitude install -y libicu67
```

Not found

No change, rebooted for good measure...

---

### Post by #&amp;thj^% on 2022-08-03
I'm running some moc test's now give me some time to verify if it works.
I won't impose this on a user, until I've actually done and proven to myself.
I'll return if I have something worth while.
Even so, you have been a very wise and tolerant Poster :KS

---

### Post by kilrah757 on 2022-08-03
> [COLOR=#000000]I'm running some moc test's now give me some time to verify if it works.[/COLOR]
[COLOR=#000000]I won't impose this on a user, until I've actually done and proven to myself.[/COLOR]

You can go unsafe, I have an image of the drive from before the dist-upgrade so could always restore that and run the upgrade again to try something else / eventually get my stuff out of it if all hope is lost... but yeah I guess it's an opportunity to maybe learn something :biggrin:

---

### Post by #&amp;thj^% on 2022-08-03
> **kilrah757 said:**
> You can go unsafe, I have an image of the drive from before the dist-upgrade so could always restore that and run the upgrade again
Actually that would be Ideal, but>> before you "Do the version upgrade" I wouldn't mind having a look at a few things first.
This version you now using is tainted, I would like to at least find why this dist-upgrade went sideways with a look at the 21.10 restore.
Thanks I'll be back in a couple of hours, i have some personal obligations to satisfy first. ;)

---

### Post by kilrah757 on 2022-08-03
> **1fallen said:**
> Actually that would be Ideal, but>> before you "Do the version upgrade" I wouldn't mind having a look at a few things first.
This version you now using is tainted, I would like to at least find why this dist-upgrade went sideways with a look at the 21.10 restore.
Thanks I'll be back in a couple of hours, i have some personal obligations to satisfy first. ;)
For the record it already went sideways previously - I imaged the drive and ran the dist-upgrade back when 2204 came out, ran into the same issue, tried things and broke it completely, so just restored and stayed on 2110 with "I'll deal with that later". Now 2110 is out of support and repos are down so it was time to have a go at it again. 

Might take some time but I could try to virtualize/sanitize the image and just share it so you can try stuff if you're interested.

---

### Post by #&amp;thj^% on 2022-08-03
Try again with the restore, Ok I found why, you just can't make this stuff up....LOL
New Install 21.10 Impish, No updates though EOL
```
 sudo apt autoremove --purge libicu67
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages will be REMOVED:
  acl* adwaita-icon-theme* aisleriot* apg* apport* apport-gtk*
  apport-symptoms* appstream* apt-config-icons* apt-config-icons-hidpi*
  aptdaemon* aptdaemon-data* apturl* apturl-common* avahi-daemon* avahi-utils*
  baobab* bind9-dnsutils* bind9-host* bind9-libs* bluez-cups* bluez-obexd*
  bolt* brltty* bubblewrap* cheese* cheese-common* colord* colord-data* cups*
  cups-browsed* cups-core-drivers* cups-daemon* cups-pk-helper*
  cups-server-common* dconf-cli* deja-dup* docbook-xml* duplicity* enchant-2*
  eog* evince* evince-common* evolution-data-server*
  evolution-data-server-common* file-roller* fwupd* fwupd-signed* gcr* gdb*
  gdm3* gedit* gedit-common* genisoimage* geoclue-2.0*
  gir1.2-accountsservice-1.0* gir1.2-atk-1.0* gir1.2-atspi-2.0*
  gir1.2-dbusmenu-glib-0.4* gir1.2-dee-1.0* gir1.2-freedesktop* gir1.2-gck-1*
  gir1.2-gcr-3* gir1.2-gdesktopenums-3.0* gir1.2-gdkpixbuf-2.0*
  gir1.2-gdm-1.0* gir1.2-geoclue-2.0* gir1.2-gnomebluetooth-1.0*
  gir1.2-gnomedesktop-3.0* gir1.2-goa-1.0* gir1.2-graphene-1.0*
  gir1.2-gst-plugins-base-1.0* gir1.2-gstreamer-1.0* gir1.2-gtk-3.0*
  gir1.2-gtk-4.0* gir1.2-gtksource-4* gir1.2-gudev-1.0* gir1.2-gweather-3.0*
  gir1.2-handy-1* gir1.2-harfbuzz-0.0* gir1.2-ibus-1.0*
  gir1.2-javascriptcoregtk-4.0* gir1.2-json-1.0* gir1.2-mutter-8*
  gir1.2-nm-1.0* gir1.2-nma-1.0* gir1.2-notify-0.7* gir1.2-packagekitglib-1.0*
  gir1.2-pango-1.0* gir1.2-peas-1.0* gir1.2-polkit-1.0* gir1.2-rb-3.0*
  gir1.2-rsvg-2.0* gir1.2-secret-1* gir1.2-snapd-1* gir1.2-soup-2.4*
  gir1.2-totem-1.0* gir1.2-totemplparser-1.0* gir1.2-udisks-2.0*
  gir1.2-unity-7.0* gir1.2-upowerglib-1.0* gir1.2-vte-2.91*
  gir1.2-webkit2-4.0* gir1.2-wnck-3.0* gjs* gkbd-capplet* glib-networking*
  glib-networking-common* glib-networking-services* gnome-bluetooth*
  gnome-calculator* gnome-calendar* gnome-characters* gnome-control-center*
  gnome-control-center-faces* gnome-desktop3-data* gnome-disk-utility*
  gnome-font-viewer* gnome-initial-setup* gnome-keyring* gnome-keyring-pkcs11*
  gnome-logs* gnome-mahjongg* gnome-mines* gnome-online-accounts*
  gnome-power-manager* gnome-remote-desktop* gnome-screenshot*
  gnome-session-bin* gnome-session-canberra* gnome-session-common*
  gnome-settings-daemon* gnome-settings-daemon-common* gnome-shell*
  gnome-shell-common* gnome-shell-extension-appindicator*
  gnome-shell-extension-desktop-icons-ng* gnome-shell-extension-ubuntu-dock*
  gnome-startup-applications* gnome-sudoku* gnome-system-monitor*
  gnome-terminal* gnome-terminal-data* gnome-themes-extra*
  gnome-themes-extra-data* gnome-todo* gnome-todo-common* gnome-user-docs*
  gnome-video-effects* grilo-plugins-0.3-base* gstreamer1.0-clutter-3.0*
  gstreamer1.0-gl* gstreamer1.0-gtk3* gstreamer1.0-packagekit*
  gstreamer1.0-pipewire* gstreamer1.0-plugins-good* gstreamer1.0-pulseaudio*
  gstreamer1.0-x* gtk-update-icon-cache* gtk2-engines-murrine*
  gtk2-engines-pixbuf* guile-2.2-libs* gvfs-backends* hicolor-icon-theme*
  hplip* hplip-data* humanity-icon-theme* hunspell-en-us* ibus* ibus-data*
  ibus-gtk* ibus-gtk3* ibus-gtk4* ibus-table* iio-sensor-proxy* ipp-usb*
  language-selector-gnome* libaa1* libabw-0.1-1* libappstream4* libarchive13*
  libatkmm-1.6-1v5* libavahi-core7* libavahi-glib1* libavahi-ui-gtk3-0*
  libavc1394-0* libayatana-appindicator3-1* libayatana-ido3-0.4-0*
  libayatana-indicator3-7* libbabeltrace1* libboost-filesystem1.74.0*
  libboost-iostreams1.74.0* libboost-locale1.74.0* libboost-regex1.74.0*
  libboost-thread1.74.0* libbrlapi0.8* libc6-dbg* libcaca0*
  libcairo-gobject-perl* libcairo-gobject2* libcairo-perl*
  libcairo-script-interpreter2* libcairomm-1.0-1v5* libcamel-1.2-62*
  libcanberra-gtk3-0* libcanberra-gtk3-module* libcanberra-pulse*
  libcanberra0* libcdio-cdda2* libcdio-paranoia2* libcdio19* libcdr-0.1-1*
  libcheese-gtk25* libcheese8* libclucene-contribs1v5* libclucene-core1v5*
  libclutter-1.0-0* libclutter-1.0-common* libclutter-gst-3.0-0*
  libclutter-gtk-1.0-0* libcmis-0.5-5v5* libcogl-common* libcogl-pango20*
  libcogl-path20* libcogl20* libcolamd2* libcolord-gtk1* libcolord2*
  libcolorhug2* libcue2* libcupsimage2* libcurl4* libdazzle-1.0-0*
  libdazzle-common* libdbusmenu-glib4* libdbusmenu-gtk3-4*
  libdebuginfod-common* libdebuginfod1* libdee-1.0-4* libdjvulibre-text*
  libdjvulibre21* libdmapsharing-3.0-2* libdpkg-perl* libdrm-amdgpu1*
  libdrm-intel1* libdrm-nouveau2* libdrm-radeon1* libdv4* libe-book-0.1-1*
  libebackend-1.2-10* libebook-1.2-20* libebook-contacts-1.2-3* libecal-2.0-1*
  libedata-book-1.2-26* libedata-cal-2.0-1* libedataserver-1.2-26*
  libedataserverui-1.2-3* libegl-mesa0* libegl1* libenchant-2-2* libeot0*
  libepoxy0* libepubgen-0.1-1* libetonyek-0.1-1* libevdev2* libevdocument3-4*
  libevent-2.1-7* libevview3-3* libexempi8* libexif12* libexiv2-27*
  libexttextcat-2.0-0* libexttextcat-data* libextutils-depends-perl*
  libextutils-pkgconfig-perl* libfile-basedir-perl* libfile-desktopentry-perl*
  libfile-fcntllock-perl* libfile-mimeinfo-perl* libflashrom1* libfontenc1*
  libfreehand-0.1-1* libfreerdp-client2-2* libfreerdp2-2* libftdi1-2*
  libfwupd2* libfwupdplugin1* libgail-common* libgail18* libgbm1* libgc1*
  libgcab-1.0-0* libgcr-ui-3-1* libgd3* libgdata-common* libgdata22*
  libgdk-pixbuf-2.0-0* libgdk-pixbuf2.0-bin* libgdk-pixbuf2.0-common* libgdm1*
  libgee-0.8-2* libgeoclue-2-0* libgeocode-glib0* libgexiv2-2* libgif7*
  libgjs0g* libgl1* libgl1-mesa-dri* libglapi-mesa* libgles2*
  libglib-object-introspection-perl* libglib-perl* libglibmm-2.4-1v5*
  libglu1-mesa* libglvnd0* libglx-mesa0* libglx0* libgnome-autoar-0-0*
  libgnome-bluetooth13* libgnome-desktop-3-19* libgnome-games-support-1-3*
  libgnome-games-support-common* libgnome-todo* libgnomekbd-common*
  libgnomekbd8* libgoa-1.0-0b* libgoa-1.0-common* libgoa-backend-1.0-1*
  libgom-1.0-0* libgpgmepp6* libgphoto2-6* libgphoto2-l10n* libgphoto2-port12*
  libgpod-common* libgpod4* libgraphene-1.0-0* libgrilo-0.3-0* libgsf-1-114*
  libgsf-1-common* libgsound0* libgspell-1-2* libgspell-1-common*
  libgssdp-1.2-0* libgstreamer-gl1.0-0* libgstreamer-plugins-good1.0-0*
  libgtk-3-0* libgtk-3-bin* libgtk-3-common* libgtk-4-1* libgtk-4-bin*
  libgtk-4-common* libgtk2.0-0* libgtk2.0-bin* libgtk2.0-common* libgtk3-perl*
  libgtkmm-3.0-1v5* libgtksourceview-4-0* libgtksourceview-4-common*
  libgtop-2.0-11* libgtop2-common* libgupnp-1.2-0* libgupnp-av-1.0-2*
  libgupnp-dlna-2.0-3* libgweather-3-16* libgweather-common* libgxps2*
  libhandy-1-0* libharfbuzz-icu0* libhpmud0* libhunspell-1.7-0* libhyphen0*
  libibus-1.0-5* libical3* libicu67* libiec61883-0* libieee1284-3*
  libimagequant0* libimobiledevice6* libinput-bin* libinput10*
  libio-stringy-perl* libipc-system-simple-perl* libipt2*
  libjavascriptcoregtk-4.0-18* libjcat1* libjson-glib-1.0-0*
  libjson-glib-1.0-common* libkpathsea6* liblangtag-common* liblangtag1*
  libldb2* liblirc-client0* libllvm12* liblmdb0* liblouis-data* liblouis20*
  liblouisutdml-bin* liblouisutdml-data* liblouisutdml9* liblua5.3-0*
  libmanette-0.2-0* libmaxminddb0* libmediaart-2.0-0* libmessaging-menu0*
  libmhash2* libminiupnpc17* libmozjs-78-0* libmp3lame0* libmpg123-0*
  libmspub-0.1-1* libmtdev1* libmtp-common* libmtp-runtime* libmtp9*
  libmutter-8-0* libmwaw-0.3-3* libmythes-1.2-0* libnatpmp1*
  libnautilus-extension1a* libneon27-gnutls* libnfs13* libnma-common* libnma0*
  libnotify-bin* libnotify4* libnss-mdns* libodfgen-0.1-1* liborcus-0.16-0*
  liborcus-parser-0.16-0* libpackagekit-glib2-18* libpagemaker-0.0-0*
  libpangomm-1.4-1v5* libpangoxft-1.0-0* libpciaccess0* libpcre2-32-0*
  libpeas-1.0-0* libpeas-common* libphonenumber8* libpipewire-0.3-0*
  libpipewire-0.3-common* libpipewire-0.3-modules* libpkcs11-helper1*
  libplist3* libpoppler-glib8* libprotobuf23* libpulse-mainloop-glib0*
  libpulsedsp* libpython3.9* libqqwing2v5* libraptor2-0* librasqal3*
  libraw1394-11* libraw20* librdf0* libreoffice-base-core* libreoffice-calc*
  libreoffice-common* libreoffice-core* libreoffice-draw* libreoffice-gnome*
  libreoffice-gtk3* libreoffice-help-common* libreoffice-help-en-us*
  libreoffice-impress* libreoffice-math* libreoffice-ogltrans*
  libreoffice-pdfimport* libreoffice-style-elementary* libreoffice-style-yaru*
  libreoffice-writer* librest-0.7-0* librevenge-0.0-0* librhythmbox-core10*
  librsvg2-2* librsvg2-common* librsync2* librygel-core-2.6-2*
  librygel-db-2.6-2* librygel-renderer-2.6-2* librygel-server-2.6-2*
  libsane-common* libsane-hpaio* libsane1* libsbc1* libsensors-config*
  libsensors5* libsgutils2-2* libshout3* libsigc++-2.0-0v5* libsmbclient*
  libsmbios-c2* libsnapd-glib1* libsnmp-base* libsnmp40* libsodium23*
  libsoup-gnome2.4-1* libsoup2.4-1* libsource-highlight-common*
  libsource-highlight4v5* libsoxr0* libspa-0.2-modules* libspectre1*
  libspeex1* libspeexdsp1* libstartup-notification0* libstemmer0d*
  libsuitesparseconfig5* libsynctex2* libsysmetrics1* libtag1v5*
  libtag1v5-vanilla* libtalloc2* libtdb1* libtevent0*
  libtotem-plparser-common* libtotem-plparser18* libtotem0*
  libtracker-sparql-3.0-0* libtss2-esys-3.0.2-0* libtss2-mu0* libtss2-sys1*
  libtss2-tcti-cmd0* libtss2-tcti-device0* libtss2-tcti-mssim0*
  libtss2-tcti-swtpm0* libtwolame0* libunity-protocol-private0*
  libunity-scopes-json-def-desktop* libunity9* libuno-cppu3*
  libuno-cppuhelpergcc3-3* libuno-purpenvhelpergcc3-3* libuno-sal3*
  libuno-salhelpergcc3-3* libupower-glib3* libusbmuxd6* libuv1* libv4l-0*
  libv4lconvert0* libvisio-0.1-1* libvncclient1* libvncserver1*
  libvorbisfile3* libvpx6* libvte-2.91-0* libvte-2.91-common* libvulkan1*
  libwacom-bin* libwacom-common* libwacom2* libwavpack1* libwayland-client0*
  libwayland-cursor0* libwayland-egl1* libwayland-server0* libwbclient0*
  libwebkit2gtk-4.0-37* libwebpdemux2* libwebpmux3*
  libwebrtc-audio-processing1* libwhoopsie-preferences0* libwinpr2-2*
  libwmf0.2-7* libwmf0.2-7-gtk* libwnck-3-0* libwnck-3-common* libwoff1*
  libwpd-0.10-10* libwpg-0.3-3* libwps-0.4-4* libxatracker2* libxcb-dri2-0*
  libxcb-dri3-0* libxcb-glx0* libxcb-icccm4* libxcb-image0* libxcb-keysyms1*
  libxcb-present0* libxcb-randr0* libxcb-render-util0* libxcb-res0*
  libxcb-shape0* libxcb-sync1* libxcb-util1* libxcb-xfixes0* libxcb-xkb1*
  libxcb-xv0* libxcomposite1* libxdamage1* libxfont2* libxft2* libxinerama1*
  libxkbcommon-x11-0* libxkbcommon0* libxkbfile1* libxkbregistry0*
  libxklavier16* libxml2* libxmlb1* libxmlsec1* libxmlsec1-nss* libxres1*
  libxshmfence1* libxslt1.1* libxss1* libxv1* libxvmc1* libxxf86dga1*
  libyajl2* libyelp0* lp-solve* media-player-info* mesa-vulkan-drivers*
  mobile-broadband-provider-info* mousetweaks* mutter-common* nautilus*
  nautilus-data* nautilus-extension-gnome-terminal* nautilus-share*
  network-manager-gnome* network-manager-openvpn*
  network-manager-openvpn-gnome* network-manager-pptp-gnome* openvpn* orca*
  p11-kit* p11-kit-modules* packagekit* packagekit-tools* patch*
  pinentry-gnome3* pipewire* pipewire-bin* pipewire-media-session* pkg-config*
  power-profiles-daemon* printer-driver-hpcups* printer-driver-postscript-hp*
  printer-driver-splix* pulseaudio* pulseaudio-module-bluetooth*
  pulseaudio-utils* python3-apport* python3-aptdaemon*
  python3-aptdaemon.gtk3widgets* python3-bcrypt* python3-brlapi*
  python3-cairo* python3-certifi* python3-chardet* python3-cups*
  python3-cupshelpers* python3-dateutil* python3-debconf* python3-debian*
  python3-defer* python3-fasteners* python3-future* python3-gi-cairo*
  python3-ibus-1.0* python3-idna* python3-ldb* python3-lib2to3*
  python3-lockfile* python3-louis* python3-macaroonbakery* python3-mako*
  python3-markupsafe* python3-monotonic* python3-nacl* python3-olefile*
  python3-paramiko* python3-pexpect* python3-pil* python3-problem-report*
  python3-protobuf* python3-ptyprocess* python3-pyatspi* python3-pymacaroons*
  python3-renderpm* python3-reportlab* python3-reportlab-accel*
  python3-requests* python3-rfc3339* python3-software-properties*
  python3-speechd* python3-systemd* python3-talloc* python3-tz* python3-uno*
  python3-urllib3* python3-xdg* remmina* remmina-common* remmina-plugin-rdp*
  remmina-plugin-secret* remmina-plugin-vnc* rhythmbox* rhythmbox-data*
  rhythmbox-plugin-alternative-toolbar* rhythmbox-plugins* rtkit* rygel*
  samba-libs* sane-airscan* sane-utils* seahorse* session-migration*
  sgml-base* sgml-data* shared-mime-info* shotwell* shotwell-common*
  simple-scan* software-properties-common* software-properties-gtk*
  sound-theme-freedesktop* spice-vdagent* ssl-cert* switcheroo-control*
  system-config-printer* system-config-printer-common*
  system-config-printer-udev* thermald* thunderbird*
  thunderbird-gnome-support* thunderbird-locale-en* thunderbird-locale-en-us*
  totem* totem-common* totem-plugins* tpm-udev* tracker* tracker-extract*
  tracker-miner-fs* transmission-common* transmission-gtk* ubuntu-desktop*
  ubuntu-desktop-minimal* ubuntu-docs* ubuntu-mono*
  ubuntu-release-upgrader-gtk* ubuntu-session* ubuntu-standard*
  unattended-upgrades* uno-libs-private* update-manager* update-notifier*
  update-notifier-common* upower* ure* usb-creator-common* usb-creator-gtk*
  usbmuxd* whoopsie-preferences* x11-apps* x11-session-utils* x11-utils*
  x11-xkb-utils* xbitmaps* xbrlapi* xdg-dbus-proxy* xdg-desktop-portal*
  xdg-desktop-portal-gtk* xdg-user-dirs-gtk* xfonts-base* xfonts-encodings*
  xfonts-scalable* xfonts-utils* xinit* xinput* xml-core* xorg*
  xserver-common* xserver-xephyr* xserver-xorg* xserver-xorg-core*
  xserver-xorg-input-all* xserver-xorg-input-libinput*
  xserver-xorg-input-wacom* xserver-xorg-legacy* xserver-xorg-video-all*
  xserver-xorg-video-amdgpu* xserver-xorg-video-ati* xserver-xorg-video-fbdev*
  xserver-xorg-video-intel* xserver-xorg-video-nouveau*
  xserver-xorg-video-qxl* xserver-xorg-video-radeon* xserver-xorg-video-vesa*
  xserver-xorg-video-vmware* xwayland* yaru-theme-gtk* yelp* yelp-xsl* zenity*
  zenity-common*
0 upgraded, 0 newly installed, 798 to remove and 0 not upgraded.
After this operation, 1,653 MB disk space will be freed.
Do you want to continue? [Y/n] 


```
I went for the whole kit and kaboodle, I want nothing from the list above.
NOTE: In this session I kept the Software Updater opened and poised for the Dist-Upgrade as soon as Apt was finished removing the above packages.
As expected that did not work out, so I rebooted to Recovery/Networking mode via Grub.
and then manually upgraded via:
```
sudo do-release-upgrade
```
After rebooted, To a sparkly shiny new OS, with a working gnome-terminal and language-support locale-support. FTR: libc6 was needed for the process, but don't install it, it gets handled in the process

[B]Score for personal challenge: 1fallen=#1 | libicu67=0 
I win! LOL[/B]

---

### Post by kilrah757 on 2022-08-03
Did you try updating "normally" from the clean install and replicate the issue?

This is madness though, pretty sure on a working system that'll nuke most of the stuff I had installed, but who knows...

I sanitized/shrunk/imaged the broken system, doing a pre-update restore now...

---

### Post by #&amp;thj^% on 2022-08-03
> **kilrah757 said:**
> Did you try updating "normally" from the clean install and replicate the issue?


No Reason to, Why? >>>EOL
I already knew what the problem was, (libicu67)
I just wanted to see how far in, it was linked in the system.
It was linked to the core of the OS in 21.10
You still have your original .img back-up right?

---

### Post by kilrah757 on 2022-08-03
Yup sure, here's my 6.8GB list :mrgreen:

```
Reading package lists...Building dependency tree...
Reading state information...
The following packages will be REMOVED:
  acl* adwaita-icon-theme* adwaita-qt* aisleriot* apg* apport* apport-gtk*
  apport-symptoms* appstream* apt-config-icons* apt-config-icons-hidpi*
  aptdaemon* aptdaemon-data* apturl* apturl-common* asunder* asymptote*
  asymptote-doc* asymptote-x11* autopoint* avahi-daemon* avahi-utils* baobab*
  battery-monitor* bind9-dnsutils* bind9-host* bind9-libs* blueman*
  bluez-cups* bluez-obexd* bolt* brasero* brasero-cdrkit* brasero-common*
  brave-browser* brave-keyring* breeze* breeze-cursor-theme* brltty*
  bubblewrap* ca-certificates-java* catdoc* cdparanoia* cdrdao* chafa* cheese*
  cheese-common* cinnamon* cinnamon-common* cinnamon-control-center*
  cinnamon-control-center-data* cinnamon-control-center-goa* cinnamon-core*
  cinnamon-desktop-data* cinnamon-screensaver* cinnamon-session*
  cinnamon-session-common* cinnamon-settings-daemon* cjs* cmake* cmake-data*
  colord* colord-data* companion23* cryptsetup-bin* csvkit* cups*
  cups-browsed* cups-core-drivers* cups-daemon* cups-pk-helper*
  cups-server-common* dconf-cli* dconf-editor* ddrescue-gui* debhelper*
  debugedit* default-jre-headless* deja-dup* desktop-base* dh-autoreconf*
  dh-strip-nondeterminism* dmeventd* docbook-xml* duplicity* dvdauthor*
  dvgrab* dvipng* dvisvgm* dwz* enchant-2* eog* evince* evince-common*
  evolution-data-server* evolution-data-server-common* ffmpeg* file-roller*
  flac* fonts-dejavu-extra* fonts-gfs-baskerville* fonts-gfs-porson*
  fonts-lato* fonts-lmodern* fonts-lyx* fonts-quicksand* fonts-wine*
  freeglut3* freeglut3-dev* frei0r-plugins* fwupd* gcdemu* gcr* gdal-data*
  gdb* gdm3* geany* geany-common* gedit* gedit-common* genisoimage*
  geoclue-2.0* gettext* gir1.2-accountsservice-1.0* gir1.2-appindicator3-0.1*
  gir1.2-atk-1.0* gir1.2-atspi-2.0* gir1.2-ayatanaappindicator3-0.1*
  gir1.2-caribou-1.0* gir1.2-cinnamondesktop-3.0* gir1.2-clutter-1.0*
  gir1.2-cmenu-3.0* gir1.2-cogl-1.0* gir1.2-coglpango-1.0* gir1.2-cvc-1.0*
  gir1.2-dazzle-1.0* gir1.2-dbusmenu-glib-0.4* gir1.2-dee-1.0* gir1.2-gck-1*
  gir1.2-gcr-3* gir1.2-gdata-0.0* gir1.2-gdesktopenums-3.0*
  gir1.2-gdkpixbuf-2.0* gir1.2-gdm-1.0* gir1.2-geoclue-2.0* gir1.2-gkbd-3.0*
  gir1.2-gnomebluetooth-1.0* gir1.2-gnomedesktop-3.0* gir1.2-goa-1.0*
  gir1.2-graphene-1.0* gir1.2-gst-plugins-base-1.0* gir1.2-gtk-2.0*
  gir1.2-gtk-3.0* gir1.2-gtk-4.0* gir1.2-gtkclutter-1.0* gir1.2-gtksource-4*
  gir1.2-gudev-1.0* gir1.2-gweather-3.0* gir1.2-handy-1* gir1.2-harfbuzz-0.0*
  gir1.2-ibus-1.0* gir1.2-javascriptcoregtk-4.0* gir1.2-json-1.0*
  gir1.2-keybinder-3.0* gir1.2-meta-muffin-0.0* gir1.2-mutter-8*
  gir1.2-nautilus-3.0* gir1.2-nemo-3.0* gir1.2-nm-1.0* gir1.2-nma-1.0*
  gir1.2-notify-0.7* gir1.2-packagekitglib-1.0* gir1.2-pango-1.0*
  gir1.2-peas-1.0* gir1.2-polkit-1.0* gir1.2-rb-3.0* gir1.2-rsvg-2.0*
  gir1.2-secret-1* gir1.2-snapd-1* gir1.2-soup-2.4* gir1.2-timezonemap-1.0*
  gir1.2-totem-1.0* gir1.2-totemplparser-1.0* gir1.2-udisks-2.0*
  gir1.2-unity-5.0* gir1.2-vte-2.91* gir1.2-webkit2-4.0* gir1.2-wnck-3.0*
  gir1.2-xapp-1.0* gir1.2-xkl-1.0* gist* gitg* gjs* gkbd-capplet*
  glib-networking* glib-networking-common* glib-networking-services*
  gnome-backgrounds* gnome-bluetooth* gnome-calculator* gnome-calendar*
  gnome-characters* gnome-common* gnome-control-center*
  gnome-control-center-faces* gnome-desktop3-data* gnome-disk-utility*
  gnome-font-viewer* gnome-initial-setup* gnome-keyring* gnome-keyring-pkcs11*
  gnome-logs* gnome-mahjongg* gnome-mines* gnome-online-accounts*
  gnome-power-manager* gnome-remote-desktop* gnome-screenshot*
  gnome-session-bin* gnome-session-canberra* gnome-session-common*
  gnome-settings-daemon* gnome-settings-daemon-common* gnome-shell*
  gnome-shell-common* gnome-shell-extension-appindicator*
  gnome-shell-extension-desktop-icons-ng* gnome-shell-extension-ubuntu-dock*
  gnome-startup-applications* gnome-sudoku* gnome-system-monitor*
  gnome-terminal* gnome-terminal-data* gnome-themes-extra*
  gnome-themes-extra-data* gnome-todo* gnome-todo-common* gnome-user-docs*
  gnome-user-docs-fr* gnome-video-effects* google-chrome-stable* gparted*
  gparted-common* gpicview* grilo-plugins-0.3-base* growisofs*
  grub-customizer* gsettings-desktop-schemas-dev* gstreamer1.0-clutter-3.0*
  gstreamer1.0-gl* gstreamer1.0-gtk3* gstreamer1.0-libav*
  gstreamer1.0-packagekit* gstreamer1.0-pipewire* gstreamer1.0-plugins-bad*
  gstreamer1.0-plugins-good* gstreamer1.0-pulseaudio* gstreamer1.0-vaapi*
  gstreamer1.0-x* gtk-update-icon-cache* gtk2-engines-murrine*
  gtk2-engines-pixbuf* guile-2.2-libs* gvfs-backends* hddtemp*
  heif-gdk-pixbuf* hplip* hplip-data* httptoolkit* humanity-icon-theme*
  hunspell-en-us* hwdata* hwinfo* i965-va-driver* ibus* ibus-data* ibus-gtk*
  ibus-gtk3* ibus-gtk4* ibus-table* icu-devtools* iio-sensor-proxy*
  imagemagick* imagemagick-6-common* imagemagick-6.q16* intel-media-va-driver*
  intltool* intltool-debian* inxi* ipp-usb* iso-flags-png-320x240* jackd*
  jackd1-firewire* java-common* kaccounts-providers* kactivities-bin*
  kactivitymanagerd* kde-style-breeze* kdeconnect* kded5* kdenlive*
  kdenlive-data* keditbookmarks* kinit* kio* kpackagelauncherqml*
  kpackagetool5* kpartx* kpeople-vcard* krita* krita-data* krita-gmic*
  ktexteditor-data* ktexteditor-katepart* kwayland-data* kwayland-integration*
  kwin-style-breeze* language-selector-gnome* libaa1* libaacs0* libabw-0.1-1*
  libaccounts-glib0* libaccounts-qt5-1* libadwaitaqt1* libadwaitaqtpriv1*
  libaec0* libaio1* libalien-wxwidgets-perl* libapache-pom-java* libappimage0*
  libappindicator3-1* libappstream4* libarchive-cpio-perl*
  libarchive-zip-perl* libarchive13* libarmadillo10* libarpack2* libass9*
  libatk-bridge2.0-dev* libatk-wrapper-java* libatk-wrapper-java-jni*
  libatk1.0-dev* libatkmm-1.6-1v5* libatspi2.0-dev* libavahi-core7*
  libavahi-glib1* libavahi-ui-gtk3-0* libavc1394-0* libavcodec58*
  libavdevice58* libavfilter7* libavformat58* libavutil56*
  libayatana-appindicator3-1* libayatana-ido3-0.4-0* libayatana-indicator3-7*
  libbabeltrace1* libbdplus0* libbluray2* libboost-iostreams1.74.0*
  libboost-locale1.74.0* libboost-regex1.74.0* libbrasero-media3-1*
  libbrlapi0.8* libbrotli-dev* libbs2b0* libburn4* libc6-dbg* libcaca-dev*
  libcairo-gobject-perl* libcairo-gobject2* libcairo-perl*
  libcairo-script-interpreter2* libcairo2-dev* libcairomm-1.0-1v5*
  libcamel-1.2-62* libcanberra-gtk3-0* libcanberra-gtk3-module*
  libcanberra-pulse* libcapi20-3* libcaribou-common* libcaribou0* libcddb2*
  libcdio-cdda2* libcdio-paranoia2* libcdr-0.1-1* libcfitsio9* libchafa0*
  libcharls2* libcheese-gtk25* libcheese8* libchromaprint1*
  libcinnamon-control-center1* libcinnamon-desktop4* libcinnamon-menu-3-0*
  libcjs0* libclang1-11* libclass-data-inheritable-perl*
  libclucene-contribs1v5* libclucene-core1v5* libclutter-1.0-0*
  libclutter-1.0-common* libclutter-1.0-dev* libclutter-gst-3.0-0*
  libclutter-gtk-1.0-0* libclutter-gtk-1.0-dev* libcmis-0.5-5v5*
  libcodec2-0.9* libcogl-common* libcogl-dev* libcogl-pango-dev*
  libcogl-pango20* libcogl-path-dev* libcogl-path20* libcogl20* libcolamd2*
  libcolord-gtk1* libcolord2* libcolorhug2* libcommons-logging-java*
  libcommons-parent-java* libconfig++9v5* libcscreensaver0* libcue2*
  libcups2-dev* libcupsfilters-dev* libcupsimage2* libcupsimage2-dev* libcvc0*
  libdap27* libdapclient6v5* libdatrie-dev* libdazzle-1.0-0*
  libdazzle-1.0-dev* libdazzle-common* libdbusmenu-glib4* libdbusmenu-gtk3-4*
  libdbusmenu-qt5-2* libdc1394-25* libdca0* libdebhelper-perl*
  libdebuginfod-common* libdebuginfod1* libdee-1.0-4* libdeflate-dev*
  libdevel-globaldestruction-perl* libdevmapper-event1.02.1*
  libdist-checkconflicts-perl* libdjvulibre-text* libdjvulibre21*
  libdmapsharing-3.0-2* libdouble-conversion3* libdrm-amdgpu1* libdrm-dev*
  libdrm-intel1* libdrm-nouveau2* libdrm-radeon1* libdv4* libdvdnav4*
  libe-book-0.1-1* libebackend-1.2-10* libebook-1.2-20*
  libebook-contacts-1.2-3* libebur128-1* libecal-2.0-1* libedata-book-1.2-26*
  libedata-cal-2.0-1* libedataserver-1.2-26* libedataserverui-1.2-3*
  libeditorconfig0* libegl-dev* libegl1-mesa-dev* libemail-date-format-perl*
  libenca0* libenchant-2-2* libeot0* libepoxy-dev* libepoxy0* libepsilon1*
  libepub0* libepubgen-0.1-1* libetonyek-0.1-1* libeval-closure-perl*
  libevdev-dev* libevdev2* libevdocument3-4* libevview3-3*
  libexception-class-perl* libexempi8* libexiv2-27* libexttextcat-2.0-0*
  libexttextcat-data* libextutils-depends-perl* libextutils-pkgconfig-perl*
  libfaad2* libfakekey0* libfam0* libfaudio0* libffado2* libfftw3-double3*
  libfile-basedir-perl* libfile-desktopentry-perl* libfile-homedir-perl*
  libfile-mimeinfo-perl* libfile-stripnondeterminism-perl* libfile-which-perl*
  libflashrom1* libfontbox-java* libfontconfig-dev* libfontconfig1-dev*
  libfontenc1* libfox-1.6-0* libfox-1.6-dev* libfreehand-0.1-1*
  libfreerdp-client2-2* libfreerdp2-2* libfreetype-dev* libfreetype6-dev*
  libfreexl1* libfribidi-dev* libfwupd2* libfwupdplugin5* libfyba0*
  libgail-3-0* libgail-common* libgail18* libgavl1* libgbm-dev* libgcab-1.0-0*
  libgck-1-dev* libgcr-3-dev* libgcr-ui-3-1* libgdal28* libgdata-common*
  libgdata-dev* libgdata22* libgdcm3.0* libgdk-pixbuf-2.0-0*
  libgdk-pixbuf-2.0-dev* libgdk-pixbuf-xlib-2.0-0* libgdk-pixbuf-xlib-2.0-dev*
  libgdk-pixbuf2.0-0* libgdk-pixbuf2.0-bin* libgdk-pixbuf2.0-common*
  libgdk-pixbuf2.0-dev* libgdm1* libgee-0.8-2* libgeoclue-2-0*
  libgeocode-glib0* libgeos-3.9.0* libgeos-c1v5* libgeotiff5* libgexiv2-2*
  libgit2-1.1* libgit2-glib-1.0-0* libgjs0g* libgl-dev* libgl1*
  libgl1-mesa-dev* libgl1-mesa-dri* libgles-dev* libgles1* libgles2*
  libgles2-mesa-dev* libglew2.1* libglfw3* libglfw3-dev*
  libglib-object-introspection-perl* libglib-perl* libglibmm-2.4-1v5*
  libglu1-mesa* libglu1-mesa-dev* libglvnd-core-dev* libglvnd-dev* libglx-dev*
  libglx-mesa0* libglx0* libgme0* libgmic1* libgnome-autoar-0-0*
  libgnome-bluetooth13* libgnome-desktop-3-19* libgnome-desktop-3-dev*
  libgnome-games-support-1-3* libgnome-games-support-common* libgnome-todo*
  libgnomekbd-common* libgnomekbd8* libgoa-1.0-0b* libgoa-1.0-common*
  libgoa-1.0-dev* libgoa-backend-1.0-1* libgom-1.0-0* libgpgmepp6*
  libgphoto2-6* libgphoto2-l10n* libgphoto2-port12* libgpod-common* libgpod4*
  libgraphene-1.0-0* libgraphicsmagick++-q16-12* libgraphicsmagick-q16-3*
  libgraphite2-dev* libgrilo-0.3-0* libgsf-1-114* libgsf-1-common* libgsl25*
  libgslcblas0* libgsm1* libgsoap-2.8.104* libgsound0* libgspell-1-2*
  libgspell-1-common* libgssdp-1.2-0* libgstreamer-gl1.0-0*
  libgstreamer-plugins-bad1.0-0* libgstreamer-plugins-good1.0-0* libgtk-3-0*
  libgtk-3-bin* libgtk-3-common* libgtk-3-dev* libgtk-4-1* libgtk-4-bin*
  libgtk-4-common* libgtk2.0-0* libgtk2.0-bin* libgtk2.0-common*
  libgtk2.0-dev* libgtk3-perl* libgtkmm-3.0-1v5* libgtksourceview-3.0-1*
  libgtksourceview-3.0-common* libgtksourceview-4-0*
  libgtksourceview-4-common* libgtkspell3-3-0* libgtop-2.0-11*
  libgtop2-common* libgudev-1.0-dev* libgupnp-1.2-0* libgupnp-av-1.0-2*
  libgupnp-dlna-2.0-3* libgupnp-igd-1.0-4* libgweather-3-16*
  libgweather-common* libgxps2* libhandy-1-0* libharfbuzz-dev*
  libharfbuzz-gobject0* libharfbuzz-icu0* libhd21* libhdf4-0-alt*
  libhdf5-103-1* libhdf5-hl-100* libhfstospell11* libhpmud0*
  libhttp-parser2.9* libhunspell-1.7-0* libhyphen0* libibus-1.0-5*
  libibus-1.0-dev* libical3* libicu-dev* libicu67* libiec61883-0*
  libieee1284-3* libigdgmm11* libilmbase25* libimagequant0* libinput-bin*
  libinput-dev* libinput10* libipa-hbac0* libipc-shareable-perl*
  libipc-system-simple-perl* libipt2* libisofs6* libjavascriptcoregtk-4.0-18*
  libjbig-dev* libjcat1* libjpeg-dev* libjpeg-turbo8-dev* libjpeg8-dev*
  libjson-glib-1.0-0* libjson-glib-1.0-common* libjson-glib-dev* libjsoncpp24*
  libjte2* libjxr-tools* libjxr0* libkaccounts2* libkate1*
  libkdecorations2-5v5* libkdecorations2private8* libkeybinder-3.0-0*
  libkf5activities5* libkf5archive5* libkf5attica5* libkf5auth-data*
  libkf5auth5* libkf5authcore5* libkf5bluezqt-data* libkf5bluezqt6*
  libkf5bookmarks-data* libkf5bookmarks5* libkf5calendarevents5*
  libkf5codecs-data* libkf5codecs5* libkf5completion-data* libkf5completion5*
  libkf5config-bin* libkf5config-data* libkf5configcore5* libkf5configgui5*
  libkf5configwidgets-data* libkf5configwidgets5* libkf5contacts-data*
  libkf5contacts5* libkf5coreaddons-data* libkf5coreaddons5* libkf5crash5*
  libkf5dbusaddons-bin* libkf5dbusaddons-data* libkf5dbusaddons5*
  libkf5declarative-data* libkf5declarative5* libkf5doctools5*
  libkf5filemetadata-bin* libkf5filemetadata-data* libkf5filemetadata3*
  libkf5globalaccel-bin* libkf5globalaccel-data* libkf5globalaccel5*
  libkf5globalaccelprivate5* libkf5guiaddons5* libkf5i18n-data* libkf5i18n5*
  libkf5iconthemes-bin* libkf5iconthemes-data* libkf5iconthemes5*
  libkf5idletime5* libkf5itemviews-data* libkf5itemviews5*
  libkf5jobwidgets-data* libkf5jobwidgets5* libkf5kcmutils-data*
  libkf5kcmutils5* libkf5kdelibs4support-data* libkf5kdelibs4support5*
  libkf5kdelibs4support5-bin* libkf5kiocore5* libkf5kiofilewidgets5*
  libkf5kiogui5* libkf5kiontlm5* libkf5kiowidgets5* libkf5kirigami2-5*
  libkf5newstuff-data* libkf5newstuff5* libkf5newstuffcore5*
  libkf5notifications-data* libkf5notifications5* libkf5notifyconfig-data*
  libkf5notifyconfig5* libkf5package-data* libkf5package5* libkf5parts-data*
  libkf5parts-plugins* libkf5parts5* libkf5people-data* libkf5people5*
  libkf5peoplebackend5* libkf5peoplewidgets5* libkf5plasma5*
  libkf5plasmaquick5* libkf5pulseaudioqt2* libkf5purpose-bin* libkf5purpose5*
  libkf5quickaddons5* libkf5service-bin* libkf5service-data* libkf5service5*
  libkf5solid5* libkf5solid5-data* libkf5sonnet5-data* libkf5sonnetcore5*
  libkf5sonnetui5* libkf5style5* libkf5syndication5abi1*
  libkf5syntaxhighlighting-data* libkf5syntaxhighlighting5*
  libkf5texteditor-bin* libkf5texteditor5* libkf5textwidgets-data*
  libkf5textwidgets5* libkf5wallet-bin* libkf5wallet-data* libkf5wallet5*
  libkf5waylandclient5* libkf5widgetsaddons-data* libkf5widgetsaddons5*
  libkf5windowsystem-data* libkf5windowsystem5* libkf5xmlgui-bin*
  libkf5xmlgui-data* libkf5xmlgui5* libkmlbase1* libkmldom1* libkmlengine1*
  libkpathsea6* libkwalletbackend5-5* liblangtag-common* liblangtag1*
  liblept5* liblilv-0-0* liblirc-client0* libllvm11* libllvm12*
  liblog-dispatch-perl* liblog-log4perl-perl* liblouis-data* liblouis20*
  liblouisutdml-bin* liblouisutdml-data* liblouisutdml9* liblqr-1-0* libltc11*
  liblua5.3-0* liblvm2cmd2.03* liblzf1* libmagickcore-6.q16-6*
  libmagickcore-6.q16-6-extra* libmagickwand-6.q16-6* libmail-sendmail-perl*
  libmanette-0.2-0* libmaxminddb0* libmbedcrypto3* libmbedtls12*
  libmbedx509-0* libmbim-glib4* libmbim-proxy* libmd4c0* libmediaart-2.0-0*
  libmessaging-menu0* libmfx1* libmhash2* libmime-charset-perl*
  libmime-lite-perl* libmime-types-perl* libminiupnpc17* libminizip1*
  libmjpegutils-2.1-0* libmlt++3* libmlt-data* libmlt6* libmms0* libmng2*
  libmodplug1* libmodule-pluggable-perl* libmotif-common* libmovit8*
  libmozjs-78-0* libmpcdec6* libmpeg2encpp-2.1-0* libmpg123-0*
  libmplex2-2.1-0* libmspub-0.1-1* libmtdev-dev* libmtdev1* libmtp-common*
  libmtp-runtime* libmtp9* libmuffin0* libmutter-8-0* libmwaw-0.3-3*
  libmysofa1* libmysqlclient21* libmythes-1.2-0* libnatpmp1*
  libnautilus-extension-dev* libnautilus-extension1a* libnemo-extension1*
  libneon27-gnutls* libnetcdf18* libnetpbm10* libnfs13* libnice10*
  libnma-common* libnma0* libnorm1* libnotify-bin* libnotify4* libnss-mdns*
  libnvidia-cfg1-510* libnvidia-compute-510* libnvidia-decode-510*
  libnvidia-egl-wayland1* libnvidia-encode-510* libnvidia-extra-510*
  libnvidia-fbc1-510* libnvidia-gl-510* libodbc1* libodfgen-0.1-1* libofa0*
  libogdi4.1* libopencolorio1v5* libopencv-calib3d4.5* libopencv-contrib4.5*
  libopencv-core4.5* libopencv-dnn4.5* libopencv-features2d4.5*
  libopencv-flann4.5* libopencv-highgui4.5* libopencv-imgcodecs4.5*
  libopencv-imgproc4.5* libopencv-ml4.5* libopencv-objdetect4.5*
  libopencv-video4.5* libopencv-videoio4.5* libopenexr25* libopengl-dev*
  libopengl-perl* libopengl0* libopenmpt0* libopenni2-0* liborcus-0.16-0*
  liborcus-parser-0.16-0* libosmesa6* libpackagekit-glib2-18*
  libpagemaker-0.0-0* libpango1.0-dev* libpangomm-1.4-1v5* libpangoxft-1.0-0*
  libparams-validationcompiler-perl* libpciaccess-dev* libpciaccess0*
  libpdfbox-java* libpeas-1.0-0* libpeas-common* libperl4-corelibs-perl*
  libpgm-5.3-0* libphonenumber8* libpipewire-0.3-0* libpipewire-0.3-common*
  libpipewire-0.3-modules* libpixman-1-dev* libpkcs11-helper1* libpng-dev*
  libpng-tools* libpolkit-qt5-1-1* libpoppler-glib8* libpoppler-qt5-1*
  libpostproc55* libpq5* libproj19* libprotobuf23* libpsl-dev* libptexenc1*
  libpulsedsp* libqca-qt5-2* libqca-qt5-2-plugins* libqhull8.0* libqmi-glib5*
  libqmi-proxy* libqqwing2v5* libqt5concurrent5* libqt5core5a* libqt5dbus5*
  libqt5designer5* libqt5designercomponents5* libqt5gui5* libqt5help5*
  libqt5multimedia5* libqt5multimedia5-plugins* libqt5multimediagsttools5*
  libqt5multimediaquick5* libqt5multimediawidgets5* libqt5network5*
  libqt5networkauth5* libqt5opengl5* libqt5positioning5* libqt5printsupport5*
  libqt5qml5* libqt5qmlmodels5* libqt5qmlworkerscript5* libqt5quick5-gles*
  libqt5quickcontrols2-5* libqt5quickparticles5* libqt5quicktemplates2-5*
  libqt5quickwidgets5* libqt5script5* libqt5sensors5* libqt5sql5*
  libqt5sql5-sqlite* libqt5svg5* libqt5svg5-dev* libqt5test5*
  libqt5texttospeech5* libqt5waylandclient5* libqt5waylandcompositor5*
  libqt5webchannel5* libqt5webengine-data* libqt5webengine5*
  libqt5webenginecore5* libqt5webkit5* libqt5widgets5* libqt5x11extras5*
  libqt5xml5* libquazip5-1* libquicktime2* librabbitmq4* libraptor2-0*
  librasqal3* libraw1394-11* libraw20* librdf0* libre2-9*
  libreoffice-base-core* libreoffice-calc* libreoffice-common*
  libreoffice-core* libreoffice-draw* libreoffice-gnome* libreoffice-gtk3*
  libreoffice-help-common* libreoffice-help-en-gb* libreoffice-help-en-us*
  libreoffice-help-fr* libreoffice-impress* libreoffice-l10n-en-gb*
  libreoffice-l10n-en-za* libreoffice-l10n-fr* libreoffice-math*
  libreoffice-ogltrans* libreoffice-pdfimport* libreoffice-style-elementary*
  libreoffice-style-yaru* libreoffice-writer* librest-0.7-0* librevenge-0.0-0*
  librhash0* librhythmbox-core10* librsvg2-2* librsvg2-bin* librsvg2-common*
  librsync2* librtaudio6* librttopo1* librubberband2* libruby2.7*
  librygel-core-2.6-2* librygel-db-2.6-2* librygel-renderer-2.6-2*
  librygel-server-2.6-2* libsane-common* libsane-hpaio* libsane1* libsbc1*
  libsdl1.2-dev* libsdl2-dev* libseccomp-dev* libserd-0-0* libsgutils2-2*
  libshine3* libshout3* libsigc++-2.0-0v5* libsignon-plugins-common1*
  libsignon-qt5-1* libslang2-dev* libsmbclient* libsmbios-c2* libsnapd-glib1*
  libsnappy1v5* libsndio-dev* libsnmp-base* libsnmp40* libsocket++1*
  libsodium23* libsombok3* libsord-0-0* libsoundtouch1* libsoup-gnome2.4-1*
  libsoup2.4-1* libsoup2.4-dev* libsource-highlight-common*
  libsource-highlight4v5* libsox-fmt-alsa* libsox-fmt-base* libsox3* libsoxr0*
  libspa-0.2-modules* libspandsp2* libspatialite7* libspecio-perl*
  libspectre1* libspeex1* libspeexdsp1* libsqlite3-dev* libsquashfuse0*
  libsratom-0-0* libsrt1.4-gnutls* libsrtp2-1* libssh-gcrypt-4* libssh2-1*
  libstartup-notification0* libstb0* libstemmer0d* libsub-override-perl*
  libsuitesparseconfig5* libsuperlu5* libswresample3* libswscale5*
  libsynctex2* libsys-hostname-long-perl* libsysmetrics1* libsz2* libtag1v5*
  libtag1v5-vanilla* libteckit0* libtesseract4* libtexlua53* libtexluajit2*
  libthai-dev* libtiff-dev* libtiff5-dev* libtiffxx5* libtimezonemap-data*
  libtimezonemap1* libtinyxml2.6.2v5* libtotem-plparser-common*
  libtotem-plparser18* libtotem0* libtracker-sparql-3.0-0*
  libtss2-esys-3.0.2-0* libtss2-mu0* libtss2-sys1* libtss2-tcti-cmd0*
  libtss2-tcti-device0* libtss2-tcti-mssim0* libtss2-tcti-swtpm0* libtwolame0*
  libudev-dev* libudfread0* libunicode-linebreak-perl*
  libunity-protocol-private0* libunity-scopes-json-def-desktop* libunity9*
  libuno-cppu3* libuno-cppuhelpergcc3-3* libuno-purpenvhelpergcc3-3*
  libuno-sal3* libuno-salhelpergcc3-3* liburiparser1* libuv1* libv4l-0*
  libv4lconvert0* libva-drm2* libva-wayland2* libva-x11-2* libva2* libvdpau1*
  libvidstab1.1* libvisio-0.1-1* libvkd3d1* libvo-aacenc0* libvo-amrwbenc0*
  libvoikko1* libvorbisidec1* libvpx6* libvte-2.91-0* libvte-2.91-common*
  libvulkan-dev* libvulkan1* libwacom-bin* libwacom-common* libwacom-dev*
  libwacom2* libwavpack1* libwayland-bin* libwayland-dev* libwbclient0*
  libwebcam0* libwebkit2gtk-4.0-37* libwebpdemux2* libwebpmux3*
  libwebrtc-audio-processing1* libwhoopsie-preferences0* libwildmidi2*
  libwine* libwinpr2-2* libwmf0.2-7* libwmf0.2-7-gtk* libwnck-3-0*
  libwnck-3-common* libwoff1* libwpd-0.10-10* libwpg-0.3-3* libwps-0.4-4*
  libwx-glcanvas-perl* libwx-perl* libwxbase3.0-dev*
  libwxgtk-media3.0-gtk3-0v5* libwxgtk-media3.0-gtk3-dev*
  libwxgtk3.0-gtk3-0v5* libwxgtk3.0-gtk3-dev* libx86emu3* libxapp1*
  libxatracker2* libxcb-composite0* libxcb-damage0* libxcb-glx0*
  libxcb-icccm4* libxcb-image0* libxcb-keysyms1* libxcb-randr0*
  libxcb-render-util0* libxcb-render0-dev* libxcb-res0* libxcb-shape0*
  libxcb-shm0-dev* libxcb-util1* libxcb-xinerama0* libxcb-xinput0*
  libxcb-xkb1* libxcb-xv0* libxcomposite-dev* libxcomposite1* libxcursor-dev*
  libxdamage-dev* libxerces-c3.2* libxfixes-dev* libxfont2* libxft-dev*
  libxi-dev* libxinerama-dev* libxkbcommon-dev* libxkbcommon-x11-0*
  libxkbfile1* libxkbregistry-dev* libxkbregistry0* libxklavier16* libxm4*
  libxml++2.6-2v5* libxml2* libxml2-dev* libxml2-utils* libxmlb1* libxmlsec1*
  libxmlsec1-nss* libxnvctrl0* libxrandr-dev* libxrender-dev* libxres1*
  libxslt1.1* libxss-dev* libxstring-perl* libxtst-dev* libxv-dev* libxv1*
  libxvidcore4* libxvmc1* libxxf86dga1* libxxf86vm-dev* libyajl2*
  libyaml-cpp0.6* libyaml-tiny-perl* libyelp0* libzbar0* libzimg2* libzip4*
  libzmq5* libzvbi-common* libzvbi0* libzzip-0-13* lmodern* lp-solve* lvm2*
  lyx* lyx-common* media-player-info* melt* mesa-utils* mesa-va-drivers*
  mesa-vdpau-drivers* mesa-vulkan-drivers* metacity-common*
  mobile-broadband-provider-info* mousetweaks* mplayer* muffin* muffin-common*
  mutter* mutter-common* mysql-common* nautilus* nautilus-data*
  nautilus-extension-brasero* nautilus-extension-gnome-terminal*
  nautilus-share* nemo* nemo-data* nemo-fileroller* netpbm*
  network-manager-gnome* network-manager-openvpn*
  network-manager-openvpn-gnome* network-manager-pptp-gnome*
  nvidia-compute-utils-510* nvidia-dkms-510* nvidia-driver-510*
  nvidia-kernel-common-510* nvidia-kernel-source-510* nvidia-prime*
  nvidia-settings* nvidia-utils-510* ocl-icd-libopencl1* odbcinst*
  odbcinst1debian2* openjdk-11-jdk* openjdk-11-jdk-headless* openjdk-11-jre*
  openjdk-11-jre-headless* openjdk-8-jre* openjdk-8-jre-headless* openvpn*
  orca* oxygen-icon-theme* p11-kit* p11-kit-modules* packagekit*
  packagekit-tools* pango1.0-tools* parsec* pia* pinentry-gnome3* pipewire*
  pipewire-bin* pipewire-media-session* plasma-framework* po-debconf*
  policykit-1-gnome* power-profiles-daemon* preview-latex-style*
  printer-driver-hpcups* printer-driver-postscript-hp* printer-driver-splix*
  proj-bin* proj-data* ps2eps* pulseaudio* pulseaudio-module-bluetooth*
  pulseaudio-module-jack* pulseaudio-utils* putty* putty-tools*
  python-babel-localedata* python-tinycss2-common* python3-agate*
  python3-agatedbf* python3-agateexcel* python3-agatesql* python3-apport*
  python3-aptdaemon* python3-aptdaemon.gtk3widgets* python3-babel*
  python3-bcrypt* python3-brlapi* python3-bs4* python3-cairo* python3-certifi*
  python3-chardet* python3-cson* python3-csvkit* python3-cups*
  python3-cupshelpers* python3-dateutil* python3-dbfread* python3-debconf*
  python3-debian* python3-defer* python3-et-xmlfile* python3-fasteners*
  python3-future* python3-getdevinfo* python3-gi-cairo* python3-html5lib*
  python3-ibus-1.0* python3-icu* python3-idna* python3-isodate* python3-jdcal*
  python3-ldb* python3-leather* python3-lockfile* python3-louis* python3-lxml*
  python3-macaroonbakery* python3-monotonic* python3-nacl* python3-olefile*
  python3-openpyxl* python3-pampy* python3-paramiko* python3-parsedatetime*
  python3-pil* python3-problem-report* python3-protobuf* python3-psutil*
  python3-pyatspi* python3-pyinotify* python3-pymacaroons* python3-pyqt5*
  python3-pyqt5.qtsvg* python3-pyqt5.sip* python3-pytimeparse*
  python3-renderpm* python3-reportlab* python3-reportlab-accel*
  python3-requests* python3-rfc3339* python3-setproctitle* python3-sip*
  python3-slugify* python3-software-properties* python3-soupsieve*
  python3-speechd* python3-speg* python3-sqlalchemy* python3-sqlalchemy-ext*
  python3-systemd* python3-talloc* python3-tinycss* python3-tinycss2*
  python3-tz* python3-unidecode* python3-uno* python3-urllib3*
  python3-webencodings* python3-wxgtk4.0* python3-xapp* python3-xdg*
  python3-xlib* python3-xlrd* qdoc-qt5* qhelpgenerator-qt5* qjackctl*
  qml-module-org-kde-bluezqt* qml-module-org-kde-kconfig*
  qml-module-org-kde-kirigami2* qml-module-org-kde-kquickcontrols*
  qml-module-org-kde-kquickcontrolsaddons* qml-module-org-kde-newstuff*
  qml-module-org-kde-people* qml-module-org-kde-purpose*
  qml-module-org-kde-qqc2desktopstyle* qml-module-qt-labs-folderlistmodel*
  qml-module-qt-labs-platform* qml-module-qt-labs-settings*
  qml-module-qtgraphicaleffects* qml-module-qtmultimedia* qml-module-qtqml*
  qml-module-qtqml-models2* qml-module-qtquick-controls*
  qml-module-qtquick-controls2* qml-module-qtquick-dialogs*
  qml-module-qtquick-layouts* qml-module-qtquick-particles2*
  qml-module-qtquick-privatewidgets* qml-module-qtquick-templates2*
  qml-module-qtquick-window2* qml-module-qtquick2* qml-module-qtwebengine*
  qml-module-ubuntu-onlineaccounts* qt5-assistant* qt5-gtk-platformtheme*
  qtattributionsscanner-qt5* qtchooser* qtspeech5-speechd-plugin*
  qttools5-dev-tools* qttranslations5-l10n* qtwayland5* rake* recordmydesktop*
  remmina* remmina-common* remmina-plugin-rdp* remmina-plugin-secret*
  remmina-plugin-vnc* rhythmbox* rhythmbox-data*
  rhythmbox-plugin-alternative-toolbar* rhythmbox-plugins* rtkit* ruby*
  ruby-minitest* ruby-net-telnet* ruby-power-assert* ruby-rubygems*
  ruby-test-unit* ruby-xmlrpc* ruby2.7* rubygems-integration* rygel*
  samba-libs* sane-airscan* sane-utils* scantv* screen-resolution-extra*
  seahorse* session-migration* sgml-data* shared-mime-info* shotwell*
  shotwell-common* signon-plugin-oauth2* simple-scan*
  software-properties-common* software-properties-gtk* sonnet-plugins*
  spice-vdagent* sshfs* ssl-cert* sssd* sssd-ad* sssd-ad-common* sssd-ipa*
  steam-launcher* steam-libs-amd64* swh-plugins* switcheroo-control*
  system-config-printer* system-config-printer-common*
  system-config-printer-udev* t1utils* tex-common* tex-gyre* texlive-base*
  texlive-binaries* texlive-extra-utils* texlive-font-utils*
  texlive-fonts-recommended* texlive-lang-greek* texlive-latex-base*
  texlive-latex-extra* texlive-latex-recommended* texlive-luatex*
  texlive-pictures* texlive-plain-generic* texlive-pstricks* texlive-science*
  texstudio* texstudio-doc* texstudio-l10n* thermald* thin-provisioning-tools*
  thunderbird* thunderbird-gnome-support* thunderbird-locale-en*
  thunderbird-locale-en-gb* thunderbird-locale-en-us* thunderbird-locale-fr*
  tipa* totem* totem-common* totem-plugins* tpm-udev* tracker*
  tracker-extract* tracker-miner-fs* transmission-common* transmission-gtk*
  tree* ubuntu-desktop* ubuntu-desktop-minimal* ubuntu-docs* ubuntu-mono*
  ubuntu-release-upgrader-gtk* ubuntu-session* ubuntu-standard* umbrello*
  unattended-upgrades* uno-libs-private* update-manager* update-notifier*
  update-notifier-common* ure* usb-creator-common* usb-creator-gtk*
  uvcdynctrl* uvcdynctrl-data* v4l-conf* va-driver-all* vdpau-driver-all*
  virtualbox* virtualbox-dkms* virtualbox-qt* vorbis-tools* wavpack*
  wayland-protocols* whoopsie-preferences* wine* wine64* wodim* wx3.0-headers*
  x11-apps* x11-session-utils* x11-utils* x11-xkb-utils* x11proto-input-dev*
  x11proto-randr-dev* x11proto-record-dev* x11proto-scrnsaver-dev*
  x11proto-xf86vidmode-dev* x11proto-xinerama-dev* xapps-common* xawtv*
  xawtv-plugins* xbitmaps* xbrlapi* xdg-dbus-proxy* xdg-desktop-portal*
  xdg-desktop-portal-gtk* xdg-user-dirs-gtk* xfonts-base* xfonts-encodings*
  xfonts-scalable* xfonts-utils* xinit* xinput* xml-core* xorg* xsensors*
  xserver-common* xserver-xephyr* xserver-xorg* xserver-xorg-core*
  xserver-xorg-input-all* xserver-xorg-input-libinput*
  xserver-xorg-input-wacom* xserver-xorg-legacy* xserver-xorg-video-all*
  xserver-xorg-video-amdgpu* xserver-xorg-video-ati* xserver-xorg-video-fbdev*
  xserver-xorg-video-intel* xserver-xorg-video-nouveau*
  xserver-xorg-video-nvidia-510* xserver-xorg-video-qxl*
  xserver-xorg-video-radeon* xserver-xorg-video-vesa*
  xserver-xorg-video-vmware* xsltproc* xwayland* yaru-theme-gtk* yelp*
  yelp-xsl* zenity* zenity-common*
0 upgraded, 0 newly installed, 1656 to remove and 0 not upgraded.
After this operation, 6’897 MB disk space will be freed.
Do you want to continue? [Y/n] Abort.
```

---

### Post by #&amp;thj^% on 2022-08-03
Go for it, you wanted to learn right?
let me know when you feel uncomfortable, this is a very nuclear approach. :) Not the Norm or a well advised suggestion. (Meant for on lookers)
A bit about me, I hate just hate defeat, plus i do a lot of OS testing. 
Report back any uncertain-ices.
```
$ systemctl --user status gnome-terminal-server.service
\u25cf gnome-terminal-server.service - GNOME Terminal Server
     Loaded: loaded (/usr/lib/systemd/user/gnome-terminal-server.service; stati>
     Active: active (running) since Wed 2022-08-03 15:50:36 MDT; 43s ago
   Main PID: 18709 (gnome-terminal-)
      Tasks: 4 (limit: 4600)
     Memory: 18.3M
        CPU: 386ms
     CGroup: /user.slice/user-1000.slice/user@1000.service/app.slice/app-org.gn>
             \u2514\u250018709 /usr/libexec/gnome-terminal-server

```

---

### Post by kilrah757 on 2022-08-03
Went for it, it killed the GUI almost instantly, went to raw terminal and looked at htop to see when it was done and started a do-release-upgrade from there without a reboot. Running now, will see what we get at the end...

---

### Post by #&amp;thj^% on 2022-08-03
> **kilrah757 said:**
> Went for it, it killed the GUI almost instantly, went to raw terminal and looked at htop to see when it was done and started a do-release-upgrade from there without a reboot. Running now, will see what we get at the end...
Don't be shy >> Report back any uncertain-ices.
You'll be asked some *very important choices going forward.
When you finally reach your desktop well just look at the screen shots

---

### Post by kilrah757 on 2022-08-03
So, booted back but the entire GUI was removed when getting rid of libicu, not even an X server left. 

Installed gdm3, nautilus, the gnome-shell-extensions etc, software-properties that was gone as well, and back to pretty much normal. Then installed gnome-terminal, aaaand would you know it...

```
[COLOR=#000000][FONT=&amp]/usr/bin/gnome-terminal.real: error while loading shared libraries: libicuuc.so.67: cannot open shared object file: No such file or directory[/FONT][/COLOR]
```

---

### Post by #&amp;thj^% on 2022-08-03
I wish you would have stopped  and asked, that was all wrong. :(
This is just impossible>>"error while loading shared libraries: libicuuc.so.67:"
My first try without removing first "error while loading shared libraries: libicuuc.so.67:" was the same, my second effort is how I show in this thread and my post #37

I have to leave for the evening, hope to pick this back up tomorrow.

---

### Post by kilrah757 on 2022-08-04
Can always start over, I'll just restore the image

---

### Post by kilrah757 on 2022-08-04
Ran the upgrade again and this time looked at the list of obsolete things it would autoremove at the end, that included libicu67 so I didn't go with the autoremove. But it seems now gnome-terminal-server has disappeared...

```
testuser@2110thatbreaks:/usr/lib/x86_64-linux-gnu$ gnome-terminal
# Error constructing proxy for org.gnome.Terminal:/org/gnome/Terminal/Factory0: Error calling StartServiceByName for org.gnome.Terminal: Timeout was reached
testuser@2110thatbreaks:/usr/lib/x86_64-linux-gnu$ sudo systemctl start gnome-terminal-server
Failed to start gnome-terminal-server.service: Unit gnome-terminal-server.service not found.


```

---

### Post by #&amp;thj^% on 2022-08-04
:)
Still wrong, dump it all, *everything*, so you don't have a  ghost that won't give up. ( libicu67 )
meaning there are for some reason some .configs that remain with the upgrade.
One more time on the restore, (practice makes perfect ;)>)
**Remove everything as I keep saying, >>>All, from the start of the 6.8gigs you show, and then later it will ask to remove another 45 or so more packages.**
Don't worry over being stuck in terminal, we will install "ubuntu-desktop" after you at least get to this point.

---

### Post by ActionParsnip on 2022-08-04
What is the output of:
```

sudo updatedb
locate libicuuc.so*

```
Thanks

---

### Post by kilrah757 on 2022-08-04
> **1fallen said:**
> 
**Remove everything as I keep saying, >>>All, from the start of the 6.8gigs you show, and then later it will ask to remove another 45 or so more packages.**

That's what I did yesterday!

---

### Post by kilrah757 on 2022-08-04
> **ActionParsnip said:**
> What is the output of:
```

sudo updatedb
locate libicuuc.so*

```
Thanks
Nothing

---

### Post by #&amp;thj^% on 2022-08-04
Did you install 
```
sudo apt install ubuntu-desktop
```

---

### Post by #&amp;thj^% on 2022-08-04
Did you install 
```
sudo apt install ubuntu-desktop
```
> **kilrah757 said:**
> That's what I did yesterday!

I know but it brought back an unwelcomed  guest along>>" libicuuc.so.67"
And you started installing the wrong Items IE:
> Installed gdm3, nautilus, the gnome-shell-extensions etc, software-properties 
When installing  ubuntu-desktop bring all you need in, and overwrites everything, for a clean install.

---

### Post by kilrah757 on 2022-08-04
> **1fallen said:**
> Did you install 
```
sudo apt install ubuntu-desktop
```
No, had installed gdm3 etc (mentioned in previous post) separately since I didn't know of the global package.

Nuked that install so have to start over. But I've got a minimal image I can easily duplicate now instead of restoring the full physical drive so easier. Can send it if you want to have a go.

So:
```
[COLOR=#000000][FONT=&quot]apt autoremove --purge libicu67[/FONT][/COLOR]
```
```
do-release-upgrade
```
```
apt install ubuntu-desktop
```

right?

---

### Post by #&amp;thj^% on 2022-08-04
Yeppers :D

---

### Post by kilrah757 on 2022-08-04
Same as last night...

---

### Post by #&amp;thj^% on 2022-08-04
To me that's utterly impossible.....
I've tried three more times, and before removing "libicu67" on my upgrade to 22.04, I saw/confirm what you report:
```
error while loading shared libraries: libicuuc.so.67
```
Destroyed that install, and from a new 21.10 install, proceeded with the above suggestions and perfect, everything just works.
I did have to clean-up my sources.list though.
Now It's time to move to downloading 20.04LTS or 22.04LTS and wipe your current OS meaning format it.
First back-up all you want from current OS, but don't include Directories like .config or .cache, they may interfere.

---

### Post by kilrah757 on 2022-08-04
I know it makes no sense...

After reinstalling ubuntu-desktop, comparing to a clean install gnome-terminal.real both have the same md5, but an ldd -v on both results in something different, the updated one does link to .68 while the clean install properly links to .70...

Argh forum doesn't want attachments this size...

Clean install: [https://snip.kilrah.xyz/?e52bfecb3e06300e#4KYyrBkkXNtbVAcVQ6X5adGxL7uPAM3MNYrS4niXhYzi](https://snip.kilrah.xyz/?e52bfecb3e06300e#4KYyrBkkXNtbVAcVQ6X5adGxL7uPAM3MNYrS4niXhYzi)
Updated: [https://snip.kilrah.xyz/?dc1308eeb22c942e#GTayHogzu6ETZq6H5MS9f39UgXTqcE9Do7BrsL1cTTGy](https://snip.kilrah.xyz/?dc1308eeb22c942e#GTayHogzu6ETZq6H5MS9f39UgXTqcE9Do7BrsL1cTTGy)

---

### Post by Impavidus on 2022-08-04
This is a very long thread with 90% of the posts by just 2 people, leading to a risk of tunnel vision. And very few people who are now willing to read all of it.

Actually, I decided to have a look and read most of the thread. Your last post actually tells what's going on. Maybe I'm not the person who should take the credits though.

Your upgraded version uses```
libvte-2.91.so.0 => /usr/local/lib/x86_64-linux-gnu/libvte-2.91.so.0 (0x00007f6d69eb5000)
```It's in /usr/local, so this library must be manually installed and therefore wasn't upgraded during the release upgrade. libvte depends on libicu, which is why your upgraded version still depended on the old libicu. So, yeah, keep track of manually installed stuff.

---

### Post by #&amp;thj^% on 2022-08-04
> **Impavidus said:**
> This is a very long thread with 90% of the posts by just 2 people, leading to a risk of tunnel vision. And very few people who are now willing to read all of it.

Actually, I decided to have a look and read most of the thread. Your last post actually tells what's going on. Maybe I'm not the person who should take the credits though.

Your upgraded version uses```
libvte-2.91.so.0 => /usr/local/lib/x86_64-linux-gnu/libvte-2.91.so.0 (0x00007f6d69eb5000)
```It's in /usr/local, so this library must be manually installed and therefore wasn't upgraded during the release upgrade. libvte depends on libicu, which is why your upgraded version still depended on the old libicu. So, yeah, keep track of manually installed stuff.

+1 I just had a chance to go through all OP's text files
Nice catch Impavidus, and also a big heads-up this thread should not be followed for anyone else besides the OP
So>>> YOU ALL HAVE BEEN WARNED... and I have mentioned that in other post's in this thread now.

---

### Post by kilrah757 on 2022-08-04
Welp, bingo... It didn't actually prevent the upgrade but was just taken first in the chain, on the broken updated install simply removing [COLOR=#000000][FONT=&amp]/usr/local/lib/x86_64-linux-gnu/[/FONT][/COLOR]libvte* fixed everything straight away.

It's 2.91 like in the ubuntu package for jammy though, so just so I understand what causes it to keep a link to the old libicu? Just the fact that this was the version when it was built, whenver that was?
 
Thanks anyway, gonna update the actual install now and it should be all good!

---

### Post by Impavidus on 2022-08-04
When you compiled and linked libvte, it was linked to the version of libicu that was then installed. If you want to continue using a manually compiled libvte, you have to relink it. Recompiling may be necessary, but certainly relinking. But I suppose you just installed libvte 2.91 to get a newer version, which is no longer needed as you're now on Ubuntu 22.04, which has that version by default.

---

### Post by #&amp;thj^% on 2022-08-04
> **Impavidus said:**
> When you compiled and linked libvte, it was linked to the version of libicu that was then installed. If you want to continue using a manually compiled libvte, you have to relink it. Recompiling may be necessary, but certainly relinking. But I suppose you just installed libvte 2.91 to get a newer version, which is no longer needed as you're now on Ubuntu 22.04, which has that version by default.

Again spot on, in my very tunneled view, and after going over the dist-upgrade log I saw where this was installed and over written " libvte" but I had to give it permission or allow the change.
So maybe the kind reminder from you over the fact I was very focused in the wrong area was needed. ;)

---

