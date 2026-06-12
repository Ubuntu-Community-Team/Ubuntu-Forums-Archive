---
title: "Ubuntu 10.10 fresh install"
date: 2010-11-18
forum: Installation &amp; Upgrades
---

### Post by kevorski on 2010-11-18
So I just got 10.10 and wanted a fresh installation on my HDD but whenever I try to run the install, via USB or CD, I get the error:

GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)

It just reboots itself and continues to do it.

I tried re-downloading 10.10 and it still didn't work, anyone have any ideas?

---

### Post by sikander3786 on 2010-11-18
Did you check the integrity of downloaded image?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by kevorski on 2010-11-18
no i haven't done that, i'll have to check that out but i really don't think that is the issue. i have done a little bit of research on google and found a lot of people having the same issue but with 10.4. so i dunno. any other suggestions?

---

### Post by Hippytaff on 2010-11-18
Can you run the live environment ok?
 
I had this error, but I could still log in via command line, and had to reinstall gdm (Gnome-desktop) but that might not be the same issue for you :-)

---

### Post by kevorski on 2010-11-18
i haven't tried that. would that fix the issue if it isn't completely installed?

---

### Post by mörgæs on 2010-11-18
The download itself is very rarely the source of problems. You can of course do the MD5 test, but I doubt that it will find any errors. 

This error message you mention has been a wide-spread problem for 10.04 and 10.10, but now there finally seems to be a cure:
[http://ubuntuforums.org/showthread.php?p=10128911#post10128911](http://ubuntuforums.org/showthread.php?p=10128911#post10128911)

That means, if only you manage to get the system installed, for example using the alternate CD, the bug will most likely be fixed on your machine as soon as you get web access (preferably during installation).

---

### Post by kevorski on 2010-11-18
the problem is that I can't get anything to install, it will ask for the language go to a splash screen and then error out. all the fixes are for an installed version. i haven't tried running it in live mode, would that potentially fix the issue?

---

### Post by Hippytaff on 2010-11-18
Running it in live mode is a good idea, to see if it works ok in the first place. That there are no hardware issues and that your specs are up to scratch. Secondly, you can use the live environment to fix some issues.

If it's not properly installed and keeps rebooting I'd say take Morgaes advice and install the alternate cd (which has no gui, and therefore no gui issues) whilst online (ie your ethernet cable plugged in) and then download the gui (I use Gnome and so does a standard 10.10 installation) by doing
```

sudo apt-get install ubuntu-desktop

```
any troubles post back :-)

---

### Post by kevorski on 2010-11-18
i will be trying that out. setting up my thumb drive right now with the alternate ubuntu

---

