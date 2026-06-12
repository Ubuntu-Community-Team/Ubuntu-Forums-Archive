---
title: "Upgrade from lucid to precise (yes, I know they are old..)"
date: 2018-11-26
forum: Installation &amp; Upgrades
---

### Post by SteMMo on 2018-11-26
Hi all,
I've got a VM with an old lucid version **Ubuntu 10.04.4 LTS**.
I decided to move to precise and I modified the sources files: no problem with 'sudo apt-get update'.

**sudo apt-get upgrade** returns:
```

  ..
  xserver-xorg-video-sis xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident
  xserver-xorg-video-tseng xserver-xorg-video-vesa xserver-xorg-video-vmware xserver-xorg-video-voodoo xterm xz-utils yelp
  zenity zlib1g
0 aggiornati, 0 installati, 0 da rimuovere e 845 non aggiornati.
mora@ubuntu:/etc/apt$ 
```
and do nothing.
If I type **sudo apt-get dist-upgrade** I have:
```
E: Impossibile eseguire immediatamente la configurazione su "python-minimal".Per maggiori informazioni, consultare "man 5 apt.conf" alla sezione "APT::Immediate-Configure" (2).

```

So I changed in **sudo apt-get dist-upgrade -o APT::Immediate-Configure=0**:
```
E: Couldn't configure pre-depend multiarch-support for libgomp1, probably a dependency cycle.
```

I've read a lot of articles but I'm still in a mess.
I try to remove the package but I receive:
```
mora@ubuntu:/etc/apt$ sudo apt-get remove libgomp1
...

I seguenti pacchetti hanno dipendenze non soddisfatte:
  libasound2: Rompe: libasound2-plugins (< 1.0.24) ma 1.0.22-0ubuntu6 sta per essere installato
  libglib2.0-0: Rompe: gvfs (< 1.8) ma 1.6.1-0ubuntu1build1 sta per essere installato
  libgnome-keyring0: Rompe: gnome-keyring (< 3.0) ma 2.92.92.is.2.30.3-0ubuntu1.1 sta per essere installato
  libpango1.0-0: Rompe: plymouth (< 0.8.2-2ubuntu19) ma 0.8.2-2ubuntu2.2 sta per essere installato
  ppp: Rompe: network-manager-pptp (<= 0.8.0.999-1) ma 0.8-0ubuntu3 sta per essere installato

```

Almost every operation on packages returns with **Broke package**

Any idea?
Thanks!

---

### Post by QIII on 2018-11-26
Hello!

To upgrade from an unsupported version, [this]("https://help.ubuntu.com/community/EOLUpgrades") is the appropriate method.

However, you are certainly in for a significant emotional event even under the best of circumstances.  

From where you are right now, you would be far better off doing a complete re-installation.  I'd create an entirely new VM rather than overwriting the virtual disk you are using right now.  That will allow you to attempt to recover and back up any important files.

Since 14.04 will go out of support in a few months, I'd steer clear of it and move directly to 16.04 or 18.04.

Cheers!

---

