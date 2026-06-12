---
title: "dpkg = fail"
date: 2010-02-26
forum: Installation &amp; Upgrades
---

### Post by Ratchet-- on 2010-02-26
When I try to install something VIA Software center, there's always something else installing first.

So, I chose the obvious thing, and ran sudo dpkg --configure -a

Here's what it fed me 
```
joshua@joshua-laptop:~$ sudo dpkg --configure -a
[sudo] password for joshua: 
Setting up sun-java6-doc (6-15-1) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6u10-docs.zip jdk-6u10-docs-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 

```

Can someone give me step by step instructions? I went to the website and couldn't find either file.

---

### Post by Ratchet-- on 2010-02-26
Also, as a side note, whenever I try to install anything I get this error.

```
joshua@joshua-laptop:~$ sudo apt-get install gparted
[sudo] password for joshua: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
joshua@joshua-laptop:~$ 




```

---

### Post by drs305 on 2010-02-26
This message (second post) means that some other APT process is running. Often it is because the user is trying to run an apt command from terminal while Synaptic is open.

Check to see if any other installation apps are open. If not, and you really need to do something soon, the safest way is probably to log out and back in again, or reboot. That should definitely clear any locks on the APT processes.

You can physically delete the lock file, but removing a 'lock' on an open process is not recommended, so don't try this at least until after you have tried rebooting.

---

### Post by Ratchet-- on 2010-02-26
Okay, I  rebooted and ran this.

```
joshua@joshua-laptop:~$ sudo apt-get install gparted
[sudo] password for joshua: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
joshua@joshua-laptop:~$ sudo dpkg --configure -a
Setting up sun-java6-doc (6-15-1) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6u10-docs.zip jdk-6u10-docs-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 

```

---

### Post by Ratchet-- on 2010-02-26
Noticing that I cannot view the root folder physically, I tabbed it in terminal and got this (It may or may not be helpful)

```
joshua@joshua-laptop:~$ '/root' 
.adobe/                           jagex_runescape_preferences2.dat
.armagetronad/                    jagex_runescape_preferences.dat
armagetronad-0.2.8.2.1-win/       .java/
.bash_history                     java_ee_sdk-5_01-linux.bin
.bash_logout                      java_ee_sdk-5_01-linux.bin.sdm
.bashrc                           jdk-6u18-docs.zip
.blender/                         jdk-6u18-linux-i586.bin
.cache/                           jdk-6u18-linux-i586.bin.bak
.compiz/                          .kde/
.config/                          .local/
.dbus/                            .macromedia/
Desktop/                          .mission-control/
.dmrc                             .mozilla/
docs/                             Music/
Documents/                        nano.save
Downloads/                        .nautilus/
eagle/                            .openoffice.org/
.eagle/                           photos-20100215-0.db
.eaglerc                          Pictures/
.earth3d/                         .pida2/
.eric4/                           .profile
.esd_auth                         Public/
.eva/                             .pulse/
.evolution/                       .pulse-cookie
examples.desktop                  .pype/
Firefox_wallpaper.png             .qt/
.fontconfig/                      .recently-used
.galeon/                          .recently-used.xbel
.gconf/                           .SimDock/
.gconfd/                          .Skype/
.gegl-0.0/                        .ssh/
.gimp-2.6/                        .sudo_as_admin_successful
.gksu.lock                        .SunDownloadManager/
.gnome2/                          Swirly_Blue_Abstract.jpg
.gnome2_private/                  Templates/
.gnupg/                           .themes/
.gpilotd/                         .thumbnails/
.gpilotd.pid                      .tr2norigins/
.gstreamer-0.10/                  .update-manager-core/
.gtk-bookmarks                    .update-notifier/
.gvfs/                            .usbcreator.log
hs_err_pid1886.log                Videos/
hs_err_pid2096.log                .viminfo
hs_err_pid2528.log                .wapi/
hs_err_pid4093.log                .wine/
hs_err_pid4249.log                .wxFormBuilder
hs_err_pid4868.log                .xscreensaver-getimage.cache
.ICEauthority                     .xsession-errors
.icons/                           .xsession-errors.old
.jagex_cache_32/                  
joshua@joshua-laptop:~$ '/root' 

```

So, in mind's eye, everything is requiring the 6u10 docs, and I have 6u18.

I therefore need instructions on how to get the 6u10 docs and how to place them where they belong.

---

### Post by Ratchet-- on 2010-02-26
bump?

---

### Post by Ratchet-- on 2010-02-26
come on guys, this is frustrating and i want help.

---

### Post by oldos2er on 2010-02-26
Go to [http://java.sun.com/javase/downloads/index.jsp#docs](http://java.sun.com/javase/downloads/index.jsp#docs) , Java SE 6 Documentation , click Download.

---

### Post by Ratchet-- on 2010-02-27
That's java 6u18 documents! i already have that ! :( I need 6u10

---

### Post by oldos2er on 2010-02-27
A quick google search turned up this: [http://www.filewatcher.com/m/jdk-6u10-docs.zip.58890428.0.0.html](http://www.filewatcher.com/m/jdk-6u10-docs.zip.58890428.0.0.html)

---

