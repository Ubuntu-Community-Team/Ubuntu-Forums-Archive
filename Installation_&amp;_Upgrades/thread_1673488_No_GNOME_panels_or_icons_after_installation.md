---
title: "No GNOME panels or icons after installation"
date: 2011-01-22
forum: Installation &amp; Upgrades
---

### Post by KneusExMachina on 2011-01-22
After a new installation of Ubuntu 10.10 (regular or alternative) I get to the login screen as usual. However, after logging in I get no panels or icons. In fact, I only get the Ubuntu background and a working mouse cursor. The same happens when I try Ubuntu from the live CD (with a black background). The installation itself was performed in a high resolution with no problems at all! I got a panel there (for sound, wireless, etc.).

After installation I can also Ctrl-Alt-F1 to login textually to see my processes. When I restart GDM I will get back to the login screen, but I after visually logging in I again see no panels or icons! Where should I start with a working visual installation and login screen, but a blank desktop environment after login?

Reinstalling or creating another user will not work.

---

### Post by akand074 on 2011-01-22
Hey, welcome to the forums!

You can try pressing Alt + F2 and running the command:

```
metacity --replace
```

in the dialogue box.

If that doesn't work you can try pressing Alt + F2 again and running this:

```
/usr/bin/jockey-gtk
```

This will open an additional drivers dialogue box. Install any proprietary drivers available (video card driver is what is important) then restart and see if that fixes the issue. That's all I can think of right now. Post back if neither works.

---

### Post by KneusExMachina on 2011-01-22
Hi,

The Alt-F2 dialog box won't show, just like the panels and icons won't show. Therefore, I cannot know if it got the input. When I try those commands in textual mode I need an X running. The only thing I could do is start the textual jockey:
```
oet@nec:~$/usr/bin/jockey-text
/usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py:57: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)

Searching for available drivers...
oet@nec:~$
```

As you can see, it returns nothing but a GTK error and standard output (don't know why, because it's the text jockey version).

I have an ATI Radeon Mobility X300 (no longer supported by ATI I guess). Furthermore, I noticed the file '.x-session-errors' in my home directory. I don't know if it's relevant but here's it's content:
```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-irWP4C
GNOME_KEYRING_CONTROL=/tmp/keyring-irWP4C
GNOME_KEYRING_CONTROL=/tmp/keyring-irWP4C
SSH_AUTH_SOCK=/tmp/keyring-irWP4C/ssh
** Message: adding killswitch idx 0 state KILLSWITCH_STATE_UNBLOCKED
** Message: killswitch 0 is KILLSWITCH_STATE_UNBLOCKED
** Message: killswitches state KILLSWITCH_STATE_UNBLOCKED

(polkit-gnome-authentication-agent-1:1436): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1436): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** Message: killswitch 0 is KILLSWITCH_STATE_UNBLOCKED
** Message: killswitches state KILLSWITCH_STATE_UNBLOCKED
** Message: applet now removed from the notification area
** (nm-applet:1433): DEBUG: old state indicates that this was not a disconnect 0
Initializing nautilus-gdu extension

(nautilus:1428): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Starting gtk-window-decorator
** Message: applet now embedded in the notification area
I/O warning : failed to load external entity "/home/oet/.compiz/session/102a4f250ee1fff46e12954735721616400000013620028"
```

What should I do next? The video card worked when I was installing Ubuntu...

---

### Post by akand074 on 2011-01-22
hmm.. give this a try, perhaps the problem is with gnome-settings-daemon:

```
sudo killall gnome-settings-daemon
```

then 

```
sudo gnome-settings-daemon
```

Possibly nautilus I doubt it.. but you can try this if the top doesn't work:

```
rm -vr ~/.gconf/apps/nautilus && killall nautilus
```

(I assume you can get to a command prompt). Though even your Alt+F2 dialogue box isn't coming up.. seems like a more major issue. Judging by your original post, I assume you have already tried a clean install several times?

---

### Post by KneusExMachina on 2011-01-22
Hi again,

It seems like the problem's fixed! But since I did some stuff myself and your stuff I have to pinpoint the exact solution. I will do a fresh install (again) and trace which command solved the problem. I'll get back to you when I figure it out.

Thanx!

---

### Post by akand074 on 2011-01-22
> **KneusExMachina said:**
> Hi again,

It seems like the problem's fixed! But since I did some stuff myself and your stuff I have to pinpoint the exact solution. I will do a fresh install (again) and trace which command solved the problem. I'll get back to you when I figure it out.

Thanx!

Fantastic. That's kind of you to do, because this can be helpful to others in the future.

---

### Post by KneusExMachina on 2011-01-23
Seems like my panels DO work in safe mode (I did not know that you could choose that after clicking on a login name and before entering the password at the panel below).

