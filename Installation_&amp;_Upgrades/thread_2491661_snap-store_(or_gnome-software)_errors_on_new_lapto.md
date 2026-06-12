---
title: "snap-store (or gnome-software) errors on new laptop"
date: 2023-10-16
forum: Installation &amp; Upgrades
---

### Post by ittayd on 2023-10-16
I have a brand new laptop. The first thing I did was uninstall firefox and thunderbird from apt and then firefox from snap-store. I'm not sure if it is related to the errors.

Before I uninstalled firefox from snap-store, it showed some updates are available. After I uninstalled firefox snap-store stopped and then launched again, without updates.

Running from the console I see: not handling error failed for action refresh: E: Failed to fetch [http://il.archive.ubuntu.com/ubuntu/dists/jammy/InRelease](http://il.archive.ubuntu.com/ubuntu/dists/jammy/InRelease)
E: Failed to fetch [http://il.archive.ubuntu.com/ubuntu/dists/jammy-updates/InRelease](http://il.archive.ubuntu.com/ubuntu/dists/jammy-updates/InRelease)
E: Failed to fetch [http://il.archive.ubuntu.com/ubuntu/dists/jammy-backports/InRelease](http://il.archive.ubuntu.com/ubuntu/dists/jammy-backports/InRelease)
E: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jammy-security/InRelease](http://security.ubuntu.com/ubuntu/dists/jammy-security/InRelease)
E: Failed to fetch [https://dl.google.com/linux/chrome/deb/dists/stable/InRelease](https://dl.google.com/linux/chrome/deb/dists/stable/InRelease)
E: Some index files failed to download. They have been ignored, or old ones used instead.

17:07:09:0735 Gs  not handling error failed for action refresh: E: Failed to fetch [http://il.archive.ubuntu.com/ubuntu/dists/jammy/InRelease](http://il.archive.ubuntu.com/ubuntu/dists/jammy/InRelease)  
E: Failed to fetch [http://il.archive.ubuntu.com/ubuntu/dists/jammy-updates/InRelease](http://il.archive.ubuntu.com/ubuntu/dists/jammy-updates/InRelease)  
E: Failed to fetch [http://il.archive.ubuntu.com/ubuntu/dists/jammy-backports/InRelease](http://il.archive.ubuntu.com/ubuntu/dists/jammy-backports/InRelease)  
E: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jammy-security/InRelease](http://security.ubuntu.com/ubuntu/dists/jammy-security/InRelease)  
E: Failed to fetch [https://dl.google.com/linux/chrome/deb/dists/stable/InRelease](https://dl.google.com/linux/chrome/deb/dists/stable/InRelease)  
E: Some index files failed to download. They have been ignored, or old ones used instead.

I'm connected to the internet (writing this question on said laptop)

I googled a bit and saw a recommendation to stop and refresh snap-store (sudo snap refresh snap-store). Didn't help. Then I saw a recommendation to uninstall snap-store and install again (sudo snap remove snap-store and sudo snap install snap-store). So I did. Apprently that removed some of the configured repositories above. Now I see this error:

17:09:59:0693 Gs  not handling error failed for action refresh: E: Failed to fetch [http://il.archive.ubuntu.com/ubuntu/dists/jammy-backports/InRelease](http://il.archive.ubuntu.com/ubuntu/dists/jammy-backports/InRelease)  
E: Some index files failed to download. They have been ignored, or old ones used instead.

Any other suggestions? Also, how do I add the repositories back?

---

### Post by ittayd on 2023-10-16
Maybe related, I tried to find where the repositories above are defined by find /etc | xargs grep and this showed up:
grep: /etc/systemd/system/snap-snapdx2ddesktopx2dintegration-49.mount: No such file or directory
grep: /etc/systemd/system/snap-snapdx2ddesktopx2dintegration-83.mount: No such file or directory
grep: /etc/systemd/system/snap-gnomex2d42x2d2204-141.mount: No such file or directory
grep: /etc/systemd/system/snap-gtkx2dcommonx2dthemes-1535.mount: No such file or directory
grep: /etc/systemd/system/snap-gnomex2d3x2d38x2d2004-119.mount: No such file or directory
grep: /etc/systemd/system/snap-snapx2dstore-959.mount: No such file or directory
grep: /etc/systemd/system/snap-gnomex2d3x2d38x2d2004-143.mount: No such file or directory

---

### Post by #&amp;thj^% on 2023-10-16
That looks ugly, show us this please:
```
tac '/etc/apt/sources.list' 
```
And please use Code Tags to wrap the return in.
[noparse]```
your output here
```[/noparse]

---

### Post by ittayd on 2023-10-16
```
# see the sources.list(5) manual.
# For information about how to configure apt package sources,
# entries were disabled at the end of the installation process.
# (e.g. netinst, live or single CD). The matching "deb cdrom"
# This system was installed using small removable media

# deb-src http://security.ubuntu.com/ubuntu jammy-security multiverse
deb http://security.ubuntu.com/ubuntu jammy-security multiverse
# deb-src http://security.ubuntu.com/ubuntu jammy-security universe
# deb-src http://security.ubuntu.com/ubuntu jammy-security main restricted
deb http://security.ubuntu.com/ubuntu jammy-security restricted main universe

# deb-src http://il.archive.ubuntu.com/ubuntu/ jammy-backports main restricted universe multiverse
deb http://il.archive.ubuntu.com/ubuntu/ jammy-backports restricted multiverse main universe
## or updates from the Ubuntu security team.
## Also, please note that software in backports WILL NOT receive any review
## newer versions of some applications which may provide useful features.
## extensively as that contained in the main release, although it includes
## N.B. software from this repository may not have been tested as

# deb-src http://il.archive.ubuntu.com/ubuntu/ jammy-updates multiverse
deb http://il.archive.ubuntu.com/ubuntu/ jammy-updates multiverse
# deb-src http://il.archive.ubuntu.com/ubuntu/ jammy multiverse
deb http://il.archive.ubuntu.com/ubuntu/ jammy multiverse
## security team.
## multiverse WILL NOT receive any review or updates from the Ubuntu
## your rights to use the software. Also, please note that software in 
## team, and may not be under a free licence. Please satisfy yourself as to 
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 

# deb-src http://il.archive.ubuntu.com/ubuntu/ jammy-updates universe
# deb-src http://il.archive.ubuntu.com/ubuntu/ jammy universe
## review or updates from the Ubuntu security team.
## team. Also, please note that software in universe WILL NOT receive any
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu

# deb-src http://il.archive.ubuntu.com/ubuntu/ jammy-updates main restricted
deb http://il.archive.ubuntu.com/ubuntu/ jammy-updates restricted main universe
## distribution.
## Major bug fix updates produced after the final release of the

# deb-src http://il.archive.ubuntu.com/ubuntu/ jammy main restricted
deb http://il.archive.ubuntu.com/ubuntu/ jammy restricted main universe
# newer versions of the distribution.
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to

# deb cdrom:[Ubuntu 22.04.2 LTS _Jammy Jellyfish_ - Release amd64 (20230223)]/ jammy main restricted

```

I rebotted the laptop and now snap-store shows errors for all repositories as before I removed and installed

---

### Post by #&amp;thj^% on 2023-10-16
I'm having a bit a problem understanding you:
please run:
```
sudo apt update
```
And show us that

---

### Post by ittayd on 2023-10-16
Thanks for your help!

```
$ sudo apt update
[sudo] password for ittay: 
Hit:1 http://il.archive.ubuntu.com/ubuntu jammy InRelease
Hit:2 http://il.archive.ubuntu.com/ubuntu jammy-updates InRelease                                  
Hit:3 http://il.archive.ubuntu.com/ubuntu jammy-backports InRelease                                
Hit:4 http://security.ubuntu.com/ubuntu jammy-security InRelease    
Hit:5 https://dl.google.com/linux/chrome/deb stable InRelease
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
2 packages can be upgraded. Run 'apt list --upgradable' to see them.

```

---

### Post by #&amp;thj^% on 2023-10-16
So far so good, and now run and show us:
```
 sudo apt upgrade
```

---

### Post by ittayd on 2023-10-16
```
$ sudo apt upgrade
[sudo] password for ittay: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
Get more security updates through Ubuntu Pro with 'esm-apps' enabled:
  libpostproc55 libavcodec58 libavutil56 libswscale5 libswresample3
  libavformat58 libavfilter7
Learn more about Ubuntu Pro at https://ubuntu.com/pro
The following packages have been kept back:
  gjs libgjs0g
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
```

---

### Post by #&amp;thj^% on 2023-10-16
Hmmm? everything looks as expected and  the packages have been kept back are in a phased state and will come in on due time.
Now lets check this one:
```
apt policy gnome-software
```
I'm not real sure what you have done, so I'm moving slowly here as to not add to your woes.

---

### Post by ittayd on 2023-10-16
```
$ apt policy gnome-software
gnome-software:
  Installed: (none)
  Candidate: 41.5-2ubuntu2
  Version table:
     41.5-2ubuntu2 500
        500 http://il.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 Packages
     41.5-2 500
        500 http://il.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages

```

---

### Post by deadflowr on 2023-10-16
> ```
The following packages have been kept back:
  gjs libgjs0g
```

Those are being held back because of issues.
Currently in pending phased updates: [https://ubuntu-archive-team.ubuntu.com/phased-updates.html]("https://ubuntu-archive-team.ubuntu.com/phased-updates.html")

So no worries on your end about those, for now.

---

### Post by ittayd on 2023-10-16
About what I have done: literally what I wrote. Removed firefox and thunderbird using apt and when I saw FF is still there, removed it via snap store which then restarted and after that stopped showing there are updates

---

### Post by #&amp;thj^% on 2023-10-16
> **ittayd said:**
> About what I have done: literally what I wrote. Removed firefox and thunderbird using apt and when I saw FF is still there, removed it via snap store which then restarted and after that stopped showing there are updates

Allrighty then we move forward:
```
sudo apt install gnome-software
```
And I have a question for you are you trying to remove snap and snapd?

---

### Post by ittayd on 2023-10-16
Not trying to remove snap or snapd

```
$ sudo apt install gnome-software
[sudo] password for ittay: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  gnome-software-common gnome-software-plugin-snap libmalcontent-0-0
Suggested packages:
  gnome-software-plugin-flatpak
The following NEW packages will be installed:
  gnome-software gnome-software-common gnome-software-plugin-snap libmalcontent-0-0
0 upgraded, 4 newly installed, 0 to remove and 2 not upgraded.
Need to get 678 kB of archives.
After this operation, 3,335 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://il.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 gnome-software-common all 41.5-2ubuntu2 [20.4 kB]
Get:2 http://il.archive.ubuntu.com/ubuntu jammy/universe amd64 libmalcontent-0-0 amd64 0.10.4-1 [22.7 kB]
Get:3 http://il.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 gnome-software amd64 41.5-2ubuntu2 [606 kB]
Get:4 http://il.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 gnome-software-plugin-snap amd64 41.5-2ubuntu2 [28.8 kB]
Fetched 678 kB in 1s (1,062 kB/s)                    
Selecting previously unselected package gnome-software-common.
(Reading database ... 202617 files and directories currently installed.)
Preparing to unpack .../gnome-software-common_41.5-2ubuntu2_all.deb ...
Unpacking gnome-software-common (41.5-2ubuntu2) ...
Selecting previously unselected package libmalcontent-0-0:amd64.
Preparing to unpack .../libmalcontent-0-0_0.10.4-1_amd64.deb ...
Unpacking libmalcontent-0-0:amd64 (0.10.4-1) ...
Selecting previously unselected package gnome-software.
Preparing to unpack .../gnome-software_41.5-2ubuntu2_amd64.deb ...
Unpacking gnome-software (41.5-2ubuntu2) ...
Selecting previously unselected package gnome-software-plugin-snap.
Preparing to unpack .../gnome-software-plugin-snap_41.5-2ubuntu2_amd64.deb ...
Unpacking gnome-software-plugin-snap (41.5-2ubuntu2) ...
Setting up gnome-software-common (41.5-2ubuntu2) ...
Setting up libmalcontent-0-0:amd64 (0.10.4-1) ...
Setting up gnome-software (41.5-2ubuntu2) ...
Processing triggers for desktop-file-utils (0.26-1ubuntu3) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu3) ...
Processing triggers for libglib2.0-0:amd64 (2.72.4-0ubuntu2.2) ...
Processing triggers for libc-bin (2.35-0ubuntu3.4) ...
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for mailcap (3.70+nmu1ubuntu1) ...
Setting up gnome-software-plugin-snap (41.5-2ubuntu2) ...

```

---

### Post by #&amp;thj^% on 2023-10-16
You should be good to go now.

---

### Post by ittayd on 2023-10-16
snap-store still shows the same errors

---

### Post by #&amp;thj^% on 2023-10-16
well I'm no fan of snaps and avoid them at all costs, that said show me this now:
```
sudo snap refresh 
```
And
```
snap refresh --list
```

---

### Post by ittayd on 2023-10-16
Both return
```
All snaps up to date.

```

(which makes sense if it can't pull any updates)

---

### Post by #&amp;thj^% on 2023-10-16
I still hate snaps :P
All I can offer now is to see if a new channel will help.
```
snap refresh snap-store --beta --ignore-running
```
And check again in snap store

---

### Post by ittayd on 2023-10-16
Will that make it switch to beta ? I don't really want that. 

Isn't there a way to get logs that show why it couldn't connect ? (--verbose doesn't show much)

---

### Post by #&amp;thj^% on 2023-10-16
> **ittayd said:**
> Will that make it switch to beta ? I don't really want that. 

Isn't there a way to get logs that show why it couldn't connect ? (--verbose doesn't show much)

We can switch it back to stable later, we are just trying to get it to work properly.
Like this:
```
snap refresh snap-store --stable
```

---

### Post by ittayd on 2023-10-17
Sorry, just noticed this message. The results of --beta are 
```
snap-store (candidate) 41.3-76-g2e8f3b0 from Canonical** refreshed
Channel latest/beta for snap-store is closed; temporarily forwarding to latest/candidate.

```

If I then load snap-store I get the same errors

---

### Post by #&amp;thj^% on 2023-10-17
Can you please show me this:
```
snap run snap-store
```
And 
```
snap version
```

---

### Post by ittayd on 2023-10-17
(I'm back on stable)
```
$ snap run snap-store
Warning: Schema &#8220;org.gnome.system.locale&#8221; has path &#8220;/system/locale/&#8221;.  Paths starting with &#8220;/apps/&#8221;, &#8220;/desktop/&#8221; or &#8220;/system/&#8221; are deprecated.
Warning: Schema &#8220;org.gnome.system.proxy&#8221; has path &#8220;/system/proxy/&#8221;.  Paths starting with &#8220;/apps/&#8221;, &#8220;/desktop/&#8221; or &#8220;/system/&#8221; are deprecated.
Warning: Schema &#8220;org.gnome.system.proxy.http&#8221; has path &#8220;/system/proxy/http/&#8221;.  Paths starting with &#8220;/apps/&#8221;, &#8220;/desktop/&#8221; or &#8220;/system/&#8221; are deprecated.
Warning: Schema &#8220;org.gnome.system.proxy.https&#8221; has path &#8220;/system/proxy/https/&#8221;.  Paths starting with &#8220;/apps/&#8221;, &#8220;/desktop/&#8221; or &#8220;/system/&#8221; are deprecated.
Warning: Schema &#8220;org.gnome.system.proxy.ftp&#8221; has path &#8220;/system/proxy/ftp/&#8221;.  Paths starting with &#8220;/apps/&#8221;, &#8220;/desktop/&#8221; or &#8220;/system/&#8221; are deprecated.
Warning: Schema &#8220;org.gnome.system.proxy.socks&#8221; has path &#8220;/system/proxy/socks/&#8221;.  Paths starting with &#8220;/apps/&#8221;, &#8220;/desktop/&#8221; or &#8220;/system/&#8221; are deprecated.
17:41:28:0166 Gtk Not loading module "atk-bridge": The functionality is provided by GTK natively. Please try to not load it.
17:41:45:0586 Gs  adding wildcard app */*/*/org.gnome.Builder.desktop/* to plugin cache
17:41:45:0586 Gs  adding wildcard app */*/*/org.gnome.Calculator.desktop/* to plugin cache
17:41:45:0586 Gs  adding wildcard app */*/*/org.gnome.clocks.desktop/* to plugin cache
17:41:45:0586 Gs  adding wildcard app */*/*/org.gnome.Dictionary.desktop/* to plugin cache
17:41:45:0586 Gs  adding wildcard app */*/*/org.gnome.Documents.desktop/* to plugin cache
17:41:45:0586 Gs  adding wildcard app */*/*/org.gnome.Evince/* to plugin cache
17:41:45:0586 Gs  adding wildcard app */*/*/org.gnome.gedit.desktop/* to plugin cache
17:41:45:0586 Gs  adding wildcard app */*/*/org.gnome.Maps.desktop/* to plugin cache
17:41:45:0586 Gs  adding wildcard app */*/*/org.gnome.Weather/* to plugin cache
17:41:45:0587 Gs  Only 0 apps for recent list, hiding
17:41:46:0666 Gs  not handling error failed for action refresh: E: Failed to fetch https://packagecloud.io/slacktechnologies/slack/debian/dists/jessie/InRelease  
E: Some index files failed to download. They have been ignored, or old ones used instead.

17:41:47:0561 Gs  not handling error failed for action refresh: E: Failed to fetch http://il.archive.ubuntu.com/ubuntu/dists/jammy/InRelease  
E: Failed to fetch http://il.archive.ubuntu.com/ubuntu/dists/jammy-updates/InRelease  
E: Failed to fetch http://il.archive.ubuntu.com/ubuntu/dists/jammy-backports/InRelease  
E: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jammy-security/InRelease  
E: Failed to fetch https://dl.google.com/linux/chrome/deb/dists/stable/InRelease  
E: Failed to fetch https://packagecloud.io/slacktechnologies/slack/debian/dists/jessie/InRelease  
E: Some index files failed to download. They have been ignored, or old ones used instead.


```

```
$ snap version
snap    2.60.4
snapd   2.60.4
series  16
ubuntu  22.04
kernel  6.2.0-34-generic
```

---

### Post by #&amp;thj^% on 2023-10-17
It just seems lost, lets see if we can give it a proper close:
```
snap-store --quit-on-close-for-update
```
Please show me that return

---

### Post by ittayd on 2023-10-17
```
$ snap-store --quit-on-close-for-update
Unknown option --quit-on-close-for-update

```

---

### Post by #&amp;thj^% on 2023-10-17
You say that's all you did was to remove firefox?
```
killall snap-store
```

---

### Post by ittayd on 2023-10-17
OK, I think I found something:
```
Oct 17 21:05:26 LT-IttayD systemd[2001]: Started snap.snap-store.snap-store-1f053e99-5a06-45cd-93e3-0c1b7851b7ed.scope.
Oct 17 21:05:26 LT-IttayD audit[1041]: USER_AVC pid=1041 uid=102 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/Po>
                                        exe="/usr/bin/dbus-daemon" sauid=102 hostname=? addr=? terminal=?'
Oct 17 21:05:26 LT-IttayD kernel: audit: type=1107 audit(1697565926.909:145): pid=1041 uid=102 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="sys>
                                   exe="/usr/bin/dbus-daemon" sauid=102 hostname=? addr=? terminal=?'
Oct 17 21:05:26 LT-IttayD kernel: audit: type=1107 audit(1697565926.909:146): pid=1041 uid=102 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="sys>
                                   exe="/usr/bin/dbus-daemon" sauid=102 hostname=? addr=? terminal=?'
Oct 17 21:05:26 LT-IttayD kernel: audit: type=1107 audit(1697565926.909:147): pid=1041 uid=102 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="sys>
                                   exe="/usr/bin/dbus-daemon" sauid=102 hostname=? addr=? terminal=?'
Oct 17 21:05:26 LT-IttayD kernel: audit: type=1107 audit(1697565926.909:148): pid=1041 uid=102 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="sys>
                                   exe="/usr/bin/dbus-daemon" sauid=102 hostname=? addr=? terminal=?'
Oct 17 21:05:26 LT-IttayD audit[1041]: USER_AVC pid=1041 uid=102 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/Po>
                                        exe="/usr/bin/dbus-daemon" sauid=102 hostname=? addr=? terminal=?'
Oct 17 21:05:26 LT-IttayD audit[1041]: USER_AVC pid=1041 uid=102 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/Po>
                                        exe="/usr/bin/dbus-daemon" sauid=102 hostname=? addr=? terminal=?'
Oct 17 21:05:26 LT-IttayD audit[1041]: USER_AVC pid=1041 uid=102 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/Po>
                                        exe="/usr/bin/dbus-daemon" sauid=102 hostname=? addr=? terminal=?'
Oct 17 21:05:27 LT-IttayD audit[49841]: AVC apparmor="DENIED" operation="open" class="file" profile="snap.snap-store.snap-store" name="/etc/appstream.conf" pid=49841 comm="snap-store" requested_mask="r" >
Oct 17 21:05:27 LT-IttayD kernel: audit: type=1400 audit(1697565927.017:149): apparmor="DENIED" operation="open" class="file" profile="snap.snap-store.snap-store" name="/etc/appstream.conf" pid=49841 com>
Oct 17 21:05:27 LT-IttayD PackageKit[1656]: uid 1000 is trying to obtain org.freedesktop.packagekit.system-sources-refresh auth (only_trusted:0)
Oct 17 21:05:27 LT-IttayD PackageKit[1656]: uid 1000 obtained auth for org.freedesktop.packagekit.system-sources-refresh
Oct 17 21:05:27 LT-IttayD systemd[1]: Starting Update APT News...
Oct 17 21:05:27 LT-IttayD systemd[1]: Starting Update the local ESM caches...
Oct 17 21:05:27 LT-IttayD systemd[1]: apt-news.service: Deactivated successfully.
Oct 17 21:05:27 LT-IttayD systemd[1]: Finished Update APT News.
Oct 17 21:05:27 LT-IttayD systemd[1]: esm-cache.service: Deactivated successfully.
Oct 17 21:05:27 LT-IttayD systemd[1]: Finished Update the local ESM caches.
Oct 17 21:05:29 LT-IttayD PackageKit[1656]: refresh-cache transaction /214_daaabbec from uid 1000 finished with success after 2499ms
Oct 17 21:05:29 LT-IttayD PackageKit[1656]: uid 1000 is trying to obtain org.freedesktop.packagekit.system-sources-refresh auth (only_trusted:0)
Oct 17 21:05:29 LT-IttayD PackageKit[1656]: uid 1000 obtained auth for org.freedesktop.packagekit.system-sources-refresh
Oct 17 21:05:30 LT-IttayD snapd[1109]: storehelpers.go:773: cannot refresh: snap has no updates available: "bare", "core20", "core22", "gnome-3-38-2004", "gnome-42-2204", "gtk-common-themes", "snap-store>
Oct 17 21:05:30 LT-IttayD systemd[1]: Starting Update APT News...
Oct 17 21:05:30 LT-IttayD systemd[1]: Starting Update the local ESM caches...
Oct 17 21:05:30 LT-IttayD packagekitd[1656]: Failed to fetch http://il.archive.ubuntu.com/ubuntu/dists/jammy/InRelease  
Oct 17 21:05:30 LT-IttayD packagekitd[1656]: Failed to fetch http://il.archive.ubuntu.com/ubuntu/dists/jammy-updates/InRelease  
Oct 17 21:05:30 LT-IttayD packagekitd[1656]: Failed to fetch http://il.archive.ubuntu.com/ubuntu/dists/jammy-backports/InRelease  
Oct 17 21:05:30 LT-IttayD packagekitd[1656]: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jammy-security/InRelease  
Oct 17 21:05:30 LT-IttayD packagekitd[1656]: Failed to fetch https://dl.google.com/linux/chrome/deb/dists/stable/InRelease  
Oct 17 21:05:30 LT-IttayD packagekitd[1656]: Failed to fetch https://packagecloud.io/slacktechnologies/slack/debian/dists/jessie/InRelease  
Oct 17 21:05:30 LT-IttayD packagekitd[1656]: Some index files failed to download. They have been ignored, or old ones used instead.
Oct 17 21:05:30 LT-IttayD PackageKit[1656]: refresh-cache transaction /215_caadcdcb from uid 1000 finished with cancelled-priority after 836ms
Oct 17 21:05:30 LT-IttayD systemd[1]: apt-news.service: Deactivated successfully.

```

So apparmor is denying call to d-bus?

---

### Post by #&amp;thj^% on 2023-10-17
Did I mention my Love for snaps:
```
 sudo apparmor_status | grep snap
```

---

### Post by ittayd on 2023-10-17
```
$  sudo apparmor_status | grep snap
   /snap/snapd/18357/usr/lib/snapd/snap-confine
   /snap/snapd/18357/usr/lib/snapd/snap-confine//mount-namespace-capture-helper
   /snap/snapd/20290/usr/lib/snapd/snap-confine
   /snap/snapd/20290/usr/lib/snapd/snap-confine//mount-namespace-capture-helper
   /usr/lib/snapd/snap-confine
   /usr/lib/snapd/snap-confine//mount-namespace-capture-helper
   snap-update-ns.snap-store
   snap-update-ns.snapd-desktop-integration
   snap.snap-store.hook.configure
   snap.snap-store.snap-store
   snap.snap-store.ubuntu-software
   snap.snap-store.ubuntu-software-local-file
   snap.snapd-desktop-integration.hook.configure
   snap.snapd-desktop-integration.snapd-desktop-integration
   /snap/snapd-desktop-integration/83/usr/bin/snapd-desktop-integration (2787) snap.snapd-desktop-integration.snapd-desktop-integration
   /snap/snapd-desktop-integration/83/usr/bin/snapd-desktop-integration (2862) snap.snapd-desktop-integration.snapd-desktop-integration

```

---

### Post by #&amp;thj^% on 2023-10-17
The long and winding road, (Great name for a song huh)
```
dpkg -S /etc/apparmor.d/snap

```

---

### Post by ittayd on 2023-10-17
```
$ dpkg -S /etc/apparmor.d/snap
dpkg-query: no path found matching pattern /etc/apparmor.d/snap

```

also, there is no such file /etc/apparmor.d/snap. only /etc/apparmor.d/usr.lib.snapd.snap-confine.real

---

### Post by #&amp;thj^% on 2023-10-17
> **ittayd said:**
> 
also, there is no such file /etc/apparmor.d/snap. only /etc/apparmor.d/usr.lib.snapd.snap-confine.real

Well I can't see why this won't work then, my last suggestion is:
```
killall snap-store
``` 
And:
```
sudo snap refresh snap-store

```
So if that don't bring any joy I can only point you to snapcraft: [https://forum.snapcraft.io/](https://forum.snapcraft.io/)

---

### Post by ittayd on 2023-10-17
Same results. Thanks for the effort!

---

### Post by #&amp;thj^% on 2023-10-17
Good Luck and keep us updated, I'm very curious about this now.

---

### Post by MAFoElffen on 2023-10-19
I hate to throw this into this (with a slight hint of desperation):
gnome-software has 328 bug files against it.
snap-store has 128 bugs filed against it.

I see outside of this Forum, where Ubuntu users are having problems updating the caches from within gnome-software, where those problems do not really exist from doing 'apt update' in a terminal... That seems to be a known problem with gnome-software.

The snap-store has a problem of refreshing, because it autostarts in the background, so is running. It can't 'refresh' if it is running, so the work-around for that has been to do
```

sudo killall snap-store && sudo snap refresh snap-store

```
As one inline command so that the snap-store doesn't get a chance to autostart before the user gets a chance to issue the second command... ](*,)

Some users have resorted to uninstalling gnome-software and snap-store as "their solution". <-- I don't see that as "a solution"... but rather an avoidance. I am not a big fan (I had a Freudian slip, and typed 'bug fan' by mistake, Dang) of Snaps myself, but I think if it is there, it should at least work as designed, without causing the user problems. The same goes for gnome-software...

I am a fan of working from a terminal. Maybe that might sound masochistic... But I'm comfortable with that. Yet I work on GUI's to make things easier for users. Doesn't make sense does that?

I would suggest that this is ,and suggests another reportable Bug so that things can get worked on and fixed by the maintainers.

---

### Post by ittayd on 2023-10-20
I tried refresh. Did not solve this. 
Right now, I don't know what the bug is, if I just report this, there is probably little that can be done.

---

### Post by MAFoElffen on 2023-10-21
> **ittayd said:**
> I don't know what the bug is, if I just report this, there is probably little that can be done.
Yes...
> **MAFoElffen said:**
> I would suggest that this is ,and suggests  another reportable Bug so that things can get worked on and fixed by the  maintainers.
I would file it against gnome-software
```

ubuntu-bug gnome-software

```

---

