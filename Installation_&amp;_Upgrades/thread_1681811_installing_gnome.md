---
title: "installing gnome"
date: 2011-02-04
forum: Installation &amp; Upgrades
---

### Post by thedoctor81877 on 2011-02-04
Hullo all. I am trying to install gnome through the terminal, but keep getting the following error message:

```

The following packages have unmet dependencies:
 gnome : Depends: swfdec-mozilla but it is not going to be installed
E: Broken packages

```

Any help would be greatly appreciated. Thanks.

---

### Post by tommcd on 2011-02-04
How exactly are you trying to install gnome? Please list the commands you are using.
What version of Ubuntu are you using? And what desktop are you using now?

You need to provide some pertinent information if you want anyone to help you.

Do you have any third party repositories in your sources? This includes those all too problematic PPA repositories???

The easy way to install gnome, and the whole Ubuntu desktop with gnome, is to run in the terminal:
```
sudo apt-get install ubuntu-desktop
```
You could then uninstall any programs that you do not want.

---

### Post by thedoctor81877 on 2011-02-04
I am running Ubuntu 10.10 on a netbook, so UNR 10.10. Here is how I have been trying to install GNOME:

```

thedoctor@TheDoctorsTARDIS:~$ sudo apt-get install ubuntu-desktop
[sudo] password for thedoctor: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
thedoctor@TheDoctorsTARDIS:~$ sudo apt-get install gnome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnome : Depends: swfdec-mozilla but it is not going to be installed
E: Broken packages

```

I know I have third-party repos in my source (at least I think I do), so how do I find that info, so I can display it to get more help? Thanks.

---

### Post by tommcd on 2011-02-04
> **thedoctor81877 said:**
> 
I know I have third-party repos in my source (at least I think I do), so how do I find that info, so I can display it to get more help?
You should know if you if you have installed any third party repos, since this is something that you have done to your system.

Post your /etc/apt/sources.list file. 
Also post any files you may have in your /etc/apt/sources.list.d/ directory.

Your output from <sudo apt-get install ubuntu-desktop>indicates that you already have gnome installed.

---

### Post by thedoctor81877 on 2011-02-04
But, and maybe I just do not know enough about this, but when I say try to use the Ubuntu Software Center to install GNOME desktop environment with the extras (for lack of the proper term), I get the previous unmet dependencies as I did when using the terminal.

---

### Post by tommcd on 2011-02-05
Can you post the contents of your /etc/apt/sources.list file as I asked in my last post?
Also post any files in your /etc/apt/sources.d/ directory.

---

### Post by kansasnoob on 2011-02-05
That behavior is typical when trying to install the package "gnome". UNR uses Unity which is a "tweak" to the Ubuntu desktop.

Try either logging out, or killing X with Alt>SysReq>K, and when you click on the username window look at the bottom panel. I think you'll be able to "toggle" and select "Classic desktop".

BTW the package to install the actual Debian flavor gnome desktop is "gnome-desktop-environment" but it will not look at all like Ubuntu, it'll look much more like Debian.

---

### Post by thedoctor81877 on 2011-02-05
To: tommcd. When I try the /etc/apt/sources, all I get is the following.

```

thedoctor@TheDoctorsTARDIS:~$ /etc/apt/sources.list 
bash: /etc/apt/sources.list: Permission denied

```

For the /etc/apt/sources.d/ directory, I get the following:
```

/etc/apt/sources.d/ directory

```

That is what you were referring to isn't it?
Thanks again.

---

### Post by thedoctor81877 on 2011-02-05
To kansasnoob : When I try to use the terminal to sudo-apt get install gnome-desktop-envioronment, I get the following:

```

thedoctor@TheDoctorsTARDIS:~$ sudo apt-get install gnome-desktop-envioronment
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gnome-desktop-envioronment

```

Thanks.

---

### Post by kansasnoob on 2011-02-05
> **thedoctor81877 said:**
> To kansasnoob : When I try to use the terminal to sudo-apt get install gnome-desktop-envioronment, I get the following:

