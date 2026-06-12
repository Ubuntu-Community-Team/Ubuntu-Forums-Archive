---
title: "xserver-xorg is not installing."
date: 2009-09-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Sslaxx on 2009-09-28
```
stuart@sslaxxworks:~$ sudo dpkg -i --force-all /var/cache/apt/archives/xserver-xorg_1%3a7.4+3ubuntu5_i386.deb 
(Reading database ... 283024 files and directories currently installed.)
Preparing to replace xserver-xorg 1:7.4+3ubuntu5 (using .../xserver-xorg_1%3a7.4+3ubuntu5_i386.deb) ...
Unpacking replacement xserver-xorg ...
Setting up xserver-xorg (1:7.4+3ubuntu5) ...
restart: Unknown instance: 
invoke-rc.d: initscript hal, action "restart" failed.
dpkg: error processing xserver-xorg (--install):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for hal ...
Regenerating hal fdi cache ...
restart: Unknown instance: 
Processing triggers for man-db ...
Errors were encountered while processing:
 xserver-xorg
```

I doubt it'd be safe to restart my machine while this problem exists. Anyone else encountered this? Any suggestions for a workaround?

---

### Post by LowSky on 2009-09-28
what wrong with using the normal method of ```
sudo apt-get update && sudo apt-get up ugrade
```?

---

### Post by Sslaxx on 2009-09-28
> **LowSky said:**
> what wrong with using the normal method of ```
sudo apt-get update && sudo apt-get up ugrade
```?
Because I had, you know, *already tried that*?

---

### Post by grturner on 2009-09-28
did you try
```
sudo dpkg-reconfigure -pigh xserver-xorg
```
and then running the update?

---

### Post by dinxter on 2009-09-28
looks like the postinst script is failing to restart hal because hal isnt running, try
$sudo start hal
before installing, are your 'forcing all' for a reason by the way?

---

### Post by Sslaxx on 2009-09-28
> **grturner said:**
> did you try
```
sudo dpkg-reconfigure -pigh xserver-xorg
```
and then running the update?
Returns this:
```
stuart@sslaxxworks:~$ sudo dpkg-reconfigure -phigh xserver-xorg
/usr/sbin/dpkg-reconfigure: xserver-xorg is broken or not fully installed.
```

Oh, and I did try to ensure HAL was running beforehand, makes no difference to the error. Using --force-all to try and force it to install after all else had failed.

---

### Post by dinxter on 2009-09-28
doh, looked like a hal/upstart thing, you might get a bit more info if you add 'set -x' to 
/var/lib/dpkg/info/xserver-xorg.postinst 
before running 'dpkg --configure -a' and then see if that shines any light on it

---

### Post by Sslaxx on 2009-09-28
This is what it comes up with:

