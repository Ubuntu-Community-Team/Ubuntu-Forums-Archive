---
title: "installing music/video player in ubuntu fiesty fawn"
date: 2007-05-13
forum: Installation &amp; Upgrades
---

### Post by amrith on 2007-05-13
hi all,

I am new to ubuntu and linux and this might be a very silly question.

I installed ubuntu fiesty fawn but i am not able to listen to mp3 or watch any videos ( i dont have a internet connection at home ) The default players show some errors :( 

I would be thankful if someone helps me guiding in how to manually install one ...


Thanks :)

---

### Post by nubutu on 2007-05-13
Download it from somewhere and save/print it. 

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

Enjoy it.

---

### Post by amrith on 2007-05-13
[B]thanks i went thru it...

so this means i can install without internet ??

some commands link to websites so how will those work ? [/B]

---

### Post by orb9220 on 2007-05-13
> so this means i can install without internet ??

No all packages in synaptic are fetched from the internet.

The easy way is Automatix2 which will let you select install a multitude of codecs and multimedia stuff.   [http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by mikewhatever on 2007-05-13
Hi amrith, there was a very similar post a few hours ago [http://ubuntuforums.org/showthread.php?t=442235](http://ubuntuforums.org/showthread.php?t=442235)
but no solution so far. Theoretically, you can copy the list of packages needed (see below) to a text file, and then search and download them from here [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
> THE LIST OF PACKAGES
ubuntu-restricted-extras libxine-extracodecs gstreamer0.10-plugins-base gstreamer0.10-plugins-good 
gstreamer0.10-plugins-bad gstreamer0.10-pitfdll

Those will be deb files which you can double click and install. Try that and tell us how it went.

An alternative would be to install [VLC media player](http://www.videolan.org/vlc/), which supports most multimedia formats.

---

### Post by amrith on 2007-05-13
> **mikewhatever said:**
>  Theoretically, you can copy the list of packages needed (see below) to a text file, and then search and download them from here [http://packages.ubuntu.com/](http://packages.ubuntu.com/)


 .


Lemme try my best .....
Thanks all ...

I have downloaded some of the tar.gz files(from [http://packages.ubuntu.com/feisty/](http://packages.ubuntu.com/feisty/))  will go home and try out if these work out somehow(fingers crossed)  

My only problem is that i dont have internet at home :(

---

### Post by mikewhatever on 2007-05-13
Hmm..., tar.gz? All I saw was *.deb files there.

---

### Post by amaroKer on 2007-05-13
No don't use .tar.gz.  Those are source files.  Get *.deb because they're installable upon doubleclick.

---

### Post by amrith on 2007-05-13
> **mikewhatever said:**
> Hmm..., tar.gz? All I saw was *.deb files there.
I didnt get any .deb files ! have a chk at this link...[http://packages.ubuntu.com/feisty/sound/cynthiune.app](http://packages.ubuntu.com/feisty/sound/cynthiune.app) is for "cynthiune" ..i didnt find any file from this website with *.deb ?? 

or Am i searching in the wrong place ?

---

### Post by amrith on 2007-05-13
[B]OR have a check on this link for VLC player and guide me ..........
[http://packages.ubuntu.com/feisty/net/vlc-nox](http://packages.ubuntu.com/feisty/net/vlc-nox)[/B]

---

### Post by mikewhatever on 2007-05-13
OK, I've downloaded the debs for you. Get them from here [http://www.filefactory.com/file/e1ca48/](http://www.filefactory.com/file/e1ca48/)
Just download the ta.gz file, and move it to Ubuntu to the desktop or any other safe location. Right click it and select 'Extract Here'. That should give you a folder called Codecs with eight deb packages inside. Here is the list
> ubuntu-restricted-extras
libxine-extracodecs
gstreamer0.10-plugins-base
gstreamer0.10-plugins-good 
gstreamer0.10-plugins-bad
gstreamer0.10-pitfdll

w32codecs
libdvdcss
A *.deb file in Ubuntu is the same as an *.exe in Windows. Double clicking it should launch the installer and install the file if all the dependencies are met. If not, you'll see a message saying another package is required. Write the name down and post here. Hope it'll work
Good luck.

PS: Here is the link to the vlc-nox file [http://mirrors.kernel.org/ubuntu/pool/universe/v/vlc/vlc-nox_0.8.6.release-0ubuntu4_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/v/vlc/vlc-nox_0.8.6.release-0ubuntu4_i386.deb)

---

### Post by lo900 on 2007-05-18
mikewhatever  , I like to thank you for this effort

---

### Post by bung33 on 2007-05-18
By default, 7.04 doesn't come packaged with support for mp3s. You have to install the gstreamer mp3 plugins that you can find using the synaptic package manager. Search for gstreamer mp3 and you should find quite a few relevant packages that you can install. When I installed mp3 support on my distro, I downloaded and installed the packages below...

[LIST]
[*]gstreamer0.10-fluendo-mp3
[*]gstreamer0.8-lame
[*]gstreamer0.8-misc
[/LIST]

After that, I was able to play mp3s in rythmbox and xine without any problems. Hope it helps...

---

### Post by JSThePatriot on 2007-05-22
bung33

Thanks for letting me know those libraries! They helped in getting some music to play!

JS

---

