---
title: "Flatpak install and update only works with sudo"
date: 2023-10-26
forum: Installation &amp; Upgrades
---

### Post by francwalter on 2023-10-26
Hallo
since a while, flatpak works only as root. When I do:
```
flatpak update
```
I get the error:
```
Error: Can't pull from untrusted non-gpg verified remote
```
In the "Software" app it seems the same, I cannot install via Flatpak (Flathub), I get "Installation von ... nicht möglich: Can't pull from untrusted non-gpg verified remote" see attached Screenshot.
In the Terminal, when I do:
```
sudo flatpak update
```
it works, also installing. But not without sudo. 
And ***sudo flatpak repair*** does not fix it.
I looked where my flatpak apps are in the file system and found e.g. brave Browser in:
```
/var/lib/flatpak/app/com.brave.Browser
```
var is owned by root and has 755, so does .../app/... and all apps there in it, is this normal?

Anybody knows how to fix this?

Thanks, frank

---

### Post by #&amp;thj^% on 2023-10-26
I don't use brave or software-center but will you show this please:
```
stat /var/lib/flatpak/
  File: /var/lib/flatpak/
  Size: 7         	Blocks: 18         IO Block: 512    directory
Device: 0,44	Inode: 10304       Links: 6
Access: (0755/drwxr-xr-x)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2023-10-22 07:50:06.233937824 -0600
Modify: 2023-10-22 07:55:53.452249458 -0600
Change: 2023-10-22 07:55:53.452249458 -0600
 Birth: 2023-10-22 07:50:06.233937824 -0600

```
is how mine reads, 
Do you remember how you installed flatpak?

---

### Post by francwalter on 2023-10-26
```
$ stat /var/lib/flatpak/
  Datei: /var/lib/flatpak/
 Größe: 4096          Blöcke: 8          EA Block: 4096   Verzeichnis
Gerät: 832h/2098d    Inode: 18092860    Verknüpfungen: 8
Zugriff: (0755/drwxr-xr-x)  Uid: (    0/    root)   Gid: (    0/    root)
Zugriff: 2023-10-26 13:49:55.638699126 +0200
Modifiziert: 2023-10-26 13:29:36.181706911 +0200
Geändert: 2023-10-26 13:29:36.181706911 +0200
Geburt: 2023-02-21 23:15:56.254613372 +0100
```

I remember that there was a how-to and I followed it. Half a year ago. I wanted to install the app**Tangram**, so I had to install Flatpak or so.
It worked for a good while, but since maybe two months I have these issues.

---

### Post by #&amp;thj^% on 2023-10-26
I kind of suspected that, but for what it's worth:
```
flatpak install Tangram
Looking for matches&#8230;
Similar refs found for &#8216;Tangram&#8217; in remote &#8216;flathub&#8217; (system):

   1) app/dk.tangramgames.mrrescue/x86_64/stable
   2) app/re.sonny.Tangram/x86_64/stable

Which do you want to use (0 to abort)? [0-2]: 

```
No special method used on my end.
maybe remove and purge flatpak and reinstall normally.
```
sudo apt autoremove --purge flatpak
```
A dry run shows this:
```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages will be REMOVED:
  flatpak* libmalcontent-0-0* libostree-1-1*
0 upgraded, 0 newly installed, 3 to remove and 4 not upgraded.
Purg flatpak [1.14.4-2]
Purg libmalcontent-0-0 [0.11.1-1]
Purg libostree-1-1 [2023.6-1]

```
If happy with that return re-install:
```
sudo apt install flatpak
```
and a source for applications:
```
flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
```
log-out first then check with flatpak:
```
flatpak update
Looking for updates&#8230;

Nothing to do.

```
You may have to re-install any flatpaks you once had so fist get a list if needed:
```
flatpak list
Name           Application ID                 Version Branch      Installation
Tor Browser L&#8230; &#8230;micahflee.torbrowser-launcher 0.3.6   stable      system
Mesa           &#8230;eedesktop.Platform.GL.default 23.2.1  23.08       system
Mesa (Extra)   &#8230;eedesktop.Platform.GL.default 23.2.1  23.08-extra system
nvidia-535-11&#8230; &#8230;Platform.GL.nvidia-535-113-01         1.4         system
openh264       &#8230;freedesktop.Platform.openh264 2.1.0   2.2.0       system
KDE Applicati&#8230; org.kde.Platform                       5.15-23.08  system

```
I'm not a fan of GUI's so i never install this, but you might want it:
```
sudo apt install gnome-software-plugin-flatpak
```