```
+ . /usr/share/debconf/confmodule
+ [ !  ]
+ PERL_DL_NONLAZY=1
+ export PERL_DL_NONLAZY
+ [  ]
+ exec /usr/share/debconf/frontend /var/lib/dpkg/info/xserver-xorg.postinst configure 1:7.4~5ubuntu18
+ . /usr/share/debconf/confmodule
+ [ ! 1 ]
+ [ -z  ]
+ exec
+ [  ]
+ exec
+ DEBCONF_REDIR=1
+ export DEBCONF_REDIR
+ THIS_PACKAGE=xserver-xorg
+ THIS_SCRIPT=postinst
+ SOURCE_VERSION=1:7.4+3ubuntu5
+ OFFICIAL_BUILD=
+ SHELL_LIB_INTERNAL_ERROR=86
+ SHELL_LIB_THROWN_ERROR=74
+ SHELL_LIB_USAGE_ERROR=99
+ [ -z  ]
+ [ -n  ]
+ [ -z  ]
+ [ -n  ]
+ [ -z xserver-xorg ]
+ [ -z postinst ]
+ [ configure = reconfigure ]
+ [ -n  ]
+ RECONFIGURE=
+ [ configure = install ]
+ [ configure = configure ]
+ [ -z 1:7.4~5ubuntu18 ]
+ [ -z  ]
+ [ -z  ]
+ UPGRADE=yes
+ trap message;      message "Received signal.  Aborting xserver-xorg package postinst script.";      message;      exit 1 HUP INT QUIT TERM
+ stty size
+ awk {print $2}
+ DEFCOLUMNS=
+ expr  : [[:digit:]]\+$
+ DEFCOLUMNS=80
+ [ -e /etc/default/xorg ]
+ CONFIG_DIR=/etc/X11
+ CONFIG_AUX_DIR=/var/lib/x11
+ SERVER_SYMLINK=/etc/X11/X
+ XORGCONFIG=/etc/X11/xorg.conf
+ CONFIG_AUX_DIR=/var/lib/x11
+ SERVER_SYMLINK_CHECKSUM=/var/lib/x11/X.md5sum
+ SERVER_SYMLINK_ROSTER=/var/lib/x11/X.roster
+ XORGCONFIG_CHECKSUM=/var/lib/x11/xorg.conf.md5sum
+ XORGCONFIG_ROSTER=/var/lib/x11/xorg.conf.roster
+ THIS_SERVER=/usr/bin/Xorg
+ debug_echo Configuring xserver-xorg.
+ [ -n  ]
+ [  = user ]
+ [  = .* ]
+ [ -e /etc/X11/X ]
+ readlink /etc/X11/X
+ [ /usr/bin/Xorg = /bin/true ]
+ [ -n yes ]
+ dpkg --compare-versions 1:7.4~5ubuntu18 le 1:7.3+5
+ dpkg --compare-versions 1:7.4~5ubuntu18 lt-nl 1:7.4
+ db_unregister xserver-xorg/config/null_string_error
+ _db_cmd UNREGISTER xserver-xorg/config/null_string_error
+ IFS=  printf %s\n UNREGISTER xserver-xorg/config/null_string_error
+ IFS=
 read -r _db_internal_line
+ RET=10 xserver-xorg/config/null_string_error doesn't exist
+ return 10
+ true
+ db_unregister xserver-xorg/config/doublequote_in_string_error
+ _db_cmd UNREGISTER xserver-xorg/config/doublequote_in_string_error
+ IFS=  printf %s\n UNREGISTER xserver-xorg/config/doublequote_in_string_error
+ IFS=
 read -r _db_internal_line
+ RET=10 xserver-xorg/config/doublequote_in_string_error doesn't exist
+ return 10
+ true
+ db_unregister xserver-xorg/config/nonnumeric_string_error
+ _db_cmd UNREGISTER xserver-xorg/config/nonnumeric_string_error
+ IFS=  printf %s\n UNREGISTER xserver-xorg/config/nonnumeric_string_error
+ IFS=
 read -r _db_internal_line
+ RET=10 xserver-xorg/config/nonnumeric_string_error doesn't exist
+ return 10
+ true
+ db_unregister xserver-xorg/config/device/use_fbdev
+ _db_cmd UNREGISTER xserver-xorg/config/device/use_fbdev
+ IFS=  printf %s\n UNREGISTER xserver-xorg/config/device/use_fbdev
+ IFS=
 read -r _db_internal_line
+ RET=10 xserver-xorg/config/device/use_fbdev doesn't exist
+ return 10
+ true
+ db_unregister xserver-xorg/config/device/driver
+ _db_cmd UNREGISTER xserver-xorg/config/device/driver
+ IFS=  printf %s\n UNREGISTER xserver-xorg/config/device/driver
+ IFS=
 read -r _db_internal_line
+ RET=10 xserver-xorg/config/device/driver doesn't exist
+ return 10
+ true
+ db_unregister xserver-xorg/config/inputdevice/keyboard/rules
+ _db_cmd UNREGISTER xserver-xorg/config/inputdevice/keyboard/rules
+ IFS=  printf %s\n UNREGISTER xserver-xorg/config/inputdevice/keyboard/rules
+ IFS=
 read -r _db_internal_line
+ RET=10 xserver-xorg/config/inputdevice/keyboard/rules doesn't exist
+ return 10
+ true
+ db_unregister xserver-xorg/config/inputdevice/keyboard/model
+ _db_cmd UNREGISTER xserver-xorg/config/inputdevice/keyboard/model
+ IFS=  printf %s\n UNREGISTER xserver-xorg/config/inputdevice/keyboard/model
+ IFS=
 read -r _db_internal_line
+ RET=10 xserver-xorg/config/inputdevice/keyboard/model doesn't exist
+ return 10
+ true
+ db_unregister xserver-xorg/config/inputdevice/keyboard/layout
+ _db_cmd UNREGISTER xserver-xorg/config/inputdevice/keyboard/layout
+ IFS=  printf %s\n UNREGISTER xserver-xorg/config/inputdevice/keyboard/layout
+ IFS=
 read -r _db_internal_line
+ RET=10 xserver-xorg/config/inputdevice/keyboard/layout doesn't exist
+ return 10
+ true
+ db_unregister xserver-xorg/config/inputdevice/keyboard/variant
+ _db_cmd UNREGISTER xserver-xorg/config/inputdevice/keyboard/variant
+ IFS=  printf %s\n UNREGISTER xserver-xorg/config/inputdevice/keyboard/variant
+ IFS=
 read -r _db_internal_line
+ RET=10 xserver-xorg/config/inputdevice/keyboard/variant doesn't exist
+ return 10
+ true
+ db_unregister xserver-xorg/config/inputdevice/keyboard/options
+ _db_cmd UNREGISTER xserver-xorg/config/inputdevice/keyboard/options
+ IFS=  printf %s\n UNREGISTER xserver-xorg/config/inputdevice/keyboard/options
+ IFS=
 read -r _db_internal_line
+ RET=10 xserver-xorg/config/inputdevice/keyboard/options doesn't exist
+ return 10
+ true
+ db_unregister xserver-xorg/autodetect_keyboard
+ _db_cmd UNREGISTER xserver-xorg/autodetect_keyboard
+ IFS=  printf %s\n UNREGISTER xserver-xorg/autodetect_keyboard
+ IFS=
 read -r _db_internal_line
+ RET=10 xserver-xorg/autodetect_keyboard doesn't exist
+ return 10
+ true
+ dpkg --compare-versions 1:7.4~5ubuntu18 lt-nl 1:7.4+2
+ db_unregister xserver-xorg/config/device/bus_id
+ _db_cmd UNREGISTER xserver-xorg/config/device/bus_id
+ IFS=  printf %s\n UNREGISTER xserver-xorg/config/device/bus_id
+ IFS=
 read -r _db_internal_line
+ RET=10 xserver-xorg/config/device/bus_id doesn't exist
+ return 10
+ true
+ db_unregister xserver-xorg/config/device/bus_id_error
+ _db_cmd UNREGISTER xserver-xorg/config/device/bus_id_error
+ IFS=  printf %s\n UNREGISTER xserver-xorg/config/device/bus_id_error
+ IFS=
 read -r _db_internal_line
+ RET=10 xserver-xorg/config/device/bus_id_error doesn't exist
+ return 10
+ true
+ rm -f /var/lib/x11/xorg.conf.roster /var/lib/x11/xorg.conf.md5sum
+ rm -f /var/lib/x11/X.md5sum /var/lib/x11/X.roster
+ dpkg --compare-versions 1:7.4~5ubuntu18 lt-nl 1:7.4~5ubuntu1
+ dpkg --compare-versions 1:7.4~5ubuntu18 lt-nl 1:7.3+11
+ dpkg --compare-versions 1:7.4~5ubuntu18 lt-nl 1:7.3+13
+ dpkg --compare-versions 1:7.4~5ubuntu18 lt 1:7.4
+ invoke-rc.d hal restart
restart: Unknown instance: 
invoke-rc.d: initscript hal, action "restart" failed.
dpkg: error processing xserver-xorg (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 xserver-xorg
```

