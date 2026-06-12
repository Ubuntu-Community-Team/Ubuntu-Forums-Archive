---
title: "Can't upgrade to 15.10"
date: 2016-05-12
forum: Installation &amp; Upgrades
---

### Post by enekoalfer on 2016-05-12
Hey! :)

I have been trying to upgrade from Ubuntu 14.04 LTS to 15.10, so that I can upgrade to 16.04 later. The problem is that when I try to upgrade to 15.10 with the software manager, an error message appears, which says that the upgrade couldn't be calculated. I have googled that, and some people agree that the problem may be broken packages in my system. I looked for broken packages via terminal, and I've got a huuuuge quantity of them. So, first of all, what do I have to do to upgrade to 15.10? If the solution has something to do with removing broken packages, how can I do that?

Thanks!

---

### Post by grahammechanical on 2016-05-12
Did you know that 14.04 users can upgrade direct to 16.04? You need to do two things. 1) Go to System Settings>Software & Updates>Update tab and make sure that "Notify me of a new Ubuntu version" is set to "For Long Term Support versions." 2) Wait until the summer when 16.04.1 is released. The 16.04 release notes say this:

> 14.04 LTS to LTS upgrades will be enabled with the 16.04.1 LTS point release, in approximately 3 months time.

[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes)

If you succeed in upgrading to 15.10 you will have to upgrade to 16.04 anyway when 15.10 reaches end of life in July 2016.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

But you have other things to do before you upgrade to a new version because upgrading to a new version will not fix problems. Only a fresh installation will do that. You need to revert to using an open source video driver, disable any PPAs and revert the desktop to a default standard as much as possible.

You also need to fix those broken packages if you do indeed have broken packages.

```
sudo apt-get install -f
```

But if you want to go ahead and upgrade to 15.10, then make sure that "Notify me of a new Ubuntu version" of set to "For any new version."

Regards.

---

### Post by enekoalfer on 2016-05-13
Ok, so I will wait until summer. Thank you for that information. Anyway, I'm still not sure of how to remove or fix broken packages :( (still new user)

---

### Post by deadflowr on 2016-05-13
Best to post the output from the terminal that shows what broken packages you have.
Otherwise, we might be at a loss.

---

### Post by Bucky Ball on 2016-05-13
> **enekoalfer said:**
> ... I'm still not sure of how to remove or fix broken packages :( (still new user)

You try with the command that grahammechanical just provided. 

```
sudo apt-get install -f
```

;)

PS: You don't need to wait until the first 16.04 point release to upgrade to it. You can do so via a terminal anytime. Personally, as you are a new user, I would still advise that wait, or at least a few months, before the upgrade. 14.04 is very stable, has plenty of support left (2019) and if it ain't broke, don't fix it! 16.04 is still a little wobbly for some and will take a while to get some bugs squashed, as per normal with any new release, LTS or otherwise.

---

### Post by enekoalfer on 2016-05-13
The problem is that when I locate broken packages with **grep Broken /var/log/dist-upgrade/apt.log**, I get this huuuuuuge list (in terminal):

