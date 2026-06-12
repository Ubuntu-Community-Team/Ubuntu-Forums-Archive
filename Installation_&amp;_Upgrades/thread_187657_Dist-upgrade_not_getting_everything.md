---
title: "Dist-upgrade not getting everything?"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by Scarabomb on 2006-06-03
I'm scared to reboot my system after a dist-upgrade, install ubuntu-base and, install ubuntu-desktop.

At the end of my dist-upgrade I got this
```
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/scrollkeeper/lib scrollkeeper0_0.3.14-11ubuntu6_i386.deb  Error reading from server - read (104 C onnection reset by peer) [IP: 85.133.25.8 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gksu/gksu_1.3.7- 0ubuntu9_i386.deb  Error reading from server - read (104 Connection reset by pee r) [IP: 85.133.25.8 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-mis sing?

```

The ubuntu-base went through but I got this for install ubuntu-desktop
```
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-desktop: Depends: deskbar-applet but it is not going to be installed
                  Depends: ekiga but it is not going to be installed
                  Depends: gdebi but it is not going to be installed
                  Depends: gnome-power-manager but it is not going to be install ed
                  Depends: gnome-screensaver but it is not going to be installed
                  Depends: gnome-system-monitor but it is not going to be instal led
                  Depends: gnome-volume-manager but it is not going to be instal led
                  Depends: gnopernicus but it is not going to be installed
                  Depends: gok but it is not going to be installed
                  Depends: libgnomevfs2-bin but it is not going to be installed
                  Depends: libgnomevfs2-extra but it is not going to be installe d
                  Depends: openoffice.org-gnome but it is not going to be instal led
E: Broken packages

```

If any advice or assistance can be thrown this way I would much appreciate it, thanks!

~Aspiring Dapper User

---

### Post by llamakc on 2006-06-03
Do you have mixed sources.list entries? What does your /etc/apt/sources.list look like?

---

### Post by Scarabomb on 2006-06-03
I swear I'm retarded...I didn't even get Alien!! I'll see how this goes

---

### Post by Scarabomb on 2006-06-03
My Source list is basically the default breezy list with breezy replaced with dapper.

I did a clean install on JUST to see if this dist upgrade would go through, it's working through right now, I just hope it works when it's all said and done

---

### Post by llamakc on 2006-06-03
Good luck. Don't forget to give [http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/) a try when you're up and running.

---

### Post by Scarabomb on 2006-06-03
Cool, I'm in Dapper which is nice but here's where it gets fun

I'm here but my I had the Xserver problem where it won't go to 1280x800 (my "optimum" resolution)

I'm going to search around the forus some more because I know for a fact that there's a thread on it somewhere but if someone would like to give input then that would be great.  Just to say though before I go off to the world of searching is that when I boot into Dapper WITHOUT Vesa and ati on instead, it just sorta goes black.  I end up switching out tty#'s so I can get a good thing to dpkg-reconfigure xserver-xorg.

Thanks in advanced.

---

