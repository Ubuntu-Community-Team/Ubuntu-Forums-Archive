---
title: "Installing from a Local Repositry"
date: 2007-03-14
forum: Installation &amp; Upgrades
---

### Post by oneofth3m on 2007-03-14
Hello,

Recently i migrated to Ubuntu (6.06). I have downloded the necessary softwares using synaptic and have all the .deb files in my /var/cache/apt/archives/ folder.

I have started a local repository and all the files are accesible using http.

I copied all the files to '/home/userName/ubuntu/apt/archives/debs/' folder. I added Packages.gz file using:
  dpkg-scanpackages /dev/null > .debs/Packages.gz

The above command succesfully completed and wrote to the file some 300+ entries

using [http://192.168.0.7/archives/debs/package_name.deb](http://192.168.0.7/archives/debs/package_name.deb) i am able to download the files.

In a different ubuntu machine i added :

[http://192.168.0.7/archives](http://192.168.0.7/archives) debs/

in /etc/sources.list.

When i opened synaptic it showed me the softwares available on my repository (i am sure that softwares showed are from my repository and not others because i removed every other repository from sources.list and checked)

The problem occurs when i am trying to install. I marked VLC for installation and it says :

 Depends: liba52-0.7.4  but it is not installable
 Depends: libdc1394-13  but it is not installable
 Depends: libdvbpsi4  but it is not installable
 Depends: libdvdnav4 (>=0.1.9) but it is not installable
 Depends: libdvdread3  but it is not installable
 Depends: libgsm1 (>=1.0.10) but it is not installable
 Depends: libiso9660-4  but it is not installable
 Depends: libmad0 (>=0.15.1b) but it is not installable
 Depends: libmodplug0c2 (>=1:0.7-4.1) but it is not installable
 Depends: libtar  but it is not installable
 Depends: libvcdinfo0 (>0.7.23) but it is not installable
 Depends: wxvlc but it is not going to be installed
 Depends: vlc-plugin-alsa but it is not going to be installed

wxvlc, vlc-plugin-alsa are available in my repository but i still get this error.

The same problem also occurs for many other softwares.

But I was able to successfully  install 'binutils'.

I think the error is because of the softwares being from universe multiverse and other categories.

Please point me in the right direction?

---

### Post by zvacet on 2007-03-14
I think you are right.Just add all availabe repositories.

---

### Post by oneofth3m on 2007-03-15
How am i supposed to add the main multiverse and other repositories when i specify this in my /etc/sources.list :

deb [http://192.168.0.7/archives/](http://192.168.0.7/archives/) debs/ main multiverse main universe

i get an error that its not able to find the files in my server corresponding to those entries.

---

### Post by zvacet on 2007-03-15
if you don´t have some specific reason to make your own repositories look this
[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