---

### Post by #&amp;thj^% on 2023-10-26
> **1fallen said:**
> I kind of suspected that, but for what it's worth:
```
flatpak install Tangram
Looking for matches…
Similar refs found for ‘Tangram’ in remote ‘flathub’ (system):

   1) app/dk.tangramgames.mrrescue/x86_64/stable
   2) app/re.sonny.Tangram/x86_64/stable

Which do you want to use (0 to abort)? [0-2]: 

```
No special method used on my end.
maybe remove and purge flatpak and reinstall normally.
```
sudo apt autoremove --purge flatpak
```
A dry run shows this:
```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages will be REMOVED:
  flatpak* libmalcontent-0-0* libostree-1-1*
0 upgraded, 0 newly installed, 3 to remove and 4 not upgraded.
Purg flatpak [1.14.4-2]
Purg libmalcontent-0-0 [0.11.1-1]
Purg libostree-1-1 [2023.6-1]

```
If happy with that return re-install:
```
sudo apt install flatpak
```
and a source for applications:
```
flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
```
log-out first then check with flatpak:
```
flatpak update
Looking for updates…

Nothing to do.

```
You may have to re-install any flatpaks you once had so fist get a list if needed:
```
flatpak list
Name           Application ID                 Version Branch      Installation
Tor Browser L… …micahflee.torbrowser-launcher 0.3.6   stable      system
Mesa           …eedesktop.Platform.GL.default 23.2.1  23.08       system
Mesa (Extra)   …eedesktop.Platform.GL.default 23.2.1  23.08-extra system
nvidia-535-11… …Platform.GL.nvidia-535-113-01         1.4         system
openh264       …freedesktop.Platform.openh264 2.1.0   2.2.0       system
KDE Applicati… org.kde.Platform                       5.15-23.08  system

```
I'm not a fan of GUI's so i never install this, but you might want it:
```
sudo apt install gnome-software-plugin-flatpak
```
Forgot this, my remotes used:
```
flatpak remotes --show-details
Name    Title   URL                          Collection ID Subset Filter Priority Options … … Homepage             Icon
flathub Flathub https://dl.flathub.org/repo/ -             -      -      1        system  … … https://flathub.org/ https://dl.flathub.org/repo/logo.svg

```

---

### Post by francwalter on 2023-10-27
Tried it up to here:
```

$flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpak

$f@franc-comp-ubuntu:~$ flatpak remotes --show-details
Name    Titel ADRESSE                      Sammlungskennung Teilmenge Filter Priorität Optionen &#8230; &#8230; Webseite Symbol
flathub -     https://dl.flathub.org/repo/ -                -         -      1         system   &#8230; &#8230; -        -

```
 
Now I am doing a logout...

---

### Post by francwalter on 2023-10-27
...and in the Software app (GUI) all my apps are as not installed. But they still are!
My list (before uninstall flatpak --purge) was (on pastebin): [flatpak list]("https://paste.ubuntu.com/p/kXTjwpMMV7/")
But when I look into Applications button (at the bottom left) I still can see all installed apps and start them too!
Tried different, Decoder, MAME, Brave, all start!
I thought when uninstalling flatpak (with --purge at least) my apps installed through flatpak should have been gone too. Strange.

---

### Post by francwalter on 2023-10-27
Now I get, when I do flatpak update, warnings, that an app is not installed:
```
$ flatpak update
Suche nach Aktualisierungen &#8230;
Fehler: No such ref 'runtime/org.videolan.VLC.Locale/x86_64/stable' in remote flathub
```
When I remove it:
```
$ flatpak remove vlc
Found installed ref &#8216;app/org.videolan.VLC/x86_64/stable&#8217; (system). Is this correct? [Y/n]: y


        KENNUNG                        Zweig         Op
 1. [-] org.videolan.VLC               stable        r
 2. [-] org.videolan.VLC.Locale        stable        r

Deinstallation abgeschlossen.
```
But VLC is still installed! Maybe this is my issue, that I installed some apps double (with apt and flatpak)?
After again flatpak update, the next package is missing:
```
$ flatpak update
Suche nach Aktualisierungen &#8230;
Fehler: No such ref 'runtime/org.kde.WaylandDecoration.QGnomePlatform-decoration/x86_64/5.15-22.08' in remote flathub
```

