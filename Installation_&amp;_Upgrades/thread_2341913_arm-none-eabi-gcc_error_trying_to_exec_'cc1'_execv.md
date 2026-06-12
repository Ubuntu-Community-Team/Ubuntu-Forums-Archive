---
title: "arm-none-eabi-gcc: error trying to exec 'cc1': execvp: No such file or directory"
date: 2016-11-02
forum: Installation &amp; Upgrades
---

### Post by sigfriedar1 on 2016-11-02
Hello guys,

This is my very first post in the forum because I cannot solve a bug  for many days. So basically, I am trying to use a new sensor ([https://github.com/hikob/openlab/wiki/Installation](https://github.com/hikob/openlab/wiki/Installation)) and for that I needed to install openlab (for the sensors), openocd and arm-none-eabi-gcc. I have the latest version of Ubuntu 

So everything was correct until I tried to compile my code, and then I got this 

```
$ make test_leds
[  4%] Building C object periph/CMakeFiles/lsm303dlhc.dir/lsm303dlhc/lsm303dlhc.c.o
arm-none-eabi-gcc: error trying to exec 'cc1': execvp: No such file or directory
periph/CMakeFiles/lsm303dlhc.dir/build.make:62 : la recette pour la cible « periph/CMakeFiles/lsm303dlhc.dir/lsm303dlhc/lsm303dlhc.c.o » a échouée
make[3]: *** [periph/CMakeFiles/lsm303dlhc.dir/lsm303dlhc/lsm303dlhc.c.o] Erreur 1
CMakeFiles/Makefile2:2345 : la recette pour la cible « periph/CMakeFiles/lsm303dlhc.dir/all » a échouée
make[2]: *** [periph/CMakeFiles/lsm303dlhc.dir/all] Erreur 2
CMakeFiles/Makefile2:3307 : la recette pour la cible « appli/tests/drivers/CMakeFiles/test_leds.dir/rule » a échouée
make[1]: *** [appli/tests/drivers/CMakeFiles/test_leds.dir/rule] Erreur 2
Makefile:1169 : la recette pour la cible « test_leds » a échouée
make: *** [test_leds] Erreur 2
```

So, I read many forums and try to install, reinstall and nothing happens, someone told me that it could be a problem of versions with gcc and arm-none-eabi-gcc. So I did the following: 

```

$ arm-none-eabi-gcc -print-progname=cc1
bash: /home/me/Documents/gcc-arm-none-eabi-5_4-2016q3/bin/arm-none-eabi-gcc: Aucun fichier ou dossier de ce type
```

This means that cc1 is not in this package, which is the one I trying to use, but normally it should be there. Then, I find the many versions I had in my PC

```
$ dpkg -l | grep '\<gcc'
ii  gcc                                        4:5.3.1-1ubuntu1                                            amd64        GNU C compiler
ii  gcc-5                                      5.4.0-6ubuntu1~16.04.2                                      amd64        GNU C compiler
ii  gcc-5-base:amd64                           5.4.0-6ubuntu1~16.04.2                                      amd64        GCC, the GNU Compiler Collection (base package)
ii  gcc-6-base:amd64                           6.0.1-0ubuntu1                                              amd64        GCC, the GNU Compiler Collection (base package)
ii  gcc-arm-none-eabi                          15:4.9.3+svn231177-1                                        amd64        GCC cross compiler for ARM Cortex-A/R/M processors
ii  gir1.2-packagekitglib-1.0                  0.8.17-4ubuntu6~gcc5.4ubuntu1.1                             amd64        GObject introspection data for the PackageKit GLib library
ii  libcaca0:amd64                             0.99.beta19-2build2~gcc5.2                                  amd64        colour ASCII art library
ii  libpackagekit-glib2-16:amd64               0.8.17-4ubuntu6~gcc5.4ubuntu1.1                             amd64        Library for accessing PackageKit using GLib
ii  libunity-action-qt1:amd64                  1.1.0+14.04.20140304-0ubuntu2~gcc5.1                        amd64        Unity Action Qt API
ii  libwebrtc-audio-processing-0:amd64         0.1-3ubuntu1~gcc5.1                                         amd64        AudioProcessing module from the WebRTC project.
ii  qtchooser                                  52-gae5eeef-2build1~gcc5.2                                  amd64        Wrapper to select between Qt development binary versions
ii  qtdeclarative5-unity-action-plugin:amd64   1.1.0+14.04.20140304-0ubuntu2~gcc5.1                        amd64        Unity Action QML Components
```


Right now, I don't know what to do, I am very confused with this issue, does anybody can help me to solve this problem ? Thank you

---

