---
title: "Ubuntu Tweak 'Janitor' has broken my system"
date: 2012-02-14
forum: Installation &amp; Upgrades
---

### Post by greggc2006 on 2012-02-14
Since trying Janitor once I have a growing list of problems with updates.

Problem 1 - Kernel won't update anymore, I'm stuck @ 3.0.0-15
```
gregg@ubuntu64-W150HRM:~$ sudo apt-get upgrade
[sudo] password for gregg: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  xserver-xorg-video-intel
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
5 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-3.0.0-14-generic (3.0.0-14.23) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.0.0-14.23 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.0.0-14.23 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
update-initramfs: Generating /boot/initrd.img-3.0.0-14-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
/etc/default/grub: 11: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.0.0-14-generic.postinst line 1010.
dpkg: error processing linux-image-3.0.0-14-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.0.0-15-generic (3.0.0-15.26) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.0.0-15.24 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.0.0-15.24 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
update-initramfs: Generating /boot/initrd.img-3.0.0-15-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
/etc/default/grub: 11: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.0.0-15-generic.postinst line 1010.
dpkg: error processing linux-image-3.0.0-15-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.0.0-16-generic (3.0.0-16.28) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.0.0-16-generic /boot/vmlinuz-3.0.0-16-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.0.0-16-generic /boot/vmlinuz-3.0.0-16-generic
update-initramfs: Generating /boot/initrd.img-3.0.0-16-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.0.0-16-generic /boot/vmlinuz-3.0.0-16-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.0.0-16-generic /boot/vmlinuz-3.0.0-16-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.0.0-16-generic /boot/vmlinuz-3.0.0-16-generic
/etc/default/grub: 11: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.0.0-16-generic.postinst line 1010.
dpkg: error processing linux-image-3.0.0-16-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.0.0-16-generic; however:
  Package linux-image-3.0.0-16-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.0.0.16.19); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    No apport report written because MaxReports has already been reached
                   Errors were encountered while processing:
 linux-image-3.0.0-14-generic
 linux-image-3.0.0-15-generic
 linux-image-3.0.0-16-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Problem 2 - My GIMP has run away and won't come back!!

```
gregg@ubuntu64-W150HRM:~$ sudo apt-get install gimp
[sudo] password for gregg: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 gimp : Depends: libglib2.0-0 (>= 2.31.2) but 2.31.0-0ubuntu1~oneiric1 is to be installed
E: Unable to correct problems, you have held broken packages.
```

Anyone who can point me in the right direction will be spoken of for generations!!! I would just do a fresh install of Ubuntu but I have more stuff on disk than I have external storage to back it all up!!

---

### Post by savanna on 2012-02-14
In the first lot of errors, this line gives you a hint:
[B]
/etc/default/grub: 11: splash: not found[/B]

ie looks like line 11 in that file is incorrect - comment it out, or post the contents of that file?

For the second lot of errors, run aptitude and use it to resolve the dependency problems. Do a web search on "aptitude resolve conflicts". Or if I get time I might produce a video showing how to drive aptitude :-) Aptitude is basically your "powertool" for resolving package issues (you may have to install it first).

---

### Post by drs305 on 2012-02-14
You can probably fix the 'splash' error fairly easily. The message indicates the grub update is failing because of the line 11 entry in /etc/default/grub. This is most likely the line which includes "quiet splash".

Open the file as root and remove the "splash" entry. Keep whatever else is on the line. Save the file, then update-grub.
```

