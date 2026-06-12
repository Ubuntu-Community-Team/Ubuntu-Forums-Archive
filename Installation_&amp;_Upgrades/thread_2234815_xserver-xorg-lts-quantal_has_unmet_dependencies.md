---
title: "xserver-xorg-lts-quantal has unmet dependencies"
date: 2014-07-17
forum: Installation &amp; Upgrades
---

### Post by makkekkazzo on 2014-07-17
Hi,
I was trying to install the "new Hardware support" but it gave me an error about the unmet dependencies of the * **libgl1-mesa-dev-lts-quantal***   , the   ***libgl1-mesa-glx-lts-trusty***, the ***xserver-xorg-lts-trusty*** packages. While searching on internet I have found this solution that unfortunately gave me this output (sorry that the text is in german, it says that not alla dependecies are satisfied and that they would be in conflict with other packages if installed)

```
makkekkazzo@fra:~$ sudo apt-get install -V libglapi-mesa-lts-trusty libgl1-mesa-glx-lts-trusty xserver-xorg-lts-trusty xserver-xorg-input-all-lts-trusty xserver-xorg-video-all-lts-trusty libgl1-mesa-dri-lts-trusty x11-xserver-utils-lts-trusty mesa-vdpau-drivers-lts-trusty libgles2-mesa-lts-trusty libglapi-mesa-lts-trusty
[sudo] password for makkekkazzo: 
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Statusinformationen werden eingelesen... Fertig
Einige Pakete konnten nicht installiert werden. Das kann bedeuten, dass
Sie eine unmögliche Situation angefordert haben oder, wenn Sie die
Unstable-Distribution verwenden, dass einige erforderliche Pakete noch
nicht erstellt wurden oder Incoming noch nicht verlassen haben.
Die folgenden Informationen helfen Ihnen vielleicht, die Situation zu lösen:

Die folgenden Pakete haben unerfüllte Abhängigkeiten:
 libgl1-mesa-dev-lts-quantal : Hängt ab von: libgl1-mesa-glx-lts-quantal (= 9.1.6~precise~ppa1) soll aber nicht installiert werden
 libgl1-mesa-dri-lts-trusty : Kollidiert mit: xorg-renamed-package-lts-quantal
 libgl1-mesa-glx-lts-trusty : Kollidiert mit: xorg-renamed-package-lts-quantal
 libglapi-mesa-lts-trusty : Kollidiert mit: xorg-renamed-package-lts-quantal
 libgles2-mesa-lts-trusty : Kollidiert mit: xorg-renamed-package-lts-quantal
 mesa-vdpau-drivers-lts-trusty : Kollidiert mit: xorg-renamed-package-lts-quantal
 wine1.4 : Hängt ab von: wine1.4-amd64 (= 1.4-0ubuntu4.1) soll aber nicht installiert werden
           Hängt ab von: wine1.4-i386 (= 1.4-0ubuntu4.1)
 x11-xserver-utils-lts-trusty : Kollidiert mit: xorg-renamed-package-lts-quantal
 xserver-xorg-input-all-lts-trusty : Hängt ab von: xserver-xorg-input-evdev-lts-trusty soll aber nicht installiert werden
                                     Hängt ab von: xserver-xorg-input-synaptics-lts-trusty soll aber nicht installiert werden
                                     Hängt ab von: xserver-xorg-input-vmmouse-lts-trusty soll aber nicht installiert werden
                                     Hängt ab von: xserver-xorg-input-wacom-lts-trusty soll aber nicht installiert werden
 xserver-xorg-lts-trusty : Hängt ab von: xserver-xorg-core-lts-trusty (>= 2:1.11) soll aber nicht installiert werden
                           Hängt ab von: xserver-xorg-input-evdev-lts-trusty soll aber nicht installiert werden
                           Kollidiert mit: xorg-renamed-package-lts-quantal
 xserver-xorg-video-all-lts-trusty : Hängt ab von: xserver-xorg-video-ati-lts-trusty soll aber nicht installiert werden
                                     Hängt ab von: xserver-xorg-video-cirrus-lts-trusty soll aber nicht installiert werden
                                     Hängt ab von: xserver-xorg-video-fbdev-lts-trusty soll aber nicht installiert werden
                                     Hängt ab von: xserver-xorg-video-intel-lts-trusty soll aber nicht installiert werden
                                     Hängt ab von: xserver-xorg-video-mga-lts-trusty soll aber nicht installiert werden
                                     Hängt ab von: xserver-xorg-video-modesetting-lts-trusty soll aber nicht installiert werden
                                     Hängt ab von: xserver-xorg-video-neomagic-lts-trusty soll aber nicht installiert werden
                                     Hängt ab von: xserver-xorg-video-nouveau-lts-trusty soll aber nicht installiert werden
                                     Hängt ab von: xserver-xorg-video-openchrome-lts-trusty soll aber nicht installiert werden
                                     Hängt ab von: xserver-xorg-video-s3-lts-trusty soll aber nicht installiert werden
                                     Hängt ab von: xserver-xorg-video-savage-lts-trusty soll aber nicht installiert werden
                                     Hängt ab von: xserver-xorg-video-siliconmotion-lts-trusty soll aber nicht installiert werden
                                     Hängt ab von: xserver-xorg-video-sis-lts-trusty soll aber nicht installiert werden
                                     Hängt ab von: xserver-xorg-video-sisusb-lts-trusty soll aber nicht installiert werden
                                     Hängt ab von: xserver-xorg-video-tdfx-lts-trusty soll aber nicht installiert werden
                                     Hängt ab von: xserver-xorg-video-trident-lts-trusty soll aber nicht installiert werden
                                     Hängt ab von: xserver-xorg-video-vesa-lts-trusty soll aber nicht installiert werden
                                     Hängt ab von: xserver-xorg-video-vmware-lts-trusty soll aber nicht installiert werden
E: Fehler: Unterbrechungen durch pkgProblemResolver::Resolve hervorgerufen; dies könnte durch zurückgehaltene Pakete verursacht worden sein.
```

