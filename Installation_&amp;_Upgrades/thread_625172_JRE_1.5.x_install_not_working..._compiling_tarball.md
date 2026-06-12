---
title: "JRE 1.5.x install not working... compiling tarballs is hard!"
date: 2007-11-27
forum: Installation &amp; Upgrades
---

### Post by konungursvia on 2007-11-27
I have 1.4.x but need 1.5.x for Frostwire to work. The repos don't have it but sun.com does. When you download the rpm.bin, (I have alien), you have to move it and run an install command. This mystifies me even as an intermediate user.

All the documentation on such non-deb non-repo installations is brief and assumes the user understands where to unpack and why. I can't find any lesson on the why's and wherefores about where to install such things. 

In short, I have JRE 1.5.x downloaded, but both times I tried to install it, one in home and the other in /etc/share/, it failed and I still cannot run Frostwire. 

Does anyone know where I should turn for better instructions? I thought I followed Sun's instructions to the letter, but no dice.

Thanks for any suggestions you may have.

---

### Post by rsambuca on 2007-11-27
You are mistaken.  Sun java is in the multiverse Repos.  Just ensure your multiverse repos are enabled, and you can either install them using Synaptic or via the command line.```
sudo apt-get install sun-java5-bin sun-java5-jre
```If you want java, plus codecs, etc., you can just run this command```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by konungursvia on 2007-11-27
I have multiverse and java5, but still get the error message:

peter@dual-core:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
1.4.2-02
OOPS, your java version is too old [java = 1.4.2-02]
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ror message:

---

### Post by rsambuca on 2007-11-27
Are you using 64bit Ubuntu?  If so, then you need to install the ia32 version.```
sudo apt-get install ia32-sun-java6-bin
```then```
sudo update-alternatives --config java
```

---

### Post by konungursvia on 2007-11-27
Thanks so much, that worked. Frostwire launches well now. The thing is, java doesn't work in FF, despite being installed as mozilla-plugin and enabled.

---

### Post by rsambuca on 2007-11-27
There is no sun Java plugin for 64bit Firefox.  If you need a java plugin for your browser, then you can try blackdown java, which has security issues, Icedtea java, which works sometimes, sometimes not, or install the 32bit browser and plugins.  I recommend the latter.

---

### Post by konungursvia on 2007-11-28
Ah, thanks.

---