gksu gedit +11 /etc/default/grub # Edit and save the file, then run:
sudo update-grub
```

---

### Post by greggc2006 on 2012-02-15
> **savanna said:**
> In the first lot of errors, this line gives you a hint:
[B]
/etc/default/grub: 11: splash: not found[/B]

ie looks like line 11 in that file is incorrect - comment it out, or post the contents of that file?

Great, I hadn't even noticed that error, #'d it out and that's all sorted.

> **savanna said:**
> For the second lot of errors, run aptitude and use it to resolve the dependency problems. Do a web search on "aptitude resolve conflicts". Or if I get time I might produce a video showing how to drive aptitude :-) Aptitude is basically your "powertool" for resolving package issues (you may have to install it first).

Aptitude is doing my head in, I have tried using it before and now I remember why I never made a habit of it! I'm sure it is a great powertool for those who can understand it but I find it the most difficult and unintuitive piece of software I have ever come across. Can you do that video??, I cannot get it to do anything other than tell me it's going to remove 90% of the software on my system!

---

### Post by greggc2006 on 2012-02-16
Oh dear, it seems that my short attempt at getting somewhere with Aptitude has caused a new problem, Gnome-shell is all mangled. If I try to log in to 'Gnome' it falls back to the 'Gnome no-effects' environment. I can then use a terminal to do gnome-shell --replace but it's all twitchy and full of problems. Terminal shows:-
```
gregg@ubuntu64-W150HRM:~$ gnome-shell --replace
folks-DEBUG: individual-aggregator.vala:310: Setting primary store IDs to defaults.
folks-DEBUG: individual-aggregator.vala:338: Primary store IDs are 'eds' and 'system'.
    JS ERROR: !!!   WARNING: 'assignment to undeclared variable workViewInjections'
    JS ERROR: !!!   WARNING: file '/usr/share/gnome-shell/extensions/native-window-placement@gnome-shell-extensions.gnome.org/extension.js' line 113 exception 0 number 156
      JS LOG: System monitor applet init from /usr/share/gnome-shell/extensions/system-monitor@paradoxxx.zero.gmail.com

Clutter-WARNING **: Attempting to add actor of type 'ShellGenericContainer' to a container of type 'StBoxLayout', but the actor has already a parent of type 'StBoxLayout'.

St-WARNING **: Actor of type 'ShellGenericContainer' is not a child of the StBoxLayout container
Window manager warning: Log level 16: Unable to register authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for the given subject
Window manager warning: Log level 16: Error registering polkit authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for the given subject (polkit-error-quark 0)
      JS LOG: GNOME Shell started at Thu Feb 16 2012 18:22:36 GMT+0000 (GMT)
Window manager warning: Log level 32: a new manager occured at org.globalmenu.manager, :1.6
    JS ERROR: !!!   Exception was: TypeError: Shell.util_icon_from_string is not a function
    JS ERROR: !!!     lineNumber = '1300'
    JS ERROR: !!!     fileName = '"/usr/share/gnome-shell/js/ui/telepathyClient.js"'
    JS ERROR: !!!     stack = '"()@/usr/share/gnome-shell/js/ui/telepathyClient.js:1300
("Connection error","gtk-dialog-error")@/usr/share/gnome-shell/js/ui/telepathyClient.js:1281
MultiNotificationSource("Connection error","gtk-dialog-error")@/usr/share/gnome-shell/js/ui/telepathyClient.js:1271
()@/usr/share/gnome-shell/js/ui/telepathyClient.js:474
([object _private_TelepathyGLib_Account],[object _private_GLib_ParamSpec])@/usr/share/gnome-shell/js/ui/telepathyClient.js:461
"'
    JS ERROR: !!!     message = '"Shell.util_icon_from_string is not a function"'
    JS ERROR: !!!   Exception was: TypeError: Shell.util_icon_from_string is not a function
    JS ERROR: !!!     lineNumber = '1300'
    JS ERROR: !!!     fileName = '"/usr/share/gnome-shell/js/ui/telepathyClient.js"'
    JS ERROR: !!!     stack = '"()@/usr/share/gnome-shell/js/ui/telepathyClient.js:1300
("Connection error","gtk-dialog-error")@/usr/share/gnome-shell/js/ui/telepathyClient.js:1281
MultiNotificationSource("Connection error","gtk-dialog-error")@/usr/share/gnome-shell/js/ui/telepathyClient.js:1271
()@/usr/share/gnome-shell/js/ui/telepathyClient.js:474
([object _private_TelepathyGLib_Account],[object _private_GLib_ParamSpec])@/usr/share/gnome-shell/js/ui/telepathyClient.js:461
"'
    JS ERROR: !!!     message = '"Shell.util_icon_from_string is not a function"'
    JS ERROR: !!!   Exception was: TypeError: Shell.util_icon_from_string is not a function
    JS ERROR: !!!     lineNumber = '1300'
    JS ERROR: !!!     fileName = '"/usr/share/gnome-shell/js/ui/telepathyClient.js"'
    JS ERROR: !!!     stack = '"()@/usr/share/gnome-shell/js/ui/telepathyClient.js:1300
