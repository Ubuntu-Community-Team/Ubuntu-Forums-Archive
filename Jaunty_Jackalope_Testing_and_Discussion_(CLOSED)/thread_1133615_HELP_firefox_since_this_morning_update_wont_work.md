---
title: "HELP firefox since this morning update wont work"
date: 2009-04-23
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by skedone on 2009-04-23
please help someone, My system updated this morning all the firefox stuff and crashed at refreshing list. And i had to do a hard reset and now firefox wont start, I have narrowed it down to xulrunner but i cant uninstall it or anything i always get a error. i would post a the error but im at mates house using his pc as i have no browers on my setup apart from firefox

---

### Post by alphacrucis2 on 2009-04-23
> **skedone said:**
> please help someone, My system updated this morning all the firefox stuff and crashed at refreshing list. And i had to do a hard reset and now firefox wont start, I have narrowed it down to xulrunner but i cant uninstall it or anything i always get a error. i would post a the error but im at mates house using his pc as i have no browers on my setup apart from firefox

Maybe try this from the recovery root prompt

```
apt-get install --fix-broken
```

---

### Post by skedone on 2009-04-23
how do i load the recovery console mate is that at boot where i log in. lol sorry never used it

---

### Post by alphacrucis2 on 2009-04-23
> **skedone said:**
> how do i load the recovery console mate is that at boot where i log in. lol sorry never used it

You select it from the grub boot menu. Each kernel in the list should be paired a recovery line below. It will boot up to a menu which displays a number of options. Arrow down to the one that says something like root command prompt and hit enter.

---

### Post by ubu-for on 2009-04-23
> **skedone said:**
> please help someone, My system updated this morning all the firefox stuff and crashed at refreshing list. And i had to do a hard reset and now firefox wont start, I have narrowed it down to xulrunner but i cant uninstall it or anything i always get a error. i would post a the error but im at mates house using his pc as i have no browers on my setup apart from firefox

Alternatively you could install Epiphany (Gnome browser) with Synaptic or Opera.

Have you already tried to uninstall Firefox?

> **skedone said:**
> how do i load the recovery console mate is that at boot where i log in. lol sorry never used it

During every restart Grub shows some boot options. There you can choose the recovery boot option. If Grub is hidden during the restart press "Esc" when Grub shows up.

---

### Post by ubu-for on 2009-04-23
> **alphacrucis2 said:**
> Maybe try this from the recovery root prompt

```
apt-get install --fix-broken
```

You could also try to repair the packages with Synaptic!

---

### Post by alphacrucis2 on 2009-04-23
> **ubu-for said:**
> You could also try to repair the packages with Synaptic!

Yeah. I must be asleep, I thought he was saying that X wouldn't start.

---

### Post by ubu-for on 2009-04-23
But I guess, it's a problem between Firefox and some add-ons or the add-on check.

I had similar problems two weeks ago.

---

### Post by navneeth on 2009-04-23
Yes, the updates this morning broke my installation of Firefox, also. XULrunner is also mentioned in the error messages. 

I have tried -f install, dpkg --configure -a, removing/purging firefox AND firefox-3.0. (From the terminal in the desktop, via Synaptic, and  from the root terminal in the recovery mode.) Nothing works.

It actually had 8 packages to install, but after trying to remove and re-install firefox it has changes to 6. That ttf-uralic has been a pain ever since I wanted to try Chromium. I don't remember why I installed and I am not able to remove it, as well. 


```
navneeth@ubuntu:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up xulrunner-1.9 (1.9.0.9+nobinonly-0ubuntu0.8.10.1) ...
/var/lib/dpkg/info/xulrunner-1.9.postinst: 5: /usr/bin/xulrunner-1.9: not found
dpkg: error processing xulrunner-1.9 (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of firefox-3.0:
 firefox-3.0 depends on xulrunner-1.9 (>= 1.9.0.1); however:
  Package xulrunner-1.9 is not configured yet.
dpkg: error processing firefox-3.0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-3.0-branding:
 firefox-3.0-branding depends on firefox-3.0 (= 3.0.9+nobinonly-0ubuntu0.8.10.1); however:
  Package firefox-3.0 is not configured yet.
dpkg: error processing firefox-3.0-branding (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox:
 firefox depends on firefox-3.0; however:
  Package firefox-3.0 is not configured yet.
 firefox depends on firefox-3.0-branding; however:
  Package firefox-3.0-branding is not configured yet.
dpkg: error processing firefox (--configure):
 dependency problems - leaving unconfigured
Setting up ttf-uralic (0.0.20040829-1ubuntu2) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    No apport report written because MaxReports is reached already
                                  /etc/defoma/hints/ttf-uralic.hints: Unable to open, or empty.
dpkg: error processing ttf-uralic (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubufox:
 ubufox depends on firefox | abrowser | firefox-3.0 | firefox-2; however:
  Package firefox is not configured yet.
  Package abrowser is not installed.
  Package firefox-3.0 is not configured yet.
  Package firefox-2 is not installed.
dpkg: error processing ubufox (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            Errors were encountered while processing:
 xulrunner-1.9
 firefox-3.0
 firefox-3.0-branding
 firefox
 ttf-uralic
 ubufox
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by skedone on 2009-04-23
navneeth that is the same problem as me mate if the error messages are a match, any solution yet guys

---

### Post by ubu-for on 2009-04-23
I had similar problems three days ago with non Firefox packages. I couldn't remove them, too but found out that a reinstall of these packages with Synaptic ("mark to reinstall") solved my problem.

---

