---
title: "sub-process /usr/bin/dpkg returned an error code (1)"
date: 2007-08-06
forum: Installation &amp; Upgrades
---

### Post by steel_lady on 2007-08-06
I am getting this all the time, I have read all previous posts about this problem but I didn't know how to get rid of it. I am getting an error when I try to install any program or update. I tried to update to tje new version of ubuntu but it didn't let me either. It seems to me that I also have some network firewall problem. The error example when I am updating is here:

[http://i10.tinypic.com/4zyhhd2](http://i10.tinypic.com/4zyhhd2)

Please help!!!

---

### Post by Seisen on 2007-08-06
Try this

```
sudo dpkg --configure -a 
sudo apt-get -f install
```

---

### Post by steel_lady on 2007-08-06
> **Seisen said:**
> Try this

```
sudo dpkg --configure -a 
sudo apt-get -f install
```

it gives me again:

Setting up linux-igd (0.cvs20060201-1) ...
External interface not specified in /etc/default/upnpd
invoke-rc.d: initscript upnpd, action "start" failed.
dpkg: error processing linux-igd (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-igd

---

### Post by Pumalite on 2007-08-06
Try: sudo dpkg --remove --force-remove-<packagename>

---

### Post by steel_lady on 2007-08-06
but which package should I remove when I don't know which one is making problems??? it started a couple months ago and since then I couldn't install anything normally

---

### Post by Pumalite on 2007-08-06
Your problem probably started when the installation of a package got interrupted. Can you remember the package? If not, and if Synaptic works at all; then when Synaptic gets stuck you can click on 'Details' and that will let you see which package is the trouble maker.

---

### Post by steel_lady on 2007-08-06
i don't have details to click, I just get this:

[http://i18.tinypic.com/5413rpt](http://i18.tinypic.com/5413rpt)

Does it mean I have to reinstall linux-igd ?

---

### Post by Pumalite on 2007-08-06
I think that's what you have to remove. Replace <packagename> for that in the command I suggested to you.

---

### Post by steel_lady on 2007-08-06
In that case I get:

dpkg: unknown force/refuse option `remove-'

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

trying only to remove it gives previous options

---

### Post by Pumalite on 2007-08-06
Sorry, I ran out of ideas. Somebody with new ones will jump in. Good luck.

---

### Post by DaVinciXL on 2007-08-07
Are you, by any chance, running on Gutsy Gibbon?
'Cause I ran into a similar problem yesterday ([http://ubuntuforums.org/showthread.php?t=519011](http://ubuntuforums.org/showthread.php?t=519011)).

---

### Post by steel_lady on 2007-08-08
I have to lift the topic, I can not find any help on the net or IRC channel. Pleaseeee

---

### Post by jonjon09 on 2007-10-23
I don't know if anyone actually cares anymore, or if you already found the answer to the problem but just in case someone gets this problem, I'll tell you how I fixed mine:
Whenever I tried to install something with "sudo apt-get install <package>" it kept telling me:

" dpkg: error processing emifreq-applet (--configure):
 subprocess post-installation script returned error exit status 2 "

and

" E: Sub-process /usr/bin/dpkg returned an error code (1) "

I resolved my problem by removing the package that was messing everything up (in this case emifreq-applet) by using "sudo dpkg -r emifreq-applet" , and now everything works fine.

---

### Post by ibbumpin on 2008-05-12
I recently ran into this issue with the human-icon-theme package during the upgrade from 7.10 to 8.04.  I was not able to do a dpkg removal but I did physically delete the package's .deb file from /var/cache/apt/archives/.  Once I did that the system re-downloaded it and the install worked fine.

---

