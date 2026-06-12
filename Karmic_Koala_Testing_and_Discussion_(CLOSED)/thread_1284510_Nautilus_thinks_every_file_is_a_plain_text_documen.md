---
title: "Nautilus thinks every file is a plain text document"
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Bios Element on 2009-10-06
Bug report: [https://bugs.launchpad.net/ubuntu/+source/shared-mime-info/+bug/444962](https://bugs.launchpad.net/ubuntu/+source/shared-mime-info/+bug/444962)

After the latest round of updates I rebooted and now Nautilus thinks every file is a plain text document. This includes .avi, .ogg, .mp3, .doc, everything. Programs will still run fine however and I can still force totem to open video files and the like.

Anyone else having this issue?

---

### Post by Ormente on 2009-10-06
I have it to... and thumbnails are not rendered either if tey are not allready. Plus i have some cryptic overlay text on desktop and in nautilus.

---

### Post by rogerdean on 2009-10-06
yup, both symptoms here too... this is one quirky beta ;)

---

### Post by Bios Element on 2009-10-06
> **Ormente said:**
> I have it to... and thumbnails are not rendered either if tey are not allready. Plus i have some cryptic overlay text on desktop and in nautilus.

The overlay might be from the "preview" nautilus is attempting to give like it usually does with text files.

---

### Post by estevez on 2009-10-06
same here... nautilus, or file type associations are broken

---

