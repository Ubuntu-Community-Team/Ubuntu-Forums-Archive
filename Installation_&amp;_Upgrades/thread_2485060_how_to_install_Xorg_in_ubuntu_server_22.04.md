---
title: "how to install Xorg in ubuntu server 22.04"
date: 2023-03-18
forum: Installation &amp; Upgrades
---

### Post by joeythedream on 2023-03-18
Hiya, I am new in ubuntu

Just install an ubuntu server 22.04 on rpi4, not yet install any GUI/desktop, just need Xorg for realVNC and kstar for astrophotography.
There are few questions need your help.

1. Is Xorg a GUI ? in ubuntu, GUI = desktop?
2. how to install Xorg in ssh? there are some program on internet related Xorg, such as : X11-common, Xorg-core or Xorg-source etc, what is the different between them , any webpage can tell ?
3. after installation, how to startup and get into GUI ? I need to install realVNC server later.

Thanks.

---

### Post by MAFoElffen on 2023-03-19
Xorg XServer (X11) is a graphics engine for the Linuux Graphics Layer. There are other pieces needed if you want a Desktop.

Let me ask you, are you going to remote in with SSH and use XForwarding to run your application or connect to the machines Desktop through VNC? Sounds like connecting with VNC, so there will be a few more pieces to add.

Have you used a Linux Desktop? Do you have a preference in any Desktop Environment? With VNC, with a Lightweight Desktop, it might perform a bit better with less lag. Might I suggest LXDE or LXQT?