If nobody else has encountered this, I'll put it on Launchpad.

---

### Post by dinxter on 2009-09-28
i hate to harp on about it, but are you 100% sure about hal, i can get an identical bug to yours if i stop hal, otherwise its fine. 
$ps -e|grep hal
i apologise if i'm telling you stuff you already know/have done :)

---

### Post by Sslaxx on 2009-09-28
> **dinxter said:**
> i hate to harp on about it, but are you 100% sure about hal, i can get an identical bug to yours if i stop hal, otherwise its fine. 
$ps -e|grep hal
i apologise if i'm telling you stuff you already know/have done :)

Before:
```
stuart@sslaxxworks:~$ sudo service hal start
[sudo] password for stuart: 
hal start/running, process 1237
stuart@sslaxxworks:~$ ps -e | grep -i hal
 1575 ?        00:00:00 hald
 1578 ?        00:00:00 hald
 1579 ?        00:00:00 hald-runner
10149 ?        00:00:00 gvfs-hal-volume
```

```
stuart@sslaxxworks:~$ sudo dpkg --configure -a
```
Produces the same as in my prior post.

After:
```
stuart@sslaxxworks:~$ ps -e | grep -i hal
10149 ?        00:00:00 gvfs-hal-volume
```

It's stopping HAL and not restarting it.

