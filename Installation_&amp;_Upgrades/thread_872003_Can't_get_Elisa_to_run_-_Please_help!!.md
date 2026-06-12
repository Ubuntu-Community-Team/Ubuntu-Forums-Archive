---
title: "Can't get Elisa to run - Please help!!"
date: 2008-07-27
forum: Installation &amp; Upgrades
---

### Post by kmullinax on 2008-07-27
So I had Elisa 0.3.5 up and running just fine and then decided life was going too well so I just had to go messing things up.  :???:

I installed the .tar file for 0.5.2 and did everything I could to get it to run, but nothing worked.  I kept getting stuck on the "hildon" problem.
SO, I wiped it clean and went to re-install 0.3.5 and now it won't run at all...!   AAAAAA!!!!!

In terminal when I try to run it, this is what I get:

~$ elisa
Traceback (most recent call last):
  File "/usr/bin/elisa", line 22, in <module>
    from elisa.core import elisa_boot
ImportError: cannot import name elisa_boot
~$

I've opened /usr/bin/elisa in gedit but I can't figure out what the problem is and why elisa.core isn't working.
The only thing I can imagine is that some dependency was updated when installing 0.5.2 and now needs to be downgraded, but I don't know how to even go about finding out what.

Does anyone have any ideas for me?
Thanks in advance!!

---

### Post by kmullinax on 2008-07-27
Okay so I uninstalled everything again and then did a thorough sweep of the computer and found a ton of leftover Elisa files.
So I deleted everything, rebooted and then re-installed everything.

Now it at least shows the splash screen, but then tells me it can't find any plugins and closes.
When I run it in terminal I get:

Elisa failed to initialize [Failure instance: Traceback: <class 'elisa.core.plugin_registry.PluginNotFound'>: Plugin 'raval' not found
/usr/lib/python2.5/site-packages/twisted/internet/defer.py:317:_runCallbacks
/usr/lib/python2.5/site-packages/twisted/internet/defer.py:507:_cbDeferred
/usr/lib/python2.5/site-packages/twisted/internet/defer.py:239:callback
/usr/lib/python2.5/site-packages/twisted/internet/defer.py:304:_startRunCallbacks
--- <exception caught here> ---
/usr/lib/python2.5/site-packages/twisted/internet/defer.py:317:_runCallbacks
/usr/lib/python2.5/site-packages/elisa/core/application.py:425:initialize_managers_done
/usr/lib/python2.5/site-packages/elisa/core/interface_controller.py:126:initialize
/usr/lib/python2.5/site-packages/elisa/core/interface_controller.py:75:_initialize_mvc_mappings
/usr/lib/python2.5/site-packages/elisa/core/interface_controller.py:87:_get_mvc_config_file
/usr/lib/python2.5/site-packages/elisa/core/plugin_registry.py:246:get_plugin_with_name
]

So this time I unstalled and reinstalled again in order to see in terminal what happened during install and I got this...

~$ sudo apt-get install elisa
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  elisa
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/20.2kB of archives.
After this operation, 147kB of additional disk space will be used.
Selecting previously deselected package elisa.
(Reading database ... 
dpkg: serious warning: files list file for package `elisa-plugins-ugly' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `elisa-plugins-good' missing, assuming package has no files currently installed.
213239 files and directories currently installed.)
Unpacking elisa (from .../archives/elisa_0.3.5-3_all.deb) ...
Setting up elisa (0.3.5-3) ...
~$

So now I figured the plugins must not have installed correctly so I went to download the packages individually, but terminal reports that the latest version of those packages are already installed...
Anyone know how I can fix this?

---

### Post by kmullinax on 2008-07-27
*** SOLVED ***

So this time I uninstalled the plugin package instead of the main program.
It still uninstalled Elisa but for some reason focusing on the plugins seemed to work.
When I reinstalled it, everything worked.
Huh.
Go figure.

---

