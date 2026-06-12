---
title: "[SOLVED] dist-upgrade just removed evelution, update-manager etc."
date: 2008-10-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by whoop on 2008-10-15
I just did an sudo apt-get update, sudo apt-get dist-upgrade. Evolution is gone, so is update-manager; probably some other things. What the hell happened?

---

### Post by whoop on 2008-10-15
I really seem to be missing more than evolution and update-manager (ubuntu-desktop was even removed). Is there anyway I can see what apt-get removed? I do not see it in synaptic logs.

---

### Post by psyke83 on 2008-10-15
> **whoop said:**
> I just did an sudo apt-get update, sudo apt-get dist-upgrade. Evolution is gone, so is update-manager; probably some other things. What the hell happened?

Don't dist-upgrade if it elects to remove packages, unless you are 100% informed as to whether certain packages really need to be removed.

Hopefully you may be able to get things back by reinstalling the "ubuntu-desktop" metapackage.

---

### Post by whoop on 2008-10-15
I thought I looked at that and did not see anything important (guess I wasn't paying attention). If I try to install ubuntu-desktop with synaptic I get this:
```

ubuntu-desktop:
 Depends: update-manager but it is not going to be installed
 Depends: update-notifier but it is not going to be installed
 Recommends: ekiga but it is not going to be installed
 Recommends: evolution but it is not going to be installed
 Recommends: evolution-exchange but it is not going to be installed
 Recommends: evolution-plugins but it is not going to be installed

```
I cannot seem to install these packages either. When I try to install evolution f.e. I get:
```

evolution:
  Depends: evolution-common (=2.24.0-0ubuntu2) but 2.24.0-0ubuntu3 is to be installed
 Depends: evolution-data-server but it is not going to be installed
 Depends: evolution-data-server but it is not going to be installed
 Recommends: evolution-plugins but it is not going to be installed

```
looks like synaptic is linked to an old version of evolution?

any ideas?

---

### Post by yakumo9275 on 2008-10-15
I installed the update manager from /var/cache/apt/archives then did the same with evolution, then did apt-get install ubuntu-desktop

sigh...

guess we both got bit.

---

### Post by whoop on 2008-10-15
Installing via /var/cache/apt/archives does not work for me (dependency problem). so if I try:  sudo apt-get install ubuntu-desktop
I get:
```

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-desktop: Depends: update-manager but it is not going to be installed
                  Depends: update-notifier but it is not going to be installed
                  Recommends: ekiga but it is not going to be installed
                  Recommends: evolution but it is not going to be installed
                  Recommends: evolution-exchange but it is not going to be installed
                  Recommends: evolution-plugins but it is not going to be installed
E: Broken packages

```

Help would be much appreciated.

---

### Post by OrangeCrate on 2008-10-15
> **whoop said:**
> 
Help would be much appreciated.


Unless you got a lot of time to try to figure this puzzle out, out of curiosity, why don't you just backup your Home folder to a stick, and reinstall? Your current installation seems to be pretty much fried. Anyway, for what it's worth, that's what I would do.

---

### Post by Sef on 2008-10-15
> I just did an sudo apt-get update, sudo apt-get dist-upgrade. Evolution is gone, so is update-manager; probably some other things. What the hell happened?

Dist-upgrade is not supported.  To properly upgrade to Intrepid Ibex, read [this sticky]("http://ubuntuforums.org/showthread.php?t=936696").

---

### Post by dbulante on 2008-10-15
It did the same for me.  Network manager is not working.  Everything else seems to be fine.

---

### Post by rbmorse on 2008-10-15
> **Sef said:**
> Dist-upgrade is not supported.  To properly upgrade to Intrepid Ibex, read [this sticky]("http://ubuntuforums.org/showthread.php?t=936696").
I saw that, but it wasn't clear to me that this method applies to updating an existing, fully realized Intrepid installation as well as upgrading from Hardy. .

---

### Post by iponeverything on 2008-10-15
> **dbulante said:**
> It did the same for me.  Network manager is not working.  Everything else seems to be fine.

The network manager problem is fairly common.

Most of the time just running it the command line:

nm-applet

will cause it to start showing up again. If its gone again after the next reboot go to 
System -> Preferences -> Sessions 


Go to "+ Add" and fill in the fields:

Name: Network Manager
Command: nm-applet --sm-disable 
Comment: Network Manager applet

---

### Post by racmar on 2008-10-16
PS: you should make backups before attempting this!

temporary workaround to fix evolution:
```
cd /var/lib/apt/lists
sudo grep evolution-common *

```

look for the file that has this line ( yours may be different, because I'm using 64-bit intrepid ):
> **us.archive.ubuntu.com_ubuntu_dists_intrepid_main_binary-amd64_Packages**:Depends: libart-2.0-2 (>= 2.3.18), libatk1.0-0 (>= 1.20.0), libbluetooth3 (>= 4.9), libbonobo2-0 (>= 2.15.0), libbonoboui2-0 (>= 2.15.1), libc6 (>= 2.4), libcairo2 (>= 1.2.4), libcamel1.2-13 (>= 2.24.0), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.71), libebackend1.2-0 (>= 2.24.0), libebook1.2-9 (>= 2.24.0), libecal1.2-7 (>= 2.24.0), libedataserver1.2-11 (>= 2.24.0), libedataserverui1.2-8 (>= 2.24.0), libegroupwise1.2-13 (>= 2.24.0), libenchant1c2a, libexchange-storage1.2-3 (>= 2.24.0), libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.3.5), libgconf2-4 (>= 2.13.5), libgdata-google1.2-1 (>= 2.24.0), libgdata1.2-1 (>= 2.24.0), libglade2-0 (>= 1:2.6.1), libglib2.0-0 (>= 2.18.0), libgnome-pilot2 (>= 2.0.2), libgnome2-0 (>= 2.17.3), libgnomecanvas2-0 (>= 2.11.1), libgnomeui-0 (>= 2.22.0), libgnomevfs2-0 (>= 1:2.17.90), libgtk2.0-0 (>= 2.14.1), libgtkhtml-editor0, libgtkhtml3.14-19 (>= 3.24.0), libhal1 (>= 0.5.8.1), libice6 (>= 1:1.0.0), liblaunchpad-integration1 (>= 0.1.17), libldap-2.4-2 (>= 2.4.7), liblpint-bonobo0, libnotify1 (>= 0.4.4), libnotify1-gtk2.10, libnspr4-0d (>= 1.8.0.10), libnss3-1d (>= 3.12.0~1.9b1), liborbit2 (>= 1:2.14.10), libpango1.0-0 (>= 1.21.6), libpisock9, libpisync1, libpixman-1-0, libpng12-0 (>= 1.2.13-4), libpopt0 (>= 1.14), libsm6, libsoup2.4-1 (>= 2.23.91), libsqlite3-0 (>= 3.5.9), libusb-0.1-4 (>= 2:0.1.12), libx11-6, libxcb-render-util0, libxcb-render0, libxcb1, libxcomposite1 (>= 1:0.3-1), libxcursor1 (>> 1.1.2), libxdamage1 (>= 1:1.1), libxext6, libxfixes3 (>= 1:4.0.1), libxi6 (>= 2:1.1.3-1ubuntu1), libxinerama1, libxml2 (>= 2.6.27), libxrandr2, libxrender1, python2.5 (>= 2.5), zlib1g (>= 1:1.1.4), gconf2 (>= 2.12.1-1), evolution-common (= 2.24.0-0ubuntu2), evolution-data-server (>= 2.23.91), evolution-data-server (<< 2.25), gnome-icon-theme (>= 2.19.91), dbus


