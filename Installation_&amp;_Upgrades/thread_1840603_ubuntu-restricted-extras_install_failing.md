---
title: "ubuntu-restricted-extras install failing"
date: 2011-09-07
forum: Installation &amp; Upgrades
---

### Post by clubbing80s on 2011-09-07
Hi.
I'm trying to install ubuntu-restricted-extras but the process dies with  "Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/pool/universe/o/openjpeg/libopenjpeg2_1.3+dfsg-4_amd64.deb](http://nz.archive.ubuntu.com/ubuntu/pool/universe/o/openjpeg/libopenjpeg2_1.3+dfsg-4_amd64.deb)  404  Not Found"

when I go to  [http://nz.archive.ubuntu.com/ubuntu/pool/universe/o/openjpeg](http://nz.archive.ubuntu.com/ubuntu/pool/universe/o/openjpeg) with firefox there is nothing in the directory.

is this because the mirrors are syncing or is there another issues ?

Full output :

root@fatcat:/home/its/Desktop# apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsm-dev libice-dev libxrandr-dev libexpat1-dev libgpg-error-dev comerr-dev libxfixes-dev libqt3-headers x11proto-xinerama-dev x11proto-render-dev
  libxi-dev libkrb5-dev libfontconfig1-dev liblcms1-dev x11proto-randr-dev libxinerama-dev libgssrpc4 x11proto-fixes-dev libxt-dev libxmu-dev libtasn1-3-dev
  zlib1g-dev libcups2-dev libqt3-compat-headers libfreetype6-dev libgcrypt11-dev libkadm5clnt-mit7 libaudio-dev libkadm5srv-mit7 libxmu-headers
  libxrender-dev xorg-sgml-doctools libxft-dev libkdb5-4 libgnutls-dev krb5-multidev libmng-dev libjpeg62-dev libxcursor-dev libpng12-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  cabextract gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse libavcodec-extra-52 libavutil-extra-50 libfaac0 libmjpegtools-1.9
  libmp3lame0 libmp4v2-0 libopenjpeg2 libquicktime1 libxvidcore4 ttf-mscorefonts-installer unrar
Suggested packages:
  libfaad0
The following packages will be REMOVED:
  libavcodec52 libavutil50
The following NEW packages will be installed:
  cabextract gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse libavcodec-extra-52 libavutil-extra-50 libfaac0 libmjpegtools-1.9
  libmp3lame0 libmp4v2-0 libopenjpeg2 libquicktime1 libxvidcore4 ttf-mscorefonts-installer ubuntu-restricted-extras unrar
0 upgraded, 15 newly installed, 2 to remove and 7 not upgraded.
Need to get 81.2 kB/4,307 kB of archives.
After this operation, 5,489 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) natty/universe libopenjpeg2 amd64 1.3+dfsg-4
  404  Not Found
Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/pool/universe/o/openjpeg/libopenjpeg2_1.3+dfsg-4_amd64.deb](http://nz.archive.ubuntu.com/ubuntu/pool/universe/o/openjpeg/libopenjpeg2_1.3+dfsg-4_amd64.deb)  404  Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
root@fatcat:/home/its/Desktop# 

Thanks 

G

---

### Post by ottosykora on 2011-09-08
what happends when you take other mirror of the archive? I mean not the nz. but something else?

---

### Post by clubbing80s on 2011-09-08
> **ottosykora said:**
> what happends when you take other mirror of the archive? I mean not the nz. but something else?
 
the mirrors are the ones apt-get choose. How do I force a spacific mirror , and can u recommend one ?
 
 
Thanks
G

---

### Post by JD8182 on 2011-09-08
> **clubbing80s said:**
> the mirrors are the ones apt-get choose. How do I force a spacific mirror , and can u recommend one ?
 
 
Thanks
G

Try this > sudo software-properties-gtk -e multiverse
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras

---

### Post by clubbing80s on 2011-09-08
> **JD8182 said:**
> sudo software-properties-gtk -e multiverse
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras 			 		

same result.

---

### Post by dniMretsaM on 2011-09-08
Since [FONT=Courier New]ubuntu-restricted-extras[/FONT] is a meta-package, try installing all the separate components. Run this in terminal:
```
sudo apt-get update
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse ttf-mscorefonts-installer unrar gstreamer0.10-plugins-bad-multiverse libavcodec-extra-52 libmp4v2-0 adobe-flashplugin flashplugin-installer gstreamer0.10-plugins-bad gstreamer0.10-ffmpeg gstreamer0.10-pitfdll icedtea6-plugin gstreamer0.10-fluendo-mp3
```

---

### Post by sffvba[e0rt on 2011-09-08
I would edit my software sources and point them to the main server and then run it... seems the mirror is missing a few things... 

To edit the sources you can use the software center, or synaptic (depeding what you have installed)...

[IMG]https://help.ubuntu.com/community/Repositories/Ubuntu?action=AttachFile&do=get&target=SoftwareSources-UbuntuSoftware.png[/IMG]

Find the above and select Main server as in the picture ;)


404

---

### Post by clubbing80s on 2011-09-08
I have changed the repository, this resolved the problem. The NZ repository is broken / out of sync.

Thanks for the assistance.

G

---

### Post by sffvba[e0rt on 2011-09-08
> **clubbing80s said:**
> I have changed the repository, this resolved the problem. The NZ repository is broken / out of sync.

Thanks for the assistance.

G

Sweet...


404

---