```
Broken pcsx2:i386 Depende on libegl1-x11 [ i386 ] < none > ( none )
Broken pcsx2:i386 Depende on libgl1-mesa-glx [ i386 ] < none -> 11.0.2-1ubuntu4 > ( libs )
Broken pcsx2:i386 Depende on libgl1 [ i386 ] < none > ( none )
Broken libtag1c2a:amd64 Depende on libtag1-vanilla [ amd64 ] < 1.9.1-2 > ( libs ) (= 1.9.1-2)
Broken libwebkitgtk-3.0-0:amd64 Depende on libegl1-mesa [ amd64 ] < none -> 11.0.2-1ubuntu4 > ( libs ) (>= 7.8.1)
Broken libwebkitgtk-3.0-0:amd64 Depende on libgl1-mesa-glx [ amd64 ] < none -> 11.0.2-1ubuntu4 > ( libs )
Broken libtag1v5:amd64 Entra en conflicto on libtag1c2a [ amd64 ] < 1.9.1-2 > ( libs )
Broken libgl1-mesa-dri-lts-vivid:amd64 Depende on libllvm3.6 [ amd64 ] < 1:3.6-2ubuntu1~trusty1 > ( libs )
Broken libgl1-mesa-dri-lts-vivid:amd64 Entra en conflicto on libgl1-mesa-dri [ amd64 ] < none -> 11.0.2-1ubuntu4 > ( libs )
Broken libgl1-mesa-dri-lts-vivid:amd64 Entra en conflicto on libgl1-mesa-dri [ i386 ] < none -> 11.0.2-1ubuntu4 > ( libs )
Broken libegl1-mesa-dev:amd64 Depende on libegl1-mesa [ amd64 ] < none -> 11.0.2-1ubuntu4 > ( libs ) (= 10.1.3-0ubuntu0.6)
Broken libegl1-mesa-dev:amd64 Depende on libegl1-mesa-lts-utopic [ amd64 ] < none > ( none )
Broken libegl1-mesa-dev:amd64 Depende on libegl1-mesa-lts-vivid [ amd64 ] < 10.5.9-2ubuntu1~trusty2 > ( libs )
Broken libegl1-mesa-dev:amd64 Depende on libegl1-mesa-lts-wily [ amd64 ] < none > ( none )
Broken libegl1-mesa-dev:amd64 Depende on libegl1-mesa-lts-xenial [ amd64 ] < none > ( none )
Broken libwayland-egl1-mesa-lts-vivid:amd64 Depende on libegl1-mesa-lts-vivid [ amd64 ] < 10.5.9-2ubuntu1~trusty2 > ( libs ) (= 10.5.9-2ubuntu1~trusty2)
Broken libglu1-mesa:i386 Depende on libgl1-mesa-glx [ i386 ] < none -> 11.0.2-1ubuntu4 > ( libs )
Broken libegl1-mesa:amd64 Depende on libgl1-mesa-dri [ amd64 ] < none -> 11.0.2-1ubuntu4 > ( libs ) (= 11.0.2-1ubuntu4)
Broken xserver-xorg-video-vmware-lts-vivid:amd64 Depende on libxatracker2-lts-vivid [ amd64 ] < 10.5.9-2ubuntu1~trusty2 > ( libs )
Broken libgles2-mesa-dev:amd64 Depende on libegl1-mesa-dev [ amd64 ] < 10.1.3-0ubuntu0.6 -> 11.0.2-1ubuntu4 > ( libdevel )
Broken libtag1v5-vanilla:amd64 Rompe on libtag1-vanilla [ amd64 ] < 1.9.1-2 > ( libs )
Broken libglapi-mesa-lts-vivid:amd64 Entra en conflicto on libglapi-mesa [ amd64 ] < none -> 11.0.2-1ubuntu4 > ( libs )
Broken libglapi-mesa-lts-vivid:amd64 Entra en conflicto on libglapi-mesa [ i386 ] < none -> 11.0.2-1ubuntu4 > ( libs )
Broken libwebkitgtk-1.0-0:amd64 Depende on libegl1-mesa [ amd64 ] < none -> 11.0.2-1ubuntu4 > ( libs ) (>= 7.8.1)
Broken libllvm3.6v5:amd64 Entra en conflicto on libllvm3.6 [ amd64 ] < 1:3.6-2ubuntu1~trusty1 > ( libs )
Broken libllvm3.6v5:i386 Entra en conflicto on libllvm3.6 [ amd64 ] < 1:3.6-2ubuntu1~trusty1 > ( libs )
Broken libsdl2-2.0-0:amd64 Depende on libwayland-egl1-mesa [ amd64 ] < none -> 11.0.2-1ubuntu4 > ( libs ) (>= 10.0.2)
Broken xserver-xorg-lts-vivid:amd64 Entra en conflicto on libegl1-mesa [ amd64 ] < none -> 11.0.2-1ubuntu4 > ( libs ) (>= 0~)
Broken nepomuk-core-runtime:amd64 Depende on libtag1c2a [ amd64 ] < 1.9.1-2 > ( libs ) (>= 1.5)
Broken libgl1-mesa-dri:i386 Depende on libllvm3.6v5 [ i386 ] < none -> 1:3.6.2-1 > ( libs )
Broken libgl1-mesa-glx:amd64 Depende on libglapi-mesa [ amd64 ] < none -> 11.0.2-1ubuntu4 > ( libs ) (= 11.0.2-1ubuntu4)
Broken libwebkitgtk-3.0-0:amd64 Depende on libjavascriptcoregtk-3.0-0 [ amd64 ] < 2.4.10-0ubuntu0.14.04.1 -> 2.4.10-0ubuntu0.15.10.1 > ( libs ) (= 2.4.10-0ubuntu0.14.04.1)
Broken libwebkitgtk-3.0-0:amd64 Depende on libgl1-mesa-glx [ amd64 ] < none -> 11.0.2-1ubuntu4 > ( libs )
Broken libgl1-mesa-glx:i386 Depende on libglapi-mesa [ i386 ] < none -> 11.0.2-1ubuntu4 > ( libs ) (= 11.0.2-1ubuntu4)
Broken libgl1-mesa-dri-lts-vivid:amd64 Entra en conflicto on libgl1-mesa-dri [ amd64 ] < none -> 11.0.2-1ubuntu4 > ( libs )
Broken libgl1-mesa-dri:amd64 Depende on libllvm3.6v5 [ amd64 ] < none -> 1:3.6.2-1 > ( libs )
Broken libgbm1:amd64 Depende on libgl1-mesa-dri [ amd64 ] < none -> 11.0.2-1ubuntu4 > ( libs )
Broken libglu1-mesa:i386 Depende on libgl1-mesa-glx [ i386 ] < none -> 11.0.2-1ubuntu4 > ( libs )
Broken libegl1-mesa:amd64 Depende on libgbm1 [ amd64 ] < 10.1.3-0ubuntu0.6 -> 11.0.2-1ubuntu4 > ( libs ) (>= 8.1~0)
Broken xorg:amd64 Depende on xserver-xorg [ amd64 ] < none -> 1:7.7+7ubuntu4 > ( x11 ) (>= 1:7.7+1ubuntu8.1)
Broken libglapi-mesa-lts-vivid:amd64 Entra en conflicto on libglapi-mesa [ amd64 ] < none -> 11.0.2-1ubuntu4 > ( libs )
Broken libgles1-mesa-lts-vivid:amd64 Depende on libglapi-mesa-lts-vivid [ amd64 ] < 10.5.9-2ubuntu1~trusty2 > ( libs ) (= 10.5.9-2ubuntu1~trusty2)
Broken libgbm1-lts-vivid:amd64 Depende on libgl1-mesa-dri-lts-vivid [ amd64 ] < 10.5.9-2ubuntu1~trusty2 > ( libs ) (= 10.5.9-2ubuntu1~trusty2)
Broken xserver-xorg-core-lts-vivid:amd64 Depende on libgbm1-lts-vivid [ amd64 ] < 10.5.9-2ubuntu1~trusty2 > ( libs ) (>= 8.1~0)
Broken libwayland-egl1-mesa:amd64 Depende on libegl1-mesa [ amd64 ] < none -> 11.0.2-1ubuntu4 > ( libs ) (= 11.0.2-1ubuntu4)
Broken qtwayland5:amd64 Depende on libwayland-egl1-mesa [ amd64 ] < none -> 11.0.2-1ubuntu4 > ( libs ) (>= 10.0.2)
Broken qtwayland5:amd64 Depende on libwayland-egl1 [ amd64 ] < none > ( none )
Broken vlc:amd64 Depende on libgles1-mesa [ amd64 ] < none -> 11.0.2-1ubuntu4 > ( libs ) (>= 7.8.1)
Broken libxatracker2-lts-vivid:amd64 Depende on libllvm3.6 [ amd64 ] < 1:3.6-2ubuntu1~trusty1 > ( libs )
Broken vlc-plugin-pulse:amd64 Depende on vlc [ amd64 ] < 2.1.6-0ubuntu14.04.2 -> 2.2.1-3 > ( universe/graphics ) (>= 2.2.1-3)
Broken libglapi-mesa-lts-vivid:i386 Entra en conflicto on libglapi-mesa [ amd64 ] < none -> 11.0.2-1ubuntu4 > ( libs )
Broken libgstreamer-plugins-bad1.0-0:amd64 Depende on libwayland-egl1-mesa [ amd64 ] < none -> 11.0.2-1ubuntu4 > ( libs ) (>= 10.0.2)
Broken libgstreamer-plugins-bad1.0-0:amd64 Depende on libwayland-egl1 [ amd64 ] < none > ( none )
Broken libgtk-3-0:amd64 Depende on libwayland-egl1-mesa [ amd64 ] < none -> 11.0.2-1ubuntu4 > ( libs ) (>= 10.0.2)
Broken libgtk-3-0:amd64 Depende on libwayland-egl1 [ amd64 ] < none > ( none )
Broken libegl1-mesa-lts-vivid:amd64 Depende on libgbm1-lts-vivid [ amd64 ] < 10.5.9-2ubuntu1~trusty2 > ( libs ) (>= 7.11~1)
Broken libcogl20:amd64 Depende on libegl1-mesa [ amd64 ] < none -> 11.0.2-1ubuntu4 > ( libs ) (>= 7.8.1)
Broken libcogl20:amd64 Depende on libegl1-x11 [ amd64 ] < none > ( none )
Broken libwayland-egl1-mesa-lts-vivid:amd64 Depende on libegl1-mesa-lts-vivid [ amd64 ] < 10.5.9-2ubuntu1~trusty2 > ( libs ) (= 10.5.9-2ubuntu1~trusty2)
Broken xserver-xorg-input-evdev-lts-vivid:amd64 Depende on xserver-xorg-core-lts-vivid [ amd64 ] < 2:1.17.1-0ubuntu3.1~trusty1 > ( x11 ) (>= 2:1.16.99.901)
Broken libclutter-gst-2.0-0:amd64 Depende on libcogl20 [ amd64 ] < none -> 1.20.0-2 > ( libs ) (>= 1.17.4)
Broken xserver-xorg-video-neomagic-lts-vivid:amd64 Depende on xserver-xorg-core-lts-vivid [ amd64 ] < 2:1.17.1-0ubuntu3.1~trusty1 > ( x11 ) (>= 2:1.16.99.901)
Broken xserver-xorg-video-sisusb-lts-vivid:amd64 Depende on xserver-xorg-core-lts-vivid [ amd64 ] < 2:1.17.1-0ubuntu3.1~trusty1 > ( x11 ) (>= 2:1.16.99.901)
Broken xserver-xorg-input-synaptics-lts-vivid:amd64 Depende on xserver-xorg-core-lts-vivid [ amd64 ] < 2:1.17.1-0ubuntu3.1~trusty1 > ( x11 ) (>= 2:1.16.99.901)
Broken xserver-xorg-video-nouveau-lts-vivid:amd64 Depende on xserver-xorg-core-lts-vivid [ amd64 ] < 2:1.17.1-0ubuntu3.1~trusty1 > ( x11 ) (>= 2:1.16.99.901)
Broken xserver-xorg-video-all-lts-vivid:amd64 Depende on xserver-xorg-video-neomagic-lts-vivid [ amd64 ] < 1:1.2.8-1ubuntu1~trusty1 > ( x11 )
Broken xserver-xorg-input-vmmouse-lts-vivid:amd64 Depende on xserver-xorg-core-lts-vivid [ amd64 ] < 2:1.17.1-0ubuntu3.1~trusty1 > ( x11 ) (>= 2:1.16.99.901)
Broken xserver-xorg-input-wacom-lts-vivid:amd64 Depende on xserver-xorg-core-lts-vivid [ amd64 ] < 2:1.17.1-0ubuntu3.1~trusty1 > ( x11 ) (>= 2:1.16.99.901)
Broken xserver-xorg-video-tdfx-lts-vivid:amd64 Depende on xserver-xorg-core-lts-vivid [ amd64 ] < 2:1.17.1-0ubuntu3.1~trusty1 > ( x11 ) (>= 2:1.16.99.901)
Broken xserver-xorg-video-siliconmotion-lts-vivid:amd64 Depende on xserver-xorg-core-lts-vivid [ amd64 ] < 2:1.17.1-0ubuntu3.1~trusty1 > ( x11 ) (>= 2:1.16.99.901)
Broken xserver-xorg-video-savage-lts-vivid:amd64 Depende on xserver-xorg-core-lts-vivid [ amd64 ] < 2:1.17.1-0ubuntu3.1~trusty1 > ( x11 ) (>= 2:1.16.99.901)
Broken xserver-xorg-input-all-lts-vivid:amd64 Depende on xserver-xorg-input-evdev-lts-vivid [ amd64 ] < 1:2.9.0-1ubuntu2~trusty1 > ( x11 )
Broken xserver-xorg-video-vmware-lts-vivid:amd64 Depende on libxatracker2-lts-vivid [ amd64 ] < 10.5.9-2ubuntu1~trusty2 > ( libs )
Broken xserver-xorg-video-ati-lts-vivid:amd64 Depende on xserver-xorg-core-lts-vivid [ amd64 ] < 2:1.17.1-0ubuntu3.1~trusty1 > ( x11 ) (>= 2:1.16.99.901)
Broken libgles2-mesa-lts-vivid:amd64 Depende on libglapi-mesa-lts-vivid [ amd64 ] < 10.5.9-2ubuntu1~trusty2 > ( libs ) (= 10.5.9-2ubuntu1~trusty2)
Broken xserver-xorg-video-intel-lts-vivid:amd64 Depende on xserver-xorg-core-lts-vivid [ amd64 ] < 2:1.17.1-0ubuntu3.1~trusty1 > ( x11 ) (>= 2:1.16.99.901)
Broken libcogl-path20:amd64 Depende on libcogl20 [ amd64 ] < none -> 1.20.0-2 > ( libs ) (>= 1.18.0)
Broken xserver-xorg-video-vesa-lts-vivid:amd64 Depende on xserver-xorg-core-lts-vivid [ amd64 ] < 2:1.17.1-0ubuntu3.1~trusty1 > ( x11 ) (>= 2:1.16.99.901)
Broken xserver-xorg-video-trident-lts-vivid:amd64 Depende on xserver-xorg-core-lts-vivid [ amd64 ] < 2:1.17.1-0ubuntu3.1~trusty1 > ( x11 ) (>= 2:1.16.99.901)
Broken xserver-xorg-video-mga-lts-vivid:amd64 Depende on xserver-xorg-core-lts-vivid [ amd64 ] < 2:1.17.1-0ubuntu3.1~trusty1 > ( x11 ) (>= 2:1.16.99.901)
Broken xserver-xorg:amd64 Depende on xserver-xorg-input-evdev [ amd64 ] < none -> 1:2.9.2-1ubuntu1 > ( x11 )
Broken xserver-xorg-video-openchrome-lts-vivid:amd64 Depende on xserver-xorg-core-lts-vivid [ amd64 ] < 2:1.17.1-0ubuntu3.1~trusty1 > ( x11 ) (>= 2:1.16.99.901)
Broken xserver-xorg-video-cirrus-lts-vivid:amd64 Depende on xserver-xorg-core-lts-vivid [ amd64 ] < 2:1.17.1-0ubuntu3.1~trusty1 > ( x11 ) (>= 2:1.16.99.901)
Broken xserver-xorg-video-fbdev-lts-vivid:amd64 Depende on xserver-xorg-core-lts-vivid [ amd64 ] < 2:1.17.1-0ubuntu3.1~trusty1 > ( x11 ) (>= 2:1.16.99.901)
Broken libglapi-mesa-lts-vivid:amd64 Entra en conflicto on libglapi-mesa [ amd64 ] < none -> 11.0.2-1ubuntu4 > ( libs )
Broken libglapi-mesa-lts-vivid:amd64 Entra en conflicto on libglapi-mesa [ i386 ] < none -> 11.0.2-1ubuntu4 > ( libs )
Broken xserver-xorg-input-mouse-lts-vivid:amd64 Depende on xserver-xorg-core-lts-vivid [ amd64 ] < 2:1.17.1-0ubuntu3.1~trusty1 > ( x11 ) (>= 2:1.16.99.901)
Broken xserver-xorg-video-radeon-lts-vivid:amd64 Depende on xserver-xorg-core-lts-vivid [ amd64 ] < 2:1.17.1-0ubuntu3.1~trusty1 > ( x11 ) (>= 2:1.16.99.901)
Broken xserver-xorg-video-r128-lts-vivid:amd64 Depende on xserver-xorg-core-lts-vivid [ amd64 ] < 2:1.17.1-0ubuntu3.1~trusty1 > ( x11 ) (>= 2:1.16.99.901)
Broken xserver-xorg-video-mach64-lts-vivid:amd64 Depende on xserver-xorg-core-lts-vivid [ amd64 ] < 2:1.17.1-0ubuntu3.1~trusty1 > ( x11 ) (>= 2:1.16.99.901)
Broken libchamplain-0.12-0:amd64 Depende on libcogl-path20 [ amd64 ] < none -> 1.20.0-2 > ( libs ) (>= 1.17.4)
Broken gstreamer1.0-plugins-bad-faad:amd64 Depende on libgstreamer-plugins-bad1.0-0 [ amd64 ] < 1.2.4-1~ubuntu1 -> 1.6.3-1ubuntu1 > ( universe/libs ) (= 1.6.3-1ubuntu1)
Broken libcogl-pango20:amd64 Depende on libcogl20 [ amd64 ] < none -> 1.20.0-2 > ( libs ) (>= 1.17.4)
Broken libgles1-mesa:amd64 Depende on libglapi-mesa [ amd64 ] < none -> 11.0.2-1ubuntu4 > ( libs ) (= 11.0.2-1ubuntu4)
Broken gstreamer1.0-plugins-bad-videoparsers:amd64 Depende on libgstreamer-plugins-bad1.0-0 [ amd64 ] < 1.2.4-1~ubuntu1 -> 1.6.3-1ubuntu1 > ( universe/libs ) (= 1.6.3-1ubuntu1)
Broken libclutter-gst-3.0-0:amd64 Depende on libcogl20 [ amd64 ] < none -> 1.20.0-2 > ( libs ) (>= 1.17.4)
Broken libgl1-mesa-glx:amd64 Depende on libglapi-mesa [ amd64 ] < none -> 11.0.2-1ubuntu4 > ( libs ) (= 11.0.2-1ubuntu4)
Broken libwebkitgtk-3.0-0:amd64 Depende on libgl1-mesa-glx [ amd64 ] < none -> 11.0.2-1ubuntu4 > ( libs )
Broken libcheese-gtk23:amd64 Depende on libcogl20 [ amd64 ] < none -> 1.20.0-2 > ( libs ) (>= 1.17.4)
Broken empathy:amd64 Depende on libcheese-gtk23 [ amd64 ] < 3.10.2-0ubuntu2 -> 3.16.1-1ubuntu2 > ( libs ) (>= 3.4.0)
Broken mcp-account-manager-uoa:amd64 Depende on empathy [ amd64 ] < 3.8.6-0ubuntu9.2 -> 3.12.10-0ubuntu2 > ( gnome ) (= 3.12.10-0ubuntu2)
Broken libcheese7:amd64 Depende on libclutter-gst-2.0-0 [ amd64 ] < 2.0.8-1build1 -> 2.0.16-1 > ( libs ) (>= 0.10.0)
Broken libgl1-mesa-glx:i386 Depende on libglapi-mesa [ i386 ] < none -> 11.0.2-1ubuntu4 > ( libs ) (= 11.0.2-1ubuntu4)
Broken account-plugin-salut:amd64 Depende on empathy [ amd64 ] < 3.8.6-0ubuntu9.2 -> 3.12.10-0ubuntu2 > ( gnome ) (= 3.12.10-0ubuntu2)
Broken account-plugin-aim:amd64 Depende on empathy [ amd64 ] < 3.8.6-0ubuntu9.2 -> 3.12.10-0ubuntu2 > ( gnome ) (= 3.12.10-0ubuntu2)
Broken libclutter-1.0-0:amd64 Depende on libcogl-pango20 [ amd64 ] < none -> 1.20.0-2 > ( libs ) (>= 1.17.4)
Broken libtotem0:amd64 Depende on libclutter-1.0-0 [ amd64 ] < 1.16.4-0ubuntu2 -> 1.22.4-1build1 > ( libs ) (>= 1.17.6)
Broken account-plugin-jabber:amd64 Depende on empathy [ amd64 ] < 3.8.6-0ubuntu9.2 -> 3.12.10-0ubuntu2 > ( gnome ) (= 3.12.10-0ubuntu2)
Broken account-plugin-yahoo:amd64 Depende on empathy [ amd64 ] < 3.8.6-0ubuntu9.2 -> 3.12.10-0ubuntu2 > ( gnome ) (= 3.12.10-0ubuntu2)
Broken libclutter-gtk-1.0-0:amd64 Depende on libclutter-1.0-0 [ amd64 ] < 1.16.4-0ubuntu2 -> 1.22.4-1build1 > ( libs ) (>= 1.22.4)
Broken gstreamer1.0-clutter:amd64 Depende on libclutter-1.0-0 [ amd64 ] < 1.16.4-0ubuntu2 -> 1.22.4-1build1 > ( libs ) (>= 1.13.0)
Broken libegl1-mesa-lts-vivid:amd64 Depende on libgbm1-lts-vivid [ amd64 ] < 10.5.9-2ubuntu1~trusty2 > ( libs ) (>= 7.11~1)
Broken libegl1-mesa-lts-vivid:amd64 Depende on libgl1-mesa-dri-lts-vivid [ amd64 ] < 10.5.9-2ubuntu1~trusty2 > ( libs ) (= 10.5.9-2ubuntu1~trusty2)
Broken totem-plugins:amd64 Depende on libtotem0 [ amd64 ] < 3.10.1-1ubuntu4 -> 3.16.4-0ubuntu2 > ( video ) (>= 3.16.4-0ubuntu2)
Broken gnome-contacts:amd64 Depende on libchamplain-0.12-0 [ amd64 ] < none -> 0.12.11-1 > ( libs ) (>= 0.12.4)
Broken totem:amd64 Depende on libtotem0 [ amd64 ] < 3.10.1-1ubuntu4 -> 3.16.4-0ubuntu2 > ( video ) (>= 3.16.4-0ubuntu2)
Broken libclutter-gst-2.0-0:amd64 Depende on libclutter-1.0-0 [ amd64 ] < 1.16.4-0ubuntu2 -> 1.22.4-1build1 > ( libs ) (>= 1.13.0)
Broken libclutter-gst-2.0-0:amd64 Depende on libcogl15 [ amd64 ] < 1.16.2-1 > ( libs ) (>= 1.15.8)
Broken libglu1-mesa:i386 Depende on libgl1-mesa-glx [ i386 ] < none -> 11.0.2-1ubuntu4 > ( libs )
Broken gir1.2-totem-1.0:amd64 Depende on libtotem0 [ amd64 ] < 3.10.1-1ubuntu4 -> 3.16.4-0ubuntu2 > ( video ) (< 3.17)
Broken cheese:amd64 Depende on libcheese-gtk23 [ amd64 ] < 3.10.2-0ubuntu2 -> 3.16.1-1ubuntu2 > ( libs ) (>= 3.4.0)
Broken xserver-xorg:amd64 Depende on xserver-xorg-input-all [ amd64 ] < none -> 1:7.7+7ubuntu4 > ( x11 )
Broken xserver-xorg:amd64 Depende on xorg-driver-input [ amd64 ] < none > ( none )
Broken xserver-xorg:amd64 Depende on xserver-xorg-input-evdev [ amd64 ] < none -> 1:2.9.2-1ubuntu1 > ( x11 )
Broken libglapi-mesa-lts-vivid:amd64 Entra en conflicto on libglapi-mesa [ amd64 ] < none -> 11.0.2-1ubuntu4 > ( libs )
Broken vlc:amd64 Depende on libgles1-mesa [ amd64 ] < none -> 11.0.2-1ubuntu4 > ( libs ) (>= 7.8.1)
Broken unity-control-center:amd64 Depende on libcheese-gtk23 [ amd64 ] < 3.10.2-0ubuntu2 -> 3.16.1-1ubuntu2 > ( libs ) (>= 3.4.0)
Broken libcheese-gtk23:amd64 Depende on libclutter-gtk-1.0-0 [ amd64 ] < 1.4.4-3ubuntu2.2 -> 1.6.2-1 > ( libs ) (>= 0.91.8)
Broken libcheese-gtk23:amd64 Depende on cheese-common [ amd64 ] < 3.10.2-0ubuntu2 -> 3.16.1-1ubuntu2 > ( gnome ) (= 3.10.2-0ubuntu2)
Broken libcheese7:amd64 Depende on cheese-common [ amd64 ] < 3.10.2-0ubuntu2 -> 3.16.1-1ubuntu2 > ( gnome ) (= 3.16.1-1ubuntu2)
Broken libgl1-mesa-dri-lts-vivid:amd64 Depende on libllvm3.6 [ amd64 ] < 1:3.6-2ubuntu1~trusty1 > ( libs )
Broken libgl1-mesa-dri-lts-vivid:amd64 Entra en conflicto on libgl1-mesa-dri [ amd64 ] < none -> 11.0.2-1ubuntu4 > ( libs )
Broken libgl1-mesa-dri-lts-vivid:amd64 Entra en conflicto on libgl1-mesa-dri [ i386 ] < none -> 11.0.2-1ubuntu4 > ( libs )
Broken libclutter-1.0-0:amd64 Depende on libcogl-pango15 [ amd64 ] < 1.16.2-1 > ( libs ) (>= 1.15.8)
Broken libgbm1:amd64 Depende on libgl1-mesa-dri [ amd64 ] < none -> 11.0.2-1ubuntu4 > ( libs ) (= 11.0.2-1ubuntu4)
Broken xorg:amd64 Depende on xserver-xorg [ amd64 ] < none -> 1:7.7+7ubuntu4 > ( x11 ) (>= 1:7.7+1ubuntu8.1)
Broken libgles2-mesa-lts-vivid:amd64 Depende on libglapi-mesa-lts-vivid [ amd64 ] < 10.5.9-2ubuntu1~trusty2 > ( libs ) (= 10.5.9-2ubuntu1~trusty2)
Broken libllvm3.6v5:amd64 Entra en conflicto on libllvm3.6 [ amd64 ] < 1:3.6-2ubuntu1~trusty1 > ( libs )
Broken libllvm3.6v5:i386 Entra en conflicto on libllvm3.6 [ amd64 ] < 1:3.6-2ubuntu1~trusty1 > ( libs )
Broken libgbm1:i386 Depende on libgl1-mesa-dri [ i386 ] < none -> 11.0.2-1ubuntu4 > ( libs ) (= 11.0.2-1ubuntu4)
Broken vlc:amd64 Depende on vlc-nox [ amd64 ] < 2.1.6-0ubuntu14.04.2 -> 2.2.1-3 > ( universe/net ) (= 2.1.6-0ubuntu14.04.2)
Broken xserver-xorg-core:amd64 Depende on libgbm1 [ amd64 ] < 10.1.3-0ubuntu0.6 -> 11.0.2-1ubuntu4 > ( libs ) (>= 8.1~0)
Broken xserver-xorg-input-mouse:amd64 Depende on xorg-input-abi-21 [ amd64 ] < none > ( none )
Broken xserver-xorg-video-vesa:amd64 Depende on xorg-video-abi-19 [ amd64 ] < none > ( none )
Broken xserver-xorg-video-cirrus:amd64 Depende on xorg-video-abi-19 [ amd64 ] < none > ( none )
Broken xserver-xorg-video-all:amd64 Depende on xserver-xorg-video-cirrus [ amd64 ] < none -> 1:1.5.3-1ubuntu1 > ( x11 )
Broken xserver-xorg-video-intel:amd64 Depende on xorg-video-abi-19 [ amd64 ] < none > ( none )
Broken xserver-xorg-video-ati:amd64 Depende on xorg-video-abi-19 [ amd64 ] < none > ( none )
Broken xserver-xorg-video-mach64:amd64 Depende on xorg-video-abi-19 [ amd64 ] < none > ( none )
Broken xserver-xorg-video-tdfx:amd64 Depende on xorg-video-abi-19 [ amd64 ] < none > ( none )
Broken xserver-xorg-video-fbdev:amd64 Depende on xorg-video-abi-19 [ amd64 ] < none > ( none )
Broken xserver-xorg-video-trident:amd64 Depende on xorg-video-abi-19 [ amd64 ] < none > ( none )
Broken xserver-xorg-video-openchrome:amd64 Depende on xorg-video-abi-19 [ amd64 ] < none > ( none )
Broken xserver-xorg-input-vmmouse:amd64 Depende on xorg-input-abi-21 [ amd64 ] < none > ( none )
Broken xserver-xorg-video-radeon:amd64 Depende on xorg-video-abi-19 [ amd64 ] < none > ( none )
Broken xserver-xorg-video-r128:amd64 Depende on xorg-video-abi-19 [ amd64 ] < none > ( none )
Broken xserver-xorg-video-mga:amd64 Depende on xorg-video-abi-19 [ amd64 ] < none > ( none )
Broken xserver-xorg-video-nouveau:amd64 Depende on xorg-video-abi-19 [ amd64 ] < none > ( none )
Broken libcogl15:amd64 Depende on libgbm1 [ amd64 ] < 10.1.3-0ubuntu0.6 -> 11.0.2-1ubuntu4 > ( libs ) (>= 8.1~0)
Broken unity-control-center:amd64 Depende on libcheese7 [ amd64 ] < 3.10.2-0ubuntu2 -> 3.16.1-1ubuntu2 > ( libs ) (>= 3.0.1)
Broken libqt5gui5:amd64 Depende on libgbm1 [ amd64 ] < 10.1.3-0ubuntu0.6 -> 11.0.2-1ubuntu4 > ( libs ) (>= 8.1~0)
Broken libqt5quick5:amd64 Depende on libqt5gui5 [ amd64 ] < 5.2.1+dfsg-1ubuntu14.3 -> 5.4.2+dfsg-2ubuntu9 > ( libs ) (>= 5.2.0)
Broken libcheese-gtk23:amd64 Depende on libcheese7 [ amd64 ] < 3.10.2-0ubuntu2 -> 3.16.1-1ubuntu2 > ( libs ) (>= 3.4.0)
Broken qml-module-qtquick2:amd64 Depende on libqt5quick5 [ amd64 ] < 5.2.1-3ubuntu15.1 -> 5.4.2-1ubuntu6 > ( libs ) (>= 5.4.1)
Broken qml-module-qtquick2:amd64 Depende on libqt5quick5-gles [ amd64 ] < none -> 5.4.2-1ubuntu7 > ( universe/libs ) (>= 5.4.1)
Broken indicator-bluetooth:amd64 Depende on unity-control-center [ amd64 ] < 14.04.3+14.04.20150916-0ubuntu1 -> 15.04.0+15.10.20150923-0ubuntu1 > ( gnome )
Broken indicator-bluetooth:amd64 Depende on gnome-control-center [ amd64 ] < none -> 1:3.16.3-0ubuntu1 > ( universe/gnome )
Broken libqt5widgets5:amd64 Depende on libqt5gui5 [ amd64 ] < 5.2.1+dfsg-1ubuntu14.3 -> 5.4.2+dfsg-2ubuntu9 > ( libs ) (>= 5.4.1)
Broken libqt5widgets5:amd64 Depende on libqt5gui5-gles [ amd64 ] < none -> 5.4.2+dfsg-2ubuntu9 > ( universe/libs ) (>= 5.4.1)
Broken qtdeclarative5-qtquick2-plugin:amd64 Depende on qml-module-qtquick2 [ amd64 ] < none -> 5.4.2-1ubuntu6 > ( libs )
Broken qml-module-qtquick-window2:amd64 Depende on libqt5quick5 [ amd64 ] < 5.2.1-3ubuntu15.1 -> 5.4.2-1ubuntu6 > ( libs ) (>= 5.0.2)
Broken qml-module-qtquick-window2:amd64 Depende on libqt5quick5-gles [ amd64 ] < none -> 5.4.2-1ubuntu7 > ( universe/libs ) (>= 5.0.2)
Broken libgl1-mesa-glx:i386 Depende on libgl1-mesa-dri [ i386 ] < none -> 11.0.2-1ubuntu4 > ( libs ) (>= 7.2)
Broken libgl1-mesa-dri-lts-vivid:amd64 Entra en conflicto on libgl1-mesa-dri [ amd64 ] < none -> 11.0.2-1ubuntu4 > ( libs )
Broken unity-control-center-signon:amd64 Depende on unity-control-center [ amd64 ] < 14.04.3+14.04.20150916-0ubuntu1 -> 15.04.0+15.10.20150923-0ubuntu1 > ( gnome )
Broken libqt5svg5:amd64 Depende on libqt5widgets5 [ amd64 ] < 5.2.1+dfsg-1ubuntu14.3 -> 5.4.2+dfsg-2ubuntu9 > ( libs ) (>= 5.3.0)
Broken signon-ui-x11:amd64 Depende on libqt5quick5 [ amd64 ] < 5.2.1-3ubuntu15.1 -> 5.4.2-1ubuntu6 > ( libs ) (>= 5.0.2)
Broken signon-ui-x11:amd64 Depende on libqt5quick5-gles [ amd64 ] < none -> 5.4.2-1ubuntu7 > ( universe/libs ) (>= 5.0.2)
Broken signon-ui-x11:amd64 Depende on libqt5widgets5 [ amd64 ] < 5.2.1+dfsg-1ubuntu14.3 -> 5.4.2+dfsg-2ubuntu9 > ( libs ) (>= 5.2.0)
Broken qtdeclarative5-ubuntu-ui-toolkit-plugin:amd64 Depende on libqt5svg5 [ amd64 ] < 5.2.1-1 -> 5.4.2-2build1 > ( libs )
Broken libclutter-gtk-1.0-0:amd64 Depende on libcogl15 [ amd64 ] < 1.16.2-1 > ( libs ) (>= 1.15.8)
Broken qml-module-qtgraphicaleffects:amd64 Depende on qml-module-qtquick2 [ amd64 ] < none -> 5.4.2-1ubuntu6 > ( libs )
Broken qml-module-qtquick-layouts:amd64 Depende on libqt5quick5 [ amd64 ] < 5.2.1-3ubuntu15.1 -> 5.4.2-1ubuntu6 > ( libs ) (>= 5.2.0)
Broken qml-module-qtquick-layouts:amd64 Depende on libqt5quick5-gles [ amd64 ] < none -> 5.4.2-1ubuntu7 > ( universe/libs ) (>= 5.2.0)
Broken gnome-control-center:amd64 Depende on libclutter-gtk-1.0-0 [ amd64 ] < 1.4.4-3ubuntu2.2 -> 1.6.2-1 > ( libs ) (>= 0.91.8)
Broken libegl1-mesa-lts-vivid:amd64 Depende on libgl1-mesa-dri-lts-vivid [ amd64 ] < 10.5.9-2ubuntu1~trusty2 > ( libs ) (= 10.5.9-2ubuntu1~trusty2)
Broken signon-ui:amd64 Depende on signon-ui-x11 [ amd64 ] < none -> 0.17+15.10.20150810-0ubuntu1 > ( gnome )
Broken libgl1-mesa-dri:amd64 Depende on libllvm3.6v5 [ amd64 ] < none -> 1:3.6.2-1 > ( libs )
Broken qtdeclarative5-window-plugin:amd64 Depende on qml-module-qtquick-window2 [ amd64 ] < none -> 5.4.2-1ubuntu6 > ( libs )
Broken libqt5qml-graphicaleffects:amd64 Depende on qml-module-qtgraphicaleffects [ amd64 ] < none -> 5.4.2-1ubuntu2 > ( libs )
Broken webapp-container:amd64 Depende on qml-module-qtquick2 [ amd64 ] < none -> 5.4.2-1ubuntu6 > ( libs ) (>= 5.4)
Broken qml-module-ubuntu-onlineaccounts:amd64 Depende on qtdeclarative5-qtquick2-plugin [ amd64 ] < 5.2.1-3ubuntu15.1 -> 5.4.2-1ubuntu6 > ( libs )
Broken libwayland-egl1-mesa-lts-vivid:amd64 Depende on libegl1-mesa-lts-vivid [ amd64 ] < 10.5.9-2ubuntu1~trusty2 > ( libs ) (= 10.5.9-2ubuntu1~trusty2)
Broken unity-webapps-service:amd64 Depende on webapp-container [ amd64 ] < 0.23+14.04.20140428-0ubuntu1 -> 0.23+15.10.20150929-0ubuntu1 > ( x11 )
Broken libunity-webapps0:amd64 Depende on unity-webapps-service [ amd64 ] < 2.5.0~+14.04.20140409-0ubuntu1 -> 2.5.0~+15.10.20151002-0ubuntu1 > ( gnome )
Broken libgbm1:amd64 Depende on libgl1-mesa-dri [ amd64 ] < none -> 11.0.2-1ubuntu4 > ( libs ) (= 11.0.2-1ubuntu4)
Broken libclutter-gst-2.0-0:amd64 Depende on libcogl15 [ amd64 ] < 1.16.2-1 > ( libs ) (>= 1.15.8)
Broken libglu1-mesa:i386 Depende on libgl1-mesa-glx [ i386 ] < none -> 11.0.2-1ubuntu4 > ( libs )
Broken unity-webapps-qml:amd64 Depende on qtdeclarative5-qtquick2-plugin [ amd64 ] < 5.2.1-3ubuntu15.1 -> 5.4.2-1ubuntu6 > ( libs )
Broken libegl1-mesa:amd64 Depende on libgbm1 [ amd64 ] < 10.1.3-0ubuntu0.6 -> 11.0.2-1ubuntu4 > ( libs ) (>= 8.1~0)
Broken xorg:amd64 Depende on libgl1-mesa-dri [ amd64 ] < none -> 11.0.2-1ubuntu4 > ( libs )
Broken webbrowser-app:amd64 Depende on qml-module-qtquick2 [ amd64 ] < none -> 5.4.2-1ubuntu6 > ( libs ) (>= 5.4)
Broken checkbox-gui:amd64 Depende on qtdeclarative5-qtquick2-plugin [ amd64 ] < 5.2.1-3ubuntu15.1 -> 5.4.2-1ubuntu6 > ( libs )
Broken qml-module-qtquick-controls:amd64 Depende on qml-module-qtquick-layouts [ amd64 ] < none -> 5.4.2-1ubuntu2 > ( libdevel ) (= 5.4.2-1ubuntu2)
Broken xserver-xorg:amd64 Depende on xserver-xorg-core [ amd64 ] < none -> 2:1.17.2-1ubuntu9.1 > ( x11 ) (>= 2:1.17)
Broken ubuntu-desktop:amd64 Depende on checkbox-gui [ amd64 ] < 0.17.6-0ubuntu6 -> 0.18-0ubuntu3 > ( utils )
Broken libwebkitgtk-1.0-0:amd64 Depende on libegl1-mesa [ amd64 ] < none -> 11.0.2-1ubuntu4 > ( libs ) (>= 7.8.1)
Broken qtdeclarative5-ubuntu-ui-extras-browser-plugin:amd64 Depende on qml-module-qtquick2 [ amd64 ] < none -> 5.4.2-1ubuntu6 > ( libs ) (>= 5.4)
Broken libsdl2-2.0-0:amd64 Depende on libwayland-egl1-mesa [ amd64 ] < none -> 11.0.2-1ubuntu4 > ( libs ) (>= 10.0.2)
Broken libgbm1-lts-vivid:amd64 Depende on libgl1-mesa-dri-lts-vivid [ amd64 ] < 10.5.9-2ubuntu1~trusty2 > ( libs ) (= 10.5.9-2ubuntu1~trusty2)
Broken xserver-xorg-video-qxl:amd64 Depende on xorg-video-abi-19 [ amd64 ] < none > ( none )
Broken libqt5gui5-gles:amd64 Entra en conflicto on libqt5gui5 [ amd64 ] < 5.2.1+dfsg-1ubuntu14.3 -> 5.4.2+dfsg-2ubuntu9 > ( libs )
Broken qtdeclarative5-ubuntu-web-plugin:amd64 Depende on qml-module-qtquick2 [ amd64 ] < none -> 5.4.2-1ubuntu6 > ( libs ) (>= 5.4)
Broken xul-ext-websites-integration:amd64 Depende on libunity-webapps0 [ amd64 ] < 2.5.0~+14.04.20140409-0ubuntu1 -> 2.5.0~+15.10.20151002-0ubuntu1 > ( libs )
Broken qml-module-org-kde-kquickcontrols:amd64 Depende on qml-module-qtquick-controls [ amd64 ] < none -> 5.4.2-1ubuntu2 > ( libs )
Broken plasma-framework:amd64 Depende on qml-module-org-kde-kquickcontrols [ amd64 ] < none -> 5.15.0-0ubuntu1 > ( universe/libs )
Broken libxatracker2-lts-vivid:amd64 Depende on libllvm3.6 [ amd64 ] < 1:3.6-2ubuntu1~trusty1 > ( libs )
Broken xserver-xorg-video-vmware:amd64 Depende on libxatracker2 [ amd64 ] < none -> 11.0.2-1ubuntu4 > ( libs )
Broken xserver-xorg-video-siliconmotion:amd64 Depende on xorg-video-abi-19 [ amd64 ] < none > ( none )
Broken libcogl-pango15:amd64 Depende on libcogl15 [ amd64 ] < 1.16.2-1 > ( libs ) (>= 1.15.8)
Broken xserver-xorg-video-sisusb:amd64 Depende on xorg-video-abi-19 [ amd64 ] < none > ( none )
Broken xserver-xorg-video-savage:amd64 Depende on xorg-video-abi-19 [ amd64 ] < none > ( none )
Broken xserver-xorg-input-all:amd64 Depende on xserver-xorg-input-vmmouse [ amd64 ] < none -> 1:13.1.0-0ubuntu1 > ( x11 )
Broken xserver-xorg-input-wacom:amd64 Depende on xorg-input-abi-21 [ amd64 ] < none > ( none )
Broken xserver-xorg-video-neomagic:amd64 Depende on xorg-video-abi-19 [ amd64 ] < none > ( none )
Broken xserver-xorg-input-synaptics:amd64 Depende on xorg-input-abi-21 [ amd64 ] < none > ( none )
Broken libkf5iconthemes5:amd64 Depende on libqt5svg5 [ amd64 ] < 5.2.1-1 -> 5.4.2-2build1 > ( libs )
Broken xserver-xorg-input-evdev:amd64 Depende on xorg-input-abi-21 [ amd64 ] < none > ( none )
Broken libkf5xmlgui5:amd64 Depende on libkf5iconthemes5 [ amd64 ] < none -> 5.15.0-0ubuntu1 > ( universe/libs ) (>= 4.96.0)
Broken libkf5iconthemes-bin:amd64 Depende on libkf5iconthemes5 [ amd64 ] < none -> 5.15.0-0ubuntu1 > ( universe/libs ) (>= 4.96.0)
Broken libkf5declarative5:amd64 Depende on libkf5iconthemes5 [ amd64 ] < none -> 5.15.0-0ubuntu1 > ( universe/libs ) (>= 4.96.0)
Broken libkf5textwidgets5:amd64 Depende on libkf5iconthemes5 [ amd64 ] < none -> 5.15.0-0ubuntu1 > ( universe/libs ) (>= 4.96.0)
Broken webaccounts-extension-common:amd64 Depende on unity-control-center-signon [ amd64 ] < 0.1.7~+14.04.20140211.2-0ubuntu4 -> 0.1.7~+14.10.20140814-0ubuntu1 > ( gnome )
Broken webaccounts-extension-common:amd64 Depende on gnome-control-center-signon [ amd64 ] < none > ( none )
Broken libkf5plasma5:amd64 Depende on libkf5declarative5 [ amd64 ] < none -> 5.15.0-0ubuntu1 > ( universe/libs ) (>= 4.96.0)
Broken libkf5plasmaquick5:amd64 Depende on libkf5declarative5 [ amd64 ] < none -> 5.15.0-0ubuntu1 > ( universe/libs ) (>= 5.12.0)
Broken xul-ext-unity:amd64 Depende on libunity-webapps0 [ amd64 ] < 2.5.0~+14.04.20140409-0ubuntu1 -> 2.5.0~+15.10.20151002-0ubuntu1 > ( libs ) (>= 1.8.0+r699)
Broken libcheese-gtk23:amd64 Depende on libclutter-gtk-1.0-0 [ amd64 ] < 1.4.4-3ubuntu2.2 -> 1.6.2-1 > ( libs ) (>= 0.91.8)
Broken indicator-bluetooth:amd64 Depende on unity-control-center [ amd64 ] < 14.04.3+14.04.20150916-0ubuntu1 -> 15.04.0+15.10.20150923-0ubuntu1 > ( gnome )
Broken indicator-bluetooth:amd64 Depende on gnome-control-center [ amd64 ] < none -> 1:3.16.3-0ubuntu1 > ( universe/gnome )
Broken libcheese7:amd64 Depende on libclutter-gst-2.0-0 [ amd64 ] < 2.0.8-1build1 -> 2.0.16-1 > ( libs ) (>= 0.10.0)
Broken gnome-control-center:amd64 Depende on libcheese7 [ amd64 ] < 3.10.2-0ubuntu2 -> 3.16.1-1ubuntu2 > ( libs ) (>= 3.0.1)
Broken qtdeclarative5-accounts-plugin:amd64 Depende on qml-module-ubuntu-onlineaccounts [ amd64 ] < none -> 0.5+15.04.20150415.1-0ubuntu2~gcc5.1 > ( libs )
Broken kpackagelauncherqml:amd64 Depende on libkf5declarative5 [ amd64 ] < none -> 5.15.0-0ubuntu1 > ( universe/libs ) (>= 5.7.0+git20150305.0804+15.04)
Broken kactivities:amd64 Depende on plasma-framework [ amd64 ] < none -> 5.15.0-0ubuntu1 > ( universe/libs )
Broken libwebkitgtk-1.0-0:amd64 Depende on libjavascriptcoregtk-1.0-0 [ amd64 ] < 2.4.10-0ubuntu0.14.04.1 -> 2.4.10-0ubuntu0.15.10.1 > ( libs ) (= 2.4.10-0ubuntu0.14.04.1)
Broken kcalc:amd64 Depende on libkf5xmlgui5 [ amd64 ] < none -> 5.15.0-0ubuntu1 > ( universe/libs ) (>= 4.98.0)
Broken midori:amd64 Depende on libwebkitgtk-1.0-0 [ amd64 ] < 2.4.10-0ubuntu0.14.04.1 -> 2.4.10-0ubuntu0.15.10.1 > ( libs ) (>= 1.3.13)
Broken qml-module-org-kde-kquickcontrolsaddons:amd64 Depende on libkf5declarative5 [ amd64 ] < none -> 5.15.0-0ubuntu1 > ( universe/libs ) (>= 5.15.0-0ubuntu1)
Broken libkf5quickaddons5:amd64 Depende on libkf5declarative5 [ amd64 ] < none -> 5.15.0-0ubuntu1 > ( universe/libs ) (>= 5.12.0)
Broken xul-ext-webaccounts:amd64 Depende on webaccounts-extension-common [ amd64 ] < 0.5-0ubuntu2.14.04.1 > ( web ) (= 0.5-0ubuntu2.14.04.1)
Broken libkf5style5:amd64 Depende on libkf5iconthemes5 [ amd64 ] < none -> 5.15.0-0ubuntu1 > ( universe/libs ) (>= 4.96.0)
Broken libkf5kiowidgets5:amd64 Depende on libkf5iconthemes5 [ amd64 ] < none -> 5.15.0-0ubuntu1 > ( universe/libs ) (>= 4.96.0)
Broken kde-style-breeze:amd64 Depende on libkf5style5 [ amd64 ] < none -> 5.15.0-0ubuntu1 > ( universe/libs ) (>= 4.96.0)
```