So I uninstalled one after the other manually often I had to uninstall first apps because of dependencies (e.g. KDE Application Platform could not be uninstalled before many other apps).
And now with flatpak update it is empty:
```
$ flatpak update
Suche nach Aktualisierungen &#8230;

Nichts zu tun.
```
Now I have to reinstall with Software (GUI) all my apps and look if all that helped...

Btw:the package gnome-software-plugin-flatpak I had already installed. And Tangram was the browser like Tangram (app/re.sonny.Tangram/x86_64/stable).

---

### Post by #&amp;thj^% on 2023-10-27
```
flatpak install Tangram
Looking for matches…
Similar refs found for ‘Tangram’ in remote ‘flathub’ (system):

   1) app/dk.tangramgames.mrrescue/x86_64/stable
   2) app/re.sonny.Tangram/x86_64/stable

Which do you want to use (0 to abort)? [0-2]: 2
Required runtime for re.sonny.Tangram/x86_64/stable (runtime/org.gnome.Platform/x86_64/44) found in remote flathub
Do you want to install it? [Y/n]: 

re.sonny.Tangram permissions:
    ipc            network       fallback-x11       pulseaudio
    wayland        x11           dri                system dbus access [1]

    [1] org.freedesktop.GeoClue2


        ID                          Branch   Op  Remote   Download
 1.     org.gnome.Platform.Locale   44       i   flathub  < 340.6*MB (partial)
 2.     org.gnome.Platform          44       i   flathub  < 326.8*MB
 3.     re.sonny.Tangram.Locale     stable   i   flathub   < 66.1*kB (partial)
 4.     re.sonny.Tangram            stable   i   flathub  < 243.4*kB

Proceed with these changes to the system installation? [Y/n]: 
```

