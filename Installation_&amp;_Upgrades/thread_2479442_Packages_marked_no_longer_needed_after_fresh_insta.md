---
title: "Packages marked no longer needed after fresh install"
date: 2022-09-24
forum: Installation &amp; Upgrades
---

### Post by donald187 on 2022-09-24
Hi everybody.  I just did a fresh install of Ubuntu on a new Dell Inspiron 3910.  As soon as I installed some applications I got the message as in this example.

```

sudo apt -s install firejail
[sudo] password for donald: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  chromium-codecs-ffmpeg-extra gstreamer1.0-vaapi i965-va-driver
  intel-media-va-driver libaacs0 libaom3 libass9 libavcodec58 libavformat58
  libavutil56 libbdplus0 libblas3 libbluray2 libbs2b0 libchromaprint1
  libcodec2-1.0 libdav1d5 libflite1 libgme0 libgsm1
  libgstreamer-plugins-bad1.0-0 libigdgmm12 liblilv-0-0 libmessaging-menu0
  libmfx1 libmysofa1 libnorm1 libopenmpt0 libpgm-5.3-0 libpostproc55
  librabbitmq4 librubberband2 libserd-0-0 libshine3 libsnappy1v5 libsord-0-0
  libsratom-0-0 libsrt1.4-gnutls libssh-gcrypt-4 libswresample3 libswscale5
  libudfread0 libva-drm2 libva-wayland2 libva-x11-2 libva2 libvdpau1
  libvidstab1.1 libx265-199 libxvidcore4 libzimg2 libzmq5 libzvbi-common
  libzvbi0 mesa-va-drivers mesa-vdpau-drivers pocketsphinx-en-us
  systemd-hwe-hwdb va-driver-all vdpau-driver-all
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  firejail-profiles
The following NEW packages will be installed:
  firejail firejail-profiles
0 upgraded, 2 newly installed, 0 to remove and 15 not upgraded.
Inst firejail (0.9.66-2 Ubuntu:22.04/jammy [amd64])
Inst firejail-profiles (0.9.66-2 Ubuntu:22.04/jammy [all])
Conf firejail (0.9.66-2 Ubuntu:22.04/jammy [amd64])
Conf firejail-profiles (0.9.66-2 Ubuntu:22.04/jammy [all])

```

Using

```

$ apt show <package>

```

on various packages in that list they seem to relate to music or video files.  So on a hunch I ran

```

$ sudo apt -s install soundconverter
[sudo] password for donald: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  chromium-codecs-ffmpeg-extra gstreamer1.0-vaapi
  libgstreamer-plugins-bad1.0-0 libmessaging-menu0 libva-wayland2
  systemd-hwe-hwdb
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  gstreamer1.0-libav libavfilter7 libgfortran5 liblapack3 libpocketsphinx3
  libquadmath0 libsphinxbase3
The following NEW packages will be installed:
  gstreamer1.0-libav libavfilter7 libgfortran5 liblapack3 libpocketsphinx3
  libquadmath0 libsphinxbase3 soundconverter
0 upgraded, 8 newly installed, 0 to remove and 15 not upgraded.
Inst libquadmath0 (12.1.0-2ubuntu1~22.04 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [amd64])
Inst libgfortran5 (12.1.0-2ubuntu1~22.04 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [amd64])
Inst liblapack3 (3.10.0-2ubuntu1 Ubuntu:22.04/jammy [amd64])
Inst libsphinxbase3 (0.8+5prealpha+1-13build1 Ubuntu:22.04/jammy [amd64])
Inst libpocketsphinx3 (0.8.0+real5prealpha+1-14ubuntu1 Ubuntu:22.04/jammy [amd64])
Inst libavfilter7 (7:4.4.2-0ubuntu0.22.04.1 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [amd64])
Inst gstreamer1.0-libav (1.20.3-0ubuntu1 Ubuntu:22.04/jammy-updates [amd64])
Inst soundconverter (4.0.3-2 Ubuntu:22.04/jammy [all])
Conf libquadmath0 (12.1.0-2ubuntu1~22.04 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [amd64])
Conf libgfortran5 (12.1.0-2ubuntu1~22.04 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [amd64])
Conf liblapack3 (3.10.0-2ubuntu1 Ubuntu:22.04/jammy [amd64])
Conf libsphinxbase3 (0.8+5prealpha+1-13build1 Ubuntu:22.04/jammy [amd64])
Conf libpocketsphinx3 (0.8.0+real5prealpha+1-14ubuntu1 Ubuntu:22.04/jammy [amd64])
Conf libavfilter7 (7:4.4.2-0ubuntu0.22.04.1 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [amd64])
Conf gstreamer1.0-libav (1.20.3-0ubuntu1 Ubuntu:22.04/jammy-updates [amd64])
Conf soundconverter (4.0.3-2 Ubuntu:22.04/jammy [all])

```

and you can see that fewer packages are listed now.  I was wondering if there was some metapackage that failed to install that would have included many of these packages.

I've done a few reinstallations recently (for unrelated reasons).  On one of them I ran

```

sudo apt autoremove

```

even before update manager (I think that's what it's called) wanted to upgrade my packages but still got a list of packages that could be autoremoved.

Doing the following takes it down even further.

