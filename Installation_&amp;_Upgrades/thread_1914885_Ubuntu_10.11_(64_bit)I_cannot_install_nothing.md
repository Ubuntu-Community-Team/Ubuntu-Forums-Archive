---
title: "Ubuntu 10.11 (64 bit):I cannot install nothing"
date: 2012-01-25
forum: Installation &amp; Upgrades
---

### Post by tempiese on 2012-01-25
Hi,

I hava installed Ubuntu 11.10 (64 bit) in my Sony Vaio but I cannot install pretty nothing! The message that i get is :

gcc-4.6-base:i386 ia32-libs ia32-libs-multiarch:i386 lib32asound2 lib32ffi6 lib32gcc1 lib32ncurses5 lib32ncursesw5 lib32stdc++6 lib32tinfo5 lib32z1 libacl1:i386 libattr1:i386 libaudio2:i386 libavahi-client3:i386 libavahi-common-data:i386 libavahi-common3:i386 libc6-i386 libc6:i386 libcomerr2:i386 libcurl3:i386 libdb5.1:i386 libdbus-1-3:i386 libdrm-intel1:i386 libdrm-nouveau1a:i386 libdrm-radeon1:i386 libdrm2:i386 libexpat1:i386 libffi6:i386 libfontconfig1:i386 libgcc1:i386 libgcrypt11:i386 libgdbm3:i386 libgl1-mesa-dri:i386 libgl1-mesa-glx:i386 libglapi-mesa:i386 libglib2.0-0:i386 libgnutls26:i386 libgpg-error0:i386 libice6:i386 libidn11:i386 libjpeg62:i386 libkeyutils1:i386 liblcms1:i386 libllvm2.9:i386 libmng1:i386 libnspr4:i386 libnss3:i386 libpciaccess0:i386 libpcre3:i386 libpng12-0:i386 libqt4-dbus:i386 libqt4-declarative:i386 libqt4-designer:i386 libqt4-network:i386 libqt4-opengl:i386 libqt4-qt3support:i386 libqt4-script:i386 libqt4-scripttools:i386 libqt4-sql:i386 libqt4-svg:i386 libqt4-test:i386 libqt4-xml:i386 libqt4-xmlpatterns:i386 libqtcore4:i386 libqtgui4:i386 librtmp0:i386 libsasl2-2:i386 libsasl2-modules:i386 libselinux1:i386 libsm6:i386 libsqlite3-0:i386 libssl1.0.0:i386 libstdc++6:i386 libtasn1-3:i386 libtiff4:i386 libuuid1:i386 libx11-6:i386 libxau6:i386 libxcb1:i386 libxdamage1:i386 libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxi6:i386 libxrender1:i386 libxss1:i386 libxt6:i386 libxxf86vm1:i386 zlib1g:i386

What can I do?

Thank u very much!

---

### Post by stefangr1 on 2012-01-25
What steps did you take before those messages appeared?

---

### Post by tempiese on 2012-01-25
those message appear all the times i tried to download an application :for example skype or flash plugin. I tried download with the ubuntu download interface or manually but the result is the same. i'm thinking that is bettere if i uninstall ubuntu 10.11 and i install an old version.

---

### Post by elizeb on 2012-01-25
I am not sure whether this is the right place to ask help, please forgive me if I am in the wrong forum.
I am trying to dual boot my DELL inspiron laptop with Ubuntu and Windows 7. May I know whether that is possible?, if possible how can I do that.
____________________________________________________
[free joomla 1.5, 1.6, 1.7 templates]("http://www.websiteoutfit.com/downloads/joomla") | [free wordpress themes]("http://www.websiteoutfit.com/downloads/wordpress")

---

### Post by stefangr1 on 2012-01-25
> **elizeb said:**
> I am not sure whether this is the right place to ask help, please forgive me if I am in the wrong forum.
I am trying to dual boot my DELL inspiron laptop with Ubuntu and Windows 7. May I know whether that is possible?, if possible how can I do that.

It's possible. Have a look [at this Howto]("https://help.ubuntu.com/community/WindowsDualBoot") for more information.

Please start a new topic for your question, otherwise different topics get mixed up. Furthermore, please do not post spam in your posts.

---

### Post by stefangr1 on 2012-01-25
> **tempiese said:**
> those message appear all the times i tried to download an application :for example skype or flash plugin. I tried download with the ubuntu download interface or manually but the result is the same. i'm thinking that is bettere if i uninstall ubuntu 10.11 and i install an old version.

I don't quite follow you. So you open a terminal, and update all installed programs to the latest version in the repositories, using
```
sudo apt-get update
sudo apt-get upgrade
```

Do any error messages appear?

Then, you (for example) attempt to install gcc, by running
```
sudo apt-get install gcc
```

Can you post the *entire* output you get in the terminal?

---

### Post by tempiese on 2012-01-25
Ok thank u for your patience and help! I'll try to explain better using my poor English and my worst knowledge of Ubuntu...

I 'll tried to enter in the "Update Manager" I clicked "Install Updates" and the message is "
Requires installation of untrusted packages

The action would require the installation of packages from not authenticated sources."

---

### Post by mastablasta on 2012-01-25
that message is there if you added some outside repositories. if you know they are OK and that you chose them you put in your password and it should start installing the updates. it seems the named packages are needed for a 32bit applicaiton you installed on 64 bit os.
 
you never wrote what programme you try to run/install or anyhting else. how are we suppose to know what causes the issue?

---

### Post by elizeb on 2012-01-30
> **stefangr1 said:**
> It's possible. Have a look [at this Howto]("https://help.ubuntu.com/community/WindowsDualBoot") for more information.

Please start a new topic for your question, otherwise different topics get mixed up. Furthermore, please do not post spam in your posts.
  Thanks stefangr1, the link was helpful.

---

