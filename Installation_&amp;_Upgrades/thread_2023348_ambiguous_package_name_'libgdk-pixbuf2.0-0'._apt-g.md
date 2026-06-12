---
title: "ambiguous package name 'libgdk-pixbuf2.0-0'. apt-get fails to upgrade"
date: 2012-07-12
forum: Installation &amp; Upgrades
---

### Post by amermc on 2012-07-12
I have kernel 3.2.0-2-amd64, "apt-get -f install" failed .. I have issues with ia32-libs dependencies like : ia32-libs-multiarch (no candidates). Cannot install anything ... 
apt-get fails to upgrade with the following message :
"ambiguous package name 'libgdk-pixbuf2.0-0' ...more than one one installed instance" 
Any help ??

Thanks

---

### Post by drs305 on 2012-07-12
I have two packages with that name. Perhaps if you tried installing them directly. I don't know if the error will prevent installation of these packages individually but it would probably clear the error if it does.
```

sudo apt-get install libgdk-pixbuf2.0-0:i386 libgdk-pixbuf2.0-common
```

---

### Post by amermc on 2012-07-12
Thanks dr. ...I have tried what you suggested ...not working... it gives this output : 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libgdk-pixbuf2.0-0:i386
E: Couldn't find any package by regex 'libgdk-pixbuf2.0-0'

---

### Post by drs305 on 2012-07-12
I am not sure why  it's not finding it. The packages are located in the precise *main* repository. Can you run "sudo apt-get update"?

That repository should be enabled, but you can quickly check with:
```
sudo grep "main" /etc/apt/sources.list
```
There should be no # symbol at the start of the line.
> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse restricted **main** universe

---

### Post by amermc on 2012-07-12
Thanks you Drs .. I have updated the **sources.****list** file and did **apt-get update **(was ok), but output is same as above when trying to install pixbuf2 libraries.

I have tried also : [COLOR=Red]**apt-get remove --purge libgdk-pixbuf2.***[/COLOR]            (which gives the following):
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libgdk-pixbuf2.0-0' for regex 'libgdk-pixbuf2.*'
Note, selecting 'libgdk-pixbuf2.0-dev' for regex 'libgdk-pixbuf2.*'
Note, selecting 'libgdk-pixbuf2.0-doc' for regex 'libgdk-pixbuf2.*'
Note, selecting 'libgdk-pixbuf2-ruby1.8-dbg' for regex 'libgdk-pixbuf2.*'
Note, selecting 'libgdk-pixbuf2-ruby1.8' for regex 'libgdk-pixbuf2.*'
Note, selecting 'libgdk-pixbuf2.0-common' for regex 'libgdk-pixbuf2.*'
Note, selecting 'libgdk-pixbuf2-ruby' for regex 'libgdk-pixbuf2.*'
Package libgdk-pixbuf2.0-doc is not installed, so not removed
Package libgdk-pixbuf2-ruby is not installed, so not removed
Package libgdk-pixbuf2-ruby1.8 is not installed, so not removed
Package libgdk-pixbuf2-ruby1.8-dbg is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 activity-log-manager-control-center : Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but it is not going to be installed
 aisleriot : Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but it is not going to be installed
 -session-fallback but it is not going to be installed
.... 
 gnome-system-tools : Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but it is not going to be installed
 ...
 libgweather-3-0 : Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but it is not going to be installed
 libgwibber-gtk2 : Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but it is not going to be installed
 libindicate-gtk3 : Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but it is not going to be installed
 libindicator3-7 : Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but it is not going to be installed
 libindicator7 : Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but it is not going to be installed
 libmetacity-private0 : Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but it is not going to be installed
 libnotify4 : Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but it is not going to be installed
 libnux-2.0-0 : Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but it is not going to be installed
 libpeas-1.0-0 : Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but it is not going to be installed
...
 xfce4-systemload-plugin : Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but it is not going to be installed
 xfce4-taskmanager : Depends: libgdk-pixbuf2.0-0 (>= 2.21.6) but it is not going to be installed
 xfce4-terminal : Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but it is not going to be installed
 xfce4-verve-plugin : Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but it is not going to be installed
 xfce4-weather-plugin : Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but it is not going to be installed
 xfce4-xkb-plugin : Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but it is not going to be installed
 xfdesktop4 : Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but it is not going to be installed
 xfwm4 : Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but it is not going to be installed
 xscreensaver-data : Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but it is not going to be installed
 xscreensaver-data-extra : Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but it is not going to be installed
 xscreensaver-gl : Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but it is not going to be installed
 xscreensaver-gl-extra : Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but it is not going to be installed
 zenity : Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but it is not going to be installed
[B]E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


[COLOR=Blue]>>>>> I keep getting this noisy message :[/COLOR] 
[COLOR=Red]dpkg-query: error: file triggers record mentions illegal package name `libgdk-pixbuf2.0-0'[/COLOR]
[/B]

---

### Post by amermc on 2012-07-12
SOLVED : I got it .. I have edited the following file : 
[COLOR=Red]**sudo nano /var/lib/dpkg/triggers/File**[/COLOR]

It has had several packages in it with **i386** tag .. I have changed them to [COLOR=Red]**am64**[/COLOR]. That made some duplicate entries ....which I have deleted. It worked for me.

I have found this information in this link > [http://ubuntuforums.org/showthread.php?t=2006840](http://ubuntuforums.org/showthread.php?t=2006840)
Replace the following lines:
 
 /usr/lib/x86_64-linux-gnu/gio/modules libglib2.0-0
 /usr/lib/gio/modules libglib2.0-0
 /usr/share/glib-2.0/schemas libglib2.0-0
 
 With this:
 
 /usr/lib/x86_64-linux-gnu/gio/modules libglib2.0-0:**amd64**
 /usr/lib/gio/modules libglib2.0-0:**amd64**
 /usr/share/glib-2.0/schemas libglib2.0-0:**amd64**
 
 Then run:
 
 sudo dpkg --configure -a[COLOR=Red]The problem was caused by some package installed in both versions i386 and am64 (32-bit and 64-bit). I have had to keep only the 64-bit versions.[/COLOR]
Now apt-get behaves well as usual.

Thank you drs305 for your fast replies. ;)

---

### Post by drs305 on 2012-07-12
Thanks for sharing the solution. :-)

That's a new one for me.

If you don't have any other issues, would you please mark the thread SOLVED via the 'Thread Tools' link to the top right of the first post. It will help others who might have the same problem pinpoint the solution.

Happy Ubuntu-ing !

---

### Post by amermc on 2012-07-13
> **drs305 said:**
> Thanks for sharing the solution. :-)

That's a new one for me.

If you don't have any other issues, would you please mark the thread SOLVED via the 'Thread Tools' link to the top right of the first post. It will help others who might have the same problem pinpoint the solution.

Happy Ubuntu-ing !
Thank you too. :)

---