```
makkekkazzo@fra:~$ sudo apt-get install linux-generic-lts-quantal xserver-xorg-lts-quantal
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Statusinformationen werden eingelesen... Fertig
Einige Pakete konnten nicht installiert werden. Das kann bedeuten, dass
Sie eine unmögliche Situation angefordert haben oder, wenn Sie die
Unstable-Distribution verwenden, dass einige erforderliche Pakete noch
nicht erstellt wurden oder Incoming noch nicht verlassen haben.
Die folgenden Informationen helfen Ihnen vielleicht, die Situation zu lösen:

Die folgenden Pakete haben unerfüllte Abhängigkeiten:
 xserver-xorg-lts-quantal : Empfiehlt: libgl1-mesa-dri-lts-quantal soll aber nicht installiert werden
                            Empfiehlt: libgl1-mesa-glx-lts-quantal soll aber nicht installiert werden
                            Empfiehlt: xserver-xorg-video-all-lts-quantal soll aber nicht installiert werden
                            Kollidiert mit: libgl1-mesa-glx (>= 0~)
                            Kollidiert mit: libgl1-mesa-glx:i386 (>= 0~)
                            Kollidiert mit: libglapi-mesa (>= 0~)
                            Kollidiert mit: libglapi-mesa:i386 (>= 0~)
E: Probleme können nicht korrigiert werden, Sie haben zurückgehaltene defekte Pakete.


```

What do I have to do? Disinstall the packages that makes conflict and install the new ones?

I know that some other people are having problems with the New Hardware Support, but I haven't find any post or article that was talking about this specific problem.

Thanks

---

### Post by ajgreeny on 2014-07-17
That is because the quantal hardware support, along with quantal OS (12.10), has now lost support.

Why not try the trust hardware stack?  That is now, I believe the only one that retains support if running 12.04.

---

### Post by makkekkazzo on 2014-07-17
Thanks a lot, but can I ask you: how can I do that?

---

### Post by ajgreeny on 2014-07-17
have a look at [http://askubuntu.com/questions/493541/hardware-enablement-stack-hwe-out-of-support](http://askubuntu.com/questions/493541/hardware-enablement-stack-hwe-out-of-support) which has a lot of info about this, and a few possible problems that might appear as well.

I have just updated my system, running Xubuntu 12.04 64bit, updating to the trusty HWE by following Dogsbody's first answer, ie, installed xserver-xorg-lts-trusty and now I'm now running the OS with all the xorg and kernels from trusty.  Runs smooth as silk, just like it has since installing the OS.

---

### Post by makkekkazzo on 2014-07-18
Thanks again but, with both the solutions, it says that the they can't install ***libgl1-mesa-dri-lts-trusty*** because makes conflict with ***xorg-renamed-package-lts-raring ***(and this is only one of the conflicts that it's showing). How do I solve this conflict?

---

### Post by coffeecat on 2014-07-18
@makkekkazzo, it is not at all clear which release of Ubuntu you are running. So that we can be sure, please post the output of this terminal command:

```
 cat /etc/lsb-release
```

---

### Post by makkekkazzo on 2014-07-18
Oh sorry I thought that people more expert than me could have managed to figure the release from the previous outputs.

Here for you guys:
```
makkekkazzo@fra:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.4 LTS"
```

---

### Post by coffeecat on 2014-07-18
I'm sure we could, but your title misled some people into thinking that you were running an out of support version. It's best to be sure. Thanks. :)

---

### Post by makkekkazzo on 2014-07-19
Yours is for sure a good point. Sorry again for the confusion. Doctors, is there a solution for my problem?

---

