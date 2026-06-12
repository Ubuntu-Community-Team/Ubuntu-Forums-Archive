---
title: "Update Dapper -&gt; Hardy; dependency problems, etc."
date: 2008-10-22
forum: Installation &amp; Upgrades
---

### Post by cryptopsy777 on 2008-10-22
Hello all!

I tried to upgrade Ubuntu 6.06 LTS to 8.04 LTS by using the update-manager. The system has been up-to-date before I started the update-procedure.
This did not work that well since several error messages appeared.

After the (incomplete?) update I tried 3 or 4 times to start Ubuntu. I got "fsck died with exit status 8" error messages.
However, these errors disappeared, don't ask me why.

Now the system proceedes until the login screen. After logging-in, it freezes.

Here are the log files from /var/log/dist-upgrade/

In apt.log (all files included in the attached zip file), the errors look like
```
Starting
Starting 2
Investigating dbus
Package dbus has broken dep on dbus-1-utils
  Considering dbus-1-utils -1 as a solution to dbus 133
  Added dbus-1-utils to the remove list
  Fixing dbus via remove of dbus-1-utils
Investigating python-gtk2
Package python-gtk2 has broken dep on python-gtk-1.2
  Considering python-gtk-1.2 1 as a solution to python-gtk2 104
  Added python-gtk-1.2 to the remove list
```

In apt-term.log
```
dpkg: libxft-dev: dependency problems, but removing anyway as you request:
 libqt3-mt-dev depends on libxft-dev; however:
  Package libxft-dev is to be removed.
 libqt4-dev depends on libxft-dev; however:
  Package libxft-dev is to be removed.
```

In main.log
```
2008-10-22 13:20:03,229 ERROR got an error from dpkg for pkg: 'synaptic': 'subprocess post-installation script returned error exit status 127
'
2008-10-22 13:20:03,316 DEBUG running apport_pkgfailure() synaptic: subprocess post-installation script returned error exit status 127

2008-10-22 13:20:03,623 ERROR got an error from dpkg for pkg: 'synaptic': 'subprocess post-installation script returned error exit status 127
'
2008-10-22 13:22:42,438 ERROR got an error from dpkg for pkg: 'update-manager': 'dependency problems - leaving unconfigured
```

