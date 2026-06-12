---
title: "Change to please gnome-shell-extension-weather load with Focal &amp; up"
date: 2020-04-28
forum: Installation &amp; Upgrades
---

### Post by dino99 on 2020-04-28
Sadly neither Debian nor Ubuntu archives have recent version; and that useful applet  fails to load.

What to do for solving the issue ? :
- goto [https://gitlab.com/jenslody/gnome-shell-extension-openweather/-/blob/d9a90d38439d81544ce7d1307ea74f16f2d8cb72/src/extension.js](https://gitlab.com/jenslody/gnome-shell-extension-openweather/-/blob/d9a90d38439d81544ce7d1307ea74f16f2d8cb72/src/extension.js)
- and click on the "copy file content" icon (first one on the right side)

- open a terminal, and edit /usr/share/gnome-shell/extensions/openweather-extension@jenslody.de/extension.js
- select and erase the code, then paste by right clicking, and save then exit gedit

- do the same steps for prefs.js to get a working icon

That it, now do "Alt+F2+r" to reload gnome-shell: you might see the weather icon ontop bar
Add your weather Api Key provider if not already registered.

---

### Post by curts on 2020-05-09
Many thanks to @dino99 for this patch. This at least gets the temperature visible. Icons appear to be broken, however, so not a complete fix.

Here are the warnings and error from /var/log/syslog for the repo version of the extension:

```
ay  9 13:53:29 panther2 gnome-shell[3497]: Usage of object.actor is deprecated 
for OpenweatherMenuButton#012get@resource:///org/gnome/shell/ui/environment.js:2
87:29#012_init@/usr/share/gnome-shell/extensions/openweather-extension@jenslody.
de/extension.js:192:9#012wrapper@resource:///org/gnome/gjs/modules/script/_legac
y.js:82:27#012enable@/usr/share/gnome-shell/extensions/openweather-extension@jen
slody.de/extension.js:1648:23#012_callExtensionEnable@resource:///org/gnome/shel
l/ui/extensionSystem.js:166:32#012loadExtension@resource:///org/gnome/shell/ui/e
xtensionSystem.js:336:26#012_loadExtensions/<@resource:///org/gnome/shell/ui/ext
ensionSystem.js:577:18#012collectFromDatadirs@resource:///org/gnome/shell/misc/f
ileUtils.js:27:17#012_loadExtensions@resource:///org/gnome/shell/ui/extensionSys
tem.js:552:19#012_enableAllExtensions@resource:///org/gnome/shell/ui/extensionSy
stem.js:586:18#012_sessionUpdated@resource:///org/gnome/shell/ui/extensionSystem.js:617:18#012init@resource:///org/gnome/shell/ui/extensionSystem.js:55:14#012_initializeUI@resource:///org/gnome/shell/ui/main.js:257:22#012start@resource:///org/gnome/shell/ui/main.js:146:5#012@<main>:1:47
May  9 13:53:29 panther2 gnome-shell[3497]: Usage of object.actor is deprecated for OpenweatherMenuButton#012get@resource:///org/gnome/shell/ui/environment.js:287:29#012_init@/usr/share/gnome-shell/extensions/openweather-extension@jenslody.de/extension.js:195:9#012wrapper@resource:///org/gnome/gjs/modules/script/_legacy.js:82:27#012enable@/usr/share/gnome-shell/extensions/openweather-extension@jenslody.de/extension.js:1648:23#012_callExtensionEnable@resource:///org/gnome/shell/ui/extensionSystem.js:166:32#012loadExtension@resource:///org/gnome/shell/ui/extensionSystem.js:336:26#012_loadExtensions/<@resource:///org/gnome/shell/ui/extensionSystem.js:577:18#012collectFromDatadirs@resource:///org/gnome/shell/misc/fileUtils.js:27:17#012_loadExtensions@resource:///org/gnome/shell/ui/extensionSystem.js:552:19#012_enableAllExtensions@resource:///org/gnome/shell/ui/extensionSystem.js:586:18#012_sessionUpdated@resource:///org/gnome/shell/ui/extensionSystem.js:617:18#012init@resource:///org/gnome/shell/ui/extensionSystem.js:55:14#012_initializeUI@resource:///org/gnome/shell/ui/main.js:257:22#012start@resource:///org/gnome/shell/ui/main.js:146:5#012@<main>:1:47
May  9 13:53:29 panther2 gnome-shell[3497]: JS ERROR: Extension [email]openweather-extension@jenslody.de[/email]: TypeError: this.actor.reparent is not a function#012_init@/usr/share/gnome-shell/extensions/openweather-extension@jenslody.de/extension.js:195:20#012wrapper@resource:///org/gnome/gjs/modules/script/_legacy.js:82:27#012enable@/usr/share/gnome-shell/extensions/openweather-extension@jenslody.de/extension.js:1648:23#012_callExtensionEnable@resource:///org/gnome/shell/ui/extensionSystem.js:166:32#012loadExtension@resource:///org/gnome/shell/ui/extensionSystem.js:336:26#012_loadExtensions/<@resource:///org/gnome/shell/ui/extensionSystem.js:577:18#012collectFromDatadirs@resource:///org/gnome/shell/misc/fileUtils.js:27:17#012_loadExtensions@resource:///org/gnome/shell/ui/extensionSystem.js:552:19#012_enableAllExtensions@resource:///org/gnome/shell/ui/extensionSystem.js:586:18#012_sessionUpdated@resource:///org/gnome/shell/ui/extensionSystem.js:617:18#012init@resource:///org/gnome/shell/ui/extensionSystem.js:55:14#012_initializeUI@resource:///org/gnome/shell/ui/main.js:257:22#012start@resource:///org/gnome/shell/ui/main.js:146:5#012@<main>:1:47
```

---

### Post by dino99 on 2020-05-10
HI Curts

follow the same steps but within prefs.js to fix the icon issue ):P

