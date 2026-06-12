---
title: "dpkg: error processing apt (--configure):"
date: 2010-04-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by I Forgot My Username on 2010-04-10
I'm having problems getting apt-get and dpkg to do any thing here's the output of apt-get -f install
```

tyler@server:~$ sudo apt-get -f install
[sudo] password for tyler: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  mesa-utils libtalloc1 linux-backports-modules-nouveau-lucid-generic
  linux-headers-2.6.31-19 libdmraid1.0.0.rc15 libdmraid1.0.0.rc16
  xulrunner-1.9.1 libsensors3 linux-headers-2.6.32-15
  linux-headers-2.6.32-15-generic libicu40 libjpeg7
  xulrunner-1.9.1-gnome-support ttf-dejavu-extra
  linux-backports-modules-nouveau-2.6.32-15-generic ggzcore-bin libevview1
  libindicate-gtk1 libdns53 libesd-alsa0 libggzmod4 libcompress-bzip2-perl
  gnome-pilot-conduits libtotem-plparser12 gnome-pilot python2.5 libisccc50
  libcdio7 policykit sdparm redland-utils python-celementtree liblwres50
  libkpathsea4 libprotobuf3 libpolkit-gnome0 python-sexy libggz2
  libpolkit-dbus2 libbind9-50 libevdocument1 libxtrap6 libgdata5 libiw29
  nvidia-185-modaliases ttf-dejavu linux-headers-2.6.31-19-generic libisccfg50
  libxklavier15 libdb4.6 libindicate3 compiz-fusion-plugins-extra libggzcore9
  miscfiles dmraid python-elementtree libgnome-desktop-2-11 libisc50
  gnome-blackjack raptor-utils libreadline5 libpolkit-grant2 sound-juicer
  libpolkit2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 617 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up apt (0.7.25.3ubuntu5) ...
dpkg: error processing apt (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 apt
E: Sub-process /usr/bin/dpkg returned an error code (1)

```Any help would be appreciated, I haven't been able to update since Alpha 3.

---

### Post by I Forgot My Username on 2010-04-12
ANY help would be appreciated.  Is there any command you need to see the output of?  Literally every attempt to install anything results in
```
[FONT=monospace]
[/FONT]dpkg: error processing apt (--configure):[FONT=monospace]
   [/FONT]subprocess installed post-installation script returned error exit status 1[FONT=monospace]
[/FONT]Errors were encountered while processing:[FONT=monospace]
 [/FONT]apt[FONT=monospace]
[/FONT]E: Sub-process /usr/bin/dpkg returned an error code (1)[FONT=monospace]
[/FONT]
```

---

### Post by TrueJournals on 2010-04-13
Don't know if it will do anything, but try doing the following:
```
sudo apt-get clean
sudo apt-get -f install
```

The problem is that the "apt" update you downloaded seems to have a post-install script that fails.  I believe apt-get clean will clear out this file, causing apt-get -f install to re-download the apt package.

---

### Post by SevenMachines on 2010-04-13
you could either run 
$dpkg --configure -a
but add the -D<octal> option to generate more debug output. See dpkg -Dh for a handy list of debugging codes to replace <octal>

or you could try adding
set -x
to /var/lib/dpkg/info/apt.postinst (after set -e) then running 
$ sudo dpkg --configure -a
should give a better idea of where its failing

---

### Post by I Forgot My Username on 2010-04-14
Unfortunately, the apt-get clean, apt-get -f install didn't work, so I looked in /var/lib/dpgk/info to try SevenMachine's suggestion, but the directory was empty(no hidden files either) and dpkg --configure -a returned the same error as sll the other attempts.  dpkg --configure -a -D2 printed fork/exec [that file SevenMachine mentioned] and exited with the same error.

---

### Post by SevenMachines on 2010-04-14
hi, 2 things.
Firstly, the info dir must surely exist, thats where the script lives thats failing! i notice you mis-spelled dpkg in your last post as dpgk, the script you are looking for is
/var/lib/dpkg/info/apt.postinst

