---
title: "upgrading to geubuntu from 7.04"
date: 2007-09-23
forum: Installation &amp; Upgrades
---

### Post by patsfan on 2007-09-23
i would like to know how to upgrade to geubuntu from 7.04 and if its better? or can i have a triple boot machine? if anyone can help please let me know. thanks alot.:)

---

### Post by Angellis_ater on 2007-11-19
Well, Geubuntu is still in the development stage for 7.10, so there are no current updates from 7.04. You can have as many OS's on your machine as you have space and interest in, so go ahead!

---

### Post by darkmaster on 2007-11-30
> **patsfan said:**
> i would like to know how to upgrade to geubuntu from 7.04 and if its better? or can i have a triple boot machine? if anyone can help please let me know. thanks alot.:)

Hello, Please visit the Geubuntu home page, I don't need help with deb packages anymore, learned how to manage them
Packages for Prima Luna has already been released. And they can be tested and installed on any *ubuntu system without any fear of creating errors in it. So there's no real need to download the Live CD of Prima Luna if you already have an Ubuntu system installed. In any case, Geubuntu Luna Nuova (7.10) will come out in a few days
Thank you for the attention.
[http://geubuntu.intilinux.com](http://geubuntu.intilinux.com)

I suggest you to install the deb packages and wait a few days as Luna Nuova is released. Then you'll be able to dist-upgrade normally, changing the geubuntu repo to gutsy of course :)

---

### Post by sandysandy on 2007-12-08
> **darkmaster said:**
> Hello, Please visit the Geubuntu home page, I don't need help with deb packages anymore, learned how to manage them
Packages for Prima Luna has already been released. And they can be tested and installed on any *ubuntu system without any fear of creating errors in it. So there's no real need to download the Live CD of Prima Luna if you already have an Ubuntu system installed. In any case, Geubuntu Luna Nuova (7.10) will come out in a few days
Thank you for the attention.
[http://geubuntu.intilinux.com](http://geubuntu.intilinux.com)

I suggest you to install the deb packages and wait a few days as Luna Nuova is released. Then you'll be able to dist-upgrade normally, changing the geubuntu repo to gutsy of course :)

Hi

can u tell me the code for upgrading edubuntu 7.10 to Geubuntu 7.10 or for downloading and installing the geubuntu packages only on edubuntu 7.10.

thanks

---

### Post by sandysandy on 2007-12-09
i added the following to my sources after opening with code [COLOR="Blue"]gksudo gedit /etc/apt/sources.list [/COLOR]

deb [http://download.tuxfamily.org/geubuntu](http://download.tuxfamily.org/geubuntu) gutsy/

after opening [COLOR="Navy"]synaptic package manage[/COLOR]r the geubuntu packages were listed under [COLOR="Navy"]new in repository.[/COLOR]
i was able to install some of the packages like geubuntu themes, geubuntu artwork-usplash

but some packages like geubuntu configuration could not be installed and the following error came

[COLOR="Blue"]geubuntu-configurations:
 Depends: e17  but it is not installable[/COLOR]

kindly help

regards

---

### Post by zoe-scutterbug on 2007-12-09
I know little myself

 It is  a e17 occasional  *temporary* problem I encountered a couple of times before 
and I too had something very similar prior to guebutu with the E17 repository

 I think when the folks are e17 are working on something and something else temporarily does not fit??? E17 is in heavy development. Wonderful Geubuntu is working on top of other peoples Great work...not only E17, but xfce, gnome and ubuntu

wait a couple of days and I found it all has been worked on and ready to go.

---

### Post by darkmaster on 2007-12-09
> **sandysandy said:**
> i added the following to my sources after opening with code [COLOR="Blue"]gksudo gedit /etc/apt/sources.list [/COLOR]

deb [http://download.tuxfamily.org/geubuntu](http://download.tuxfamily.org/geubuntu) gutsy/

after opening [COLOR="Navy"]synaptic package manage[/COLOR]r the geubuntu packages were listed under [COLOR="Navy"]new in repository.[/COLOR]
i was able to install some of the packages like geubuntu themes, geubuntu artwork-usplash

but some packages like geubuntu configuration could not be installed and the following error came

[COLOR="Blue"]geubuntu-configurations:
 Depends: e17  but it is not installable[/COLOR]

kindly help

regards

Hallo, not a big problem, but you should read the geubuntu wiki:

[http://geubuntu.wikispaces.com/Installing+Geubuntu+7.10+from+packages](http://geubuntu.wikispaces.com/Installing+Geubuntu+7.10+from+packages)

You just missed two passages I think, you had to:

wget [http://lut1n.ifrance.com/repo_key.asc](http://lut1n.ifrance.com/repo_key.asc)
sudo apt-key add repo_key.asc

And than add to the repos this line too:

deb [http://e17.dunnewind.net/ubuntu](http://e17.dunnewind.net/ubuntu) gutsy e17

Then you can update and upgrade. Also install the missing geubuntu packages: you just missed the repo with e17 inside it ;)

---

### Post by sandysandy on 2007-12-13
> **darkmaster said:**
> Hallo, not a big problem, but you should read the geubuntu wiki:

[http://geubuntu.wikispaces.com/Installing+Geubuntu+7.10+from+packages](http://geubuntu.wikispaces.com/Installing+Geubuntu+7.10+from+packages)

You just missed two passages I think, you had to:

wget [http://lut1n.ifrance.com/repo_key.asc](http://lut1n.ifrance.com/repo_key.asc)
sudo apt-key add repo_key.asc

And than add to the repos this line too:

deb [http://e17.dunnewind.net/ubuntu](http://e17.dunnewind.net/ubuntu) gutsy e17

Then you can update and upgrade. Also install the missing geubuntu packages: you just missed the repo with e17 inside it ;)

thanks.

geubuntu is fantastic

regards

---

### Post by sandysandy on 2007-12-14
[QUOTE=http://geubuntu.wikispaces.com/Installing+Geubuntu+7.10+from+packages
]  from
[    http://geubuntu.wikispaces.com/Installing+Geubuntu+7.10+from+packages](    http://geubuntu.wikispaces.com/Installing+Geubuntu+7.10+from+packages)

"Remember to only run geubuntu-configuration once for each user booting Geubuntu! If you run it again, any configuration you did to Enlightenment will be lost and E17 will return to the standard and initial Geubuntu configuration. This tool can also be used if you messed things up in E17 and don't know how to revert to a safe configuration: in this case, just run geubuntu-configuration from any session, even from Gnome or KDE. Then you'll be able to log to E17 again with the default configurations. 

[/QUOTE]

hi 

my enlightenment session had configured corrrectly and the effects were good. however i upgraded to e17cvs and the enlightenment desktop and session vanished. i reinstalled geubuntu and e17 but am not getting the enlightenment login. the link above does talk about problem solving but its not clear to me.

kindly help me in restoring the enlightenment session.

thanks

---

### Post by darkmaster on 2007-12-15
> **sandysandy said:**
> hi 

my enlightenment session had configured corrrectly and the effects were good. however i upgraded to e17cvs and the enlightenment desktop and session vanished. i reinstalled geubuntu and e17 but am not getting the enlightenment login. the link above does talk about problem solving but its not clear to me.

kindly help me in restoring the enlightenment session.

thanks

Hello, this hasn't been a smart choice, sorry. I should have mentioned it in the wiki too since there's this automated tool to compile E17cvs in the net...
 SO, I don't know exactly what you could do to fix your session. E17 binaries cannot exist together with the compiled from CVS version. I'll be back with a solution shortly.

---

### Post by sandysandy on 2007-12-16
> **darkmaster said:**
> Hello, this hasn't been a smart choice, sorry. I should have mentioned it in the wiki too since there's this automated tool to compile E17cvs in the net...
 SO, I don't know exactly what you could do to fix your session. E17 binaries cannot exist together with the compiled from CVS version. I'll be back with a solution shortly.

Thanks

waiting eagerly for the solution.


regards

---

### Post by Rui Pais on 2007-12-16
> **sandysandy said:**
> hi 

my enlightenment session had configured corrrectly and the effects were good. however i upgraded to e17cvs and the enlightenment desktop and session vanished. i reinstalled geubuntu and e17 but am not getting the enlightenment login. the link above does talk about problem solving but its not clear to me.

kindly help me in restoring the enlightenment session.

thanks


Hi,
By reinstalled you mean that you format and reinstall the full Geubuntu or that you delete your e17cvs version and reinstall the deb packages only?

Can you be more precise on what you mean by "vanished"? Does GDM do not list Enlightenment? Or can you log but you don't see no e17 desktop/session?

---

### Post by sandysandy on 2007-12-17
> **Rui Pais said:**
> Hi,
By reinstalled you mean that you format and reinstall the full Geubuntu or that you delete your e17cvs version and reinstall the deb packages only?

when i went to synaptic package manager i realised that geubuntu packages and e17 were uninstalled automatically once i installed e17cvs. so i installed the missing geubuntu packages and e17 packages again. e17cvs got uninstalled.

> Can you be more precise on what you mean by "vanished"? Does GDM do not list Enlightenment? Or can you log but you don't see no e17 desktop/session?

thats right Enlightenment is not listed at all. i just get gnome and other desktop options but not enlightenment.

thanks

---

### Post by Rui Pais on 2007-12-17
> **sandysandy said:**
> when i went to synaptic package manager i realised that geubuntu packages and e17 were uninstalled automatically once i installed e17cvs. so i installed the missing geubuntu packages and e17 packages again. e17cvs got uninstalled.

Ok, just to make sure, from which repos do you get e17cvs? (or it's e17-cvs?) 
You need to check where those packages install and if they left things after uninstall (some times only purge removes all files, sometimes some need to be delete by hand...) 

> **sandysandy said:**
> 
thats right Enlightenment is not listed at all. i just get gnome and other desktop options but not enlightenment.
can you post the output of
```
ls -l /usr/share/xsessions/
```
and 
```
cat /usr/share/xsessions/enlightenment.desktop
``` please?

---

### Post by sandysandy on 2007-12-25
> **Rui Pais said:**
> Ok, just to make sure, from which repos do you get e17cvs? (or it's e17-cvs?) 
You need to check where those packages install and if they left things after uninstall (some times only purge removes all files, sometimes some need to be delete by hand...) 


can you post the output of
```
ls -l /usr/share/xsessions/
```
and 
```
cat /usr/share/xsessions/enlightenment.desktop
``` please?

hi

the output is as follows:-

XXX@edubuntu:~$ [COLOR="Blue"]ls -l /usr/share/xsessions/[/COLOR]
total 4
-rw-r--r-- 1 root root 2948 2007-10-05 14:02 gnome.desktop
XXX@edubuntu:~$ [COLOR="Blue"]cat /usr/share/xsessions/enlightenment.desktop[/COLOR]
cat: /usr/share/xsessions/enlightenment.desktop: No such file or directory
XXX@edubuntu:~$ 

thanxs

---

### Post by sandysandy on 2007-12-30
Hi

has anyone found a solution to get back the enlightenment desktop and features once e17cvs has been removed and e17 reinstalled.

has anyone else also faced a similar problem ?

thanks

:guitar:

---

### Post by Rui Pais on 2008-01-01
> **sandysandy said:**
> hi

the output is as follows:-

XXX@edubuntu:~$ [COLOR="Blue"]ls -l /usr/share/xsessions/[/COLOR]
total 4
-rw-r--r-- 1 root root 2948 2007-10-05 14:02 gnome.desktop
XXX@edubuntu:~$ [COLOR="Blue"]cat /usr/share/xsessions/enlightenment.desktop[/COLOR]
cat: /usr/share/xsessions/enlightenment.desktop: No such file or directory
XXX@edubuntu:~$ 

thanxs

> **sandysandy said:**
> Hi

has anyone found a solution to get back the enlightenment desktop and features once e17cvs has been removed and e17 reinstalled.

has anyone else also faced a similar problem ?

thanks

Hi, sorry this late answer, i've been out of town ...

You still haven't said how you installed your e17cvs. 
Did you use my deb package (e17-cvs?) or Morlenxus script?

Anyway you need to remove any versions of e17 from cvs. It's usually installed on /opt/e17. Check if you have any /opt/e17/bin or /opt/e17/lib. (another possible locations other packages sometimes use it's /usr/local/lib). 
If so, remove it:
```
sudo rm -rf /opt/e17
```
for sure do a:
```
sudo ldconfig
```
and then reinstall geubuntu:
```
sudo aptitude reinstall geubuntu-desktop
```
or even better:
```
sudo apt-get remove --purge geubuntu-desktop
sudo apt-get install geubuntu-desktop
```

Good luck

---

### Post by sandysandy on 2008-01-12
> **Rui Pais said:**
> Hi, sorry this late answer, i've been out of town ...

You still haven't said how you installed your e17cvs. 
Did you use my deb package (e17-cvs?) or Morlenxus script?

Anyway you need to remove any versions of e17 from cvs. It's usually installed on /opt/e17. Check if you have any /opt/e17/bin or /opt/e17/lib. (another possible locations other packages sometimes use it's /usr/local/lib). 
If so, remove it:
```
sudo rm -rf /opt/e17
```
for sure do a:
```
sudo ldconfig
```
and then reinstall geubuntu:
```
sudo aptitude reinstall geubuntu-desktop
```
or even better:
```
sudo apt-get remove --purge geubuntu-desktop
sudo apt-get install geubuntu-desktop
```

Good luck

thanks a lot

my geubuntu desktop is restored.

regards

---

### Post by Rui Pais on 2008-01-12
> **sandysandy said:**
> thanks a lot

my geubuntu desktop is restored.

regards

You're welcome :)

---