```

thedoctor@TheDoctorsTARDIS:~$ sudo apt-get install gnome-desktop-envioronment
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gnome-desktop-envioronment

```

Thanks.

Your spelling is wrong, but I really don't think that's what you want to do!

Did you try logging into the Classic Desktop option? Right after clicking on the username click on Session in the lower panel and I believe you'll find that option.

---

### Post by thedoctor81877 on 2011-02-05
I am currently in the Desktop Environment rather than Unity.

---

### Post by kansasnoob on 2011-02-06
> **thedoctor81877 said:**
> I am currently in the Desktop Environment rather than Unity.

And you still dislike that?

---

### Post by kansasnoob on 2011-02-06
Just FYI I'm not trying to beat you up, I just don't like breaking peoples computers :p

As an example only, I'm running 10.10 (aka: Maverick) desktop edition and if I install gnome-desktop-environment it installs lots of stuff I normally wouldn't use:

```
lance@lance-desktop:~$ sudo apt-get install gnome-desktop-environment
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  hplip-cups
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  alsa-oss cheese cheese-common dasher dasher-data deskbar-applet ekiga
  festival festlex-cmu festlex-poslex festvox-kallpc16k freeglut3
  gir1.0-atk-1.0 gir1.0-clutter-1.0 gir1.0-clutter-gtk-0.10 gir1.0-gconf-2.0
  gir1.0-gdkpixbuf-2.0 gir1.0-gstreamer-0.10 gir1.0-gtk-2.0
  gir1.0-json-glib-1.0 gir1.0-pango-1.0 glchess glines gnash gnash-common
  gnect gnibbles gnobots2 gnome-accessibility gnome-core gnome-games
  gnome-js-common gnome-netstatus-applet gnome-themes gnotravex gnotski gok
  gtali hamster-applet iagno libboost-date-time1.42.0 libboost-thread1.42.0
  libcheese-gtk18 libdiscid0 libestools2.0 libgnome-speech7 libgtkglext1
  libmusicbrainz3-6 libopal3.6.8 libpt2.6.7 libseed0 libsrtp0 lightsoff
  oss-compat python-evolution python-gnomedesktop python-gtkglext1
  python-opengl python-rsvg seahorse-plugins seed sound-juicer swell-foop
  swfdec-gnome
Suggested packages:
  siproxd gnugk mediaproxy ser rtpproxy asterisk yate pidgin-festival
  festival-freebsoft-utils gnome-dbg gnome-hearts gok-doc srtp-utils python-tk
  python-numpy libgle3 gstreamer0.10-plugins-really-bad
Recommended packages:
  python-beagle
The following NEW packages will be installed:
  alsa-oss cheese cheese-common dasher dasher-data deskbar-applet ekiga
  festival festlex-cmu festlex-poslex festvox-kallpc16k freeglut3
  gir1.0-atk-1.0 gir1.0-clutter-1.0 gir1.0-clutter-gtk-0.10 gir1.0-gconf-2.0
  gir1.0-gdkpixbuf-2.0 gir1.0-gstreamer-0.10 gir1.0-gtk-2.0
  gir1.0-json-glib-1.0 gir1.0-pango-1.0 glchess glines gnash gnash-common
  gnect gnibbles gnobots2 gnome-accessibility gnome-core
  gnome-desktop-environment gnome-games gnome-js-common gnome-netstatus-applet
  gnome-themes gnotravex gnotski gok gtali hamster-applet iagno
  libboost-date-time1.42.0 libboost-thread1.42.0 libcheese-gtk18 libdiscid0
  libestools2.0 libgnome-speech7 libgtkglext1 libmusicbrainz3-6 libopal3.6.8
  libpt2.6.7 libseed0 libsrtp0 lightsoff oss-compat python-evolution
  python-gnomedesktop python-gtkglext1 python-opengl python-rsvg
  seahorse-plugins seed sound-juicer swell-foop swfdec-gnome
0 upgraded, 65 newly installed, 0 to remove and 1 not upgraded.
Need to get 48.9MB of archives.
After this operation, 179MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.

```

