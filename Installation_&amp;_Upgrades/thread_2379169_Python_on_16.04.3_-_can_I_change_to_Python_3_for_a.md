---
title: "Python on 16.04.3 - can I change to Python 3 for all packages ?"
date: 2017-12-01
forum: Installation &amp; Upgrades
---

### Post by oygle on 2017-12-01
I have only just started using Python a little bit to try and parse audio files and use Speech Recognition software ( [https://pypi.python.org/pypi/SpeechRecognition/](https://pypi.python.org/pypi/SpeechRecognition/) ) to produce text output (transcript). In installing all that was required, it seems quite a collection of python and other associated packages. My question is, do I really need Python 2 , and therefore, can I update everything to python 3 ??

I found a few threads regards Python and versions, and this one was interesting - [https://ubuntuforums.org/showthread.php?t=2325365](https://ubuntuforums.org/showthread.php?t=2325365)

```
python3 --version
```
Python 3.5.2

```
python2 --version
```
Python 2.7.12

```
python --version
```
Python 2.7.12

Using synaptic and searched for string 'python' found many packages, however without looking through all of those, I'm not sure whether they are dependant on version 2.7.12 or version 3.5.2 . If I tried **forcing** version 3.5.2 for all packages that are installed, I may **break** something. Looking with find/search, there are folders/files in the path *~/local/.lib/* to do with python and pip and the speech recognition software. Can I move them to / , so that all the software is in one place ?

Getting the Speech Recognition software ( [https://pypi.python.org/pypi/SpeechRecognition/](https://pypi.python.org/pypi/SpeechRecognition/) ) properly installed relied on various other packages needing to be installed. Will everything always be shown within synaptic or other package managers, or could there be parts of the installation that placed software outside of a package manager ? Just trying to keep it all tidy and easy to manage. I didn't record what was installed, but from the 'history' of commands, this is the best list I can come up with ..

```

sudo apt install python-pip
pip install SpeechRecognition
sudo apt-get install python-pyaudio python3-pyaudio
Pip: execute sudo apt-get install portaudio19-dev python-all-dev python3-all-dev && sudo pip install pyaudio
sudo apt-get install portaudio19-dev python-all-dev python3-all-dev && sudo pip install pyaudio
pip install --upgrade pip
sudo pip install --upgrade pyaudio
pip install pocketsphinx
sudo apt-get install python python-all-dev python-pip build-essential swig git libpulse-dev

```

Is it true to say that any of the above commands with either *apt install* or *apt-get install* has resulted in the addition/update of a package that will be shown in synaptic or similar package manager ? I'm not sure about *pip install* though. It was used to install *pocketsphinx* and that shows in synaptic, yet **pip** was also used to install *SpeechRecognition* , and that doesn't show in synaptic.

It wasn't a clear/clean installation , to get this all in place, and I'm wanting to keep it all tidy, in the one place, and make for easy management. Can I upgrade everything to python 3 ?

---

### Post by photonxp on 2017-12-02
> If I tried **forcing** version 3.5.2 for all packages that are installed, I may **break** something.
This would definitely break something.
> there are folders/files in the path *~/local/.lib/* to do with  python and pip and the speech recognition software. Can I move them to /  , so that all the software is in one place ?
This would break things too. It also requires root permission to do so.

If you want to know your package dependencies, try:
  ```

sudo apt-get update && sudo apt-get install aptitude
aptitude show python-pyaudio

```


If you want to experiment on something new without being afraid of rolling up your sleeves and digging up some dirt, just try virtual machine software such as Virtualbox where you can install a virtual Ubuntu OS. Then all the damage done is limited within that virtual OS.

---

### Post by oygle on 2017-12-09
> **photonxp said:**
> If you want to experiment on something new without being afraid of rolling up your sleeves and digging up some dirt, just try virtual machine software such as Virtualbox where you can install a virtual Ubuntu OS. Then all the damage done is limited within that virtual OS.

Thanks for your replies.I have used VM before, to install windows within a VM. The article at [https://python-forum.io/Thread-Basic-Part-1-Linux-Python-3-environment](https://python-forum.io/Thread-Basic-Part-1-Linux-Python-3-environment)  describes how to setup a virtual environment, and since reading that article, have seen a number of installation instructions mentioning a virtual environment. It keeps packages seperate and minimises the risk of conflicts. It creates an isolated environment.

---

### Post by ian-weisser on 2017-12-09
The old-timer advice is simple: DO NOT CHANGE the system-provided versions of Python. Essential parts of your system (like apt) depend upon python.
People have tried it before, and it BROKE THEIR SYSTEMS HORRIBLY.

Don't do it. If you insist upon trying, have good backups before you start and have a handy LiveUSB...because you will be reinstalling very soon.

Ubuntu completed it's multi-year conversion of Main packages to Python3 in 17.10. New-installs of 17.10 do not include Python2 anymore, though it is in the repository, and is quickly pulled in by many packages in Universe.

---

### Post by oygle on 2017-12-09
> **ian-weisser said:**
> The old-timer advice is simple: DO NOT CHANGE the system-provided versions of Python. Essential parts of your system (like apt) depend upon python.
People have tried it before, and it BROKE THEIR SYSTEMS HORRIBLY.

Don't do it. If you insist upon trying, have good backups before you start and have a handy LiveUSB...because you will be reinstalling very soon.

Ubuntu completed it's multi-year conversion of Main packages to Python3 in 17.10. New-installs of 17.10 do not include Python2 anymore, though it is in the repository, and is quickly pulled in by many packages in Universe.

Okay thanks for your advice. When you say 'system provided versions of python' , I assume that doesn't include a virtual environment. I've only used a VM, not a virtual environment as discussed in that article, and see the virtual environment as keeping different versions of packages in an isolated environment.

Seems there are a few issues with 17.10 being version 3.6 - [https://github.com/MartinSahlen/cloud-functions-python/issues/21](https://github.com/MartinSahlen/cloud-functions-python/issues/21) , and I see there is already an 18.04 version in beta.

---

### Post by vasa1 on 2017-12-09
> can I change to Python 3 for all packages ?If a package uses an older version of Python, how can you do what you want?

Have you looked at```
apt-get purge -s python
```to see which packages on **your system** will be affected? The "-s" is for *simulation* and so *sudo* isn't needed.

Here's part of the output on my Kubuntu 16.04:```
$ apt-get purge -s python
NOTE: This is only a simulation!
      apt-get needs root privileges for real execution.
      Keep also in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  calligra-data calligra-libs calligrawords-common calligrawords-data libatkmm-1.6-1v5 libblas-common libblas3 libcairomm-1.0-1v5 libcauchy0.0v5
  libenca0 libgfortran3 libglibmm-2.4-1v5 libgtkmm-2.4-1v5 libgtkspell0 libimage-magick-perl libimage-magick-q16-perl libkdegames6abi1
  libkdegamesprivate1abi1 libkrossui4 liblapack3 libm2mml0.0v5 libmagick++-6.q16-5v5 libpangomm-1.4-1v5 libphononexperimental4 libpoppler-glib8
  libqaccessibilityclient0 libsoprano4 libspnav0 libvorbisidec1 qml-module-org-kde-kirigami soprano-daemon
Use 'apt autoremove' to remove them.
The following packages will be REMOVED:
  apturl-kde* calligrawords* gdebi-kde* inkscape* iotop* k3b* k3b-i18n* kde-baseapps-bin* kde-runtime* kdemultimedia-kio-plugins* kdesudo*
  kio-audiocd* kio-extras* kmag* kolourpaint4* kommander* ksudoku* ktorrent* kubuntu-settings-desktop* language-pack-kde-en* libreoffice-kde*
  libsmbclient* mplayer* muon-notifier* muon-updater* okular* plasma-discover* python* python-bs4* python-chardet* python-dbus* python-gi*
  python-html5lib* python-lxml* python-numpy* python-pkg-resources* python-qt4-dbus* python-six* python-talloc* python3-pykde4* samba-libs*
  skanlite* ubuntu-release-upgrader-qt* vlc-plugin-samba*
0 upgraded, 0 newly installed, 44 to remove and 0 not upgraded.

```I can post the same for Kubuntu 17.10 or Kubuntu 18.04 if you're interested.

In short, +1 to what ian-weisser said!

Edit: by the way, plain python refers to python 2*. You can see that by running```
apt policy python
```

---

### Post by oygle on 2017-12-10
> **vasa1 said:**
> If a package uses an older version of Python, how can you do what you want?

Yes, that's a good question. I tried the

```

$ apt-get purge -s python
```

> NOTE: This is only a simulation!
      apt-get needs root privileges for real execution.
      Keep also in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gimp-data gir1.2-atk-1.0 gir1.2-freedesktop gir1.2-gdkpixbuf-2.0 gir1.2-gtk-3.0 gir1.2-javascriptcoregtk-3.0 gir1.2-pango-1.0 gir1.2-soup-2.4 gir1.2-webkit-3.0 gnome-icon-theme
  gnome-icon-theme-symbolic gnome-keyring kmymoney-common libalkimia4 libamd2.4.1 libaqbanking-data libaqbanking35 libaqbanking35-plugins libaqebics0 libaqhbci22 libaqofxconnect7
  libasound2:i386 libasyncns0:i386 libbabl-0.1-0 libcamd2.4.1 libccolamd2.9.1 libcholmod3.0.6 libenca0 libflac8:i386 libgdata-common libgdata22 libgegl-0.3-0 libgimp2.0 libglib2.0-bin
  libgoa-1.0-0b libgoa-1.0-common libgpgme++2v5 libguess1 libgwengui-cpp0 libgwengui-qt4-0 libgwenhywfar-data libgwenhywfar60 libjavascriptcoregtk-3.0-0 libjson-c2:i386 libkholidays4
  libkonq5abi1 libktoblzcheck1v5 libmpg123-0 liboauth0 libofx6 libopencore-amrnb0 libopencore-amrwb0 libosp5 libp11-kit-gnome-keyring libpam-gnome-keyring libpangoxft-1.0-0 libpcre3-dev
  libpcre32-3 libpcrecpp0v5 libpoppler-glib8 libpulse0:i386 libpython-all-dev libpython-dev libpython2.7-dev librubberband2v5 libsamplerate0:i386 libsdl2-2.0-0 libsnack-alsa libsndfile1:i386
  libsndio6.1 libsox-fmt-alsa libsox-fmt-base libsox2 libspeexdsp1:i386 libtcl8.5 libtk8.5 libumfpack5.7.1 libva-wayland1 libwebkitgtk-3.0-0 libwebkitgtk-3.0-common libwrap0:i386 libxmlsec1
  linux-headers-4.4.0-96 linux-headers-4.4.0-96-generic linux-headers-4.4.0-97 linux-headers-4.4.0-97-generic linux-headers-4.4.0-98 linux-headers-4.4.0-98-generic
  linux-image-4.4.0-96-generic linux-image-4.4.0-97-generic linux-image-4.4.0-98-generic linux-image-extra-4.4.0-96-generic linux-image-extra-4.4.0-97-generic
  linux-image-extra-4.4.0-98-generic mpv p11-kit p11-kit-modules pinentry-qt4 python2.7-dev rtmpdump sox tcl-snack tcl-tclex tcl8.5 tk8.5 zlib1g-dev
Use 'apt autoremove' to remove them.
The following packages will be REMOVED:
  amarok* amarok-utils* apturl-kde* gimp* gufw* gvfs-backends* k3b* k3b-i18n* kde-baseapps-bin* kde-runtime* kdeconnect* kdemultimedia-kio-plugins* kdesudo* kfind* kio-audiocd* kio-extras*
  kmymoney* krdc* ktorrent* kubuntu-settings-desktop* kuser* language-pack-kde-en* libglib2.0-dev* libpulse-dev* libreoffice-kde* libsmbclient* okular* plasma-discover* python* python-all*
  python-all-dev* python-cairo* python-dbus* python-dev* python-gi* python-gobject-2* python-gtk2* python-netifaces* python-pip* python-pkg-resources* python-pyaudio* python-qt4-dbus*
  python-setuptools* python-talloc* python-wheel* python3-pykde4* samba-libs* skanlite* ubuntu-release-upgrader-qt* vlc-plugin-samba* youtube-dl*
0 to upgrade, 0 to newly install, 51 to remove and 0 not to upgrade.

Also ```
$ apt policy python
```

> python:
  Installed: 2.7.11-1
  Candidate: 2.7.11-1
  Version table:
 *** 2.7.11-1 500
        500 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) xenial/main amd64 Packages
        100 /var/lib/dpkg/status


So, in summary, to answer my question (thread topic), .. **NO**.  However if I wanted to _firstly_ setup a virtual environment and then run package/s within that, and change to python3 for those package/s, it would appear that it is safe to do so. _Within_ the virtual environment as the restriction. Obviously it will also be advantageous to be running 17.10 at least.

---

### Post by monkeybrain20122 on 2017-12-10
> **oygle said:**
> 
Is it true to say that any of the above commands with either *apt install* or *apt-get install* has resulted in the addition/update of a package that will be shown in synaptic or similar package manager ? I'm not sure about *pip install* though. It was used to install *pocketsphinx* and that shows in synaptic, yet **pip** was also used to install *SpeechRecognition* , and that doesn't show in synaptic.

It wasn't a clear/clean installation , to get this all in place, and I'm wanting to keep it all tidy, in the one place, and make for easy management. Can I upgrade everything to python 3 ?


pip has nothing to do with apt, therefore you have two different pocketsphinx, one from pip one from apt. if you want things separated maybe should try anaconda?

---

### Post by oygle on 2017-12-10
> **monkeybrain20122 said:**
> pip has nothing to do with apt, therefore you have two different pocketsphinx, one from pip one from apt. if you want things separated maybe should try anaconda?

Okay, thanks for clarifying that for me. I see there is a guide on  [How To Install the Anaconda Python Distribution on Ubuntu 16.04 ]("https://www.digitalocean.com/community/tutorials/how-to-install-the-anaconda-python-distribution-on-ubuntu-16-04")

---

### Post by vasa1 on 2017-12-10
> **oygle said:**
> ... However if I wanted to _firstly_ setup a virtual environment and then run package/s within that, and change to python3 for those package/s, it would appear that it is safe to do so. _Within_ the virtual environment as the restriction. Obviously it will also be advantageous to be running 17.10 at least.
You can safely do most things in a virtual machine, but, without rewriting code, I don't see how you can "change to python3 for those package/s". If it were that trivial, don't you think it would have been done already?

---

### Post by oygle on 2017-12-10
> **vasa1 said:**
> .. I don't see how you can "change to python3 for those package/s". If it were that trivial, don't you think it would have been done already?

For example, where a package has both python2 and python3 versions, it may be suitable to install within the virtual environment.

---

### Post by ian-weisser on 2017-12-12
A whole team of volunteers spent years doing exactly that (among other actions) to make 17.10 the first Py3-only release.
They wanted to complete by 16.04 (it was a five-or-so year project), but found a few significant blockers that took another 18 months to overcome.

Sound like a fun experiment, as long as you know it's an already-trod path. And not an easy path.

---

### Post by vasa1 on 2017-12-12
[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2017-December/001234.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2017-December/001234.html)

---

### Post by oygle on 2017-12-12
> **ian-weisser said:**
> A whole team of volunteers spent years doing exactly that (among other actions) to make 17.10 the first Py3-only release.
They wanted to complete by 16.04 (it was a five-or-so year project), but found a few significant blockers that took another 18 months to overcome.

Sound like a fun experiment, as long as you know it's an already-trod path. And not an easy path.

Sounds like it was a lot of work, and great that Python3 is now in 17.10. Yes, a fun experiment, but it may be wise to do a clean install of 17.10 on a 'test' machine, and then try the virtual environment on that machine. Then I can keep this one just for 17.10 with nothing that would break it.

> **vasa1 said:**
> [https://lists.ubuntu.com/archives/ubuntu-devel-announce/2017-December/001234.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2017-December/001234.html)

Thanks, that's good news. The irony is that this thread was only started a few days ago, and in that time, I have now found another project which may well suit my needs much better. But, it uses Python 2.7 - [DeepSpeech]("https://github.com/mozilla/DeepSpeech")  ...   :)

---

