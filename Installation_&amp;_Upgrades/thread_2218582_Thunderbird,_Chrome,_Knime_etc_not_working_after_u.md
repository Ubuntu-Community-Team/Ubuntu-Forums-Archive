---
title: "Thunderbird, Chrome, Knime etc not working after upgrading to 14:04"
date: 2014-04-21
forum: Installation &amp; Upgrades
---

### Post by Wayne Twine on 2014-04-21
Hi

I was running my PC on Ubuntu 12.04.   After upgrading to 14:04 this weekend, key packages no longer open succesfully when I click on their icon in Unity launcher (or dash).   For example:

Thunderbird: launcher icon pulses but nothing happens.  Thunderbird appears in list of processes in System Monitor, with sleeping status.   If I click on Thunderbird icon again, I get an error message saying that it is already running but not responding.

Chrome: launcher icon pulses but nothing happens.   Absent from list of running processes in sys mon.

Knime: Starts loading, but then disappears, and absent from list of running processes in sys mon.

MS Office running in Wine (Crossover): launcher icon pulses but nothing happens.   Absent from list of running processes in sys mon.

Othe programs, like Libre Office, Rstudio and Qgis work fine.

Also, a less serious irritation is that the System Monitor app indicator icon in the top panel has now been replaced by a red circle, crossed out.

Any suggestions?

Thanks
W

---

### Post by ivan-janes on 2014-04-21
You can try to fix broken packages from terminal

1.) Clean cache
```
sudo apt-get clean
```

2.) Check for updates
```
sudo apt-get update
```

3.) Install updates
```
sudo apt-get upgrade
```

4.) Fix broken packages
```
sudo apt-get -f install
```

---

### Post by Wayne Twine on 2014-04-21
Thanks Ivan-Janes for quick response.  
Alas, I had already tried that (and I followed your steps again in case I had missed something) but to no avail.

---

### Post by ivan-janes on 2014-04-21
Did you try to run thunderbird from terminal ? What is the output ?

---

### Post by Wayne Twine on 2014-04-22
Thanks

Here is the output when I run Thunderbird in terminal:

(process:4281): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed

(thunderbird:4281): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::sm-connect after class was initialised

(thunderbird:4281): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::show-crash-dialog after class was initialised

(thunderbird:4281): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::display after class was initialised

(thunderbird:4281): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::default-icon after class was initialised
[calBackendLoader] Using libical backend at /home/wayne/.thunderbird/s4f56rex.default/extensions/{e2fda1a4-762b-4020-b5ad-a41df1933103}/components/libical.manifest

(thunderbird:4281): GLib-GObject-WARNING **: cannot register existing type 'DbusmenuMenuitem'

(thunderbird:4281): GLib-CRITICAL **: g_once_init_leave: assertion 'result != 0' failed

(thunderbird:4281): GLib-GObject-CRITICAL **: g_param_spec_object: assertion 'g_type_is_a (object_type, G_TYPE_OBJECT)' failed

(thunderbird:4281): GLib-GObject-CRITICAL **: g_object_class_install_property: assertion 'G_IS_PARAM_SPEC (pspec)' failed

---

### Post by Wayne Twine on 2014-04-22
Another update:

I can get Thunderbird to start in safe mode from terminal.  Although I still get the GLib error messages, at least TB launches in safe mode.

Chrome, Crossover and Knime are now work in Ubuntu 14.04, after I re-installed latest versions of these packages.  However, removing and re-installing latest version of Thunderbird did NOT fix the TB issue.

---

### Post by ivan-janes on 2014-04-22
```
[calBackendLoader] Using libical backend at   /home/wayne/.thunderbird/s4f56rex.default/extensions/{e2fda1a4-762b-4020-b5ad-a41df1933103}/components/libical.manifest
```

Start in safe mode and disable lightning  plugin - [https://bugzilla.mozilla.org/show_bug.cgi?id=925840](https://bugzilla.mozilla.org/show_bug.cgi?id=925840)

---

### Post by Wayne Twine on 2014-04-23
Aha! Thanks.


I checked the "disable all add-ons" and then "make changes and restart" in the dialogue box that appears after running TB in safe mode from terminal.  Now Thunderbird launches from Unity dash and launcher.  I hope this gets fixed soon, because I rely heavily on lightning calendar, but at least I have my mail back!


Thanks again

---

### Post by Wayne Twine on 2014-04-23
Quick update:

Once all TB add-ons were disabled, I enabled one at a time and restarted each time to see which one is giving trouble.  It turns out that lightning is not the issue.  It was the "Messaging menu and Unity launcher" add-on  that was causing TB not to launch.  I have left that one disabled, but others like Lightning, Gnome Integration, GContactSync, Provider for Google Calendar, and Google Task Sync all work fine.  If I run in TB in terminal (not safe mode), I still get the GLib error messages, but TB launches and functions fine.

---

### Post by ivan-janes on 2014-04-23
Strange. Plugin "Messaging menu and Unity launcher" is working for me. Which version of plugin do you have ? Mine is 1.3.1.

---

