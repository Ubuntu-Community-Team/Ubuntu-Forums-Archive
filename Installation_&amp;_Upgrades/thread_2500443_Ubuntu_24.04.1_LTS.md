---
title: "Ubuntu 24.04.1 LTS"
date: 2024-09-02
forum: Installation &amp; Upgrades
---

### Post by entwistles on 2024-09-02
I somewhat ill-advisedly, in retrospect, upgraded from 22.04 LTS to Ubuntu 24.04.1 LTS whilst not having the skillset required to deal with a number of issues. Having resolved a number of what may be considered 'minor' problems I am left with the following final point of pain. How do I get past unmet dependencies? I'm throwing myself at the mercy of others better suited to dealing with such issues and relying on a degree of good fortune in resolving the following.

[INDENT]*The following packages have unmet dependencies.*[/INDENT]
[INDENT]* libgweather-3-15 : Depends: libgeocode-glib0 (>= 0.99.1) but it is not installable*[/INDENT]
[INDENT]*                    Depends: libgweather-common (>= 3.5.0) but it is not installable*[/INDENT]
[INDENT]* libllvm6.0 : Depends: libffi7 (>= 3.3~20180313) but it is not installable*[/INDENT]
[INDENT]* libmagickcore-6.q16-3 : Depends: libtiff5 (>= 4.0.3) but it is not installable*[/INDENT]
[INDENT]* libreadline7 : Depends: libtinfo5 (>= 6) but it is not installable*[/INDENT]
[INDENT]* libusbmuxd4 : Depends: libplist3 (>= 1.11) but it is not installable*[/INDENT]
[INDENT]* linux-headers-5.15.0-119-generic : Depends: linux-headers-5.15.0-119 but it is not installable*[/INDENT]
[INDENT]* python-talloc : Depends: libpython2.7 (>= 2.7) but it is not installable*[/INDENT]
[INDENT]* zoneminder : Depends: libavcodec58 (>= 7:4.4) but it is not installable*[/INDENT]
[INDENT]*              Depends: libavformat58 (>= 7:4.4) but it is not installable*[/INDENT]
[INDENT]*              Depends: libavutil56 (>= 7:4.4) but it is not installable*[/INDENT]
[INDENT]*              Depends: libjwt-gnutls0 (>= 1.9.0) but it is not installable*[/INDENT]
[INDENT]*              Depends: libswresample3 (>= 7:4.4) but it is not installable*[/INDENT]
[INDENT]*              Depends: libswscale5 (>= 7:4.4) but it is not installable*[/INDENT]
[INDENT]*E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).*[/INDENT]

Running the suggested *'apt --fix-broken install' *returns the following response which I am loathe to enact as it would remove Zoneminder which is the sole purpose/function of the system and I am therefore loathe to do.[INDENT]*The following packages will be REMOVED*[/INDENT]
[INDENT]*  libgweather-3-15 libllvm6.0 libmagickcore-6.q16-3 libmagickwand-6.q16-3*[/INDENT]
[INDENT]*  libreadline7 libusbmuxd4 linux-headers-5.15.0-119-generic python-talloc*[/INDENT]
[INDENT]*  zoneminder*[/INDENT]



Regards

---

### Post by jscaparro87 on 2024-10-10
Yeah I'm having the same issues down to the T. I've been searching for days now for an answer with no resolve. The 'apt --fix-broken install' is not working for any of my issues. No matter if I try to do a clean refresh and update the repositories, it still will not work. Any suggestions?
sudo apt --fix-broken install
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libavcodec58 libavfilter7 libavformat58 libavutil56 libcodec2-1.0 libdav1d5
  libevdi1 libmfx1 libpostproc55 libsrt1.4-gnutls libswresample3 libswscale5
  libvpx7 libx264-163 mailcap
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  evdi
The following NEW packages will be installed:
  evdi
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0 B/52.2 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 177845 files and directories currently installed.)
Preparing to unpack .../evdi_1.14.7-109_amd64.deb ...
Unpacking evdi (1.14.7-109) ...
dpkg: error processing archive /var/cache/apt/archives/evdi_1.14.7-109_amd64.deb
 (--unpack):
 trying to overwrite '/usr/lib/libevdi.so.1', which is also in package libevdi1 
1.14.2+dfsg-1build1
Errors were encountered while processing:
 /var/cache/apt/archives/evdi_1.14.7-109_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by ian-weisser on 2024-10-10
@jscaparro87, your output looks completely different from @entwistles had.

@entwistle's problem is a non-Ubuntu package (possibly zoneminder).

Your problem is trying to install two packages that try to provide the same file.
One is already installed. The second can't be installed for that reason.

Looking at the package names (evdi_1.14.7-109 and libevdi1_1.14.2+dfsg-1build1), looks like you tried to install evdi multiple times without cleaning up after earlier attempts. Simply clean up your previous attempts, and the problem is likely to vanish.

If your problem is indeed a non-Ubuntu zoneminder package, then please accept my apologies for error.

---