Some things like flash break because of package conflicts and dependencies!

I think it'd be best to explain what UNR is doing, or not doing, that you don't like. This review reflects that you're not alone in not loving 10.10 UNR:

[http://www.dedoimedo.com/computers/unr-maverick.html](http://www.dedoimedo.com/computers/unr-maverick.html)

I don't do much work on netbooks very often because I'm visually impaired but I've had a few people express strong preferences in favor of either Lubuntu or Peppermint:

[http://distrowatch.com/table.php?distribution=lubuntu](http://distrowatch.com/table.php?distribution=lubuntu)

[http://distrowatch.com/table.php?distribution=peppermint](http://distrowatch.com/table.php?distribution=peppermint)

Both are based on Ubuntu but Peppermint uses some Mint tools which I personally find to be a bit of a kludge. OTOH Peppermint comes set up with a full array of Cloud-based applications which is great for those with the new, but small, SSD drives.

So many distros, so little time ;)

---

### Post by tommcd on 2011-02-06
> **thedoctor81877 said:**
> To: tommcd. When I try the /etc/apt/sources, all I get is the following.

thedoctor@TheDoctorsTARDIS:~$ /etc/apt/sources.list 
bash: /etc/apt/sources.list: Permission denied


For the /etc/apt/sources.d/ directory, I get the following:
/etc/apt/sources.d/ directory

That is what you were referring to isn't it?

Simply open a terminal and type: **cat /etc/apt/sources.list** And post the output here. NOTE: You may need to scroll up and down in order to post the whole output.

Also post the output of: **ls /etc/apt/sources.d/**

As John Lennon once sung: "It's easy if you try".

Also, when I said "*You should know if you if you have installed any third party repos*", I meant that the only way you would have 3rd party repos on your system is if you added them yourself. Thus you would know if you have added any 3rd party repos or not.

---

### Post by kansasnoob on 2011-02-06
> **tommcd said:**
> Simply open a terminal and type: **cat /etc/apt/sources.list** And post the output here. NOTE: You may need to scroll up and down in order to post the whole output.

Also post the output of: **ls /etc/apt/sources.d/**

As John Lennon once sung: "It's easy if you try".

Also, when I said "*You should know if you if you have installed any third party repos*", I meant that the only way you would have 3rd party repos on your system is if you added them yourself. Thus you would know if you have added any 3rd party repos or not.

There is no need to mess around with software sources in this case. Anyone running Ubuntu desktop will get that error regarding "swfdec-mozilla". This is from my 10.10 desktop version:

```
lance@lance-desktop:~$ aptitude show swfdec-mozilla
Package: swfdec-mozilla                  
New: yes
State: not installed
Version: 0.8.8-5ubuntu1
Priority: extra
Section: universe/video
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 61.4k
**Depends: browser-plugin-gnash (= 0.8.8-5ubuntu1)**
Description: dummy package for transition to browser-plugin-gnash
 This package is a transitional package for upgrading to browser-plugin-gnash. 
 
 It can be safely removed when browser-plugin-gnash is installed.
Homepage: http://www.gnu.org/software/gnash/

lance@lance-desktop:~$ sudo apt-get install gnome
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnome : Depends: swfdec-mozilla but it is not going to be installed
E: Broken packages

```

---

### Post by tommcd on 2011-02-07
> **kansasnoob said:**
> There is no need to mess around with software sources in this case. Anyone running Ubuntu desktop will get that error regarding "swfdec-mozilla".
I just wanted to check if the OP had any 3rd party repos that may be causing dependency issues here. I have seen 3rd party repos cause problems like this before.

And thanks for the info about the problematic swfdec-mozilla package.

---

### Post by chris954 on 2012-09-10
Solved:

I had the same problem:
Ran command #sudo apt-get update
then ran #sudo apt-get upgrade
then ran #apt-get install gnome-desktop-environment

---