("Connection error","gtk-dialog-error")@/usr/share/gnome-shell/js/ui/telepathyClient.js:1281
MultiNotificationSource("Connection error","gtk-dialog-error")@/usr/share/gnome-shell/js/ui/telepathyClient.js:1271
()@/usr/share/gnome-shell/js/ui/telepathyClient.js:474
([object _private_TelepathyGLib_Account],[object _private_GLib_ParamSpec])@/usr/share/gnome-shell/js/ui/telepathyClient.js:461
"'
    JS ERROR: !!!     message = '"Shell.util_icon_from_string is not a function"'
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus 0x2c00007 (InfoPanelS) with a timestamp of 0.  This shouldn't happen!
```

It appears that a metric shed-load of 'stuff' has been removed and I would like to know exactly what has gone so I can use apt-get or synaptic to put it all back. How do I find out, I assume that Aptitude creates a log somewhere?

Thanks.

---

### Post by drs305 on 2012-02-17
You can open the log file viewer (I get to it by typing 'log' in Dash) and take a look at 'dpkg.log'. You can also open the /var/log/dpkg.log manually. It has a record of installs and removals and might include the actions affecting your system. 

It might be easier to view what's happened by filtering the file with the grep command to include only 'install ' or 'remove'. I know if you purge a package it shows up as remove. I don't know if automatically removed packages display as 'remove' but you run this command. If it doesn't return a list of removed file, inspect the contents of the log and perhaps use a different filter:
```
grep 'remove' /var/log/dpkg.log
```

---

### Post by greggc2006 on 2012-02-18
> **drs305 said:**
> You can open the log file viewer (I get to it by typing 'log' in Dash) and take a look at 'dpkg.log'. You can also open the /var/log/dpkg.log manually. It has a record of installs and removals and might include the actions affecting your system. 

It might be easier to view what's happened by filtering the file with the grep command to include only 'install ' or 'remove'. I know if you purge a package it shows up as remove. I don't know if automatically removed packages display as 'remove' but you run this command. If it doesn't return a list of removed file, inspect the contents of the log and perhaps use a different filter:
```
grep 'remove' /var/log/dpkg.log
```

Thanks, looking at them now and the grep comand shows me:-
```
2012-02-12 16:33:24 remove browser-plugin-gnash 0.8.10~git20110618-3ubuntu1 <none>
2012-02-12 16:33:26 remove ekiga 3.3.2-0ubuntu1 <none>
2012-02-12 16:33:29 remove gdebi 0.8.1 <none>
2012-02-12 16:33:31 remove gdebi-core 0.8.1 <none>
2012-02-12 16:33:34 remove gedit-plugins 3.2.0-0ubuntu1 <none>
2012-02-12 16:33:37 remove gir1.2-gucharmap-2.90 1:3.2.2-1ubuntu1~oneiric1 <none>
2012-02-12 16:33:38 remove gnome-games 1:3.2.1-0ubuntu3~oneiric1 <none>
2012-02-12 16:33:39 remove glchess 1:3.2.1-0ubuntu3~oneiric1 <none>
2012-02-12 16:33:41 remove glines 1:3.2.1-0ubuntu3~oneiric1 <none>
2012-02-12 16:33:42 remove gnash 0.8.10~git20110618-3ubuntu1 <none>
2012-02-12 16:33:43 remove gnash-common 0.8.10~git20110618-3ubuntu1 <none>
2012-02-12 16:33:45 remove gnect 1:3.2.1-0ubuntu3~oneiric1 <none>
2012-02-12 16:33:46 remove gnibbles 1:3.2.1-0ubuntu3~oneiric1 <none>
2012-02-12 16:33:47 remove gnobots2 1:3.2.1-0ubuntu3~oneiric1 <none>
2012-02-12 16:33:49 remove gnome-core 1:3.0+1ubuntu1 <none>
2012-02-12 16:33:49 remove gnome-backgrounds 3.2.0-0ubuntu1 <none>
2012-02-12 16:33:50 remove gnome-dictionary 3.2.1-0ubuntu1 <none>
2012-02-12 16:33:52 remove gnome-games-extra-data 3.2.0-0ubuntu1 <none>
2012-02-12 16:33:53 remove gnome-icon-theme-extras 3.0.0-2ubuntu1 <none>
2012-02-12 16:33:54 remove gnotravex 1:3.2.1-0ubuntu3~oneiric1 <none>
2012-02-12 16:33:55 remove gnotski 1:3.2.1-0ubuntu3~oneiric1 <none>
2012-02-12 16:33:58 remove gnuchess-book 1.01-2 <none>
2012-02-12 16:33:59 remove gnuchess 5.07-7 <none>
2012-02-12 16:33:59 remove gtali 1:3.2.1-0ubuntu3~oneiric1 <none>
2012-02-12 16:34:01 remove hamster-applet 2.32.1-0ubuntu5 <none>
2012-02-12 16:34:02 remove iagno 1:3.2.1-0ubuntu3~oneiric1 <none>
2012-02-12 16:34:03 remove libaudio2:i386 1.9.2-8ubuntu1 <none>
2012-02-12 16:34:04 remove libboost-date-time1.46.1 1.46.1-5ubuntu2 <none>
2012-02-12 16:34:05 remove libboost-program-options1.46.1 1.46.1-5ubuntu2 <none>
2012-02-12 16:34:05 remove libboost-signals1.46.1 1.46.1-5ubuntu2 <none>
2012-02-12 16:34:06 remove libopal3.10.2 3.10.2~dfsg-0ubuntu1 <none>
2012-02-12 16:34:06 remove libcapi20-3 1:3.12.20071127-0ubuntu9 <none>
2012-02-12 16:34:07 remove libdrm-intel1:i386 2.4.31+git20120208.230ec7d7-0ubuntu0sarvatt~oneiric <none>
2012-02-12 16:34:07 remove libdrm-nouveau1a:i386 2.4.31+git20120208.230ec7d7-0ubuntu0sarvatt~oneiric <none>
2012-02-12 16:34:08 remove libdrm-radeon1:i386 2.4.31+git20120208.230ec7d7-0ubuntu0sarvatt~oneiric <none>
2012-02-12 16:34:09 remove libdrm2:i386 2.4.31+git20120208.230ec7d7-0ubuntu0sarvatt~oneiric <none>
2012-02-12 16:34:09 remove libgdict-1.0-6 3.2.1-0ubuntu1 <none>
2012-02-12 16:34:10 remove libmng1:i386 1.0.10-1ubuntu1 <none>
2012-02-12 16:34:10 remove liblcms1:i386 1.19.dfsg-1ubuntu2 <none>
2012-02-12 16:34:11 remove libllvm2.9 2.9+dfsg-3ubuntu2 <none>
2012-02-12 16:34:11 remove libllvm2.9:i386 2.9+dfsg-3ubuntu2 <none>
2012-02-12 16:34:12 remove libpciaccess0:i386 0.12.902-1~oneiric1 <none>
2012-02-12 16:34:12 remove libpt2.10.2 2.10.2~dfsg-0ubuntu1 <none>
2012-02-12 16:34:13 remove libspandsp2 0.0.6~pre18-2 <none>
2012-02-12 16:34:14 remove libxxf86vm1:i386 1:1.1.1-2 <none>
2012-02-12 16:34:14 remove liferea 1.6.6b-0ubuntu2 <none>
2012-02-12 16:34:15 remove liferea-data 1.6.6b-0ubuntu2 <none>
2012-02-12 16:34:16 remove menu-xdg 0.5 <none>
2012-02-12 16:34:16 remove quadrapassel 1:3.2.1-0ubuntu3~oneiric1 <none>
2012-02-12 16:34:18 remove sound-juicer 2.32.1+20110330-1 <none>
2012-02-15 19:52:48 startup packages remove
2012-02-15 19:52:55 remove acroread 9.4.7-1oneiric1 <none>
2012-02-15 19:53:56 remove appmenu-qt 0.2.2-0ubuntu1.1 <none>
2012-02-15 19:53:57 remove nautilus-actions-extra 0.7.0~ppa1-0~88~oneiric1 <none>
2012-02-15 19:53:57 remove nautilus-multimedia-menu 0.4~ppa1-0~6~oneiric1 <none>
2012-02-15 19:53:58 remove nautilus-multimedia-bin 0.3-0~4~oneiric1 <none>
2012-02-15 19:53:59 remove faac 1.28-0ubuntu1 <none>
2012-02-15 19:53:59 remove flac 1.2.1-4ubuntu1 <none>
2012-02-15 19:54:00 remove imageshack-uploader 2.2+hg20100408.d802dea89428-3 <none>
2012-02-15 19:54:01 remove imageshack-uploader-common 2.2+hg20100408.d802dea89428-3 <none>
2012-02-15 19:54:02 remove lame 3.98.4-0ubuntu1 <none>
2012-02-15 19:54:02 remove lastfm 1:1.5.4.27091+dfsg-6ubuntu2 <none>
2012-02-15 19:54:04 remove libacl1:i386 2.2.51-3 <none>
2012-02-15 19:54:04 remove vorbis-tools 1.4.0-1ubuntu1 <none>
2012-02-15 19:54:05 remove libao4 1.1.0-1ubuntu1 <none>
2012-02-15 19:54:06 remove libao-common 1.1.0-1ubuntu1 <none>
2012-02-15 19:54:07 remove nspluginwrapper 1.4.4-0ubuntu3 <none>
2012-02-15 19:54:07 remove nspluginviewer:i386 1.4.4-0ubuntu3 <none>
2012-02-15 19:54:08 remove libgtk2.0-0:i386 2.24.8-2ubuntu4~oneiric1 <none>
2012-02-15 19:54:09 remove libatk1.0-0:i386 2.2.0-0ubuntu1 <none>
2012-02-15 19:54:09 remove libattr1:i386 1:2.4.46-3 <none>
2012-02-15 19:54:10 remove libcups2:i386 1.5.0-8ubuntu7 <none>
2012-02-15 19:54:10 remove libavahi-client3:i386 0.6.30-4ubuntu1 <none>
2012-02-15 19:54:11 remove libavahi-common3:i386 0.6.30-4ubuntu1 <none>
2012-02-15 19:54:11 remove libqt4-core:i386 4:4.7.4-0ubuntu8.1 <none>
2012-02-15 19:54:12 remove libqt4-script:i386 4:4.7.4-0ubuntu8.1 <none>
2012-02-15 19:54:13 remove libqt4-network:i386 4:4.7.4-0ubuntu8.1 <none>
2012-02-15 19:54:13 remove spotify-client-qt 1:0.6.2.291.gcccc1f5.116-1 <none>
2012-02-15 19:54:14 remove ubuntu-desktop 1.245.1 <none>
2012-02-15 19:54:15 remove unity-2d 4.12.0-0ubuntu1.1 <none>
2012-02-15 19:54:16 remove unity-2d-spread 4.12.0-0ubuntu1.1 <none>
2012-02-15 19:54:17 remove unity-2d-places 4.12.0-0ubuntu1.1 <none>
2012-02-15 19:54:18 remove unity-2d-panel 4.12.0-0ubuntu1.1 <none>
2012-02-15 19:54:20 remove unity-2d-launcher 4.12.0-0ubuntu1.1 <none>
2012-02-15 19:54:21 remove sni-qt 0.2.5-0ubuntu3 <none>
2012-02-15 19:54:21 remove libunity-2d-private0 4.12.0-0ubuntu1.1 <none>
2012-02-15 19:54:22 remove librecad 1.0.1+nolibs-2~daily~oneiric1 <none>
2012-02-15 19:54:23 remove libqt4-qt3support 4:4.7.4-0ubuntu8.1 <none>
2012-02-15 19:54:24 remove libqt4-designer 4:4.7.4-0ubuntu8.1 <none>
2012-02-15 19:54:24 remove virtualbox-4.1 4.1.8-75467~Ubuntu~oneiric <none>
2012-02-15 19:55:07 remove sopcast-player 0.7.4-1~lffl~natty~ppa <none>
2012-02-15 19:55:08 remove vlc 1.1.12-2~oneiric1 <none>
2012-02-15 19:55:09 remove ubuntustudio-video 0.90 <none>
2012-02-15 19:55:10 remove openshot 1.4.0-1 <none>
2012-02-15 19:55:11 remove python-mlt3 0.7.4-3 <none>
2012-02-15 19:55:12 remove melt 0.7.4-3 <none>
2012-02-15 19:55:13 remove libmlt++3 0.7.4-3 <none>
2012-02-15 19:55:13 remove libmlt4 0.7.4-3 <none>
2012-02-15 19:55:14 remove libqt4-svg 4:4.7.4-0ubuntu8.1 <none>
2012-02-15 19:55:14 remove libqt4-opengl 4:4.7.4-0ubuntu8.1 <none>
2012-02-15 19:55:15 remove libqt4-help 4:4.7.4-0ubuntu8.1 <none>
2012-02-15 19:55:16 remove xjadeo 0.6.1-1 <none>
2012-02-15 19:55:17 remove speedcrunch 0.10.1-2 <none>
2012-02-15 19:55:18 remove qt-at-spi 0.0~git20110628-0ubuntu1 <none>
2012-02-15 19:55:18 remove libqt4-webkit 4:4.7.4-0ubuntu8.1 <none>
2012-02-15 19:55:19 remove libqtwebkit4 2.2~2011week36-0ubuntu1 <none>
2012-02-15 19:55:20 remove libdbusmenu-qt2 0.9.0-0ubuntu2 <none>
2012-02-15 19:55:20 remove libqtgconf1 0.1-0ubuntu5 <none>
2012-02-15 19:55:21 remove libqtdee2 0.2.3-0ubuntu1 <none>
2012-02-15 19:55:21 remove libqtbamf1 0.2.2-0ubuntu1 <none>
2012-02-15 19:55:22 remove libdconf-qt0 0.0.0.110722-0ubuntu3 <none>
2012-02-15 19:55:23 remove libqt4-test:i386 4:4.7.4-0ubuntu8.1 <none>
2012-02-15 19:55:24 remove libpango1.0-0:i386 1.29.3+git20110916-0ubuntu1 <none>
2012-02-15 19:55:26 remove libgdk-pixbuf2.0-0:i386 2.24.0-1ubuntu1 <none>
2012-02-15 19:55:27 remove libllvm3.0:i386 3.0-4ubuntu1~edgers1 <none>
2012-02-15 19:55:27 remove libcairo2:i386 1.11.3+git20120210.f7eaf37f-0ubuntu0ricotz~oneiric0 <none>
2012-02-15 19:55:28 remove libpixman-1-0:i386 0.24.4-1~oneiric1 <none>
2012-02-15 19:55:29 remove libgssapi-krb5-2:i386 1.9.1+dfsg-1ubuntu2.2 <none>
2012-02-15 19:55:29 remove libkrb5-3:i386 1.9.1+dfsg-1ubuntu2.2 <none>
2012-02-15 19:55:30 remove libk5crypto3:i386 1.9.1+dfsg-1ubuntu2.2 <none>
2012-02-15 19:55:30 remove libkrb5support0:i386 1.9.1+dfsg-1ubuntu2.2 <none>
2012-02-15 19:55:31 remove libjasper1:i386 1.900.1-7ubuntu2.11.10.1 <none>
2012-02-15 19:55:31 remove libxft2:i386 2.2.0-3ubuntu1 <none>
2012-02-15 19:55:32 remove libfontconfig1:i386 2.8.0-3ubuntu2 <none>
2012-02-15 19:55:32 remove libfreetype6:i386 2.4.4-2ubuntu1.1 <none>
2012-02-15 19:55:33 remove libtiff4:i386 3.9.5-1ubuntu1 <none>
2012-02-15 19:55:33 remove libpng12-0:i386 1.2.46-3ubuntu1 <none>
2012-02-15 19:55:34 remove libgnutls26:i386 2.10.5-1ubuntu3 <none>
2012-02-15 19:55:35 remove libxt6:i386 1:1.1.1-2 <none>
2012-02-15 19:55:35 remove libxrandr2:i386 2:1.3.2-2 <none>
2012-02-15 19:55:36 remove libxcursor1:i386 1:1.1.12-1 <none>
2012-02-15 19:55:36 remove libxrender1:i386 1:0.9.6-2 <none>
2012-02-15 19:55:37 remove libxinerama1:i386 2:1.1.1-3 <none>
2012-02-15 19:55:37 remove libxi6:i386 2:1.4.3-3ubuntu1 <none>
2012-02-15 19:55:38 remove libxfixes3:i386 1:5.0-4 <none>
2012-02-15 19:55:38 remove libxext6:i386 2:1.3.0-3 <none>
2012-02-15 19:55:39 remove libxcb-shm0:i386 1.7-3 <none>
2012-02-15 19:55:40 remove libxcb-render0:i386 1.7-3 <none>
2012-02-15 19:55:40 remove libxcb-glx0:i386 1.7-3 <none>
2012-02-15 19:55:41 remove libxdamage1:i386 1:1.1.3-2 <none>
2012-02-15 19:55:41 remove libxcomposite1:i386 1:0.4.3-2 <none>
2012-02-15 19:55:42 remove libx11-6:i386 2:1.4.4-2ubuntu1 <none>
2012-02-15 19:55:42 remove libxcb1:i386 1.7-3 <none>
2012-02-15 19:55:43 remove libxdmcp6:i386 1:1.1.0-3 <none>
2012-02-15 19:55:43 remove libxau6:i386 1:1.0.6-3 <none>
2012-02-15 19:55:44 remove libx11-xcb1:i386 2:1.4.4-2ubuntu1 <none>
2012-02-15 19:55:44 remove libsm6:i386 2:1.2.0-2 <none>
2012-02-15 19:55:45 remove libuuid1:i386 2.19.1-2ubuntu3 <none>
2012-02-15 19:55:45 remove libthai0:i386 0.1.15-2 <none>
2012-02-15 19:55:46 remove libtasn1-3:i386 2.9-4 <none>
2012-02-15 19:55:46 remove libkeyutils1:i386 1.4-6 <none>
2012-02-15 19:55:47 remove libjpeg62:i386 6b1-1ubuntu2 <none>
2012-02-15 19:55:47 remove libice6:i386 2:1.0.7-2 <none>
2012-02-15 19:55:48 remove libgcrypt11:i386 1.5.0-1 <none>
2012-02-15 19:55:48 remove libgpg-error0:i386 1.10-0.3ubuntu1 <none>
2012-02-15 19:55:49 remove libexpat1:i386 2.0.1-7ubuntu3 <none>
2012-02-15 19:55:49 remove libdb5.1:i386 5.1.25-11 <none>
2012-02-15 19:55:50 remove libdatrie1:i386 0.2.4-3 <none>
2012-02-15 19:55:51 remove libcomerr2:i386 1.41.14-1ubuntu3 <none>
2012-02-15 19:55:51 remove musepack-tools 2:0.1~r459-1ubuntu1 <none>
2012-02-15 19:55:52 remove libcue1 1.4.0-1 <none>
2012-02-15 19:55:52 remove libmlt-data 0.7.4-3 <none>
2012-02-15 19:55:53 remove libreplaygain1 1.0~r447-1 <none>
2012-02-15 19:55:54 remove libsox-fmt-ffmpeg 14.3.2-1ubuntu1 <none>
2012-02-15 19:55:54 remove nautilus-gksu 2.0.2-5ubuntu2 <none>
2012-02-15 19:55:55 remove nautilus-open-terminal 0.19-1build1 <none>
2012-02-15 19:55:57 remove openshot-doc 1.4.0-1 <none>
2012-02-15 19:55:57 remove shotwell 0.11.6-0ubuntu0.1 <none>
2012-02-15 19:55:58 remove xserver-xorg-video-all 1:7.6+7ubuntu7.1 <none>
2012-02-15 19:55:59 remove xserver-xorg-video-intel 2:2.17.0+git20120208.13c960db-0ubuntu0sarvatt~oneiric <none>
2012-02-15 19:56:04 remove libqt4-dbus:i386 4:4.7.4-0ubuntu8.1 <none>
2012-02-15 19:56:06 remove libdbus-1-3:i386 1.4.14-1ubuntu1 <none>
2012-02-15 19:56:06 remove libqt4-declarative 4:4.7.4-0ubuntu8.1 <none>
2012-02-15 19:56:07 remove libqt4-script 4:4.7.4-0ubuntu8.1 <none>
2012-02-15 19:56:08 remove libqt4-xmlpatterns 4:4.7.4-0ubuntu8.1 <none>
2012-02-15 19:56:08 remove libqt4-network 4:4.7.4-0ubuntu8.1 <none>
2012-02-15 19:56:09 remove libqt4-dbus 4:4.7.4-0ubuntu8.1 <none>
2012-02-15 19:56:09 remove qdbus:i386 4:4.7.4-0ubuntu8.1 <none>
2012-02-15 19:56:10 remove libqt4-xml:i386 4:4.7.4-0ubuntu8.1 <none>
2012-02-15 19:56:10 remove libqtcore4:i386 4:4.7.4-0ubuntu8.1 <none>
2012-02-15 19:56:11 remove libglib2.0-0:i386 2.31.0-0ubuntu1~oneiric1 <none>
2012-02-15 19:56:12 remove libffi6:i386 3.0.11~rc1-5~oneiric1 <none>
2012-02-15 19:56:12 remove zlib1g:i386 1:1.2.3.4.dfsg-3ubuntu3 <none>
2012-02-15 19:56:13 remove libstdc++6:i386 4.6.1-9ubuntu3 <none>
2012-02-15 19:56:13 remove libselinux1:i386 2.0.98-1.1 <none>
2012-02-15 19:56:14 remove libpcre3:i386 8.12-3ubuntu2 <none>
2012-02-15 19:56:15 remove libgcc1:i386 1:4.6.1-9ubuntu3 <none>
2012-02-15 19:56:15 remove libqtgui4 4:4.7.4-0ubuntu8.1 <none>
2012-02-15 19:56:16 remove libc6:i386 2.13-20ubuntu5 <none>
2012-02-15 20:02:37 startup packages remove
2012-02-15 20:02:37 remove libavahi-common-data:i386 0.6.30-4ubuntu1 <none>
2012-02-15 20:02:38 remove libdconf-dbus-1-0 0.10.0-0ubuntu1 <none>
2012-02-15 20:02:38 remove libmng1 1.0.10-1ubuntu1 <none>
2012-02-15 20:02:39 remove libqt4-sql-mysql 4:4.7.4-0ubuntu8.1 <none>
2012-02-15 20:02:39 remove libmysqlclient16 5.1.58-1ubuntu1 <none>
2012-02-15 20:02:40 remove libqt4-sql-sqlite 4:4.7.4-0ubuntu8.1 <none>
2012-02-15 20:02:41 remove libqt4-sql 4:4.7.4-0ubuntu8.1 <none>
2012-02-15 20:02:41 remove libqt4-test 4:4.7.4-0ubuntu8.1 <none>
2012-02-15 20:02:42 remove libqt4-xml 4:4.7.4-0ubuntu8.1 <none>
2012-02-15 20:02:42 remove libqtcore4 4:4.7.4-0ubuntu8.1 <none>
2012-02-15 20:02:43 remove libtar0 1.2.11-8 <none>
2012-02-15 20:02:43 remove libva-x11-1 1.0.15-1~xup1 <none>
2012-02-15 20:02:44 remove libvlc-dev 1.1.12-2~oneiric1 <none>
2012-02-15 20:02:44 remove libvlccore-dev 1.1.12-2~oneiric1 <none>
2012-02-15 20:02:45 remove libxcb-keysyms1 0.3.8-1 <none>
2012-02-15 20:02:45 remove libxcb-randr0 1.7-3 <none>
2012-02-15 20:02:46 remove libxcb-xv0 1.7-3 <none>
2012-02-15 20:02:46 remove mysql-common 5.1.58-1ubuntu1 <none>
2012-02-15 20:02:47 remove vlc-plugin-notify 1.1.12-2~oneiric1 <none>
2012-02-15 20:02:48 remove vlc-plugin-pulse 1.1.12-2~oneiric1 <none>
2012-02-15 20:10:10 startup packages remove
2012-02-15 20:10:10 remove gimp-dbg 2.7.5-2012020901~oo <none>
2012-02-15 20:13:43 startup packages remove
2012-02-15 20:13:43 remove gimp 2.6.11-2ubuntu4+painter~oneiric1 <none>
```

I think I have a looooong task at hand!!

I have disabled all the repo's other than the cannonical and gnome ones till I get things resolved, is there an easy way to downgrade everything on my system so it's in line with what is in the currently enabled repo's??

---

### Post by ottosykora on 2012-02-18
well, I used the Janitor one time without going through all tasks it wanted do and my system became unusable.
It did even remove my installed eagle layout software, cliaming that this is obsolete.. (why? for whom?) and removed skype as well and many other things.

hmmm, no, no more this

---

### Post by drs305 on 2012-02-18
I don't readily recommend reinstalling the OS but this might be your fastest and most complete option. Of course you would want to back up any data you have in your HOME folder first.

If you can get Ubuntu to run at all you could also move your HOME folder to a separate partition first, then reinstall using manual partitioning with the separate /home option to retain your settings. You would elect to format / but NOT /home.

If you do this still be sure to make backups of your data first.

---

### Post by greggc2006 on 2012-02-18
I give up!! I am in the midst of shifting everything from /home to my other box with WOOF then it will be a format and fresh install.

Massive pita

Thanks all for your help.

---

