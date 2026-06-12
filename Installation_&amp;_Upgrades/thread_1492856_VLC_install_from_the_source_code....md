---
title: "VLC install from the source code..."
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by ubun2warrior on 2010-05-25
Hi

I just downloaded the vlc source from the vlc website. Then i went to the terminal, extracted the tar.bz file. After that i ran ./configure command. But it shows some error and the installation ends. 

Please somebody guide me to install vlc manually from the terminal.

---

### Post by DrMelon on 2010-05-25
Well, the error is there for a reason - tell us what the error is, then we might be able to help.

---

### Post by ubun2warrior on 2010-05-25
Hi 
this is the error that i get
configure: error: Couldn't find DBus >= 1.0.0, install libdbus-dev ?

---

### Post by DrMelon on 2010-05-25
Try installing libdbus-dev in Synaptic.

---

### Post by rob-ward on 2010-05-25
I think if you run

```
sudo apt-get build-dep vlc

```

it should get all of the libraries that you will need to do a manual compile of VLC(or at least most of them)

---

### Post by ubun2warrior on 2010-05-25
hi 
while configuring there were many warnings (few listed below) and in the end the erroe message

configure: WARNING: new enough libcddb not found. CDDB access disabled
configure: WARNING: the dvb access module requires libdvbpsi

configure: WARNING: only static linking is available, you must provide a gme-tree
ERROR:-
configure: error: Could not find libmad on your system: you may get it from [http://www.underbit.com/products/mad/](http://www.underbit.com/products/mad/). Alternatively you can use --disable-mad to disable the mad plugin.

---

### Post by ubun2warrior on 2010-05-25
I installed the libdbus-dev from synaptics it did not work and i have posted the error above ..

---

### Post by vickystylton on 2010-05-25
If nothing works for you, you could always try out the offline installer for VLC. Just google for more info.

---

### Post by ubun2warrior on 2010-05-27
I tried to search for an offline installer for vlc. But they were all tarballs. I think i should be looking at a .deb package for ubuntu. So if you find any link please post it here.

Regards

---

### Post by ubun2warrior on 2010-05-27
Can somebody post the full procedure to install vlc from source code.
 Every time if i install ubuntu on somebody's machine they want their music and video files playing instantly. 
So it would be great to have an offline player for ubuntu. VLC is great because it plays most of the file formats. 
Any other player for UBUNTU would also be fine.

---

### Post by Zemblan on 2010-05-27
Why is it necessary for you to install it from source? Very much more convenient to just install it from the repos:

```
sudo apt-get install vlc
```

If you want the most recent version have a look at this thread: 

[http://ubuntuforums.org/showthread.php?t=1493653](http://ubuntuforums.org/showthread.php?t=1493653)

The problem you are having with the configure script is that you have missing headers for particular dependencies (things required for vlc to compile and work). These can be found in the 'dev' packages. So if you open the Software Centre and search for 'libmad' in this case, there will be a package called 'libmad0-dev', install it and then run the configure script again. Chances are that it will keep on having different errors until you have installed all the dependencies. 

This sort of problem is one reason why it is so much better to use the repositories than compiling from source, dependencies are resolved automatically, plus you get automatic upgrades etc.

Also you could run:

```
sudo aptitude install ubuntu-restricted-extras
```

This will install the codecs which will allow the default installed video player (Totem) to play most video formats.

---

### Post by ubun2warrior on 2010-05-28
I agree that the repositories is an excellent way to install vlc. But just in case my internet happens to be down and i have to listen to a song or something on a newly installed ubuntu then how am i supposed to play the song or the movie. 
I have found .deb packages for google chrome, adobe flash plugin, and a few more packages. And believe it is sometimes very great to have these packages handy.
Thank you for all your guidance and posts..
 ...I continue my search for offline installer for vlc

regards

---

### Post by Zemblan on 2010-05-28
The files that are in the repositories, the '.deb' files, can be saved and installed when you like. They are 'offline installers', you only need to be online to download them, once you have them you can install them as often as you like on as many computers as you like. So long as you have the other ".debs" that they depend on too.  
Alternatively you could research how to make your own, statically compiled, version of vlc.  

You can find the deb file for vlc along with a list of its dependencies here:

[http://packages.ubuntu.com/lucid/vlc]("http://packages.ubuntu.com/lucid/vlc")

if you had all those, you could use the dpkg' command to install them as you liked.

Or you could use a distro which comes with media codecs already, like the Ubuntu based Linux Mint. Then you would have no worries about having to get codecs after a new install.

---

### Post by mac9416 on 2010-05-28
> So long as you have the other ".debs" that they depend on too. 

ubun2warrior can use [Keryx]("http://keryxproject.org") to download the correct .deb packages (dependencies and all) to install VLC. It takes several steps, but it will work.

> Or you could use a distro which comes with media codecs already, like the Ubuntu based Linux Mint. Then you would have no worries about having to get codecs after a new install.

I also recommend Mint. Of course, if you want to install other applications offline, you'll still have to use Keryx, but at least codecs are not a problem.

---

### Post by imtiyaz on 2010-06-16
[SIZE="4"][B][SIZE="4"][SIZE="3"]Install [SIZE="3"]VLC Media player offline in Ubuntu 8.10/9.04/9.10[/SIZE][/SIZE][/SIZE]
[/B][/SIZE]

By following procedure VLC will be installed in any computer/notebook without having any internet connection


First you need to download VLC offline installer from [here]("http://hacktolive.org/wiki/VLC_offline_installer_(Ubuntu)")

Download VLC Offline installer for Ubuntu 9.10 (Karmic) Users from [here]("http://www.ubuntugeek.com/images/VLC_Offline_Installer_ubuntu_9.10.tar.gz")

_**Installation instructions**_
[LIST]
[*]After downloading right-click on the file & click on "extract here".
[*]A new folder will be created, double-click to open the new folder
[*]Then double-click the 'install.sh' & select "run in terminal"
[*]Enter your password if asked
[/LIST]

---

### Post by smothpocket on 2010-08-06
I know this issue was probably resolved by the offline installer, but figured I'd post the solution I found to the original problem for future reference to this thread. 

When I installed libhal-dev it resolved the error message about libdbus-dev.

sudo apt-get install libhal-dev

---