For the process... If you install a DE (desktop Environment, then it will install Xorg XServer and a DM (Desktop manager, also call the Graphical Login Manager) and the Desktop... Then you install the VNC Server, with will be configure to run with that DE. That it the logical steps for that.

Let me get some feedback, and if you have any questions about that... Then I will go on.

---

### Post by joeythedream on 2023-03-19
[COLOR=#000000]Huya Elffen, thanks for your reply. I am new in Ubuntu, with some experienced on Raspbian.

My project is "setup an remote observatory astrophotography system" in my backyard.
that is:
" a set of astrophotographers-equipment connected to and controlled by a rpi4B with ubuntu server" which located in the yard and
" the rpi4 will be remotely controlled by a window-based laptop" which located in the house.
(as you know, you can stay outdoor for few hours especially in winter)

I read some related webpage and get some idea but with more questions in all aspect. Anyway, let me directly state my questions about ubuntu.

1. VNC is preferred for remotely controlling the rpi4B in ubuntu server with desktop environment, and as you said: light weight is preferred
(I tried to check which DE is preferred for INDI/Kstar/EKOS, the software will be installed for controlling the astrophotographers-equipments, but it seem to be okay for all DE)

2. Is tigervnc server pre-installed in ubuntu server 22.04 ? Can I connected the tigervnc server in rpi4 by a realvnc viewer on my laptop ? As used realvnc for few years, I prefer use realvnc and not to install others in my laptop or other system I have. Would you also tell me the procedure for installing DE ?
(right now I still installed the server 22.04 and can controlled it by window laptop thru' putty in ssh shell, no DE right now) 

3. Although I will use VNC session at the end, I still want to know more knowledge and skill about X-forward and X-server. Do you think I can install Xorg in the same rpi4B and try to use it.
 
I got some information from a very useful YouTube linked :
[/COLOR]https://www.youtube.com/watch?v=VjhPxPuQsDc&t=90s

in 2:00, there is a flow chart about the connection related what I mentioned above.

---

### Post by MAFoElffen on 2023-03-19
I saw that it first discussed using XServer installed and making the connection via ssh and XForwarding. Then the video went to a different config, using VNC and connecting to ta Desktop (DE). (Those are two different things.)

What will be your OS and machine in your house that you will be connecting from?

---

### Post by MAFoElffen on 2023-03-19
As a start... In the first methos (Install xorg-server) and using a ssh connection using XForwarding... Assuming that your local host is Linux...

For the remote RaspPi
```

sudo apt install openssh-server

```
Generate ssh keys on the local and send them to your remote
```

ssh-keygen -t rsa 
ssh-copy-id username@remote_host

```
Then install Xorg-xserver
```

sudo apt install -y xorg xinit

```
Install the application on your RaspPi...

Start it remotely from your local Linux host, through a ssh connection
```

ssh -X application_name

```
It will run on the local Linux Host's Desktop...

---

### Post by joeythedream on 2023-03-21
Thanks Elffen
I really think that X-server and X-forward is originally designed for remote control between unix-GUI system. Am I correct ?

Anyway, I will use another rpi to try the Xorg.

Besides, back to the astrophotography project, I will use a window11 base Dell laptop as my input-end at indoor.
(somehow after everything stable, I will try all set in the outdoor dark-sky carpark and I will stay inside the car with my Dell laptop.)

waiting for your reply about real VNC installation in rpi4 ubuntu server 22.04 which DE is not yet installed.

Thanks.

---

### Post by ActionParsnip on 2023-03-21
What are you wanting to do on the remote system that needs the full desktop session? There may be a sleeker solution to what you want to do

---

### Post by MAFoElffen on 2023-03-21
@ActionParsnip --
[quote=joeythedream]My project is "setup an remote observatory astrophotography system"[/quote]
```

- Kstars/Ekos Remote to Raspberry Pi 4   
- Using ssh X-Forwarding   
- Using VNC Client Connection

```
RE: [https://www.youtube.com/watch?v=VjhPxPuQsDc&t=90s](https://www.youtube.com/watch?v=VjhPxPuQsDc&t=90s)

Connection: 
- Local: Windows Laptop
- Remote: RaspPi, which is currently running Ubuntu Server.

@joeythedream

What would be cleaner than trying to use VNCserver/VNC Client, would be to Use the RDP client that is already installed within in Windows, and install xrdp server to your RaspPi, I would install a light Desktop to the RasPi, such as LXDE.

Decide just what you want to install to your RaspPi. The basic desktop (LXDE or LXQT) or the whole Desktop suite with Applications... I prefer to go with basic, then add things as I need them.
```
 
sudo apt install lxde lightdm
sudo apt install xrdp

```
RE: [https://tecadmin.net/how-to-install-xrdp-on-ubuntu-20-04/](https://tecadmin.net/how-to-install-xrdp-on-ubuntu-20-04/) 

Follow the part about installing and configuring xrdp. Just note that RDP protocol only allows one username to be logged into the system at a time.

---

### Post by TheFu on 2023-03-21
I wouldn't use VNC.  I'd use x2go.  Windows as an x2goclient, so that works.  On the remote system, install ssh, fail2ban and x2goserver.
That should be it.  On the remote system, a light DE/WM would be best.  Ubuntu Server doesn't have any GUI, so if you install **openbox**, you'll get a light WM and it will pull in the minimal xorg stuff.

In the x2goclient on Windows, the session area, choose "openbox" and try a connection.
In theory, should be easy-peasy.

x2go is an implementation of the NX protocol. This is a highly optimized version of VNC over ssh tunnels.  Typically, it feels 2-3x faster than any VNC or RDP.  It is certainly more secure, since SSH authentication is used. If ssh-keys are exchanged, Win10/11 support that almost like normal Unix systems do, then the connection authentication can be even more secure.

Interesting project. Alas, my back yard is full of trees, so only about 10° circle straight up can be seen.  The front-yard has too much light pollution from neighbors and the street lights on all night.  Good for security, bad for seeing.

---

### Post by joeythedream on 2023-03-23
> **ActionParsnip said:**
> What are you wanting to do on the remote system that needs the full desktop session? There may be a sleeker solution to what you want to do


Hiya, I am going to setup "a remote controlled astrophotography system by rpi4+ubuntuServer" which will be used outdoor for hold night, and
it will be directly controlled window laptop indoor.

There will be no keyboard, no monitor and no mouse for the outdoor rpi4. So I think full control will be good for it.

---

### Post by TheFu on 2023-03-23
> **joeythedream said:**
>  So I think full control will be good for it.

A full remote desktop has lots of overhead, so it should be the last choice.  But if you only have MS-Windows as the client, your choices are greatly limited.

OTOH, if you have a Linux/Unix workstation (even anyother r-pi), then all sorts of easier options become possible.

Most GUI programs can be run on a remote system, but have the window displayed locally.  This is using something called X11/Forwarding and it goes through an ssh tunnel.  Using ssh makes it more secure and much more convenient because ssh will set the X/Windows settings correctly in an automatic way.

For example, I run Thunderbird on a different system than the one I'm sitting at.  A simple way to do it is
```
ssh -X  deneb /usr/bin/thunderbird $TB_OPTS $@ &
```
where "deneb" is the DNS name of the remote system.  On the same LAN, it behaves just like being on the same machine.  Each remote window run shows up and completely integrates with the local desktop, just like any locally run program.  It has been working this way about 30 yrs. Well proven.

---

### Post by MAFoElffen on 2023-03-23
He wants to install from the Universe Repo, and run this remotely:
```

mafoelffen@Mikes-ThinkPad-T520:~/Scripts$ apt-cache show kstars
Package: kstars
Architecture: amd64
Version: 5:3.5.7-1ubuntu0.1
Priority: optional
Section: universe/science
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian KDE Extras Team <pkg-kde-extras@lists.alioth.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 15621
Depends: kstars-data (= 5:3.5.7-1ubuntu0.1), libqt5sql5-sqlite, kio, libc6 (>= 2.35), libcfitsio9 (>= 3.480~), libgcc-s1 (>= 4.0), libgsl27 (>= 2.7.1), libkf5configcore5 (>= 5.44.0~), libkf5configgui5 (>= 5.44.0~), libkf5configwidgets5 (>= 4.98.0), libkf5coreaddons5 (>= 4.100.0), libkf5crash5 (>= 5.44.0~), libkf5i18n5 (>= 5.44.0~), libkf5kiocore5 (>= 5.44.0~), libkf5kiowidgets5 (>= 5.44.0~), libkf5newstuff5 (>= 5.44.0~), libkf5notifications5 (>= 5.44.0~), libkf5notifyconfig5 (>= 5.44.0~), libkf5plotting5 (>= 5.44.0~), libkf5widgetsaddons5 (>= 5.44.0~), libkf5xmlgui5 (>= 5.44.0~), libqt5concurrent5 (>= 5.9.0~), libqt5core5a (>= 5.15.1), libqt5dbus5 (>= 5.14.1), libqt5gui5 (>= 5.14.1) | libqt5gui5-gles (>= 5.14.1), libqt5keychain1 (>= 0.7.0), libqt5network5 (>= 5.15.1), libqt5printsupport5 (>= 5.9.0~), libqt5qml5 (>= 5.9.0~), libqt5quick5 (>= 5.9.0~) | libqt5quick5-gles (>= 5.9.0~), libqt5sql5 (>= 5.9.0~), libqt5svg5 (>= 5.9.0~), libqt5websockets5 (>= 5.9.0~), libqt5widgets5 (>= 5.14.1), libraw20 (>= 0.19.0), libstdc++6 (>= 11), libstellarsolver1 (>= 1.9), libwcs7 (>= 4.8.2), zlib1g (>= 1:1.1.4)
Recommends: astrometry.net, indi-bin, xplanet
Suggests: khelpcenter, konqueror
Filename: pool/universe/k/kstars/kstars_3.5.7-1ubuntu0.1_amd64.deb
Size: 5513090
MD5sum: 928fa37081950e4fb0a8ee84301a1f0d
SHA1: f22236a1eb3818ad1a9582d6164d5bbbe7e4525f
SHA256: f69e9cdf7fc54378a89f1d3504f8a34df856b83cc1c376d0949f39973aa029b7
SHA512: f40ddfd5832426d5aee73b6da83d5a08106d32095138f2ae57ff2a208ef3959cedc832a863008a70ea2765a117cc2088eaa1e155df792c349e2d9a192bf333e8
Homepage: https://edu.kde.org/kstars/
Description-en: desktop planetarium, observation planning and telescope control
 KStars is a scientifically accurate desktop planetarium, visualising a
 graphical simulation of the night sky from any location on Earth, at any date
 and time.
 The display includes 130,000 stars, 13,000 deep-sky objects, all 8 planets,
 the Sun and Moon, and thousands of comets and asteroids. KStars addresses
 students and amateur astronomers of all levels.
 .
 The database of known objects can be extended and updated from local or
 remote databases, which is prepared for in a user-extendable interface.
 KStars suggests observations of particular interest like conjunctions
 with respect to the location of the user. And for user-selected targets it
 proposes the ones that are best-observable.
 .
 The software may be used for planning experiments around the globe,
 e.g. for remote controlled commercial services. But KStars also
 features an INDI interface to control local telescopes and cameras.
 Users with programming experience can script it via the KDE desktop bus.
Description-md5: f683107e014c6cad80de4fa829c4e841

```
You can see, that deb package was written for KDE (Original-Maintainer: Debian KDE Extras Team), so it's going to pull in a myriad of KDE specific depends...

If think doing that will be the easy part... That will be okay from just your back yard. I have run my RaspPi from a Phone PowerPack to the USB C power port... As long as your WiFi access point has the range to your backyard to enable a good connection between.

The further challenge will be to be able to run it in a parking lot, away from your home, as you mentioned in a post. There, you are going to need an ADHOC WiFi network in able to connect the RaspPi and your Laptop. I do that away from my home from my smartphone.

---

### Post by joeythedream on 2023-03-27
Hiya Elffen

wonderful, I can remotely use LXDE on ubuntu server thru' my windows 11 home edition now. Thank you very much



> **MAFoElffen said:**
> @ActionParsnip --

```

- Kstars/Ekos Remote to Raspberry Pi 4   
- Using ssh X-Forwarding   
- Using VNC Client Connection

```
RE: [https://www.youtube.com/watch?v=VjhPxPuQsDc&t=90s](https://www.youtube.com/watch?v=VjhPxPuQsDc&t=90s)

Connection: 
- Local: Windows Laptop
- Remote: RaspPi, which is currently running Ubuntu Server.

@joeythedream

What would be cleaner than trying to use VNCserver/VNC Client, would be to Use the RDP client that is already installed within in Windows, and install xrdp server to your RaspPi, I would install a light Desktop to the RasPi, such as LXDE.

Decide just what you want to install to your RaspPi. The basic desktop (LXDE or LXQT) or the whole Desktop suite with Applications... I prefer to go with basic, then add things as I need them.
```
 
sudo apt install lxde lightdm
sudo apt install xrdp

```
RE: [https://tecadmin.net/how-to-install-xrdp-on-ubuntu-20-04/](https://tecadmin.net/how-to-install-xrdp-on-ubuntu-20-04/) 

Follow the part about installing and configuring xrdp. Just note that RDP protocol only allows one username to be logged into the system at a time.

---

### Post by joeythedream on 2023-03-27
Hi Fu

Thanks for your advice and it's very attractive: 2-3x faster than RDP.

However, I am a quiet new user in linux and with some experience in ssh and realvnc only. Now I have just successfully installed XRDP. Surely later after I run thru all other installation, I will try x2go.

Thanks your advice and nice to meet you here.

> **TheFu said:**
> I wouldn't use VNC.  I'd use x2go.  Windows as an x2goclient, so that works.  On the remote system, install ssh, fail2ban and x2goserver.
That should be it.  On the remote system, a light DE/WM would be best.  Ubuntu Server doesn't have any GUI, so if you install **openbox**, you'll get a light WM and it will pull in the minimal xorg stuff.

In the x2goclient on Windows, the session area, choose "openbox" and try a connection.
In theory, should be easy-peasy.

x2go is an implementation of the NX protocol. This is a highly optimized version of VNC over ssh tunnels.  Typically, it feels 2-3x faster than any VNC or RDP.  It is certainly more secure, since SSH authentication is used. If ssh-keys are exchanged, Win10/11 support that almost like normal Unix systems do, then the connection authentication can be even more secure.

Interesting project. Alas, my back yard is full of trees, so only about 10° circle straight up can be seen.  The front-yard has too much light pollution from neighbors and the street lights on all night.  Good for security, bad for seeing.

---

### Post by joeythedream on 2023-03-27
Hi Elffen, you are right, after trial and practice well in back yard with a portable wifi and battery, all will backup in my car boot and go a carpark with dark sky.

Thanks now I can remotely full control my rpi4B, now astrophoto software and hardware will try to setup.

I feel a little bit excited now.

Thanks for your help

> **MAFoElffen said:**
> He wants to install from the Universe Repo, and run this remotely:
```

mafoelffen@Mikes-ThinkPad-T520:~/Scripts$ apt-cache show kstars
Package: kstars
Architecture: amd64
Version: 5:3.5.7-1ubuntu0.1
Priority: optional
Section: universe/science
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian KDE Extras Team <pkg-kde-extras@lists.alioth.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 15621
Depends: kstars-data (= 5:3.5.7-1ubuntu0.1), libqt5sql5-sqlite, kio, libc6 (>= 2.35), libcfitsio9 (>= 3.480~), libgcc-s1 (>= 4.0), libgsl27 (>= 2.7.1), libkf5configcore5 (>= 5.44.0~), libkf5configgui5 (>= 5.44.0~), libkf5configwidgets5 (>= 4.98.0), libkf5coreaddons5 (>= 4.100.0), libkf5crash5 (>= 5.44.0~), libkf5i18n5 (>= 5.44.0~), libkf5kiocore5 (>= 5.44.0~), libkf5kiowidgets5 (>= 5.44.0~), libkf5newstuff5 (>= 5.44.0~), libkf5notifications5 (>= 5.44.0~), libkf5notifyconfig5 (>= 5.44.0~), libkf5plotting5 (>= 5.44.0~), libkf5widgetsaddons5 (>= 5.44.0~), libkf5xmlgui5 (>= 5.44.0~), libqt5concurrent5 (>= 5.9.0~), libqt5core5a (>= 5.15.1), libqt5dbus5 (>= 5.14.1), libqt5gui5 (>= 5.14.1) | libqt5gui5-gles (>= 5.14.1), libqt5keychain1 (>= 0.7.0), libqt5network5 (>= 5.15.1), libqt5printsupport5 (>= 5.9.0~), libqt5qml5 (>= 5.9.0~), libqt5quick5 (>= 5.9.0~) | libqt5quick5-gles (>= 5.9.0~), libqt5sql5 (>= 5.9.0~), libqt5svg5 (>= 5.9.0~), libqt5websockets5 (>= 5.9.0~), libqt5widgets5 (>= 5.14.1), libraw20 (>= 0.19.0), libstdc++6 (>= 11), libstellarsolver1 (>= 1.9), libwcs7 (>= 4.8.2), zlib1g (>= 1:1.1.4)
Recommends: astrometry.net, indi-bin, xplanet
Suggests: khelpcenter, konqueror
Filename: pool/universe/k/kstars/kstars_3.5.7-1ubuntu0.1_amd64.deb
Size: 5513090
MD5sum: 928fa37081950e4fb0a8ee84301a1f0d
SHA1: f22236a1eb3818ad1a9582d6164d5bbbe7e4525f
SHA256: f69e9cdf7fc54378a89f1d3504f8a34df856b83cc1c376d0949f39973aa029b7
SHA512: f40ddfd5832426d5aee73b6da83d5a08106d32095138f2ae57ff2a208ef3959cedc832a863008a70ea2765a117cc2088eaa1e155df792c349e2d9a192bf333e8
Homepage: https://edu.kde.org/kstars/
Description-en: desktop planetarium, observation planning and telescope control
 KStars is a scientifically accurate desktop planetarium, visualising a
 graphical simulation of the night sky from any location on Earth, at any date
 and time.
 The display includes 130,000 stars, 13,000 deep-sky objects, all 8 planets,
 the Sun and Moon, and thousands of comets and asteroids. KStars addresses
 students and amateur astronomers of all levels.
 .
 The database of known objects can be extended and updated from local or
 remote databases, which is prepared for in a user-extendable interface.
 KStars suggests observations of particular interest like conjunctions
 with respect to the location of the user. And for user-selected targets it
 proposes the ones that are best-observable.
 .
 The software may be used for planning experiments around the globe,
 e.g. for remote controlled commercial services. But KStars also
 features an INDI interface to control local telescopes and cameras.
 Users with programming experience can script it via the KDE desktop bus.
Description-md5: f683107e014c6cad80de4fa829c4e841

```
You can see, that deb package was written for KDE (Original-Maintainer: Debian KDE Extras Team), so it's going to pull in a myriad of KDE specific depends...

If think doing that will be the easy part... That will be okay from just your back yard. I have run my RaspPi from a Phone PowerPack to the USB C power port... As long as your WiFi access point has the range to your backyard to enable a good connection between.

The further challenge will be to be able to run it in a parking lot, away from your home, as you mentioned in a post. There, you are going to need an ADHOC WiFi network in able to connect the RaspPi and your Laptop. I do that away from my home from my smartphone.

---