### Post by Bios Element on 2009-10-06
Bug Report has already been posted: [https://bugs.launchpad.net/ubuntu/+source/shared-mime-info/+bug/444962](https://bugs.launchpad.net/ubuntu/+source/shared-mime-info/+bug/444962)

I'm posting the updates I've made since the last time I 'know' it was working correctly. Might help narrow down which package it is.

I suspect it was shared-mime-info (0.60-2) to 0.70-0ubuntu1. Anyone else recently update this?

```

Commit Log for Tue Oct  6 17:21:41 2009


Upgraded the following packages:
acpi-support (0.126) to 0.127
aptdaemon (0.10+bzr242-0ubuntu3) to 0.10+bzr258-0ubuntu1
aspell-en (6.0-0-5.1ubuntu2) to 6.0-0-5.1ubuntu3
at-spi (1.28.0-0ubuntu1) to 1.28.0-0ubuntu2
binutils (2.19.91.20091001-0ubuntu2) to 2.19.91.20091006-0ubuntu1
capplets-data (1:2.28.0-0ubuntu3) to 1:2.28.0-0ubuntu4
coreutils (7.4-2) to 7.4-2ubuntu1
devicekit-power (010+git20090913-0ubuntu2) to 011-1
empathy (2.28.0-0ubuntu2+ppa9.10+1) to 2.28.0.1-1ubuntu2
empathy-doc (2.28.0-0ubuntu2+ppa9.10+1) to 2.28.0.1-1ubuntu2
evolution-couchdb (0.3.0-0ubuntu2) to 0.3.1-0ubuntu1
gettext (0.17-6ubuntu2) to 0.17-8ubuntu1
gettext-base (0.17-6ubuntu2) to 0.17-8ubuntu1
gnome-bluetooth (2.28.0-0ubuntu2) to 2.28.1-0ubuntu1
gnome-control-center (1:2.28.0-0ubuntu3) to 1:2.28.0-0ubuntu4
gnome-power-manager (2.28.0-0ubuntu2) to 2.28.0-0ubuntu3
gstreamer0.10-ffmpeg (0.10.8.2-1) to 0.10.9-1
gstreamer0.10-tools (0.10.24.4-1) to 0.10.25-1
gtk2-engines-pixbuf (2.18.1-1ubuntu1) to 2.18.2-1
hunspell-en-us (20070829-2ubuntu3) to 20070829-2ubuntu4
libatspi1.0-0 (1.28.0-0ubuntu1) to 1.28.0-0ubuntu2
libdevkit-power-gobject1 (010+git20090913-0ubuntu2) to 011-1
libempathy-common (2.28.0-0ubuntu2+ppa9.10+1) to 2.28.0.1-1ubuntu2
libempathy-gtk-common (2.28.0-0ubuntu2+ppa9.10+1) to 2.28.0.1-1ubuntu2
libempathy-gtk28 (2.28.0-0ubuntu2+ppa9.10+1) to 2.28.0.1-1ubuntu2
libempathy30 (2.28.0-0ubuntu2+ppa9.10+1) to 2.28.0.1-1ubuntu2
libgail-common (2.18.1-1ubuntu1) to 2.18.2-1
libgail18 (2.18.1-1ubuntu1) to 2.18.2-1
libgnome-bluetooth7 (2.28.0-0ubuntu2) to 2.28.1-0ubuntu1
libgnome-window-settings1 (1:2.28.0-0ubuntu3) to 1:2.28.0-0ubuntu4
libgstreamer0.10-0 (0.10.24.4-1) to 0.10.25-1
libgtk2.0-0 (2.18.1-1ubuntu1) to 2.18.2-1
libgtk2.0-bin (2.18.1-1ubuntu1) to 2.18.2-1
libgtk2.0-common (2.18.1-1ubuntu1) to 2.18.2-1
libmp4v2-0 (1:1.6dfsg-0.2ubuntu4) to 1:1.6dfsg-0.2ubuntu5
libspeechd2 (0.6.7+git20090914~unofficial-0ubuntu1) to 0.6.7+git20090914~unofficial-0ubuntu2
linux-firmware (1.20) to 1.21
linux-generic (2.6.31.11.22) to 2.6.31.12.23
linux-headers-generic (2.6.31.11.22) to 2.6.31.12.23
linux-image-generic (2.6.31.11.22) to 2.6.31.12.23
linux-libc-dev (2.6.31-11.38) to 2.6.31-12.39
locales (2.9+git20090617-1) to 2.9+git20090617-2
os-prober (1.34) to 1.35
pm-utils (1.2.5-2ubuntu5) to 1.2.5-2ubuntu6
python-aptdaemon (0.10+bzr242-0ubuntu3) to 0.10+bzr258-0ubuntu1
python-aptdaemon-gtk (0.10+bzr242-0ubuntu3) to 0.10+bzr258-0ubuntu1
python-gst0.10 (0.10.16.3-1) to 0.10.17-1
python-pyatspi (1.28.0-0ubuntu1) to 1.28.0-0ubuntu2
python-speechd (0.6.7+git20090914~unofficial-0ubuntu1) to 0.6.7+git20090914~unofficial-0ubuntu2
shared-mime-info (0.60-2) to 0.70-0ubuntu1
software-center (0.4.5) to 0.4.6
speech-dispatcher (0.6.7+git20090914~unofficial-0ubuntu1) to 0.6.7+git20090914~unofficial-0ubuntu2
tomboy (1.0.0-0ubuntu1) to 1.0.0-0ubuntu2
wget (1.11.4-2ubuntu1) to 1.11.4-2ubuntu2

Installed the following packages:
linux-headers-2.6.31-12 (2.6.31-12.39)
linux-headers-2.6.31-12-generic (2.6.31-12.39)
linux-image-2.6.31-12-generic (2.6.31-12.39)


Commit Log for Tue Oct  6 00:24:24 2009


Upgraded the following packages:
devicekit-power (010+git20090913-0ubuntu1) to 010+git20090913-0ubuntu2
evolution (2.28.0-0ubuntu3) to 2.28.0-0ubuntu4
evolution-common (2.28.0-0ubuntu3) to 2.28.0-0ubuntu4
evolution-documentation-en (2.28.0-0ubuntu3) to 2.28.0-0ubuntu4
evolution-plugins (2.28.0-0ubuntu3) to 2.28.0-0ubuntu4
gnome-power-manager (2.28.0-0ubuntu1) to 2.28.0-0ubuntu2
libdevkit-power-gobject1 (010+git20090913-0ubuntu1) to 010+git20090913-0ubuntu2
modemmanager (0.2.git.20090923t083842.f2a3825-0ubuntu1) to 0.2.git.20091003t063318.aa78b5f-0ubuntu1
network-manager-gnome (0.8~a~git.20090923t220421.1ac8ffd-0ubuntu4) to 0.8~a~git.20091002t194214.8515a07-0ubuntu1

```

---

### Post by VMC on 2009-10-06
> **Ormente said:**
> I have it to... and thumbnails are not rendered either if tey are not allready. Plus i have some cryptic overlay text on desktop and in nautilus.

I have the same thing, and that overlay is always part of "/etc/grub/grub.cfg" right side of text!? :confused:

---

### Post by rex4u on 2009-10-06
Plz check here (alt+f2) gconf-editor>Desktop>Gnome>Thumbnailers.
Check all the associations and rectify if needed.

Good luck...

---

### Post by Bios Element on 2009-10-06
> **rex4u said:**
> Plz check here (alt+f2) gconf-editor>Desktop>Gnome>Thumbnailers.
Check all the associations and rectify if needed.

Good luck...

Thanks for the idea. I thought it might be a related issue but it's really not. The problem is mime is borked meaning everything defaults to a "text" file.

---

### Post by VMC on 2009-10-06
Thanks for finding and reporting that bug link. I updated that "It affects me too", to it.

---

### Post by rogerdean on 2009-10-06
Could some kind soul please post a link to shared-mime-info 0.60-2 mentioned in the bug? Then I can downgrade and all will be well
Cheers

---

### Post by tim1 on 2009-10-06
> **rogerdean said:**
> Could some kind soul please post a link to shared-mime-info 0.60-2 mentioned in the bug? Then I can downgrade and all will be well
Cheers

[http://archive.ubuntu.com/ubuntu/pool/main/s/shared-mime-info/](http://archive.ubuntu.com/ubuntu/pool/main/s/shared-mime-info/)

---

### Post by rogerdean on 2009-10-06
thanks very much. do you know what command i'd use to force it to install over the later version? can't seem to find the option in synaptic...

---

### Post by Bios Element on 2009-10-06
> **rogerdean said:**
> thanks very much. do you know what command i'd use to force it to install over the later version? can't seem to find the option in synaptic...

Commandline is sudo dpkg -i debnamehere.deb. I used the deb from [http://packages.debian.org/squeeze/i386/shared-mime-info/download](http://packages.debian.org/squeeze/i386/shared-mime-info/download) and it seems to have done the trick.

**Warning: I cannot promise that deb will work and I may be totally wrong.**

---

### Post by rex4u on 2009-10-06
Pray that u are right and deb works...;)

---

### Post by Bios Element on 2009-10-06
> **rex4u said:**
> Pray that u are right and deb works...;)

Well I can confirm it worked for me. Now we just need to make sure the actual problem is fixed.

---

### Post by VMC on 2009-10-06
It's a downgrade, and yes it worked for me as well.

---

### Post by todak on 2009-10-06
Apparently it only affects the user. Open nautilus as root, then browse to your home folder. Each file opens with its respective application.

---

### Post by praveenmarkandu on 2009-10-06
thanks. worked well

may i also add, that this package causes another bug which blurs the icon when you stretch it on the desktop

---

### Post by whoop on 2009-10-06
I'll just drag and drop until this gets fixed :-p

---

### Post by VMC on 2009-10-06
> **Ormente said:**
> I have it to... and thumbnails are not rendered either if tey are not allready. Plus i have some cryptic overlay text on desktop and in nautilus.

Does anyone else get this overlay. My thinking is that it came about with the new update shared-mime-info_0.70. You won't be able to see it unless you have a lighter background. Here's what it looks like. I might have to file a bug report if unrelated to this issue.

---

### Post by jhawk on 2009-10-06
try nautilus -c

```

(nautilus:2428): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
running nautilus_self_check_file_utilities
running nautilus_self_check_file_operations
running nautilus_self_check_directory
running nautilus_self_check_file
running nautilus_self_check_icon_container
running nautilus_self_check_file_utilities
running nautilus_self_check_file_operations
running nautilus_self_check_directory
running nautilus_self_check_file
running nautilus_self_check_icon_container

```

It even lists the *.desktop contents at times.

Bad initialization

---

### Post by Bios Element on 2009-10-06
> **VMC said:**
> Does anyone else get this overlay. My thinking is that it came about with the new update shared-mime-info_0.70. You won't be able to see it unless you have a lighter background. Here's what it looks like. I might have to file a bug report if unrelated to this issue.

If you read the first page you'd see other people had it + it was a related bug. >.> Reading the [bug report]("https://bugs.launchpad.net/ubuntu/+source/shared-mime-info/+bug/444962") is helpful too...

Note that the command

```
update-mime-database.real -V ~/.local/share/mime/
```

Seems to do the trick.

---

### Post by VMC on 2009-10-06
> **Bios Element said:**
> 

```
update-mime-database.real -V ~/.local/share/mime/
```

Seems to do the trick.This didn't accomplish anything. Still there.

Also, had you read my quote you would have noticed that I reference the first page. Nothing on the bug report reflects what I showed.

---

### Post by TrueJournals on 2009-10-06
> **VMC said:**
> This didn't accomplish anything. Still there.

Also, had you read my quote you would have noticed that I reference the first page. Nothing on the bug report reflects what I showed.

I had this symptom (it's hard to say about the desktop... didn't have any files there), and I ran the command given, and that fixed it for me...  Did you
```
nautilus -q
``` or restart after?

---

### Post by VMC on 2009-10-06
> **TrueJournals said:**
> I had this symptom (it's hard to say about the desktop... didn't have any files there), and I ran the command given, and that fixed it for me...  Did you
```
nautilus -q
``` or restart after?

Thanks for your help. I didn't realize I needed to, but on next boot it was all cleared up. I think that nautilus -q would have worked quicker if I had know. Thanks again.

---

### Post by autocrosser on 2009-10-06
All worked here also---many thanks!!!

---

### Post by cor2y on 2009-10-07
the fix offered is to do
```
update-mime-database.real -V ~/.local/share/mime/
```
Which should put everything back to normal.

---

### Post by beemzet on 2009-10-07
> **cor2y said:**
> the fix offered is to do
```
update-mime-database.real -V ~/.local/share/mime/
```
Which should put everything back to normal.

It says directory does not exist

---

### Post by mgsfan on 2009-10-07
> **cor2y said:**
> the fix offered is to do
```
update-mime-database.real -V ~/.local/share/mime/
```
Which should put everything back to normal.


worked like a charm..after restarting

---

### Post by beemzet on 2009-10-07
if it doesn't, then this one should:

sudo update-mime-database /usr/local/share/mime

---

### Post by oboedad55 on 2009-10-07
> **cor2y said:**
> the fix offered is to do
```
update-mime-database.real -V ~/.local/share/mime/
```
Which should put everything back to normal.

This fixed me up after a restart. Thanks!

---

### Post by mc4man on 2009-10-07
there will be an update to glib available shortly that should take care this
glib2.0 - 2.22.1-0ubuntu2

---

### Post by TonKi on 2009-10-07
rm -rf ~/.local/share/mime/

fixes it too

---

### Post by rohitfeb14 on 2009-10-07
this worked very well for me too :)

