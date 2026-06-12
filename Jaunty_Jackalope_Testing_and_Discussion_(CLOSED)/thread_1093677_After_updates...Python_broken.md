---
title: "After updates...Python broken?"
date: 2009-03-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by coffeecat on 2009-03-27
I did a fresh network install of Jaunty Development (Ubuntu/gnome) yesterday afternoon, so this was more or less equivalent to a fresh Beta install. Yesterday, System > Preferences > Main Menu was working after I had installed a number of favourite apps from the repos. After about 30MB updates this morning, it is not. Click on 'Main Menu' in the - um - main menu and nothing happens. Ditto for System > Administration > Printing, although I was able to use localhost:631 in a browser to set up a printer OK. I didn't check System > Administration > Printing before the updates.

All the other apps that I've tried from the menu open OK, except for DeVeDe. Click on DeVeDe in the menu and, again, nothing happens. The DeVeDe problem may be a separate issue but, for the record, opening from the terminal gives the following error:

```
~$ devede
Traceback (most recent call last):
  File "/usr/bin/devede", line 27, in <module>
    import gtk
  File "/var/lib/python-support/python2.6/gtk-2.0/gtk/__init__.py", line 38, in <module>
    import gobject as _gobject
  File "/var/lib/python-support/python2.6/gtk-2.0/gobject/__init__.py", line 33, in <module>
    from glib import spawn_async, idle_add, timeout_add, timeout_add_seconds, \
  File "/var/lib/python-support/python2.6/gtk-2.0/glib/__init__.py", line 30, in <module>
    from glib._glib import *
ImportError: /var/lib/python-support/python2.6/gtk-2.0/glib/_glib.so: undefined symbol: PyUnicodeUCS4_DecodeUTF8
~$ 
```Any thoughts? Would others please like to try Main Menu and Printing?

---

### Post by vredley on 2009-03-27
I noticed the menu editor problem; Rhythmbox and Quod Libet seem to be broken on my system, too. Oh well, I was planning a fresh Beta install anyway. :)

---

### Post by phenest on 2009-03-27
I just this minute did some updates, and now several apps won't start:

Avant Window Navigator
Computer Janitor
Ex Falso

I think these all use Python.

---

### Post by yaztromo on 2009-03-27
Ditto, after upgrading to beta. All python apps are broken.

I've lost deluge and emesene for the time being.

---

### Post by coffeecat on 2009-03-27
Thanks **vredley**. Some more information. I think the DeVeDe and your problems are all the same as the Main Menu one. I had to reboot into Intrepid to be able to open up Main Menu to see what the calls for 'Main Menu' and 'Printing' are so that I could reboot back into Jaunty to get some errors from the terminal. :roll:

Main Menu:

```
~$ alacarte
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 22, in <module>
    from Alacarte.MainWindow import MainWindow
  File "/usr/lib/python2.6/dist-packages/Alacarte/MainWindow.py", line 19, in <module>
    import gtk, gtk.glade, gmenu, gobject, gio
  File "/var/lib/python-support/python2.6/gtk-2.0/gtk/__init__.py", line 38, in <module>
    import gobject as _gobject
  File "/var/lib/python-support/python2.6/gtk-2.0/gobject/__init__.py", line 33, in <module>
    from glib import spawn_async, idle_add, timeout_add, timeout_add_seconds, \
  File "/var/lib/python-support/python2.6/gtk-2.0/glib/__init__.py", line 30, in <module>
    from glib._glib import *
ImportError: /var/lib/python-support/python2.6/gtk-2.0/glib/_glib.so: undefined symbol: PyUnicodeUCS4_DecodeUTF8
~$ 
```and Printing:

```
~$ system-config-printer
Traceback (most recent call last):
  File "/usr/share/system-config-printer/system-config-printer.py", line 30, in <module>
    import dbus
  File "/var/lib/python-support/python2.6/dbus/__init__.py", line 79, in <module>
    import dbus.types as types
  File "/var/lib/python-support/python2.6/dbus/types.py", line 6, in <module>
    from _dbus_bindings import ObjectPath, ByteArray, Signature, Byte,\
ImportError: /var/lib/python-support/python2.6/_dbus_bindings.so: undefined symbol: PyUnicodeUCS4_AsEncodedString
~$ 
```Expect to see some bugfixes in the python line soon. :) I didn't notice; were there any updates to any python stuff this morning?

**Edit**; to answer myself, yes there was. A quick look in dpkg.log shows libpython2.6, python2.6-minimal, python 2.6.1, python-central for this morning, and possibly some more. I'm glad the Log File Viewer doesn't use python. :lol:

---

### Post by Taiebot65 on 2009-03-27
Did a normal upgrade and apport totem rhythmbox are not starting anymore. I will wait a little bit before reporting bugs because we are moving to beta...

---

### Post by joewski on 2009-03-27
I've lost reporting bugs too, command line, from help, I can't add/remove applications. Just updated the laptop.

