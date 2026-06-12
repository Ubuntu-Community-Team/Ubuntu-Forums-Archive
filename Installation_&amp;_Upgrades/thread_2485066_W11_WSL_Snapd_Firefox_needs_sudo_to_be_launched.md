---
title: "W11 WSL Snapd Firefox needs sudo to be launched"
date: 2023-03-19
forum: Installation &amp; Upgrades
---

### Post by ortollj on 2023-03-19
Hi
Ubuntu 22.04 LTS
I lost the possibility to launch Firefox snapd after W11 update of KB5023706 and KB5022913

With Firefox Linux, I got the error:
```
cmd_run.go:1055: WARNING: cannot start document portal: dial unix /run/user/1000/bus: connect: no such file or directory
/ is not a snap cgroup
```

Something weird after uninstalled the two W11 updates KB5023706 and KB5022913 which caused the  problem the problem is still there !

The problem does not disappear. it seems that W11 is not able to come back to previous state.
W11 doesn't seem to be reliably stabilized yet.

Now I need to do ```
sudo firefox
``` to launch Firefox.

Is it possible to return to simple firefox without sudo ? because I would like my SageMath server could again launch automatically Firefox.
Without having to copy past in a browser the url given by SageMath.

---

### Post by MAFoElffen on 2023-03-19
Is your Firefox installed as Snap?
```

sudo snap list firefox

```
It should be. If so then 
```

sudo snap remove firefox
sudo snap install firefox

```
As long as you DO NOT use the "--purge" flag, it will keep your settings during that.

---

### Post by ortollj on 2023-03-19
without snapd WSL can't launch Firefox:

```
ortollj@DESKTOP-K30FLRP:~$ sudo snap list firefox
[sudo] password for ortollj:
Name     Version  Rev   Tracking       Publisher  Notes
firefox  111.0-2  2432  latest/stable  mozilla&#10003;   -
ortollj@DESKTOP-K30FLRP:~$
```

```
sudo snap remove --purge firefox
sudo snap install firefox
```

I did that above two times already without success

```
snap --version
snap                         2.58.2
snapd                        unavailable
series                       16
Windows Subsystem for Linux  -
kernel                       5.15.90.1-microsoft-standard-WSL2 (amd64)
```

why I got snapd unavailable ??

```
ortollj@DESKTOP-K30FLRP:~$ systemctl status snapd.service
&#9679; snapd.service - Snap Daemon
     Loaded: loaded (/lib/systemd/system/snapd.service; enabled; vendor preset: enabled)
     Active: active (running) since Sat 2023-03-18 06:43:51 CET; 1 day 2h ago
TriggeredBy: &#9679; snapd.socket
   Main PID: 183 (snapd)
      Tasks: 31 (limit: 19151)
     Memory: 682.4M
        CPU: 16.516s
     CGroup: /system.slice/snapd.service
             &#9492;&#9472;183 /usr/lib/snapd/snapd

Mar 18 06:49:07 DESKTOP-K30FLRP snapd[183]: storehelpers.go:769: cannot refresh snap "ubuntu-desktop-installer": snap has no updates available
Mar 18 06:59:10 DESKTOP-K30FLRP snapd[183]: storehelpers.go:769: cannot refresh: snap has no updates available: "bare", "core20", "core22", "firefox", "gnome-3-38-2004", "gtk-common->
Mar 18 17:05:51 DESKTOP-K30FLRP snapd[183]: storehelpers.go:769: cannot refresh: snap has no updates available: "bare", "core20", "core22", "firefox", "gnome-3-38-2004", "gtk-common->
Mar 18 17:05:55 DESKTOP-K30FLRP snapd[183]: services.go:1090: RemoveSnapServices - disabling snap.ubuntu-desktop-installer.subiquity-server.service
Mar 18 17:05:57 DESKTOP-K30FLRP snapd[183]: storehelpers.go:769: cannot refresh snap "ubuntu-desktop-installer": snap has no updates available
Mar 18 17:15:58 DESKTOP-K30FLRP snapd[183]: storehelpers.go:769: cannot refresh: snap has no updates available: "bare", "core20", "core22", "firefox", "gnome-3-38-2004", "gtk-common->
Mar 19 06:56:57 DESKTOP-K30FLRP snapd[183]: access.go:60: polkit error: Authorization requires interaction
Mar 19 06:57:14 DESKTOP-K30FLRP snapd[183]: api_snaps.go:366: Installing snap "firefox" revision unset
Mar 19 08:50:12 DESKTOP-K30FLRP snapd[183]: storehelpers.go:769: cannot refresh: snap has no updates available: "bare", "core20", "core22", "firefox", "gnome-3-38-2004", "gtk-common->
Mar 19 08:50:12 DESKTOP-K30FLRP snapd[183]: autorefresh.go:551: auto-refresh: all snaps are up-to-date
lines 1-21/21 (END)
```