Running "dpkg --configure -a" gives
```
Setting up gdm (2.20.7-0ubuntu1.1) ...
 * Reloading GNOME Display Manager configuration...       [80G  [33m*[39;49m Changes will take effect when all current X sessions have ended.
invoke-rc.d: initscript gdm, action "reload" failed.
dpkg: error processing gdm (--configure):
 subprocess post-installation script returned error exit status 127
Setting up gnome-user-guide (2.22.0+svn20080407ubuntu1) ...
dpkg: error processing gnome-user-guide (--configure):
 subprocess post-installation script returned error exit status 127
Setting up eog (2.22.3-0ubuntu2) ...
dpkg: error processing eog (--configure):
 subprocess post-installation script returned error exit status 127
Setting up gnome-system-monitor (2.22.3-0ubuntu2) ...
dpkg: error processing gnome-system-monitor (--configure):
 subprocess post-installation script returned error exit status 127
Setting up gconf-editor (2.22.0-0ubuntu2) ...
dpkg: error processing gconf-editor (--configure):
 subprocess post-installation script returned error exit status 127
Setting up capplets-data (1:2.22.1-0ubuntu4.1) ...
dpkg: error processing capplets-data (--configure):
 subprocess post-installation script returned error exit status 127
Setting up gedit-common (2.22.3-0ubuntu1) ...
dpkg: error processing gedit-common (--configure):
 subprocess post-installation script returned error exit status 127
Setting up seahorse (2.22.2-0ubuntu1) ...
dpkg: error processing seahorse (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of gedit:
 gedit depends on gedit-common (>= 2.22); however:
  Package gedit-common is not configured yet.
 gedit depends on gedit-common (<< 2.23); however:
  Package gedit-common is not configured yet.
dpkg: error processing gedit (--configure):
 dependency problems - leaving unconfigured
Setting up sound-juicer (2.22.0-1ubuntu2) ...
dpkg: error processing sound-juicer (--configure):
 subprocess post-installation script returned error exit status 127
Setting up gnome-nettool (2.22.0-0ubuntu2) ...
dpkg: error processing gnome-nettool (--configure):
 subprocess post-installation script returned error exit status 127
Setting up rhythmbox (0.11.5-0ubuntu8) ...
dpkg: error processing rhythmbox (--configure):
 subprocess post-installation script returned error exit status 127
Setting up vinagre (0.5.1-0ubuntu1) ...
dpkg: error processing vinagre (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of fast-user-switch-applet:
 fast-user-switch-applet depends on gdm; however:
  Package gdm is not configured yet.
dpkg: error processing fast-user-switch-applet (--configure):
 dependency problems - leaving unconfigured
Setting up gnome-pilot (2.0.15-2ubuntu3) ...
dpkg: error processing gnome-pilot (--configure):
 subprocess post-installation script returned error exit status 127
Setting up gnome-netstatus-applet (2.12.1-1ubuntu1) ...
dpkg: error processing gnome-netstatus-applet (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on capplets-data (>= 1:2.22); however:
  Package capplets-data is not configured yet.
 gnome-control-center depends on capplets-data (<< 1:2.23); however:
  Package capplets-data is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
Setting up gcalctool (5.22.3-0ubuntu0.1) ...
dpkg: error processing gcalctool (--configure):
 subprocess post-installation script returned error exit status 127
Setting up synaptic (0.61ubuntu9) ...
dpkg: error processing synaptic (--configure):
 subprocess post-installation script returned error exit status 127
Setting up evince (2.22.2-0ubuntu1) ...
dpkg: error processing evince (--configure):
 subprocess post-installation script returned error exit status 127
Setting up file-roller (2.22.3-0ubuntu1) ...
dpkg: error processing file-roller (--configure):
 subprocess post-installation script returned error exit status 127
Setting up gok (1.3.7-0ubuntu1) ...
dpkg: error processing gok (--configure):
 subprocess post-installation script returned error exit status 127
Setting up deskbar-applet (2.22.3.1-0ubuntu1) ...
dpkg: error processing deskbar-applet (--configure):
 subprocess post-installation script returned error exit status 127
Setting up tomboy (0.10.2-0ubuntu1) ...
dpkg: error processing tomboy (--configure):
 subprocess post-installation script returned error exit status 127
Setting up gucharmap (1:2.22.1-0ubuntu2) ...
dpkg: error processing gucharmap (--configure):
 subprocess post-installation script returned error exit status 127
Setting up gnome-terminal-data (2.22.1-0ubuntu2) ...
dpkg: error processing gnome-terminal-data (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of jockey-gtk:
 jockey-gtk depends on synaptic; however:
  Package synaptic is not configured yet.
dpkg: error processing jockey-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus:
 nautilus depends on gnome-control-center (>= 2.6); however:
  Package gnome-control-center is not configured yet.
dpkg: error processing nautilus (--configure):
 dependency problems - leaving unconfigured
Setting up gnome-applets-data (2.22.2-0ubuntu2) ...
dpkg: error processing gnome-applets-data (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on eog; however:
  Package eog is not configured yet.
 ubuntu-desktop depends on evince; however:
  Package evince is not configured yet.
 ubuntu-desktop depends on fast-user-switch-applet; however:
  Package fast-user-switch-applet is not configured yet.
 ubuntu-desktop depends on file-roller; however:
  Package file-roller is not configured yet.
 ubuntu-desktop depends on gcalctool; however:
  Package gcalctool is not configured yet.
 ubuntu-desktop depends on gconf-editor; however:
  Package gconf-editor is not configured yet.
 ubuntu-desktop depends on gdm; however:
  Package gdm is not configured yet.
 ubuntu-desktop depends on gedit; however:
  Package gedit is not configured yet.
 ubuntu-desktop depends on gnome-control-center; however:
  Package gnome-control-center is not configured yet.
 ubuntu-desktop depends on gnome-netstatus-applet; however:
  Package gnome-netstatus-applet is not configured yet.
 ubuntu-desktop depends on gnome-nettool; however:
  Package gnome-nettool is not configured yet.
 ubuntu-desktop depends on gnome-system-monitor; however:
  Package gnome-system-monitor is not configured yet.
 ubuntu-desktop depends on gucharmap; however:
  Package gucharmap is not configured yet.
 ubuntu-desktop depends on nautilus; however:
  Package nautilus is not configured yet.
 ubuntu-desktop depends on seahorse; however:
  Package seahorse is not configured yet.
 ubuntu-desktop depends on synaptic; however:
  Package synaptic is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Setting up gnome-utils (2.20.0.1-1ubuntu5) ...
dpkg: error processing gnome-utils (--configure):
 subprocess post-installation script returned error exit status 127
Setting up gnome-games-data (1:2.22.3-0ubuntu2) ...
dpkg: error processing gnome-games-data (--configure):
 subprocess post-installation script returned error exit status 127
Setting up gnome-panel-data (1:2.22.2-0ubuntu1.1) ...
dpkg: error processing gnome-panel-data (--configure):
 subprocess post-installation script returned error exit status 127
Setting up gthumb (3:2.10.8-0ubuntu1) ...
dpkg: error processing gthumb (--configure):
 subprocess post-installation script returned error exit status 127
Setting up gnome-system-tools (2.22.0-0ubuntu9) ...
dpkg: error processing gnome-system-tools (--configure):
 subprocess post-installation script returned error exit status 127
Setting up f-spot (0.4.3.1-0ubuntu1) ...
dpkg: error processing f-spot (--configure):
 subprocess post-installation script returned error exit status 127
Setting up zenity (2.22.1-1) ...
dpkg: error processing zenity (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of ubuntu-docs:
 ubuntu-docs depends on gnome-user-guide; however:
  Package gnome-user-guide is not configured yet.
dpkg: error processing ubuntu-docs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-applets:
 gnome-applets depends on gnome-applets-data (>= 2.22); however:
  Package gnome-applets-data is not configured yet.
 gnome-applets depends on gnome-applets-data (<< 2.23); however:
  Package gnome-applets-data is not configured yet.
dpkg: error processing gnome-applets (--configure):
 dependency problems - leaving unconfigured
Setting up totem-common (2.22.1-0ubuntu2) ...
dpkg: error processing totem-common (--configure):
 subprocess post-installation script returned error exit status 127
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Setting up evolution-common (2.22.3.1-0ubuntu1) ...
dpkg: error processing evolution-common (--configure):
 subprocess post-installation script returned error exit status 127
Setting up ekiga (2.0.12-0ubuntu2) ...
dpkg: error processing ekiga (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on synaptic (>= 0.57.8); however:
  Package synaptic is not configured yet.
dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-sendto:
 nautilus-sendto depends on nautilus-extensions-2.0; however:
  Package nautilus-extensions-2.0 is not installed.
  Package nautilus which provides nautilus-extensions-2.0 is not configured yet.
dpkg: error processing nautilus-sendto (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-gtk:
 software-properties-gtk depends on synaptic (>= 0.57.8); however:
  Package synaptic is not configured yet.
dpkg: error processing software-properties-gtk (--configure):
 dependency problems - leaving unconfigured
Setting up gnome-power-manager (2.22.1-1ubuntu4) ...
dpkg: error processing gnome-power-manager (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of gnome-terminal:
 gnome-terminal depends on gnome-control-center (>= 1:2.8.0); however:
  Package gnome-control-center is not configured yet.
 gnome-terminal depends on gnome-terminal-data (>= 2.22); however:
  Package gnome-terminal-data is not configured yet.
 gnome-terminal depends on gnome-terminal-data (<< 2.23); however:
  Package gnome-terminal-data is not configured yet.
dpkg: error processing gnome-terminal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apturl:
 apturl depends on synaptic; however:
  Package synaptic is not configured yet.
dpkg: error processing apturl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-selector:
 language-selector depends on synaptic; however:
  Package synaptic is not configured yet.
dpkg: error processing language-selector (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-share:
 nautilus-share depends on nautilus (>= 2.10); however:
  Package nautilus is not configured yet.
dpkg: error processing nautilus-share (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus-cd-burner:
 nautilus-cd-burner depends on nautilus; however:
  Package nautilus is not configured yet.
dpkg: error processing nautilus-cd-burner (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed.

```

