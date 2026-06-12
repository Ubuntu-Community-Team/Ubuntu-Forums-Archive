---
title: "dependency issues with Wireshark installation"
date: 2011-11-12
forum: Installation &amp; Upgrades
---

### Post by 1liest on 2011-11-12
hi,

Im trying to install wireshark in my xubuntu system. I was able to resolve most of the dependency issues, but when I try to install freetype2 it keeps throwing up libc6 dependency. 

I have already installed both libc6 and libc6-dev packages which where required for atk package installation. Atk detected the above packages and was successfully installed. 

But for some reason FreeType2 doesnt detect libc6. Could some one tell me whats happening?

Thanks

---

### Post by Toz on 2011-11-12
Hello and welcome to the forums.

Which version of Xubuntu are you using? And how are you trying to install wireshark (from the repositories or compiling from source)?

---

### Post by MAFoElffen on 2011-11-12
> **1liest said:**
> hi,

Im trying to install wireshark in my xubuntu system. I was able to resolve most of the dependency issues, but when I try to install freetype2 it keeps throwing up libc6 dependency. 

I have already installed both libc6 and libc6-dev packages which where required for atk package installation. Atk detected the above packages and was successfully installed. 

But for some reason FreeType2 doesnt detect libc6. Could some one tell me whats happening?

Thanks
I have it installed and working on Ubuntu:

Wireshark version 1.4.6-2

Depends:
lib6(>=2.7)
libgdk-pixbuf2.0-0 (>=2.22.0)
libglib2.0-0 (>=2.24.0)
libgtk2.0.0 (>=2.12.0)
libpango1.0-0 (>=1.14.0)
libcap0.8 (>=0.9.8 )
libportaudio2 (>=19+svn20111113)
libwireshark0 (>=1.4.2-1)
libwiretap0
libwsutil0
zlib1g (>=1:1.1.4)
wireshark-common

Dependants:
wireshark-dbg
wireshark-common
python-scapy
chaos-reader
bittwist

Hope that helps.  Your know there is swicthes with apt-get and aptitude that will intelligently work out dependencies and such, right?  Although the --full-resolver option is a last ditch option as it will remove other packages to work out the dependency... --safe-resolver is better.

---

### Post by raja.genupula on 2011-11-13
do this again 
 i mean type the command to install what ever you want.
```
sudo apt-get install <app>
```

then its shows the dependencies erros right then use 

```
sudo apt-get install -f
```

all the best.

---

### Post by MAFoElffen on 2011-11-13
> **raja.genupula said:**
> ```
sudo apt-get install -f
```all the best.
@raja

Pop up a terminal session and try that command on yours... The Man page says -f is an option, but it stopped working 3 weeks ago... For me and others it throws an error of unknown option, then prints the help page with that option as one of the options.

---