---

### Post by curts on 2020-05-12
No, manually updating prefs.js  did not fix all the icons.

---

### Post by dino99 on 2020-05-13
I have used 'copy file contents' icon on top right side of [https://gitlab.com/jenslody/gnome-shell-extension-openweather/-/blob/d9a90d38439d81544ce7d1307ea74f16f2d8cb72/src/prefs.js](https://gitlab.com/jenslody/gnome-shell-extension-openweather/-/blob/d9a90d38439d81544ce7d1307ea74f16f2d8cb72/src/prefs.js)

then erased the previous code from the installed prefs.fs, and paste the new code, save it and do Alt+F2+r

voila, running gnome-shell on X, the weather icon is ok here on Groovy, but only get a red icon on Focal.

---

### Post by dino99 on 2020-05-15
Actual prefs.js is buggy on Focal:

when clicking on temp icon, then hitting the bottom right icon of the opened temp box, get these errors:

TypeError: this.location_length_spin is null

Stack trace:
  [email]initWindow@/usr/share/gnome-shell/extensions/openweather-extension@jenslody.de/prefs.js[/email]:393:9
  [email]wrapper@resource:///org/gnome/gjs/modules/script/_legacy.js[/email]:82:27
  [email]_init@/usr/share/gnome-shell/extensions/openweather-extension@jenslody.de/prefs.js[/email]:121:14
  [email]wrapper@resource:///org/gnome/gjs/modules/script/_legacy.js[/email]:82:27
  [email]buildPrefsWidget@/usr/share/gnome-shell/extensions/openweather-extension@jenslody.de/prefs.js[/email]:1115:17
  [email]_init@resource:///org/gnome/Shell/Extensions/js/extensionsService.js[/email]:207:40
  OpenExtensionPrefsAsync/<@resource:///org/gnome/Shell/Extensions/js/extensionsService.js:122:28
  [email]asyncCallback@resource:///org/gnome/gjs/modules/core/overrides/Gio.js[/email]:132:13
  [email]run@resource:///org/gnome/Shell/Extensions/js/dbusService.js[/email]:175:20
  [email]main@resource:///org/gnome/Shell/Extensions/js/main.js[/email]:19:13
  [email]run@resource:///org/gnome/gjs/modules/script/package.js[/email]:222:19
  [email]start@resource:///org/gnome/gjs/modules/script/package.js[/email]:206:5
  @/usr/share/gnome-shell/org.gnome.Shell.Extensions:1:17

---

### Post by dino99 on 2020-05-31
Workaround about certificate expiration since May 30th

1)cd /usr/share/ca-certificates/mozilla/
2)sudo mv AddTrust_External_Root.crt  !AddTrust_External_Root.crt
3)sudo update-ca-certificates
Alt+F2+r

For knowledge
[https://www.agwa.name/blog/post/fixing_the_addtrust_root_expiration](https://www.agwa.name/blog/post/fixing_the_addtrust_root_expiration)

---

### Post by P-I H on 2020-05-31
According to this discussion there are some ways to fix the problem.
[https://gitlab.com/jenslody/gnome-shell-extension-openweather/-/issues/272#note_352539958](https://gitlab.com/jenslody/gnome-shell-extension-openweather/-/issues/272#note_352539958)

---

### Post by daniewicz on 2020-05-31
The ca-certificates.conf edit discussed in this link worked for me on 20.04

---

### Post by vaslemonidis on 2020-09-29
To skip all the trouble just run:

sudo apt install gnome-common
cd ~ && git clone git://gitlab.com/jenslody/gnome-shell-extension-openweather.git
cd ~/gnome-shell-extension-openweather
./autogen.sh && make local-install

---

### Post by curts on 2021-07-03
One needs to have libglib2.0-dev installed for the compile to succeed.

---