Here are the steps I've taken in SAFE MODE:
* Go to appearance preferences
* Go the the visual effects tab
* Select normal and get an error "Desktop effects could not be enabled"

When I login again in regular mode, I have a working desktop environment with everything on it!

Problem solved? Partially... I can see that my visual effects are (now?) set to "None" like in safe mode. When I set it to "Normal" all my stuff (except background and mouse cursor) disappear again. If I do ALT+F2 and enter "compiz --replace" the same happens :(.

I also noticed a new error in my .xsession-errors:
```
(gnome-appearance-properties:2177): Gdk-CRITICAL **: IA__gdk_display_sync: asser
tion `GDK_IS_DISPLAY (display)' failed
There is no available graphics driver for your system which supports the composite extension, or the current one already supports it.
```

So everything is working, but without visual effects. Is there a way to solve this with an ATI Mobility Radeon X300? There were also problems with a ATI Radeon X300 in [this thread]("http://ubuntuforums.org/showthread.php?t=1466210").

---

### Post by akand074 on 2011-01-23
Try installing the latest graphics drivers from AMD. [32 Bit]("http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English"). [64 Bit]("http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English"). Assuming you weren't able to get your proprietary drivers installed using System > Administration > Additional Drivers.

You could also try what the person from that thread did to solve it:

> i solved the issue. problem is when external display is connected thru  vga then i m unable to select extra or normal option under appearance. i  removed external monitor connection and restart ubuntu and everything  is working.

---

### Post by KneusExMachina on 2011-01-25
I do not use an external monitor.

Anyway, I first tried to install the driver first this way:
```
oet@nec:~$ sh ati-driver-installer-9-3-x86.x86_64.run
...
==================================================
 ATI Technologies Linux Driver Installer/Packager
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.35-24-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.xDe2mE
```

Then I read [this thread]("http://ubuntuforums.org/showthread.php?t=1221221") and listed for what distro's it can compile packages for Ubuntu:
```
oet@nec:~$ sh ati-driver-installer-9-3-x86.x86_64.run --listpkg
...
Status: *UNVERIFIED*
Ubuntu Packages:
    Ubuntu/7.10
    Ubuntu/8.04
    Ubuntu/8.10
    Ubuntu/9.04
    Ubuntu/gutsy
    Ubuntu/hardy
    Ubuntu/intrepid
    Ubuntu/jaunty
    Ubuntu/source
```

So then I chose the latest version it had:
```
oet@nec:~$ sh ati-driver-installer-9-3-x86.x86_64.run --buildpkg Ubuntu/9.04
```

It made a bunch of debian packages! After installing them, the driver showed on my jockey-gtk. However, when I wanted to activate it the following happened (run from console to show std err):
```
oet@nec:~$ /usr/bin/jockey-gtk

Traceback (most recent call last):
  File "/usr/bin/jockey-gtk", line 386, in on_button_toggle_clicked
    'toggle', False):
  File "/usr/lib/python2.6/dist-packages/jockey/ui.py", line 650, in set_handler_enable
    handler_id, enable)
  File "/usr/lib/python2.6/dist-packages/jockey/backend.py", line 98, in convert_dbus_exceptions
    return fn(*args, **kwargs)
  File "/usr/lib/python2.6/dist-packages/jockey/backend.py", line 90, in dbus_sync_call_signal_wrapper
    raise _h_exception_exc
dbus.exceptions.DBusException: org.freedesktop.DBus.Python.TypeError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.6/dist-packages/jockey/backend.py", line 337, in _f_result_wrapper
    self._f_result = f()
  File "/usr/share/jockey/handlers/fglrx.py", line 71, in enable
    self._alternatives.set_alternative(fglrx_alternative)
  File "/usr/lib/python2.6/dist-packages/NvidiaDetector/alternatives.py", line 89, in set_alternative
    subprocess.check_call([self.__command, '--set', self.__master_link, path])
  File "/usr/lib/python2.6/subprocess.py", line 483, in check_call
    retcode = call(*popenargs, **kwargs)
  File "/usr/lib/python2.6/subprocess.py", line 470, in call
    return Popen(*popenargs, **kwargs).wait()
  File "/usr/lib/python2.6/subprocess.py", line 623, in __init__
    errread, errwrite)
  File "/usr/lib/python2.6/subprocess.py", line 1141, in _execute_child
    raise child_exception
