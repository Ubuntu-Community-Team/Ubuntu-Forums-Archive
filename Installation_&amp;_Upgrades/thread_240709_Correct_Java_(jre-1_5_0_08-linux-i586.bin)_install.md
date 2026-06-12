---
title: "Correct Java (jre-1_5_0_08-linux-i586.bin) installation - ?"
date: 2006-08-21
forum: Installation &amp; Upgrades
---

### Post by GSMD on 2006-08-21
Though it seems pretty obvious, I couldnt find the right HOW-TO.

What I want is to install Java from scratch, not from packages, and make all programs that need Java refer to it.

Could anyone please provide me with the sequence of operations please?

Thanks.

---

### Post by Dinerty on 2006-08-21
**Originally created by **Artificial Intelligance**
**Slightly modified to adapt to the new version


If you want the latest version:

Download Java Runtime Environment (JRE) 5.0 Update 8: [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp) pick Linux self-extracting file. Download it to your Desktop.

```
cd Desktop
sudo apt-get install build-essential
sudo apt-get install fakeroot java-package java-common
fakeroot make-jpkg jre-1_5_0_08-linux-i586.bin
sudo dpkg -i sun-j2re1.5_1.5.0+update08_i386.deb
sudo update-alternatives --config java
```

When asking for which version you want to choose pick;

```
3        /usr/lib/j2sdk1.5-sun/bin/java
```

Testing;

```
java -version
```

Making a Launcher for Java Control Center;
```

sudo gedit /usr/share/applications/java.desktop
```

fill in;

[Desktop Entry]
Name=Java Control Center
Comment=Java Options & Configuration.
Exec=sh /usr/lib/j2re1.5-sun/bin/ControlPanel
Icon=
Terminal=false
Type=Application
Categories=Application;System;

Save and exit.
You can find it now under Applications tab ---> System Tools.

---

### Post by alynx on 2006-08-21
when i try to 

```

fakeroot make-jpkg *java.bin* 
```

i get this error

```
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk.sh

No matching plugin was found.

```

And i cant get it to turn into a java package

Please help

---

### Post by avtolle on 2006-08-21
Sorry; need to learn to read everything before jumping in.:(

---

### Post by alynx on 2006-08-22
I cant seem to find the plugins listed above in repos , so does anyone experience a simmilar problem? Or know how to fix it ?

---