Unfortunately, I haven't been able to find any helpful information. There seem to exist similar problems, but I didn't manage to extract the necessary informations to fix my system.

I hope someone is able to give me informations, tipps, instructions on how to fix these problems.

Thanx a lot in advance!
Bye

---

### Post by cariboo on 2008-10-22
The upgrade path would be 6.06-->7.04-->7.10-->8.04, you can't directly upgrade to 8.04. Seeing as your system is in an unstable state, it would probably be best to do a clean installation.

Jim

---

### Post by prshah on 2008-10-22
> **cryptopsy777 said:**
> 
I tried to upgrade Ubuntu 6.06 LTS to 8.04 LTS by using the update-manager. The system has been up-to-date before I started the update-procedure.

After the (incomplete?) update I tried 3 or 4 times to start Ubuntu. I 

If the update is incomplete, you can resume where you left off; boot into "recovery mode" from the GRUB menu, and give the command ```
dpkg --configure -a
``` (Note, no sudo).

If that fails (gives errors), use (AT YOUR OWN RISK)```

dpkg --configure -a --force-all
```


> **cariboo907 said:**
> The upgrade path would be 6.06-->7.04-->7.10-->8.04, you can't directly upgrade to 8.04.


Actually, he can upgrade LTS to LTS. And 7.04 repositories are now closed, he cannot upgrade to 7.04 (unless he grabs an 7.04 alternate CD, but then he can't upgrade to 7.10 without fully updating it; which cannot be done with closed repositories.)

---

### Post by cryptopsy777 on 2008-10-22
Thank you for your answers!


> **prshah said:**
> If the update is incomplete, you can resume where you left off; boot into "recovery mode" from the GRUB menu, and give the command...

I'm not shure if the upgrade is complete or incomplete.
GRUB states version 8.04.
Before using "dpkg --configure-all (--force-all)", I guess, I have to change the sources.list file. (hardy->dapper).

If this doesn't work, I will try a clean install.
Things can't get worse...

---

### Post by zvacet on 2008-10-22
> Before using "dpkg --configure-all (--force-all)", I guess, I have to change the sources.list file. (hardy->dapper).

If it is not too late don´t do that.It looks like you want to downgrade your system.If you allready have Hardy why change source list to Dapper?Try what **prshah** adviced to you.

---

### Post by cryptopsy777 on 2008-10-22
> **zvacet said:**
> If it is not too late don´t do that.It looks like you want to downgrade your system.If you allready have Hardy why change source list to Dapper?Try what **prshah** adviced to you.

Ok, I misunderstood that.

I tried the commands mentioned above.

"dpkg --configure -a --force all" again produced some error messages.

```

Setting up gdm (2.20.7-0ubuntu1.1) ...
 * Reloading GNOME Display Manager configuration...       [80G  [33m*[39;49m Changes will take effect when all current X sessions have ended.
invoke-rc.d: initscript gdm, action "reload" failed.
dpkg: error processing gdm (--configure):
 subprocess post-installation script returned error exit status 127
Setting up gnome-user-guide (2.22.0+svn20080407ubuntu1) ...
dpkg: error processing gnome-user-guide (--configure):
 subprocess post-installation script returned error exit status 127
Setting up eog (2.22.3-0ubuntu2) ...
dpkg: error processing eog (--configure):
 subprocess post-installation script returned error exit status 127
Setting up gnome-system-monitor (2.22.3-0ubuntu2) ...
dpkg: error processing gnome-system-monitor (--configure):
 subprocess post-installation script returned error exit status 127
Setting up gconf-editor (2.22.0-0ubuntu2) ...
dpkg: error processing gconf-editor (--configure):
 subprocess post-installation script returned error exit status 127
Setting up capplets-data (1:2.22.1-0ubuntu4.1) ...
dpkg: error processing capplets-data (--configure):
 subprocess post-installation script returned error exit status 127
Setting up gedit-common (2.22.3-0ubuntu1) ...
dpkg: error processing gedit-common (--configure):
 subprocess post-installation script returned error exit status 127
Setting up seahorse (2.22.2-0ubuntu1) ...
dpkg: error processing seahorse (--configure):
 subprocess post-installation script returned error exit status 127
Setting up sound-juicer (2.22.0-1ubuntu2) ...
dpkg: error processing sound-juicer (--configure):
 subprocess post-installation script returned error exit status 127
Setting up gnome-nettool (2.22.0-0ubuntu2) ...
dpkg: error processing gnome-nettool (--configure):
 subprocess post-installation script returned error exit status 127
Setting up rhythmbox (0.11.5-0ubuntu8) ...
dpkg: error processing rhythmbox (--configure):
 subprocess post-installation script returned error exit status 127
Setting up vinagre (0.5.1-0ubuntu1) ...
dpkg: error processing vinagre (--configure):
 subprocess post-installation script returned error exit status 127
Setting up gnome-pilot (2.0.15-2ubuntu3) ...
dpkg: error processing gnome-pilot (--configure):
 subprocess post-installation script returned error exit status 127
Setting up gnome-netstatus-applet (2.12.1-1ubuntu1) ...
dpkg: error processing gnome-netstatus-applet (--configure):
 subprocess post-installation script returned error exit status 127
Setting up gcalctool (5.22.3-0ubuntu0.1) ...
dpkg: error processing gcalctool (--configure):
 subprocess post-installation script returned error exit status 127
Setting up synaptic (0.61ubuntu9) ...
dpkg: error processing synaptic (--configure):
 subprocess post-installation script returned error exit status 127
Setting up evince (2.22.2-0ubuntu1) ...
dpkg: error processing evince (--configure):
 subprocess post-installation script returned error exit status 127
Setting up file-roller (2.22.3-0ubuntu1) ...
dpkg: error processing file-roller (--configure):
 subprocess post-installation script returned error exit status 127
Setting up gok (1.3.7-0ubuntu1) ...
dpkg: error processing gok (--configure):
 subprocess post-installation script returned error exit status 127
Setting up deskbar-applet (2.22.3.1-0ubuntu1) ...
dpkg: error processing deskbar-applet (--configure):
 subprocess post-installation script returned error exit status 127
Setting up tomboy (0.10.2-0ubuntu1) ...
dpkg: error processing tomboy (--configure):
 subprocess post-installation script returned error exit status 127
Setting up gucharmap (1:2.22.1-0ubuntu2) ...
dpkg: error processing gucharmap (--configure):
 subprocess post-installation script returned error exit status 127
Setting up gnome-terminal-data (2.22.1-0ubuntu2) ...
dpkg: error processing gnome-terminal-data (--configure):
 subprocess post-installation script returned error exit status 127
Setting up gnome-applets-data (2.22.2-0ubuntu2) ...
dpkg: error processing gnome-applets-data (--configure):
 subprocess post-installation script returned error exit status 127
Setting up gnome-utils (2.20.0.1-1ubuntu5) ...
dpkg: error processing gnome-utils (--configure):
 subprocess post-installation script returned error exit status 127
Setting up gnome-games-data (1:2.22.3-0ubuntu2) ...
dpkg: error processing gnome-games-data (--configure):
 subprocess post-installation script returned error exit status 127
Setting up gnome-panel-data (1:2.22.2-0ubuntu1.1) ...
dpkg: error processing gnome-panel-data (--configure):
 subprocess post-installation script returned error exit status 127
Setting up gthumb (3:2.10.8-0ubuntu1) ...
dpkg: error processing gthumb (--configure):
 subprocess post-installation script returned error exit status 127
Setting up gnome-system-tools (2.22.0-0ubuntu9) ...
dpkg: error processing gnome-system-tools (--configure):
 subprocess post-installation script returned error exit status 127
Setting up f-spot (0.4.3.1-0ubuntu1) ...
dpkg: error processing f-spot (--configure):
 subprocess post-installation script returned error exit status 127
Setting up zenity (2.22.1-1) ...
dpkg: error processing zenity (--configure):
 subprocess post-installation script returned error exit status 127
Setting up totem-common (2.22.1-0ubuntu2) ...
dpkg: error processing totem-common (--configure):
 subprocess post-installation script returned error exit status 127
Setting up evolution-common (2.22.3.1-0ubuntu1) ...
dpkg: error processing evolution-common (--configure):
 subprocess post-installation script returned error exit status 127
Setting up ekiga (2.0.12-0ubuntu2) ...
dpkg: error processing ekiga (--configure):
 subprocess post-installation script returned error exit status 127
Setting up gnome-power-manager (2.22.1-1ubuntu4) ...
dpkg: error processing gnome-power-manager (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: fast-user-switch-applet: dependency problems, but configuring anyway as you request:
 fast-user-switch-applet depends on gdm; however:
  Package gdm is not configured yet.
 fast-user-switch-applet depends on gnome-system-tools; however:
  Package gnome-system-tools is not configured yet.
Setting up fast-user-switch-applet (2.22.0-0ubuntu2) ...
dpkg: error processing fast-user-switch-applet (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: ubuntu-docs: dependency problems, but configuring anyway as you request:
 ubuntu-docs depends on gnome-user-guide; however:
  Package gnome-user-guide is not configured yet.
Setting up ubuntu-docs (8.04.2~hardy) ...
dpkg: error processing ubuntu-docs (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: update-manager: dependency problems, but configuring anyway as you request:
 update-manager depends on synaptic (>= 0.57.8); however:
  Package synaptic is not configured yet.
Setting up update-manager (1:0.87.30) ...
dpkg: error processing update-manager (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: gnome-app-install: dependency problems, but configuring anyway as you request:
 gnome-app-install depends on synaptic (>= 0.57.8); however:
  Package synaptic is not configured yet.
Setting up gnome-app-install (0.5.2.8-0ubuntu1) ...
dpkg: error processing gnome-app-install (--configure):
 subprocess post-installation script returned error exit status 127
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 gdm
 gnome-user-guide
 eog
 gnome-system-monitor
 gconf-editor
 capplets-data
 gedit-common
 seahorse
 sound-juicer
 gnome-nettool
 rhythmbox
 vinagre
 gnome-pilot
 gnome-netstatus-applet
 gcalctool
 synaptic
 evince
 file-roller
 gok


 deskbar-applet
 tomboy
 gucharmap
 gnome-terminal-data
 gnome-applets-data
 gnome-utils
 gnome-games-data
 gnome-panel-data
 gthumb
 gnome-system-tools
 f-spot
 zenity
 totem-common
 evolution-common
 ekiga
 gnome-power-manager
 fast-user-switch-applet
 ubuntu-docs
 update-manager
 gnome-app-install

```

But now, at least, the x-server starts.
Some additional error messages about HAL appear...

I guess, now I have to re-install all the components listed above. But I dont think, this can be done using Synaptic, as it is part of the list.
So first re-installing Synaptic manually? Then, the other components?

Thanks again!

---

### Post by zvacet on 2008-10-22
```
sudo dpkg --configure synaptic
```

That should work.If you still can not configure other packages with synaptic use same command as above(for other packages) and you should be fine.

---

### Post by prshah on 2008-10-23
> **cryptopsy777 said:**
> 
```

<..snip..>[color="red"][39;49m Changes will take effect when all current X sessions have ended.[/color]
```

But now, at least, the x-server starts.
Some additional error messages about HAL appear...


You were supposed to do the "dpkg" command from Recovery Mode; looks like you've not booted into recovery mode.

Boot into recovery mode, and repeat the command again.

---

### Post by cryptopsy777 on 2008-10-23
> **prshah said:**
> You were supposed to do the "dpkg" command from Recovery Mode; looks like you've not booted into recovery mode.

Boot into recovery mode, and repeat the command again.

Because I haven't been shure if I tried the command in recovery mode, I tried again - result is:

```
...Changes will take effect when all current X sessions have ended.
...
```

So, I have been in recovery mode.

@**zvacet**

"sudo dpkg --configure synaptic"

yields

> Setting up synaptic (0.61ubuntu9) ...
dpkg: error processing synaptic (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 synaptic


I found another error message in /var/log/dmesg

> [   61.182857] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   61.182921] ata1.00: BMDMA stat 0x25
[   61.182971] ata1.00: cmd c8/00:2e:91:a3:3d/00:00:00:00:00/e0 tag 0 dma 23552 in
[   61.182973]          res 51/40:12:ad:a3:3d/00:00:00:00:00/e0 Emask 0x9 (media error)
[   61.183032] ata1.00: status: { DRDY ERR }
[   61.183077] ata1.00: error: { UNC }

Doesn't look good. I ran the Hitachi diagnostics tool and got a report stating that there are bad sectors. Maybe that's the origin of all these error messages... :(

---

### Post by cryptopsy777 on 2008-10-24
Well, after all I decided to do a clean install.
Everything works properly now...

Thank you guys for your help!

---