change **evolution-common (= 2.24.0-0ubuntu2)** to **evolution-common (>= 2.24.0-0ubuntu2)**
```
sudo nano us.archive.ubuntu.com_ubuntu_dists_intrepid_main_binary-amd64_Packages

```

do the same for /var/lib/dpkg/status:
change **evolution-common (= 2.24.0-0ubuntu2)** to **evolution-common (>= 2.24.0-0ubuntu2)**
```
sudo nano /var/lib/dpkg/status
```


then:
```
sudo apt-get install evolution
```

PS: you should make backups before attempting this!

---

### Post by wgrant on 2008-10-16
> **racmar said:**
> [obscenity censored]

NO! Don't ever, ever do that. That's just wrong. Wrong, wrong, wrong. I hope dpkg complained at you later.

---

### Post by racmar on 2008-10-16
> 
NO! Don't ever, ever do that. That's just wrong. Wrong, wrong, wrong. I hope dpkg complained at you later.

Nope, it worked like a charm.  I'm using evolution right now.  So, if you suggest I never do that on a test system, why not?  Also, I know I could build a new package with the correct version number, but this was just easier.

---

### Post by dbulante on 2008-10-16
> **iponeverything said:**
> The network manager problem is fairly common.

Most of the time just running it the command line:

nm-applet

will cause it to start showing up again. If its gone again after the next reboot go to 
System -> Preferences -> Sessions 


Go to "+ Add" and fill in the fields:

Name: Network Manager
Command: nm-applet --sm-disable 
Comment: Network Manager applet

The problem I have is that the wireless network is not being recognized by Network Manager, after this last update.

---

### Post by Aries K on 2008-10-16
Hi, what is the correct way of fixing this? I was already running Intrepid Ibex and I did an update as usual. Next thing I know Evolution is gone. :confused: Can I just wait it out until the next update fixes the problem? Thanks in advance.

---

### Post by racmar on 2008-10-16
Aries K,

Yes, you can just wait and the update will eventually be corrected.  I was just bored, and wanted to figure out a temp solution.

---

### Post by Aries K on 2008-10-16
> **racmar said:**
> Aries K,

Yes, you can just wait, and the update will eventually be corrected.  I was just bored, and wanted to figure out a temp solution.

Alright thanks.:)

---

### Post by whoop on 2008-10-16
installing ubuntu-desktop via synaptic seems to have solved all my problems just now. It also installed evolution, update-manager and ekiga.
Problem seems to be solved for me now.

---