I do not know how I have done to have soooo much broken packages :$

Hope you know what to do :)

P.D.: Thanks Bucky Ball for the info!
P.D.2: I have tried sudo apt-get install -f, but nothing happens

---

### Post by Bucky Ball on 2016-05-13
Please use code tags. I have added them to your last post. If you're unsure how, see the green link in my signature at the bottom of this post. Thanks.

That many broken packages is probably the outcome of a screwed upgrade.

---

### Post by enekoalfer on 2016-05-13
Sure. I'm sorry, I forgot that. Thank you.

How can I do to fix that, then?

---

### Post by Bucky Ball on 2016-05-13
Code tags? See the green link in my signature at the bottom of this post titled '[Using [code] tags]("http://ubuntuforums.org/showthread.php?p=12776168#post12776168")'. ;)

---

### Post by enekoalfer on 2016-05-13
No, I have no problem with code tags, I got that. How can I fix that many broken packages was my question ;) thank you anyway :)

---

### Post by Bucky Ball on 2016-05-13
Personally, I wouldn't bother. I'd back up valuable data and do a clean install of 16.04 LTS. Spending time fixing this so you can get to a release with a month and bit's support left just to upgrade to 16.04 LTS, which may break the system and waste more time ... ?

Doing multiple upgrades like this rarely ends well and if you have a broken system to start with, never. We have seen plenty of issues with the 14.04 to 15.10 upgrade path (which is an anomaly to me). 