```
flatpak list
Name            Application ID                Version Branch      Installation
Tor Browser La… …icahflee.torbrowser-launcher 0.3.6   stable      system
Flatseal        com.github.tchx84.Flatseal    2.1.0   stable      system
System Monitor… …ing.system-monitoring-center 2.25.1  stable      system
Mesa            …edesktop.Platform.GL.default 23.1.9  22.08       system
Mesa (Extra)    …edesktop.Platform.GL.default 23.1.9  22.08-extra system
Mesa            …edesktop.Platform.GL.default 23.2.1  23.08       system
Mesa (Extra)    …edesktop.Platform.GL.default 23.2.1  23.08-extra system
nvidia-535-113… …latform.GL.nvidia-535-113-01         1.4         system
openh264        …reedesktop.Platform.openh264 2.1.0   2.0         system
openh264        …reedesktop.Platform.openh264 2.1.0   2.2.0       system
GNOME Applicat… org.gnome.Platform                    44          system
GNOME Applicat… org.gnome.Platform                    45          system
KDE Applicatio… org.kde.Platform                      5.15-22.08  system
KDE Applicatio… org.kde.Platform                      5.15-23.08  system
Tangram         re.sonny.Tangram              3.0     stable      system

```
Now I remove it:
```
flatpak remove re.sonny.Tangram 


        ID                             Branch        Op
 1. [-] re.sonny.Tangram               stable        r
 2. [-] re.sonny.Tangram.Locale        stable        r

Uninstall complete.

```
I cleanup after "every" removal
```
sudo flatpak repair
[sudo] password for me: 
[7/39] Verifying flathub:runtime/io.github.hakandundar34coding.system_monitoring[9/39] Verifying flathub:app/com.github.micahflee.torbrowser-launcher/x86_64/sta[18/39] Verifying flathub:runtime/org.freedesktop.Platform.GL.default/x86_64/22.[21/39] Verifying flathub:app/io.github.hakandundar34coding.system-monitoring-ce[32/39] Verifying flathub:runtime/org.freedesktop.Platform.GL.default/x86_64/23.[33/39] Verifying flathub:runtime/org.freedesktop.Platform.openh264/x86_64/2.2.0[34/39] Verifying flathub:runtime/org.freedesktop.Platform.GL.default/x86_64/23.[36/39] Verifying flathub:runtime/org.freedesktop.Platform.GL.default/x86_64/22.[39/39] Verifying flathub:runtime/org.freedesktop.Platform.GL.nvidia-535-113-01/x86_64/1.4…
Checking remotes...
Pruning objects
Erasing .removed

```
check again with list:
```
flatpak list
Name                                               Application ID                                                      Version              Branch                  Installation
Tor Browser Launcher                               com.github.micahflee.torbrowser-launcher                            0.3.6                stable                  system
Flatseal                                           com.github.tchx84.Flatseal                                          2.1.0                stable                  system
System Monitoring Center                           io.github.hakandundar34coding.system-monitoring-center              2.25.1               stable                  system
Mesa                                               org.freedesktop.Platform.GL.default                                 23.1.9               22.08                   system
Mesa (Extra)                                       org.freedesktop.Platform.GL.default                                 23.1.9               22.08-extra             system
Mesa                                               org.freedesktop.Platform.GL.default                                 23.2.1               23.08                   system
Mesa (Extra)                                       org.freedesktop.Platform.GL.default                                 23.2.1               23.08-extra             system
nvidia-535-113-01                                  org.freedesktop.Platform.GL.nvidia-535-113-01                                            1.4                     system
openh264                                           org.freedesktop.Platform.openh264                                   2.1.0                2.0                     system
openh264                                           org.freedesktop.Platform.openh264                                   2.1.0                2.2.0                   system
GNOME Application Platform version 44              org.gnome.Platform                                                                       44                      system
GNOME Application Platform version 45              org.gnome.Platform                                                                       45                      system
KDE Application Platform                           org.kde.Platform                                                                         5.15-22.08              system
KDE Application Platform                           org.kde.Platform                                                                         5.15-23.08              system

```
I don't use VLC but it seems to pull a lot of information ie:
```
flatpak search vlc
Name                                      Description                                                                                          Application ID                         Version   Branch    Remotes
Pause Click plugin for VLC                VLC plugin that allows to pause/play a video by clicking on the video image.                         org.videolan.VLC.Plugin.pause_click    2.2.0     3-23.08   flathub
Pause Click plugin for VLC                VLC plugin that allows to pause/play a video by clicking on the video image.                         org.videolan.VLC.Plugin.pause_click    2.2.0     3-22.08   flathub
MakeMKV plugin for VLC                    Provides MakeMKV features for direct Blu-ray playback in VLC. Use MakeMKV app to set the license.    org.videolan.VLC.Plugin.makemkv        1.17.5    3-22.08   flathub
MakeMKV plugin for VLC                    Provides MakeMKV features for direct Blu-ray playback in VLC. Use MakeMKV app to set the license.    org.videolan.VLC.Plugin.makemkv        1.16.7    3-21.08   flathub
MakeMKV plugin for VLC                    Provides MakeMKV features for direct Blu-ray playback in VLC. Use MakeMKV app to set the license.    org.videolan.VLC.Plugin.makemkv                  3-20.08   flathub
MakeMKV plugin for VLC                    Provides MakeMKV features for direct Blu-ray playback in VLC. Use MakeMKV app to set the license.    org.videolan.VLC.Plugin.makemkv                  3-19.08   flathub
Bluray Java menus (BDJ) plugin for VLC    Provides Bluray Java menus (BDJ) support in VLC.                                                     org.videolan.VLC.Plugin.bdj                      3-23.08   flathub
Bluray Java menus (BDJ) plugin for VLC    Provides Bluray Java menus (BDJ) support in VLC.                                                     org.videolan.VLC.Plugin.bdj                      3-22.08   flathub
Bluray Java menus (BDJ) plugin for VLC    Provides Bluray Java menus (BDJ) support in VLC.                                                     org.videolan.VLC.Plugin.bdj                      3-21.08   flathub
Bluray Java menus (BDJ) plugin for VLC    Provides Bluray Java menus (BDJ) support in VLC.                                                     org.videolan.VLC.Plugin.bdj                      3-20.08   flathub
Bluray Java menus (BDJ) plugin for VLC    Provides Bluray Java menus (BDJ) support in VLC.                                                     org.videolan.VLC.Plugin.bdj                      3-19.08   flathub
VLC                                       VLC media player, the open-source multimedia player                                                  org.videolan.VLC                       3.0.19    stable    flathub
FDK-AAC Encoding Plugin for VLC           Provides better AAC encoding and HE profiles support.                                                org.videolan.VLC.Plugin.fdkaac                   3-23.08   flathub
FDK-AAC Encoding Plugin for VLC           Provides better AAC encoding and HE profiles support.                                                org.videolan.VLC.Plugin.fdkaac                   3-22.08   flathub
FDK-AAC Encoding Plugin for VLC           Provides better AAC encoding and HE profiles support.                                                org.videolan.VLC.Plugin.fdkaac                   3-21.08   flathub
FDK-AAC Encoding Plugin for VLC           Provides better AAC encoding and HE profiles support.                                                org.videolan.VLC.Plugin.fdkaac                   3-20.08   flathub
FDK-AAC Encoding Plugin for VLC           Provides better AAC encoding and HE profiles support.                                                org.videolan.VLC.Plugin.fdkaac                   3-19.08   flathub
GridPlayer                                Play videos side-by-side                                                                             com.vzhd1701.gridplayer                0.5.3     stable    flathub
MediathekView                             Access to public German TV Mediathek                                                                 de.mediathekview.MediathekView         14.0.0    stable    flathub
Audio Sharing                             Share your computer audio                                                                            de.haeckerfelix.AudioSharing           0.2.2     stable    flathub
*me*&#57520;*~*&#57520;*

```
I guess it could have a impact on your system with Apt and Flatpaks, but it shouldn't.
Keep me posted