```

$ sudo apt -s install soundconverter gstreamer1.0-vaapi
[sudo] password for donald: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
gstreamer1.0-vaapi is already the newest version (1.20.1-1ubuntu1).
gstreamer1.0-vaapi set to manually installed.
The following packages were automatically installed and are no longer required:
  chromium-codecs-ffmpeg-extra libmessaging-menu0 systemd-hwe-hwdb
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  gstreamer1.0-libav libavfilter7 libgfortran5 liblapack3 libpocketsphinx3
  libquadmath0 libsphinxbase3
The following NEW packages will be installed:
  gstreamer1.0-libav libavfilter7 libgfortran5 liblapack3 libpocketsphinx3
  libquadmath0 libsphinxbase3 soundconverter
0 upgraded, 8 newly installed, 0 to remove and 15 not upgraded.
Inst libquadmath0 (12.1.0-2ubuntu1~22.04 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [amd64])
Inst libgfortran5 (12.1.0-2ubuntu1~22.04 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [amd64])
Inst liblapack3 (3.10.0-2ubuntu1 Ubuntu:22.04/jammy [amd64])
Inst libsphinxbase3 (0.8+5prealpha+1-13build1 Ubuntu:22.04/jammy [amd64])
Inst libpocketsphinx3 (0.8.0+real5prealpha+1-14ubuntu1 Ubuntu:22.04/jammy [amd64])
Inst libavfilter7 (7:4.4.2-0ubuntu0.22.04.1 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [amd64])
Inst gstreamer1.0-libav (1.20.3-0ubuntu1 Ubuntu:22.04/jammy-updates [amd64])
Inst soundconverter (4.0.3-2 Ubuntu:22.04/jammy [all])
Conf libquadmath0 (12.1.0-2ubuntu1~22.04 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [amd64])
Conf libgfortran5 (12.1.0-2ubuntu1~22.04 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [amd64])
Conf liblapack3 (3.10.0-2ubuntu1 Ubuntu:22.04/jammy [amd64])
Conf libsphinxbase3 (0.8+5prealpha+1-13build1 Ubuntu:22.04/jammy [amd64])
Conf libpocketsphinx3 (0.8.0+real5prealpha+1-14ubuntu1 Ubuntu:22.04/jammy [amd64])
Conf libavfilter7 (7:4.4.2-0ubuntu0.22.04.1 Ubuntu:22.04/jammy-updates, Ubuntu:22.04/jammy-security [amd64])
Conf gstreamer1.0-libav (1.20.3-0ubuntu1 Ubuntu:22.04/jammy-updates [amd64])
Conf soundconverter (4.0.3-2 Ubuntu:22.04/jammy [all])

```

One of the packages, systemd-hwe-hwdb, has to do with udev rules, hardware enablement, and systemd.

```

$ apt show systemd-hwe-hwdb
Package: systemd-hwe-hwdb
Version: 249.11.1
Priority: optional
Section: admin
Source: systemd-hwe
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 15.4 kB
Depends: udev
Download-Size: 2,322 B
APT-Manual-Installed: no
APT-Sources: http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
Description: udev rules for hardware enablement (HWE)
 systemd-hwe-hwdb contains hwdb rules for HWE on Ubuntu,
 which are not yet present in systemd.

```

I found a bug that says 

> 
The package systemd-hwe will generally be useful for a large part of
  our user base because it is related to HWE.


[https://bugs.launchpad.net/ubuntu/+source/systemd-hwe/+bug/1983996](https://bugs.launchpad.net/ubuntu/+source/systemd-hwe/+bug/1983996)

So maybe I should at least keep this package?

gstreamer1.0-vaapi includes libgstreamer-plugins-bad1.0-0 as a dependency and has to do with hardware video accleration.  I haven;t installed any non-stock music or video apps.  I found a bug that says in post # 36 that Totem has disabled hardware acceleration so maybe I don't need this one?

> 
     Sounds like we have a semi-permanent workaround now:
 gstreamer-vaapi (1.16.0-3ubuntu2) eoan; urgency=medium
   * debian/patches/git_no_amd.patch:
    - backport an upstream change to disable vaapi with the amd drivers,
      the current experience is buggy and it's better to just not enable it
      see the discussions on this mailing list and the referenced bug
      [https://mail.gnome.org/archives/distributor-list/2019-September](https://mail.gnome.org/archives/distributor-list/2019-September)
  -- Sebastien Bacher <email address hidden>  Mon, 09 Sep 2019 17:09:08 +0200


[https://bugs.launchpad.net/ubuntu/+source/gstreamer-vaapi/+bug/1767312](https://bugs.launchpad.net/ubuntu/+source/gstreamer-vaapi/+bug/1767312)

Thanks for looking at this. :)

EDIT:  I guess I should say that chromium-codecs-ffmpeg-extra and libmessaging-menu0 seem to be unnecessary so I'm wondering if I could autoremove all of these packages except possibly systemd-hwe-hwdb or if there's some metapackage that's missing that I could install to keep these.

---

### Post by ian-weisser on 2022-09-24
If you autoremove those packages and you don't like the result, you can simply install the packages again.

---

### Post by MAFoElffen on 2022-09-24
On a fresh install, a lot of packages are installed as transient packages... Meaning they were installed are installed temporarily for something else to be installed, but once it that or those other packages are installed and configured, those temporary packages are no longer needed.

Some packages were needed during that point install, but once updates that are downloaded during the installation are done, are no longer needed.

I don't understand that completely, why some packages are considered temporary place holders, but I have done Ubuntu for over 13 years and know it happens. If you install something else, it's going to look at it's dependency list to see what is pertinent.

I am pretty consistent in running autoremove with no problems from doing that.

---

### Post by donald187 on 2022-09-24
Ok, thanks!  I had also done a fresh install with 22.04 and there were no packages like that but I guess something changed.  I have installed Ubuntu in the past and have had several packages "no longer needed" but with there being dozens of packages this time seemingly centered around audio/video I thought I'd ask.  In the past I've always done the autoremove with no negative consequences that I was aware of.

Thanks again!

---