Was 14.04 LTS working fine before all this? If not, move on. I'd move on anyway, but that's me. Someone else may have a five minute fix for this. Somehow I doubt it but one never knows.

---

### Post by Bucky Ball on 2016-05-13
Personally, I wouldn't bother. I'd back up valuable data and do a clean install of 16.04 LTS. Spending time fixing this so you can get to a release with a month and bit's support left just to upgrade to 16.04 LTS, which may break the system and waste more time ... ?

Doing multiple upgrades like this rarely ends well and if you have a broken system to start with, never. We have seen plenty of issues with the 14.04 to 15.10 upgrade path (an 'innovation' which is an anomaly to me). 

Was 14.04 LTS working fine before all this? If not, move on. I'd move on anyway, but that's me.

Perhaps post the output of /etc/apt/sources.list, just to satisfy curiousity. You may have a heap of duplicates and a mess in there, too, and it won't fix broken packages directly, but who knows? Might throw some light.

---

### Post by enekoalfer on 2016-05-13
Ok, thaks then! I will do that when the moment arrives, a clean install ;)

I have no major problems with 14.04, but just as you, I would like to have it upgraded, so I will back my data up and I will do a clean install of Ubuntu 16.04 LTS. Thank you for everything!!

P.D.: Sorry if at any moment I kicked the english language, I'm not a native english speaker ;)

---

### Post by Bucky Ball on 2016-05-13
English is fine. We can understand you fairly well. :)

Just to add: I only use LTS releases, for a variety of reasons, but I generally install the NEXT unreleased LTS on a separate partition and play around with it, leaving my stable, day-to-day workhorse release as it was, then 'migrate' to the new LTS gradually. 

For instance, I have had 16.04 installed on my desktop for about two and half months alongside 14.04. Every now and then I'd have a fiddle with 16.04, update it, look around, do a little configuration. I have pretty much moved to 16.04 on both laptop and desktop but if things go belly-up, I have 14.04 purring away and stable if I need it. :)

Good luck and thanks for marking as solved.

---

### Post by enekoalfer on 2016-05-13
Nice idea! I will try that :)

Have a nice weekend ;)

---

