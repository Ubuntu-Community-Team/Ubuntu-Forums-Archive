---
title: "Partial Upgrade Question"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by popejeremy on 2009-10-03
Here's what I get when I do an apt-get upgrade:

```
~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  ubuntu-netbook-remix
The following packages will be upgraded:
  app-install-data apparmor apparmor-utils apport apport-gtk apt apt-transport-https apt-utils aptdaemon aptitude binutils byobu ca-certificates capplets-data command-not-found command-not-found-data console-setup couchdb couchdb-bin cpp-4.4 cups cups-bsd cups-client cups-common dbus dbus-x11 debconf debconf-i18n desktop-switcher desktopcouch devicekit-disks example-content f-spot firefox firefox-3.5 firefox-3.5-branding firefox-3.5-gnome-support firefox-gnome-support gcc-4.4 gcc-4.4-base gdb gdm genisoimage gnome-control-center gnome-disk-utility gnome-menus gnome-settings-daemon gnome-user-guide grub-common grub-pc gtk2-engines-pixbuf guile-1.8-libs hpijs hplip hplip-cups hplip-data indicator-messages indicator-session initramfs-tools initscripts jockey-common jockey-gtk language-pack-en language-pack-en-base language-pack-gnome-en language-pack-gnome-en-base libapparmor-perl libapparmor1 libasound2-plugins libbonobo2-0 libbonobo2-common libc-bin libc-dev-bin libc6 libc6-dev libc6-i686 libclutk-0.2-0 libcups2 libcupscgi1 libcupsdriver1 libcupsimage2 libcupsmime1 libcupsppdc1 libdbus-1-3 libept0 libgail-common libgail18 libgcc1 libgdu-gtk0 libgdu0 libgl1-mesa-dri libgl1-mesa-glx libglib2.0-0 libglib2.0-data libglu1-mesa libgnome-menu2 libgnome-window-settings1 libgnomeui-0 libgnomeui-common libgomp1 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtksourceview2.0-0 libgtksourceview2.0-common libgweather-common libgweather1 libindicate-gtk1 libindicate3 libnautilus-extension1 libnm-glib2 libnm-util1 libntfs-3g54 libperl5.10 libpolkit-agent-1-0 libpolkit-backend-1-0 libpolkit-gobject-1-0 libpolkit-gtk-1-0 libpython2.6 libqt4-dbus libqt4-network libqt4-sql libqt4-sql-mysql libqt4-xml libqtcore4 libqtgui4 libsmbclient libsnmp-base libsnmp15 libstdc++6 libstlport4.6ldbl libtelepathy-glib0 libtotem-plparser12 libusplash0 libvte-common libvte9 libwbclient0 libwebkit-1.0-2 libwebkit-1.0-common libxklavier15 linux-firmware linux-headers-2.6.31-11 linux-headers-2.6.31-11-generic linux-image-2.6.31-11-generic linux-libc-dev maximus memtest86+ mesa-utils nautilus nautilus-data network-manager notify-osd ntfs-3g onboard openoffice.org-base-core openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-emailmerge openoffice.org-gnome openoffice.org-gtk openoffice.org-impress openoffice.org-math openoffice.org-style-human openoffice.org-writer perl perl-base perl-modules policykit-1 policykit-1-gnome python-apport python-apt python-aptdaemon python-aptdaemon-gtk python-cupshelpers python-desktopcouch python-desktopcouch-records python-gdbm python-gmenu python-gtkhtml2 python-gtksourceview2 python-problem-report python-ubuntuone-client python-uno python-vte python2.6 python2.6-minimal samba-common samba-common-bin smbclient synaptic system-config-printer-common system-config-printer-gnome system-config-printer-udev system-tools-backends sysv-rc sysvinit-utils tasksel tasksel-data telepathy-gabble totem totem-common totem-mozilla totem-plugins transcode transcode-doc transcode-utils ttf-opensymbol tzdata ubuntu-docs ubuntu-minimal ubuntu-netbook-remix-default-settings ubuntu-standard ubuntu-xsplash-artwork ubuntuone-client ubuntuone-client-gnome uno-libs3 update-manager update-manager-core upstart ure usb-creator-common usb-creator-gtk usplash wodim xdg-user-dirs xserver-common xserver-xorg-core xserver-xorg-input-wacom xserver-xorg-video-geode xsplash

232 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

I have learned the hard way to not do partial upgrades, so I'm not doing this upgrade. My question is: Will my system always be in this state, or will ubuntu-netbook-remix eventually catch up? Or have I inadvertently gotten my system into a perpetually un-upgradeable state? Or is this the sort of partial upgrade that I should do?

Where do I go from here? Thanks!

---

### Post by Slug71 on 2009-10-03
Just wait. They will come.

---

### Post by blakamin on 2009-10-03
It's not removing anything so what is the problem?

---

### Post by popejeremy on 2009-10-03
> **blakamin said:**
> It's not removing anything so what is the problem?

I don't know. That's what I'm asking. All I know is that partial upgrades can cause problems, so I want to avoid them. Are you saying that this one should be okay?

---

### Post by trulan on 2009-10-03
It's okay to let it hold back a package.  It's when you run apt-get dist-upgrade, which lets it remove all packages necessary to enable upgrading the one being held back, that you run into trouble.  It might be removing something little and obsolete, or it might want to remove your entire desktop and all your software.

What would sensibly be called a partial upgrade (not upgrading everything) is fine.  What is actually called a partial upgrade (removing packages so others can be upgraded/installed) is dangerous.

---

### Post by psyke83 on 2009-10-04
Your output does not suggest a Partial Upgrade scenario.

A Partial Upgrade scenario occurs if you try to run a "dist-upgrade", and you see that >0 packages are to be removed.

It would be safe for you to run an upgrade, therefore.

---

### Post by blakamin on 2009-10-04
Ok, it *might* break some packages but it doesn't look that way... the reason *most* people have a problem with "partial" upgrade is due to the fact it's removing a heap of packages and not updating them and they don't notice. Yours is not removing any from what I see. Just do apt-get upgrade (not full-upgrade) and you should be fine.
That being said, some dependencies might not be resolved for other programs and it might break things like open office, gnome etc.... just pays to look at the packages that are to be upgraded.

---

### Post by popejeremy on 2009-10-04
Okay then. I'm doing the upgrade. Hopefully my computer doesn't explode.

---

### Post by blakamin on 2009-10-04
Just hide behind a piece of soft furniture after you hit enter....

---

### Post by psyke83 on 2009-10-04
> **blakamin said:**
> Just hide behind a piece of soft furniture after you hit enter....

Don't be ridiculous. The soft furniture will catch fire the quickest!

---

### Post by trulan on 2009-10-04
Maybe full football gear would be in order?  Or a firefighter's suit, boots, helmet, etc.?

---

### Post by jatinps on 2009-10-06
did it work? are you back :lolflag:
i see a partial upgrade today which is upgrading a ton of packages but removing only 1 noxpm lib and replacing with an xpm lib.
these xpm libs seem harmless, but lets see :confused:
[http://ns2.canonical.com/search?lang=ko&suite=karmic&arch=any&searchon=names&keywords=xpm](http://ns2.canonical.com/search?lang=ko&suite=karmic&arch=any&searchon=names&keywords=xpm)

---

### Post by emarkay on 2009-10-06
Correct me if I am wrong. A "Partial Upgrade" only happens in the GUI "Updare Manager" when the warning about "Partial Upgrades" appear  - AND/OR - if through Terminal or Recovery (command line), you see that there will be the removal of packages? 

Just want to confirm and clarify.

---

### Post by trulan on 2009-10-06
That's correct.  Either through the GUI, when it offers a partial upgrade, or in the terminal, if you run apt-get dist-upgrade

---