TypeError: execv() arg 2 must contain only strings
```

It won't active (can press Active as many times and get this same error). After another install, same happens.

---

### Post by akand074 on 2011-01-25
Did you run it as root? The command should have worked regardless I believe:

```
sudo sh ati-driver-installer-9-3-x86.x86_64.run
```

That should open an installer where you just follow the steps. You shouldn't have to activate the drivers from System > Administration > Additional Drivers if you already installed that. Go check out System > Preferences and see if you have "ATI Catalyst Control Center" there. That would mean it installed successfully.

---

### Post by KneusExMachina on 2011-01-29
Great... I have an option to install it automatically after it builds the packages. But... new errors! Before I begin to try anything, do you have any ideas?

```
oet@nec:~/Downloads$ sudo sh ati-driver-installer-9-3-x86.x86_64.run --buildandinstallpkg Ubuntu/9.04
Created directory fglrx-install.IYEWRN
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver 8.593..................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating and Installing package: Ubuntu/9.04
Resolving build dependencies...
Continuing package build
Package /home/oet/Downloads/xorg-driver-fglrx_8.593-0ubuntu1_i386.deb has been successfully generated
Package /home/oet/Downloads/xorg-driver-fglrx-dev_8.593-0ubuntu1_i386.deb has been successfully generated
Package /home/oet/Downloads/fglrx-kernel-source_8.593-0ubuntu1_i386.deb has been successfully generated
Package /home/oet/Downloads/fglrx-amdcccle_8.593-0ubuntu1_i386.deb has been successfully generated
Package /home/oet/Downloads/fglrx-modaliases_8.593-0ubuntu1_i386.deb has been successfully generated
Package /home/oet/Downloads/libamdxvba1_8.593-0ubuntu1_i386.deb has been successfully generated
Selecting previously deselected package xorg-driver-fglrx.
(Reading database ... 121608 files and directories currently installed.)
Unpacking xorg-driver-fglrx (from xorg-driver-fglrx_8.593-0ubuntu1_i386.deb) ...
dpkg: warning: obsolete option '--print-installation-architecture', please use '--print-architecture' instead.
Selecting previously deselected package fglrx-kernel-source.
Unpacking fglrx-kernel-source (from fglrx-kernel-source_8.593-0ubuntu1_i386.deb) ...
Selecting previously deselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from fglrx-amdcccle_8.593-0ubuntu1_i386.deb) ...
dpkg: warning: downgrading fglrx-modaliases from 2:8.780-0ubuntu2 to 2:8.593-0ubuntu1.
Preparing to replace fglrx-modaliases 2:8.780-0ubuntu2 (using fglrx-modaliases_8.593-0ubuntu1_i386.deb) ...
Unpacking replacement fglrx-modaliases ...
Setting up fglrx-kernel-source (2:8.593-0ubuntu1) ...
Adding Module to DKMS build system
Doing initial module build

Error!  Build of fglrx.ko failed for: 2.6.35-22-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.593/build/ for more information.
Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms.py", line 47, in <module>
    report['SourcePackage'] = apport.packaging.get_source(package)
  File "/usr/lib/python2.6/dist-packages/apport/packaging_impl.py", line 106, in get_source
    if self._apt_pkg(package).installed:
  File "/usr/lib/python2.6/dist-packages/apport/packaging_impl.py", line 66, in _apt_pkg
    raise ValueError, 'package does not exist'
ValueError: package does not exist
Installing initial module

Error! Could not locate fglrx.ko for module fglrx in the DKMS tree.
You must run a dkms build for kernel 2.6.35-22-generic (i686) first.
Done.
Setting up fglrx-modaliases (2:8.593-0ubuntu1) ...
Setting up xorg-driver-fglrx (2:8.593-0ubuntu1) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up fglrx-amdcccle (2:8.593-0ubuntu1) ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.C.cache...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
xorg-driver-fglrx_8.593-0ubuntu1_i386.deb fglrx-kernel-source_8.593-0ubuntu1_i386.deb fglrx-amdcccle_8.593-0ubuntu1_i386.deb fglrx-modaliases_8.593-0ubuntu1_i386.deb
Cleaning up removed packages
Warning: Could not find configuration file
Please copy configuration file template to /etc/X11
Removing temporary directory: fglrx-install.IYEWRN
```

---

### Post by akand074 on 2011-01-29
Does it not work without the "--buildandinstallpkg Ubuntu/9.04" option? It looks like you are not the only one with this problem. Check out [this]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/573748") page.. apparently they made a patch that works with .35 kernels as well. Also you can take a little look at [this]("http://secondfry.blogspot.com/2010/10/blog-post.html") page.. I think some person tried to install an ATI driver and it had the same issue then he tried to apply the patch. I think they all had issues with -22 kernel. Try doing an update (System > Administration > Update Manager). The newest update has the 2.6.35-25 kernel, perhaps it will successfully build for this kernel. Otherwise I'm at a loss. Let me know how any of this goes.

---