secondly, the -D option to dpkg can be 'bitwised', try adding various options together to get more detail, -D2 is very general, you can try -D200, -D300, -D3773, etc and see if anything comes up.

Personally i prefer the adding set -x to the failing script method as you can see all commands run and exactly whats going wrong. If /var/lib/dpkg/info really, really doesnt exist then that is likely to be a much more serious problem

---

### Post by dino99 on 2010-04-14
i've had that kind of problem recently: "1 not fully installed or removed."

how i've worked around:

- need to identify which package(s) have failed
- if that package was upgraded, ( the upgrade failed), see what synaptic said about that package and remove/purge if the previous release is still installed.
- then search locations for that package(s) with nautilus and erase it (them)
- there are some possibilities with bleachbit & gconf cleaner to wipe broken links and old settings.
- run again sudo dpkg --configure -a  &  sudo apt-get install -f
- try again update & upgrade

---

### Post by ljrmorgan on 2010-04-14
I got this error today after running sudo apt-get upgrade:
```
...
Preconfiguring packages ...
(Reading database ... 242014 files and directories currently installed.)
Preparing to replace libpam-modules 1.1.1-2ubuntu1 (using .../libpam-modules_1.1.1-2ubuntu2_amd64.deb) ...
Unpacking replacement libpam-modules ...
Processing triggers for man-db ...
Setting up libpam-modules (1.1.1-2ubuntu2) ...

E: Sub-process /usr/bin/dpkg received a segmentation fault.

```

The crash report icon came up in the system tray, but that had an error too - something to do with the report being invalid. When I ran the next upgrade libpam-modules wasn't mentioned - does anyone know if it will have been installed properly?

---

### Post by davidbarton on 2010-04-16
I had the same problem and was able to fix it.

I had a user in the admin group (/etc/groups) that no longer existed.  To test this, run:
```
getent group admin
```

If that isn't your problem, look into /var/lib/dpkg/info/apt.postinst or whatever file is referenced when you run (just search for --configure):
```
dpkg --configure -a -D 3773 2>&1 | less
```

To the top of the script, I added the command:
```
exec > /tmp/apt.log 2>&1
```
And then liberally sprinkled echo commands until I found the problem.  The script contains set -e, which forces the script to abort if any command within the script fails.

Good luck!

---

### Post by I Forgot My Username on 2010-04-18
Well, it's there now(I could swear I was in the right dir before).  Here's the output after "set -x" was added
```

tyler@server:~$ sudo dpkg --configure -a
Setting up apt (0.7.25.3ubuntu6) ...
+ test -f /etc/apt/trusted.gpg
+ dpkg --compare-versions 0.7.25.3ubuntu1 lt-nl 0.7.25.3ubuntu2
+ set_apt_proxy_from_gconf
+ cut -d, -f1
+ cut -d: -f4
+ getent group admin
+ admin_user=tyler
+ [ -n tyler ]
+ [ -x /usr/bin/sudo ]
+ [ -z  ]
+ [ -x /usr/bin/gconftool ]
+ sudo -u tyler gconftool --get /system/http_proxy/use_http_proxy
+ use=
dpkg: error processing apt (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 apt

```

---

### Post by thsths on 2010-04-20
> **I Forgot My Username said:**
> ```

+ set_apt_proxy_from_gconf

```
This line bombed for me. Maybe it is because my X session is a bit shot at the moment due to a (failed) partial upgrade. So maybe gconf does not work properly. But I would expect a package as essential as apt to be a bit more robust during installation.

---

### Post by I Forgot My Username on 2010-04-22
> **thsths said:**
> This line bombed for me. Maybe it is because my X session is a bit shot at the moment due to a (failed) partial upgrade. So maybe gconf does not work properly. But I would expect a package as essential as apt to be a bit more robust during installation.
Seems to have been my problem also, thanks to all of you for your help and insightful suggestions.  My Lucid Lynx installation is now completely up to date.

---