Another desktop machine hasn't updated yet so I'll switch off the python related files and see if the old version still work with the new updates.

---

### Post by vredley on 2009-03-27
Thanks for that - good detective work! Yes, I think there was some Python-related stuff in there. Python seems to have been the curse of Jaunty all the way through the testing stage. :D

---

### Post by taavikko on 2009-03-27
What are output's when started via terminal?

---

### Post by yaztromo on 2009-03-27
[https://bugs.launchpad.net/ubuntu/+source/python2.6/+bug/349462](https://bugs.launchpad.net/ubuntu/+source/python2.6/+bug/349462)

---

### Post by Taiebot65 on 2009-03-27
Segmentation fault (core dumped)

---

### Post by Taiebot65 on 2009-03-27
Ok maybe it s related to alsa..

i ve opened mplayer which is not crashing  and here the ouput

==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
[AO_ALSA] Unable to find simple control 'PCM',0.
Starting playback...
VDec: vo config request - 640 x 272 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 2.35:1 - prescaling to correct movie aspect.
VO: [x11] 640x272 => 640x272 Planar YV12 
[swscaler @ 0x896d370]SwScaler: using unscaled yuv420p -> rgb32 special converter
[AO_ALSA] Unable to find simple control 'PCM',0. ??% ??% ??,?% 0 0              
[AO_ALSA] Unable to find simple control 'PCM',0. ??% ??% ??,?% 1 0              
[AO_ALSA] Unable to find simple control 'PCM',0. ??% ??% ??,?% 2 0

---

### Post by roberthr on 2009-03-27
Yes, happened to me too :-(
Is there a way to fix this in console since system is almost unusable...

---

### Post by coffeecat on 2009-03-27
> **vredley said:**
> Python seems to have been the curse of Jaunty all the way through the testing stage. :D

Well I see some other threads have started. But even worse news.

```
~$ /usr/bin/update-manager
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 29, in <module>
    import gtk
  File "/var/lib/python-support/python2.6/gtk-2.0/gtk/__init__.py", line 38, in <module>
    import gobject as _gobject
  File "/var/lib/python-support/python2.6/gtk-2.0/gobject/__init__.py", line 33, in <module>
    from glib import spawn_async, idle_add, timeout_add, timeout_add_seconds, \
  File "/var/lib/python-support/python2.6/gtk-2.0/glib/__init__.py", line 30, in <module>
    from glib._glib import *
ImportError: /var/lib/python-support/python2.6/gtk-2.0/glib/_glib.so: undefined symbol: PyUnicodeUCS4_DecodeUTF8
~$ 
```Yup, that's right. Update Manager uses python too which will catch the unwary out. You can see that someone has been rebooting between Intrepid and Jaunty again. :( Synaptic's working, and there's always the command line, but when the bugfix comes through we'll have to update manually.

It rather reminds me of openSUSE 10.1, I think it was. There was a HUGE problem with the package/update/whatever manager such that it didn't work. But that was all right. They quickly released a bugfix which you could download using... Oh, wait a minute... :lol:

---

### Post by awam66 on 2009-03-27
Looks like they've found something as my updates failed to download the Python 2.6 updates with 404 not found error.

That should have bees 403 forbidden.

---

### Post by Otaconda on 2009-03-27
[https://bugs.launchpad.net/ubuntu/+source/python2.6/+bug/349467](https://bugs.launchpad.net/ubuntu/+source/python2.6/+bug/349467)

The offending update has been disabled and the package reverted. Since update-manager wont work if you been affected you'll need to run 'sudo apt-get update' and 'sudo apt-get upgrade' from a terminal.

I'm not showing any updated packages yet, guess we're waiting for the mirrors to pick it up :dunno:

---

### Post by phenest on 2009-03-27
Is there no way of reverting back manually?

---

### Post by binbash on 2009-03-27
Did you upgrade python?

---

### Post by taavikko on 2009-03-27
> **phenest said:**
> Is there no way of reverting back manually?

If you havent cleaned your cache for a while, there might still be older version of python2.6 pkg's.

/var/cache/apt/archives/

---

### Post by Taiebot65 on 2009-03-27
Maybe there was 80 updates....so maybe... i will wait till it s repaired i m not going to do any report before 2 3 days

---

### Post by vredley on 2009-03-27
:lol:

---

### Post by BUGabundo on 2009-03-27
please see bug [https://bugs.launchpad.net/ubuntu/+source/python2.6/+bug/349467](https://bugs.launchpad.net/ubuntu/+source/python2.6/+bug/349467)

---

### Post by binbash on 2009-03-27
> **Taiebot65 said:**
> Maybe there was 80 updates....so maybe... i will wait till it s repaired i m not going to do any report before 2 3 days

Then you upgraded python also which is broken at the moment

---

### Post by BUGabundo on 2009-03-27
> **binbash said:**
> Then you upgraded python also which is broken at the moment

should already be fixed for 32bits on Main mirror!
64bits is building now

---

### Post by binbash on 2009-03-27
[http://ubuntuforums.org/showthread.php?t=1107854](http://ubuntuforums.org/showthread.php?t=1107854)

---

### Post by phenest on 2009-03-27
I can confirm that the packages are ready for download on 64 bit, and do indeed resolve this problem.

---

### Post by zika on 2009-03-27
storm has passed on Main-server, all clear ... :)

---

### Post by Taiebot65 on 2009-03-27
Fixed yeah + an other bug that i reported .. :guitar:

---

### Post by pjalegria on 2009-03-27
Hi 

After today updates nothing works anymore...

Update manger i get this:

> jango@jango-AAO:~$ sudo update-manager 
[sudo] password for jango: 
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 29, in <module>
    import gtk
  File "/var/lib/python-support/python2.6/gtk-2.0/gtk/__init__.py", line 38, in <module>
    import gobject as _gobject
  File "/var/lib/python-support/python2.6/gtk-2.0/gobject/__init__.py", line 33, in <module>
    from glib import spawn_async, idle_add, timeout_add, timeout_add_seconds, \
  File "/var/lib/python-support/python2.6/gtk-2.0/glib/__init__.py", line 30, in <module>
    from glib._glib import *
ImportError: /var/lib/python-support/python2.6/gtk-2.0/glib/_glib.so: undefined symbol: PyUnicodeUCS4_DecodeUTF8
jango@jango-AAO:~$ 


all phyton based applications dont work...Help please

---

### Post by binbash on 2009-03-27
python was broken.It is fixed now (at least at 32bit).Update it via apt-get (sudo apt-get update)

---

### Post by BhumibolTheGreat on 2009-03-27
Hi Guys,

I have just upgraded my machine to 9.10
On first impression the new version seems to be slower than my previously used 8.04 LTS. 

One thing that I've encountered is when trying to run the "System Testing" in "Control Center" I'm getting an error saying:
"Sorry the program 'run' closed unexpectedly"

hitting the "Report Problem"
leads to another error:

"You have some obsolete package versions installed. Please upgrade the following packages and check if the problem still occurs:

python2.6, python2.6-minimal"


Phew .. 

On top of that, trying to upgrade the packages above gave me different error saying that access to the ***** repository was forbidden 403 error.

The last error affects only these two packages, the rest of the packages on the system were upgraded successfully. 


Well, three different issues, did anyone encounter those after upgrade?


Thanks, 
Me.

---

### Post by pjalegria on 2009-03-27
I cant get any update...

---

### Post by pjalegria on 2009-03-27
Still broken...

---

### Post by plun on 2009-03-27
> **pjalegria said:**
> Still broken...

Yup and I had trouble with ccsm and simple ccsm

```
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 336600 files and directories currently installed.)
Preparing to replace python2.6-minimal 2.6.1-1ubuntu4 (using .../python2.6-minimal_2.6.1-1ubuntu5.1_amd64.deb) ...
Moving /usr/lib/python2.6/site-packages/simple_ccsm-0.8.3-py2.6.egg-info to new location:
  --> /usr/lib/python2.6/old-site-packages/simple_ccsm-0.8.3-py2.6.egg-info (already exist in /usr/local/lib/python2.6/dist-packages/
mv: cannot move `/usr/lib/python2.6/site-packages/simple_ccsm-0.8.3-py2.6.egg-info' to `/usr/lib/python2.6/old-site-packages/': Not a directory
dpkg: error processing /var/cache/apt/archives/python2.6-minimal_2.6.1-1ubuntu5.1_amd64.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:

``` 

I just deleted those site-packages  (sudo nautilus)

and 

```
sudo apt-get-clean

sudo apt-get update && sudo apt-get dist-upgrade

sudo apt-get install -f
```

---

### Post by cariboo on 2009-03-27
I asked the mods to move this to the proper place, to fix your problems open a terminal and type:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

There is a sticky at the top of the Jaunty forum explaining what happened.

Jim

---

### Post by tjeremiah on 2009-03-27
> **cariboo907 said:**
> I asked the mods to move this to the proper place, to fix your problems open a terminal and type:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

There is a sticky at the top of the Jaunty forum explaining what happened.

Jim

didnt work, still the same problem.

---

### Post by screaminj3sus on 2009-03-27
still broken and main mirror is giving 404's

---

### Post by forumache on 2009-03-27
> **pjalegria said:**
> I cant get any update...

Open a Terminal: Applications|Accesories|Terminal
and type (without $)
$ sudo apt-get update
$ sudo apt-get upgrade

Things should be solved.
Basically you updated from the command line instead of using the update-manager (which is/was broken). Now, after the update, the update-manager should be working again.

---

### Post by cariboo on 2009-03-27
Try a different mirror.


> didnt work, still the same problem.

Is not very helpful, did it update anything?

Jim

---

### Post by excogitation on 2009-03-27
started working (can't tell when)

---