[https://askubuntu.com/questions/1317937/difference-between-snap-and-snapd](https://askubuntu.com/questions/1317937/difference-between-snap-and-snapd)

---

### Post by MAFoElffen on 2023-03-19
Next would be to do this
```

# Make a copy of your Firefox Profile
cp $HOME/.mozilla $/HOME/Downloads
sudo snap remove --purge firefox
sudo snap install firefox

```
Then try to start it up again to try.

If it does start, then look at the $HOME/Downloads/.mozilla/firefox/profiles.ini file and it will tell you what the default profile folder is under .mozilla.

It will look something like this on mine:
```

[Install4F96D1932A9F858E]
Default=5jyimcav.default-release
Locked=1

[Profile1]
Name=default
IsRelative=1
[COLOR=#ff0000]Path=l4gxr6xt.default[/COLOR]
Default=1

[Profile0]
Name=default-release
IsRelative=1
[COLOR=#ff0000]Path=5jyimcav.default-release[/COLOR]

[General]
StartWithLastProfile=1
Version=2


```

---

### Post by ortollj on 2023-03-19
* I do not find : *```
$HOME/.mozilla
```

```
ortollj@DESKTOP-K30FLRP:~$ which firefox
/usr/bin/firefox
```

```
ortollj@DESKTOP-K30FLRP:/usr/bin$ ls moz
ls: cannot access 'moz': No such file or directory
ortollj@DESKTOP-K30FLRP:/usr/bin$
```

ortollj@DESKTOP-K30FLRP:~$ ls
mozillaProfil  sage-9.8  sage-9.8.tar.gz  sage_nb.sh  snap
ortollj@DESKTOP-K30FLRP:~$ cd snap
ortollj@DESKTOP-K30FLRP:~/snap$ ls
firefox
ortollj@DESKTOP-K30FLRP:~/snap$

mozillaProfil is empty (just created by me for puting mozilla profil if I could get it)

---

### Post by MAFoElffen on 2023-03-19
Whether it uses apt or snap versions of Forefox, that directory is there...


"$HOME" is just a system environment variable for the current logged in User's Home directory...
```

mafoelffen@Mikes-ThinkPad-T520:~$ which firefox
/snap/bin/firefox

mafoelffen@Mikes-ThinkPad-T520:~$ echo $HOME
/home/mafoelffen

mafoelffen@Mikes-ThinkPad-T520:~$ ls -la $HOME/.mozilla/
total 20
drwx------  5 mafoelffen mafoelffen 4096 Sep 23  2021 .
drwxr-xr-x 38 mafoelffen mafoelffen 4096 Mar 16 21:40 ..
drwx------  2 mafoelffen mafoelffen 4096 Sep 23  2021 extensions
drwx------  6 mafoelffen mafoelffen 4096 Aug 15  2022 firefox
drwx------  2 mafoelffen mafoelffen 4096 Sep 23  2021 systemextensionsdev

mafoelffen@Mikes-ThinkPad-T520:~$ tree -L 2 $HOME/.mozilla
/home/mafoelffen/.mozilla
&#9500;&#9472;&#9472; extensions
&#9500;&#9472;&#9472; firefox
&#9474;   &#9500;&#9472;&#9472; 5jyimcav.default-release
&#9474;   &#9500;&#9472;&#9472; Crash Reports
&#9474;   &#9500;&#9472;&#9472; installs.ini
&#9474;   &#9500;&#9472;&#9472; l4gxr6xt.default
&#9474;   &#9500;&#9472;&#9472; Pending Pings
&#9474;   &#9492;&#9472;&#9472; profiles.ini
&#9492;&#9472;&#9472; systemextensionsdev

```

---

### Post by ortollj on 2023-03-19
ortollj@DESKTOP-K30FLRP:~$ echo $HOME
/home/ortollj
ortollj@DESKTOP-K30FLRP:~$ cd /home/ortollj
ortollj@DESKTOP-K30FLRP:~$ ls -ltr
total 1449628
-rw-r--r--  1 ortollj ortollj 1484394593 Feb 11 14:41 sage-9.8.tar.gz
drwx------  3 ortollj ortollj       4096 Feb 14 07:52 snap
drwxr-xr-x 16 ortollj ortollj       4096 Feb 14 09:38 sage-9.8
-rwxr-xr--  1 ortollj ortollj        122 Mar 16 09:15 sage_nb.sh
drwxr-xr-x  2 ortollj ortollj       4096 Mar 19 10:12 mozillaProfil
ortollj@DESKTOP-K30FLRP:~$

---

### Post by ortollj on 2023-03-19
I had turned off my PC to go to lunch, and when I came back the PC was on, and now Firefox is again launchable from Ubuntu cmd !!, crazy, I do not understand. despite I already did reboot few times after finding the problem. 
in windows update history I can see the last update:
Update Stack Package - (Version 1023.308.3012.0) successfully installed on 17/03/2023
all is ok now ;-)

---

### Post by MAFoElffen on 2023-03-19
Glad to see that everything is resolve. LOL

---

### Post by ortollj on 2023-03-21
The problem reappeared after returning from standby of my PC but I now know how to solve it, just reboot my PC !. there is a problem with the return from sleep with WSL see:[URL="https://answers.microsoft.com/fr-fr/insider/forum/insider_wintp-insider_personal/w11-wsl-ubuntu-22041-lts-retour-mis-en-veille/61555aff-4cb9-48f1-b401-b13c8fddcb40?messageId=02957395-2bc1-4ce8-9682-8f0db9ba2b6e"]https://answers.microsoft.com/fr-fr/insider/forum/insider_wintp-insider_personal/w11-wsl-ubuntu-22041-lts-retour-mis-en-veille/61555aff-4cb9-48f1-b401-b13c8fddcb40?messageId=02957395-2bc1-4ce8-9682-8f0db9ba2b6e

[/URL]

---

### Post by MAFoElffen on 2023-03-21
There are few bugs open for 22.04 & 22.10 on some system with Intel CPU that have integrated graphics that also have NVidia, running wayland, and having some wake problems. zbut hose were not WSL.

With WSL, is see this bug, which seems to be more like you are discribing: [https://github.com/microsoft/WSL/issues/8696](https://github.com/microsoft/WSL/issues/8696)

---

