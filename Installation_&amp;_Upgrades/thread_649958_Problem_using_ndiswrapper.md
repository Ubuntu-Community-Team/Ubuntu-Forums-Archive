---
title: "Problem using ndiswrapper"
date: 2007-12-25
forum: Installation &amp; Upgrades
---

### Post by TheUngodlySpoon on 2007-12-25
Hi everyone, I'm new to the forums and Linux in general so please be patient with my lack of experience as I don't know a lot of advanced features and commands yet.

So my trouble is that I'm trying to get my wireless card working by using ndiswrapper on the windows driver file I pulled out of my 'Drivers' folder in Windows.  The problem is that after I used:

sudo apt-get install ndiswrapper-common
  and everything ran and seemed to install properly, when I type ndiswrapper i get the following error:

error: no ndiswrapper utils found!

I'm using Gutsy Gibbon on my HP pavilion dv9000 widescreen laptop with Vista preinstalled

Can anyone help me out with how to get ndiswrapper working properly or direct me to a site in which this same problem is addressed? I looked around but couldn't find anything useful.  Thanks a lot!

---

### Post by Pumalite on 2007-12-25
It might be here:
[http://ubuntuforums.org/showthread.php?t=431815](http://ubuntuforums.org/showthread.php?t=431815)
[http://ubuntuforums.org/showthread.php?t=582220](http://ubuntuforums.org/showthread.php?t=582220)

---

### Post by Partyboi2 on 2007-12-25
> **TheUngodlySpoon said:**
> Hi everyone, I'm new to the forums and Linux in general so please be patient with my lack of experience as I don't know a lot of advanced features and commands yet.

So my trouble is that I'm trying to get my wireless card working by using ndiswrapper on the windows driver file I pulled out of my 'Drivers' folder in Windows.  The problem is that after I used:

sudo apt-get install ndiswrapper-common
  and everything ran and seemed to install properly, when I type ndiswrapper i get the following error:

error: no ndiswrapper utils found!

I'm using Gutsy Gibbon on my HP pavilion dv9000 widescreen laptop with Vista preinstalled

Can anyone help me out with how to get ndiswrapper working properly or direct me to a site in which this same problem is addressed? I looked around but couldn't find anything useful.  Thanks a lot!
You have installed ndiswrapper-common but looks like you need to install
ndiswrapper-utils package
```
sudo apt-get install ndiswrapper-utils
```

---

### Post by mun3kh on 2008-05-26
Currently with Gutsy you have to use:
```

sudo apt-get install ndiswrapper-utils-1.9

```

Don't know why they've put the version number in the package name, had to go to a system I'd already used ndiswrapper on to find this out.

---