---

### Post by rohitfeb14 on 2009-10-07
> **beemzet said:**
> if it doesn't, then this one should:

sudo update-mime-database /usr/local/share/mime

I had to create the mime folder and some other folders too..
but then it worked :)

---

### Post by chrismine on 2009-10-07
> **Bios Element said:**
> If you read the first page you'd see other people had it + it was a related bug. >.> Reading the [bug report]("https://bugs.launchpad.net/ubuntu/+source/shared-mime-info/+bug/444962") is helpful too...

Note that the command

```
update-mime-database.real -V ~/.local/share/mime/
```Seems to do the trick.
Worked for me!

---

### Post by Kazune on 2009-10-07
Worked for me too! ^-^ Yay! 
*goes to delete his thread for this problem*

---

### Post by tjeremiah on 2009-10-07
I have it too. Cant get into much detail now because I gotta run to class (:P) but basically the same as described on page one.

---

### Post by tjeremiah on 2009-10-07
> **mc4man said:**
> there will be an update to glib available shortly that should take care this
glib2.0 - 2.22.1-0ubuntu2

when and how do you know this? :P

---

### Post by Bend3r on 2009-10-07
> **Bios Element said:**
> If you read the first page you'd see other people had it + it was a related bug. >.> Reading the [bug report]("https://bugs.launchpad.net/ubuntu/+source/shared-mime-info/+bug/444962") is helpful too...

Note that the command

```
update-mime-database.real -V ~/.local/share/mime/
```

Seems to do the trick.

Worked Perfect. Thx.

---

### Post by rkelly on 2009-10-07
> **tjeremiah said:**
> when and how do you know this? :P

Check launchpad:

[https://bugs.launchpad.net/ubuntu/+source/shared-mime-info/+bug/444962](https://bugs.launchpad.net/ubuntu/+source/shared-mime-info/+bug/444962)

It's in posting #23.

---

### Post by emarkay on 2009-10-07
Yes, this one bit me late last night - it's fixed now with the methods used above.

---

### Post by whoop on 2009-10-07
It's also fixed now just by upgrading...

---