---

### Post by francwalter on 2023-10-27
> **1fallen said:**
> ...
```
flatpak update
Looking for updates…

Nothing to do.

```
...
I have the same, when there are **no** updates. *Nothing to do.* But when I have updates, I can only update (in Terminal) them with sudo.
Do **you** can update, if there are updates, **without** sudo in Terminal?
And in the GUI "Software" which I start without sudo it is the same. 
Funny that I can uninstall apps without sudo, but not install.

Is there maybe a log from flatpak?
It should say, why the remote is non-gpg verified and untrusted.

---

### Post by francwalter on 2023-10-27
> **francwalter said:**
> ...
Now I have to reinstall with Software (GUI) all my apps and look if all that helped...
...
I have to say, that I did this first on a test system (cloned from my main Ubuntu). So there it worked, and now I did the same on my main Ubuntu:
I uninstalled all my apps, removed flatpak, reinstalled it and  installed again all my apps. Without sudo, so it might work now :)
Here is the pastebin of my flatpak list before uninstall: [flatpak list]("https://paste.ubuntu.com/p/WSYqnCTrbR/")
Before I did this, I tried if my settings are untouched. I did that with Chromium, where I logged into Google account, removed Chromium, reinstalled it, and still my Google login was there :)
Here is the pastebin of my flatpak now: [flatpak list after reinstall]("https://paste.ubuntu.com/p/GQdJsDjq3T/")

I hope I am good now :)
Thanks for your help!!!
frank

---

### Post by #&amp;thj^% on 2023-10-27
Never hurts to try before you buy, All looks good now.
Happy to help

---

### Post by francwalter on 2023-10-27
I have to add, that I had to [add gnome-software-plugin-flatpak]("https://flathub.org/setup/Ubuntu"):
```
sudo apt install gnome-software-plugin-flatpak
```
because now my Icon for Software was gone :)

And I had double apps, because I forgot the Ubuntu snap, [here is my list of snaps on pastebin]("https://paste.ubuntu.com/p/xpJMbMR5ZQ/")
I found some other doubles, so I removed them on flatpak (flatpak remove <appname>)
I need to focus more on what I am doing, I guess ;)

---

### Post by #&amp;thj^% on 2023-10-29
> **francwalter said:**
> 
I need to focus more on what I am doing, I guess ;)

I at times need that as well. :)

---