---

### Post by dinxter on 2009-09-28
do you get any more info from restarting hal by hand or does that pass without errors
$invoke-rc.d hal restart
or stop hal and try
$hald --verbose=yes

---

### Post by Sslaxx on 2009-09-28
```
stuart@sslaxxworks:~$ sudo hald --verbose=yes
18:40:08.916 [I] hald.c:680: hal 0.5.13
18:40:08.916 [I] hald.c:681: using child timeout 250s
18:40:08.916 [I] hald.c:690: Will daemonize
18:40:08.916 [I] hald.c:691: Becoming a daemon
```

However, *after* running this, I got this when I tried stop on it:```
stuart@sslaxxworks:~$ sudo service hal stop
stop: Unknown instance:
```

The other method returns this:```
stuart@sslaxxworks:~$ sudo invoke-rc.d hal restart
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service hal restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the restart(8) utility, e.g. restart hal
restart: Unknown instance: 
invoke-rc.d: initscript hal, action "restart" failed.
```

sudo service hal stop then returns, perhaps unsurprisingly, the "Unknown instance" error.

---

### Post by dinxter on 2009-09-28
yeah, you need to kill the hald processes manually before 'start hal' , the init system doesnt know about processes outside of its control. dont know whats causing your dpkg failure though

---

### Post by dinxter on 2009-09-28
> **dinxter said:**
> yeah, you need to kill the hald processes manually before 'start hal' , the init system doesnt know about processes outside of its control. dont know whats causing your dpkg failure though
thinking about it, it might be worth a try to manually kill all the running hald processes before starting hal using upstart, since when the package tries to restart it you're left with one running hal process maybe thats the one the init system cant handle and is why configuring xserver-xorg fails

---

### Post by Sslaxx on 2009-09-28
It doesn't matter now, I played the pre-release game and lost. I tried to reboot, lost network connectivity under Ubuntu, everything slowed to treacle, no sound etc. Whilst I doubt that all of that can be pinned on xserver-xorg, I wouldn't be surprised if my HAL woes had bearing on that lot (not to mention problems with NetworkManager having been reported already).

I'd done a dist-upgrade from Jaunty with Medibuntu etc which probably didn't help one bit.

So I'll try a fresh reinstall sans extras like that and see what happens.

---

### Post by dinxter on 2009-09-28
ah well, i know how you feel, my grub has just plummeted and left me with nothing so the evenings dragging on :)

---

### Post by Sslaxx on 2009-09-28
> **dinxter said:**
> ah well, i know how you feel, my grub has just plummeted and left me with nothing so the evenings dragging on :)
Not a loss. I'll just try again! Glad I've got /home as a separate partition! Learnt that one years ago, glad I did.

---

### Post by jbarroso on 2009-09-28
> **Sslaxx said:**
> This is what it comes up with:

