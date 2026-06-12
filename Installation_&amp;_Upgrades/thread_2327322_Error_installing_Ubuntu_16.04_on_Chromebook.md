---
title: "Error installing Ubuntu 16.04 on Chromebook"
date: 2016-06-09
forum: Installation &amp; Upgrades
---

### Post by cblnchat on 2016-06-09
Hi there,

I'm getting an error while trying to install the latest Ubuntu version on a Chromebook. Xenial is unsupported but I'm willing to do the tinkering to get it to work. I just need to be able to get into Ubuntu to play around.

The error I'm getting is :

```

chronos@localhost / $ sudo startgnome
Entering /mnt/stateful_partition/crouton/chroots/xenial...
UID 1000 not found in xenial
Unmounting /mnt/stateful_partition/crouton/chroots/xenial...
chronos@localhost / $

```

I've never run into UID before (although I haven't used Ubuntu in a few years) so I'm not sure what to do and I couldn't find much helpful info on Google pertaining to this error with Ubuntu on a Chromebook.

Thanks!

---

### Post by Omar_Jair on 2016-06-09
have you tried the "startx unity" command? Ubuntu runs Unity now. if yo cannot manage to install it with unity desktop i recommend you to try another desktop environment like XFCE or Mate, you can also try with 
sudo service lightdm start

---

### Post by cblnchat on 2016-06-10
I hadn't tried the "start unity" command because when I tried to install the unity desktop environment with 16.04 it gave me the error:

```

chronos@localhost / $ sudo sh -e ~/Downloads/crouton -t unity -r xenial
Downloading latest crouton installer...
######################################################################## 100.0%
unity target does not work in xephyr in xenial due to missing egl support.
Invalid target "unity".

```

I've also never been a huge fan of XFCE and I don't even see Mate in the listed supported evironments. So Gnome was the only other one I wanted to use.

But I haven't come across "sudo service lightdm start"
What does this command do?

I'm currently trying to just reinstall the 16.04 Gnome to see if that fixes it.

---

### Post by cblnchat on 2016-06-10
Upon trying the installation again I noticed this message:

```

Package gnome-session-fallback is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  gnome-session-flashback

E: Package 'gnome-session-fallback' has no installation candidate
Failed to complete chroot setup.
The chroot setup script may be broken. Your chroot is not fully configured.
Removing the chroot setup script. You may want to update your chroot again.
UID 1000 not found in xenial
Unmounting /mnt/stateful_partition/crouton/chroots/xenial...
chronos@localhost / $ 

```

I'm not sure how to update the chroot, because I think what that means is that I have to update the Ubuntu environment inside of it...which I can't get to.
I also don't know what to do about the 'gnome-session-fallback'

---

### Post by cblnchat on 2016-06-11
So I tried to install XFCE and it seemed to work, until I tried to actually start it. My chromebook is now frozen so I'll only be able to put what I can see.

```

(++) Log file: "/tmp/Xorg.crouton.1.log", Time: Sat Jun 11 14:21:26 2016
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
gbm: failed to open any driver (search paths /usr/lib/arm-linux-gnueabihf/dri:${ORIGIN}/dri:/usr/lib/dri)
gbm: Last dlopen error: /usr/lib/dri/exynos_dri.so :cannot open shared object file: No such file or directory
failed to load driver: exynos
EGL_MESA_drm_image required.
crouton: version 1-20160518095657~master:fd37bb79
release: xenial
architecture: xorg
targets: xfce
host: version 7978.74.0 (Official Build) stable-channel daisy
kernel: Linux localhost 3.8.11 #1 SMP Wed May 11 21:59:05 PDT 2016 armv7l armv7l armv7l GNU/Linux
freon: yes
No Chromium OS X server is available.
_IceTransmkdir: Owner of /tmp/.ICE-unix should be set to root
xfce4-session: No GPG agent found
xfce4-session: No SSH authentication agent found

(xfce4-session:30709): xfce4-session-WARNING **: xfsm_manager_load_session: Something went wrong with /home/cody/ .cache/sessions/xfce4-session-localhost:1, Does it exist? Permissions issue?
/usr/bin/xbindkeys_autostart: line 24: CONF: unbound variable

(xfwm4:307027): GLib-CRITICAL **: g_str_has_prefix: assertion 'prefix != NULL' failed

(xfwm4:307027): xfw4-WARNING **: The property '/general/double_click_distance' of type int is not supported

(xfsettingsd:30739): GLib-CRITICAL **: g_str_has_prefix: assertion 'prefix !=NULL' failed

(xfsettingsd:30739): GLib_GObject-CRITICAL **: g_value_get_string: assertion 'G_VALUE_HOLDS_STRING (value)' failed

(xfsettingsd:30739): GLib_GObject-CRITICAL **: g_value_get_string: assertion 'G_VALUE_HOLDS_STRING (value)' failed

(xfwm4:30727): xfwm4-WARNING **: Another compositing manager is running on screen 0

```

I typed that all out so hopefully I didn't get anything wrong.

EDIT: Well I forced the Chromebook to shut down and tried to start xfce again and it just kinda worked

---

### Post by Omar_Jair on 2016-06-11
im surprised about the desktop, However mate is included on the Desktop Environments, Check for Ubuntu Flavours, there is Ubuntu Mate

---

### Post by lliseil on 2016-06-12
« crouton UID 1000 not found » returns many results from Crouton's developer dnschneid. That's also the best place to ask on this as it is Crouton related.

---

