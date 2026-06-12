---
title: "Downgrade dpkg"
date: 2012-02-02
forum: Installation &amp; Upgrades
---

### Post by jdgr on 2012-02-02
Hi all,

I'm trying to install the RSS feeder SNACKR. After a lot of troublshooting, and a post to a 2 month old topic I opened, I was pointed to having to downgrade dpkg to 1.15.8.4ubuntu3_amd64 because the newest version of dpkg forces the adherence to version numbering, and this program doesn't abide by that version numbering (I've also emailed the application builders, no response yet).

I've tried doing this with:

```
dpkg --force-downgrade -i /mypath/dpkg_1.15.8.4ubuntu3_amd64.deb
```but it gives me the following error:

> dpkg: warning: downgrading dpkg from 1.16.0.3ubuntu5 to 1.15.8.4ubuntu3.
(Reading database ... 221780 files and directories currently installed.)
Preparing to replace dpkg 1.16.0.3ubuntu5 (using dpkg_1.15.8.4ubuntu3_amd64.deb) ...
dpkg: error: You have more than one architecture instance for some
installed 'Multi-Arch: same' packages, to be able to downgrade dpkg
you will need to have only one instance installed per package.

List of co-installed packages:

gcc-4.6-base
libacl1
libasound2
libasound2-plugins
libasyncns0
libatk1.0-0
libattr1
libaudio2
libavahi-client3
libavahi-common3
libavahi-common-data
libcairo2
libcomerr2
libcups2
libcupsimage2
libdatrie1
libdb5.1
libdbus-1-3
libdrm2
libdrm-intel1
libdrm-nouveau1a
libdrm-radeon1
libexpat1
libffi6
libflac8
libfontconfig1
libfreetype6
libgcc1
libgcrypt11
libgdbm3
libgdk-pixbuf2.0-0
libgl1-mesa-dri
libgl1-mesa-glx
libglapi-mesa
libglib2.0-0
libgnutls26
libgpg-error0
libgssapi-krb5-2
libgtk2.0-0
libice6
libidn11
libjack-jackd2-0
libjasper1
libjpeg62
libjson0
libk5crypto3
libkeyutils1
libkrb5-3
libkrb5support0
liblcms1
libldap-2.4-2
libllvm2.9
libmng1
libnspr4
libnss3-1d
libnss3
libogg0
libpango1.0-0
libpciaccess0
libpcre3
libpixman-1-0
libpng12-0
libpulse0
libqt4-dbus
libqt4-declarative
libqt4-network
libqt4-opengl
libqt4-script
libqt4-sql
libqt4-svg
libqt4-xml
libqt4-xmlpatterns
libqtcore4
libqtgui4
librtmp0
libsamplerate0
libsasl2-2
libsasl2-modules
libselinux1
libsm6
libsndfile1
libspeexdsp1
libsqlite3-0
libssl1.0.0
libstdc++6
libtasn1-3
libthai0
libtiff4
libuuid1
libvorbis0a
libvorbisenc2
libwrap0
libx11-6
libxau6
libxcb1
libxcb-render0
libxcb-shm0
libxcomposite1
libxcursor1
libxdamage1
libxdmcp6
libxext6
libxfixes3
libxft2
libxi6
libxinerama1
libxrandr2
libxrender1
libxss1
libxt6
libxxf86vm1
zlib1g
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
dpkg: error processing dpkg_1.15.8.4ubuntu3_amd64.deb (--install):
 there is no script in the new version of the package - giving up
Errors were encountered while processing:
 dpkg_1.15.8.4ubuntu3_amd64.deb
The only option i have found that I could do this would be to manually remove dpkg and then reinstall the 1.15.8.4 version. But in doing this, it would also have to removed about 100 various programs, a lot of which are necessary for me and for the system; so I don't want to go through that option.

Anyone have any ideas how I can downgrade dpkg?

---

### Post by Silas (son of Silas) on 2012-06-24
I have the same issue. did you ever fix this?

---

