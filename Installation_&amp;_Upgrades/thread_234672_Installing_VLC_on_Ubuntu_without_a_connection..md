---
title: "Installing VLC on Ubuntu without a connection."
date: 2006-08-11
forum: Installation &amp; Upgrades
---

### Post by Ubempi on 2006-08-11
Hi people! 
I have just installed Ubuntu on a machine that does not have an Internet connection.

I want to install VLC ( [http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html) ) in Ubuntu but I don't Have Internet at my house, I'm writing from a Cyber right now. 

Is there some way to download the package so I can carry it in my pendrive?

If there is an explanation about how to install any other package in offline mode it would be great but for now I'm very interested in this one. Thanks!

---

### Post by mlind on 2006-08-11
> **Ubempi said:**
> Hi people! 
I have just installed Ubuntu on a machine that does not have an Internet connection.

I want to install VLC ( [http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html) ) in Ubuntu but I don't Have Internet at my house, I'm writing from a Cyber right now. 

Is there some way to download the package so I can carry it in my pendrive?

If there is an explanation about how to install any other package in offline mode it would be great but for now I'm very interested in this one. Thanks!

The problem here is that VLC has a lot of other dependencies that you need to download as well (not to mention dependencies of dependencies .. ). It's possible though.
If package would be on Ubuntu install cd (VLC isn't I guess..), you could add cdrom as repository using apt-cdrom and install packages from cd using aptitude/apt-get.

Otherwise you need to download packages from Ubuntu repository one by one.. VLC packages can be found from [http://archive.ubuntu.com/ubuntu/pool/universe/v/vlc/](http://archive.ubuntu.com/ubuntu/pool/universe/v/vlc/), dapper's version is 0.8.4.debian-1ubuntu6. 

To resolve all other packages you need (internet connection is needed for this though..)
```

apt-cache depends vlc

```
Some of the results may or may not be already installed


To install a local package
```

sudo dpkg -i *package.deb*

```


I simulated vlc install on a minimal dapper chroot, these packages are required for vlc
```

defoma dmidecode esound-common file fontconfig laptop-detect liba52-0.7.4 libaa1 libatk1.0-0 libaudiofile0 libavahi-client3 libavahi-common-data
  libavahi-common3 libcairo2 libcdio6 libdbus-1-2 libdc1394-13 libdrm2 libdvbpsi4 libdvdnav4 libdvdread3 libesd0 libexpat1 libflac7 libfontconfig1
  libfreetype6 libgl1-mesa libglib2.0-0 libglu1-mesa libgsm1 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libhal1 libid3tag0 libiso9660-4 libjpeg62
  libkrb53 liblircclient0 libmad0 libmagic1 libmodplug0c2 libmpcdec3 libmpeg2-4 libogg0 libpango1.0-0 libpango1.0-common libpng12-0 libraw1394-5
  libsmbclient libtar libtheora0 libtiff4 libvcdinfo0 libvorbis0a libvorbisenc2 libwxgtk2.6-0 libx11-6 libxau6 libxcursor1 libxext6 libxfixes3 libxft2
  libxi6 libxinerama1 libxml2 libxosd2 libxrandr2 libxrender1 libxv1 libxxf86vm1 ttf-bitstream-vera ttf-dejavu ttf-freefont ucf vlc vlc-plugin-alsa wxvlc
  x11-common

```
If you can access to Ubuntu (dapper) system with an internet connection, you could download all these packages to a folder by
```

aptitude download *package1 package2 package3* ..

```

---

### Post by Ubempi on 2006-08-14
First: Thanks for the soon response.

> 
sudo dpkg -i package.deb


That is a good one. I think I'll do a lot of things with that.

I don't have access to a Linux machine connected to the Internet. Here all of the machines are Windows based and I have to come to the cyber each time.

I'll be playing around a little and in a few days I'll came to tell how I'm doing.

Thanks a lot for your time. :-D

---

### Post by Ubempi on 2006-09-10
> I my self wrote:
...
I'll be playing around a little and in a few days I'll came to tell how I'm doing.
...

Well... it's been 3 weeks since then, I'm on a machine with an Internet connection and I've installed Kubuntu on it. Kubuntu is pretty cool, but I'm sad because I've installed Firefox and it's not working after I installed the Google Toolbar on it. That is not the metter any way.
The point is that I've installed VLC. ¡¡¡Works grat!!! :)
But, how can I make it easy to install VLC in MY machine, witch does not  have an Internet connection, I can now burn a CD.

Is there a command with wich I can install VLC and all it's dependences at once from the CD?

Almost aswering this question I've found the command:
 
  "dpkg -i -r <directory>" 
  
 witch will install all the packages placed in <directory>.

But nothing tells me that this command will install the packages in correct order, in adition I have readed of "local repositories", or something like that, and I wonder if there is a way to put all of what is necesary to install VLC on a CD and then add the CD as a repository and make apt (or whatever else) install all just like it does from the Internet...

well... how ever I've the packages downloaded into a folder now and if there is no other way I will install them one by one :(

---

### Post by orb9220 on 2006-09-10
Yes open synaptic it will allow you to add cd to it.

---

