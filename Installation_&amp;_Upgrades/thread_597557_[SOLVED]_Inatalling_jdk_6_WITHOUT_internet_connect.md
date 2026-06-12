---
title: "[SOLVED] Inatalling jdk 6 WITHOUT internet connection"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by lenB on 2007-10-30
Hi there..

I am desperately trying to install jdk 6 on my new Ubuntu Gutsy. I have tried installing the .bin file, but then the computer doesn't recognize it.. I am a developer so I run alot of applications and applets depending on it. So I got myself all the .deb packages. Problem is:

The jdk-bin depends on the JRE
and JRE depends on jdk-bin

Is there a workaround??

---

### Post by taurus on 2007-10-30
What do you mean it didn't recognize the version that you installed by hand?  You just need to configure it, telling the system to use it.

```
sudo update-alternatives --config java
```
And pick the latest version from the list.

---

### Post by lenB on 2007-10-31
I tried that command, but it didn't display my newly installed version, only some gcj or something..

---

### Post by taurus on 2007-10-31
Do you remember where you installed the latest version of java?  If not sure, post the output of this command here.

```
sudo find / -name java -print
```

p.s.  Or have you actually already installed the .bin by hand?

---

### Post by lenB on 2007-11-01
Thanx for your help, taurus..

I resolved the issue in the following way:

1.) Downloaded all the needed .deb packages (jre, jdk, bin)
2.) Created a CD with AptOnCD
3.) Added the CD to Synaptic
4.) Installed the jdk from there

:)

---