```
+ . /usr/share/debconf/confmodule
+ [ !  ]
+ PERL_DL_NONLAZY=1
+ export PERL_DL_NONLAZY
+ [  ]
+ exec /usr/share/debconf/frontend /var/lib/dpkg/info/xserver-xorg.postinst configure 1:7.4~5ubuntu18
+ . /usr/share/debconf/confmodule
+ [ ! 1 ]
+ [ -z  ]
+ exec
+ [  ]
+ exec
+ DEBCONF_REDIR=1
+ export DEBCONF_REDIR
+ THIS_PACKAGE=xserver-xorg
+ THIS_SCRIPT=postinst
+ SOURCE_VERSION=1:7.4+3ubuntu5
+ OFFICIAL_BUILD=
+ SHELL_LIB_INTERNAL_ERROR=86
+ SHELL_LIB_THROWN_ERROR=74
+ SHELL_LIB_USAGE_ERROR=99
+ [ -z  ]
+ [ -n  ]
+ [ -z  ]
+ [ -n  ]
+ [ -z xserver-xorg ]
+ [ -z postinst ]
+ [ configure = reconfigure ]
+ [ -n  ]
+ RECONFIGURE=
+ [ configure = install ]
+ [ configure = configure ]
+ [ -z 1:7.4~5ubuntu18 ]
+ [ -z  ]
+ [ -z  ]
+ UPGRADE=yes
+ trap message;      message "Received signal.  Aborting xserver-xorg package postinst script.";      message;      exit 1 HUP INT QUIT TERM
+ stty size
+ awk {print $2}
+ DEFCOLUMNS=
+ expr  : [[:digit:]]\+$
+ DEFCOLUMNS=80
+ [ -e /etc/default/xorg ]
+ CONFIG_DIR=/etc/X11
+ CONFIG_AUX_DIR=/var/lib/x11
+ SERVER_SYMLINK=/etc/X11/X
+ XORGCONFIG=/etc/X11/xorg.conf
+ CONFIG_AUX_DIR=/var/lib/x11
+ SERVER_SYMLINK_CHECKSUM=/var/lib/x11/X.md5sum
+ SERVER_SYMLINK_ROSTER=/var/lib/x11/X.roster
+ XORGCONFIG_CHECKSUM=/var/lib/x11/xorg.conf.md5sum
+ XORGCONFIG_ROSTER=/var/lib/x11/xorg.conf.roster
+ THIS_SERVER=/usr/bin/Xorg
+ debug_echo Configuring xserver-xorg.
+ [ -n  ]
+ [  = user ]
+ [  = .* ]
+ [ -e /etc/X11/X ]
+ readlink /etc/X11/X
+ [ /usr/bin/Xorg = /bin/true ]
+ [ -n yes ]
+ dpkg --compare-versions 1:7.4~5ubuntu18 le 1:7.3+5
+ dpkg --compare-versions 1:7.4~5ubuntu18 lt-nl 1:7.4
+ db_unregister xserver-xorg/config/null_string_error
+ _db_cmd UNREGISTER xserver-xorg/config/null_string_error
+ IFS=  printf %s\n UNREGISTER xserver-xorg/config/null_string_error
+ IFS=
 read -r _db_internal_line
+ RET=10 xserver-xorg/config/null_string_error doesn't exist
+ return 10
+ true
+ db_unregister xserver-xorg/config/doublequote_in_string_error
+ _db_cmd UNREGISTER xserver-xorg/config/doublequote_in_string_error
+ IFS=  printf %s\n UNREGISTER xserver-xorg/config/doublequote_in_string_error
+ IFS=
 read -r _db_internal_line
+ RET=10 xserver-xorg/config/doublequote_in_string_error doesn't exist
+ return 10
+ true
+ db_unregister xserver-xorg/config/nonnumeric_string_error
+ _db_cmd UNREGISTER xserver-xorg/config/nonnumeric_string_error
+ IFS=  printf %s\n UNREGISTER xserver-xorg/config/nonnumeric_string_error
+ IFS=
 read -r _db_internal_line
+ RET=10 xserver-xorg/config/nonnumeric_string_error doesn't exist
+ return 10
+ true
+ db_unregister xserver-xorg/config/device/use_fbdev
+ _db_cmd UNREGISTER xserver-xorg/config/device/use_fbdev
+ IFS=  printf %s\n UNREGISTER xserver-xorg/config/device/use_fbdev
+ IFS=
 read -r _db_internal_line
+ RET=10 xserver-xorg/config/device/use_fbdev doesn't exist
+ return 10
+ true
+ db_unregister xserver-xorg/config/device/driver
+ _db_cmd UNREGISTER xserver-xorg/config/device/driver
+ IFS=  printf %s\n UNREGISTER xserver-xorg/config/device/driver
+ IFS=
 read -r _db_internal_line
+ RET=10 xserver-xorg/config/device/driver doesn't exist
+ return 10
+ true
+ db_unregister xserver-xorg/config/inputdevice/keyboard/rules
+ _db_cmd UNREGISTER xserver-xorg/config/inputdevice/keyboard/rules
+ IFS=  printf %s\n UNREGISTER xserver-xorg/config/inputdevice/keyboard/rules
+ IFS=
 read -r _db_internal_line
+ RET=10 xserver-xorg/config/inputdevice/keyboard/rules doesn't exist
+ return 10
+ true
+ db_unregister xserver-xorg/config/inputdevice/keyboard/model
+ _db_cmd UNREGISTER xserver-xorg/config/inputdevice/keyboard/model
+ IFS=  printf %s\n UNREGISTER xserver-xorg/config/inputdevice/keyboard/model
+ IFS=
 read -r _db_internal_line
+ RET=10 xserver-xorg/config/inputdevice/keyboard/model doesn't exist
+ return 10
+ true
+ db_unregister xserver-xorg/config/inputdevice/keyboard/layout
+ _db_cmd UNREGISTER xserver-xorg/config/inputdevice/keyboard/layout
+ IFS=  printf %s\n UNREGISTER xserver-xorg/config/inputdevice/keyboard/layout
+ IFS=
 read -r _db_internal_line
+ RET=10 xserver-xorg/config/inputdevice/keyboard/layout doesn't exist
+ return 10
+ true
+ db_unregister xserver-xorg/config/inputdevice/keyboard/variant
+ _db_cmd UNREGISTER xserver-xorg/config/inputdevice/keyboard/variant
+ IFS=  printf %s\n UNREGISTER xserver-xorg/config/inputdevice/keyboard/variant
+ IFS=
 read -r _db_internal_line
+ RET=10 xserver-xorg/config/inputdevice/keyboard/variant doesn't exist
+ return 10
+ true
+ db_unregister xserver-xorg/config/inputdevice/keyboard/options
+ _db_cmd UNREGISTER xserver-xorg/config/inputdevice/keyboard/options
+ IFS=  printf %s\n UNREGISTER xserver-xorg/config/inputdevice/keyboard/options
+ IFS=
 read -r _db_internal_line
+ RET=10 xserver-xorg/config/inputdevice/keyboard/options doesn't exist
+ return 10
+ true
+ db_unregister xserver-xorg/autodetect_keyboard
+ _db_cmd UNREGISTER xserver-xorg/autodetect_keyboard
+ IFS=  printf %s\n UNREGISTER xserver-xorg/autodetect_keyboard
+ IFS=
 read -r _db_internal_line
+ RET=10 xserver-xorg/autodetect_keyboard doesn't exist
+ return 10
+ true
+ dpkg --compare-versions 1:7.4~5ubuntu18 lt-nl 1:7.4+2
+ db_unregister xserver-xorg/config/device/bus_id
+ _db_cmd UNREGISTER xserver-xorg/config/device/bus_id
+ IFS=  printf %s\n UNREGISTER xserver-xorg/config/device/bus_id
+ IFS=
 read -r _db_internal_line
+ RET=10 xserver-xorg/config/device/bus_id doesn't exist
+ return 10
+ true
+ db_unregister xserver-xorg/config/device/bus_id_error
+ _db_cmd UNREGISTER xserver-xorg/config/device/bus_id_error
+ IFS=  printf %s\n UNREGISTER xserver-xorg/config/device/bus_id_error
+ IFS=
 read -r _db_internal_line
+ RET=10 xserver-xorg/config/device/bus_id_error doesn't exist
+ return 10
+ true
+ rm -f /var/lib/x11/xorg.conf.roster /var/lib/x11/xorg.conf.md5sum
+ rm -f /var/lib/x11/X.md5sum /var/lib/x11/X.roster
+ dpkg --compare-versions 1:7.4~5ubuntu18 lt-nl 1:7.4~5ubuntu1
+ dpkg --compare-versions 1:7.4~5ubuntu18 lt-nl 1:7.3+11
+ dpkg --compare-versions 1:7.4~5ubuntu18 lt-nl 1:7.3+13
+ dpkg --compare-versions 1:7.4~5ubuntu18 lt 1:7.4
+ invoke-rc.d hal restart
restart: Unknown instance: 
invoke-rc.d: initscript hal, action "restart" failed.
dpkg: error processing xserver-xorg (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 xserver-xorg
```

If nobody else has encountered this, I'll put it on Launchpad.

Did you finally open in launchpad this issue ?

I've got this too ... in my upgrade from jaunty to karmic ..

I solved 'temporaly' it adding "exit 0" after lsb headers in hal init script and reruning full-upgrade. After I removed this exit 0 of course :)

But now my mother desktop is not responsive to the mouse (I can't click any icon/menu).

Regards,

---

### Post by jbarroso on 2009-09-28
I reported my intel performance/crashes issues:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/438435](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/438435)

I think the workarround about upgrading xserver-xorg is not the cause ...

Regards,

---

