---
title: "Can grub switch between server and desktop"
date: 2008-05-14
forum: Installation &amp; Upgrades
---

### Post by rgeddes on 2008-05-14
I currently have a AMD 64-bit machine setup as a server, and would like to have the option to boot it as an Ubuntu server or an Ubuntu desktop machine.

I know grub can dual boot between Windows and Ubuntu... is there a similar way to boot my machine as an Ubuntu server or an Ubuntu desktop machine?

Thanks
Richard

---

### Post by az on 2008-05-14
> **rgeddes said:**
> I currently have a AMD 64-bit machine setup as a server, and would like to have the option to boot it as an Ubuntu server or an Ubuntu desktop machine.

I know grub can dual boot between Windows and Ubuntu... is there a similar way to boot my machine as an Ubuntu server or an Ubuntu desktop machine?

Thanks
Richard

Sure.  Install the desktop version of Ubuntu.  By default, it should offer to shrink the current OS and install itself beside it as a dual boot.  Make sure you don't pick the "use entire disk" option when you install.

You could also just install the desktop packages on your server and run them only when you want.  You would prevent the desktop from being started by getting rid of the gdm symlink in the /etc/rc2.d directory.  To start the desktop, you would run

sudo /etc/init.d/gdm start

I am not sure of there are other daemons that you would need to get rid of, too.

---

### Post by lavinog on 2008-05-14
> **az said:**
> 
You could also just install the desktop packages on your server and run them only when you want.  You would prevent the desktop from being started by getting rid of the gdm symlink in the /etc/rc2.d directory.  To start the desktop, you would run

sudo /etc/init.d/gdm start

I am not sure of there are other daemons that you would need to get rid of, too.
I would imagine that there are many daemons that should be removed.

there is a way to change the default runlevel, but it looks like things have changed since i last figured it out. It used to be an entry in /etc/inittab but i don't seem to have one of those anymore???
but anyway you just tell it to only go to the runlevel for the desired setup. 

here are what my rc 2-4 entries look like on my server (still running gutsy though):
```
rc2.d:
README                       S11klogd  S16ssh            S19cupsys          S20jmon     S20samba          S89atd      S98munin-node
S10sysklogd                  S12dbus   S17mysql-ndb-mgm  S19mysql           S20makedev  S20smartmontools  S89cron     S99rc.local
S10xserver-xorg-input-wacom  S15bind9  S18mysql-ndb      S19postgresql-8.1  S20rsync    S23ntp            S91apache2  S99rmnologin

rc3.d:
README                       S11klogd  S16ssh            S19cupsys          S20jmon     S20samba          S89atd      S98munin-node
S10sysklogd                  S12dbus   S17mysql-ndb-mgm  S19mysql           S20makedev  S20smartmontools  S89cron     S99rc.local
S10xserver-xorg-input-wacom  S15bind9  S18mysql-ndb      S19postgresql-8.1  S20rsync    S23ntp            S91apache2  S99rmnologin

rc4.d:
README                       S11klogd  S16ssh            S19cupsys          S20jmon     S20samba          S89atd      S98munin-node
S10sysklogd                  S12dbus   S17mysql-ndb-mgm  S19mysql           S20makedev  S20smartmontools  S89cron     S99rc.local
S10xserver-xorg-input-wacom  S15bind9  S18mysql-ndb      S19postgresql-8.1  S20rsync    S23ntp            S91apache2  S99rmnologin


```
If i understand correctly the normal default is rc2 
so if rc 3 starts your desktop and rc2 is setup to just be the server you could just boot to your server, login in the console and type 'init 3' and your desktop should start up.
in theory of course... I would stick to dual booting though, this way if there is a bad error on one OS you can boot to the other to repair it.

I am looking to play around with the different runlevels and configuring them for when the server is on battery backup...just need the time :(

---

