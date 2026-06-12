---
title: "No Panels, Can't Update, Serious Problems - Urgent"
date: 2009-02-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by go7Ul1ai on 2009-02-20
Hello,

I've been testing Jaunty for a number of weeks now and I think it's been a great improvement. This morning after I booted up the computer and logged in, all was not well in the Jaunty Machine. It was only displaying the desktop wallpaper and the cursor, nothing else. Good job I have GNOME Do installed though, I managed to be able to load up Firefox using Do to type this message.

Everytime I open Firefox though, it acts that I've only just used it, so it opens up the "set-up" for various applications and my normal theme is gone, it does this every time I restart it. Hmmmm

Also, if I open up the Terminal I type in "sudo aptget update && sudo apt-get upgrade", it came up with an error, it told me to run another line of code which had something to do with "configure" in it, I can't remember. But I can't install new updates etc, is the only way out of this to re-install?

Thanks in advance,

Lee Jarratt

---

### Post by taavikko on 2009-02-20
Better off reading those errors, since they give you "the" clue, in which way to seek help.

I believe your error message was "dpkg was interrupted, you must manually run "dpkg --configure -a"

Just run the command, with "sudo" in front of it.

Also, run:
sudo apt-get -f install
sudo apt-get update && sudo apt-get dist-upgrade

---

### Post by go7Ul1ai on 2009-02-20
> **taavikko said:**
> Better off reading those errors, since they give you "the" clue, in which way to seek help.

I believe your error message was "dpkg was interrupted, you must manually run "dpkg --configure -a"

Just run the command, with "sudo" in front of it.

Also, run:
sudo apt-get -f install
sudo apt-get update && sudo apt-get dist-upgrade

Thanks for the reply, I get this when running sudo apt-get -f install:

```
9 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up libasound2 (1.0.18-1ubuntu7) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing libasound2 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of alsa-utils:
 alsa-utils depends on libasound2 (>> 1.0.18); however:
  Package libasound2 is not configured yet.
dpkg: error processing alsa-utils (--configure):
 dependency problems - leaving unconfigured
Setting up python-problem-report (0.134) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing python-problem-report (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on python-problem-report (>= 0.94); however:
  Package python-problem-report is not configured yet.
dpkg: error processing python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport:
 apport depends on python-apport (>= 0.120); however:
  Package python-apport is not configured yet.
dpkg: error processing apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on python-apport (>= 0.80); however:
  Package python-apport is not configured yet.
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.
dpkg: erNo apport report written because MaxReports is reached already
                                                                      No apport report written because MaxReports is reached already
                                                    No apport report written because MaxReports is reached already
                                  No apport report written because MaxReports is reached already
                No apport report written because MaxReports is reached already
                                                                              No apport report written because MaxReports is reached already
                                                            ror processing apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libsdl1.2debian-alsa:
 libsdl1.2debian-alsa depends on libasound2 (>> 1.0.18); however:
  Package libasound2 is not configured yet.
dpkg: error processing libsdl1.2debian-alsa (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libsdl1.2debian:
 libsdl1.2debian depends on libsdl1.2debian-alsa (= 1.2.13-4ubuntu3) | libsdl1.2debian-all (= 1.2.13-4ubuntu3) | libsdl1.2debian-esd (= 1.2.13-4ubuntu3) | libsdl1.2debian-oss (= 1.2.13-4ubuntu3) | libsdl1.2debian-nas (= 1.2.13-4ubuntu3) | libsdl1.2debian-pulseaudio (= 1.2.13-4ubuntu3); however:
  Package libsdl1.2debian-alsa is not configured yet.
  Package libsdl1.2debian-all is not installed.
  Package libsdl1.2debian-esd is not installed.
  Package libsdl1.2debian-oss is not installed.
  Package libsdl1.2debian-nas is not installed.
  Package libsdl1.2debian-pulseaudio is not installed.
dpkg: error processing libsdl1.2debian (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pulseaudio:
 pulseaudio depends on libasound2 (>> 1.0.18); however:
  Package libasound2 is not configured yet.
dpkg: error processing pulseaudio (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libasound2
 alsa-utils
 python-problem-report
 python-apport
 apport
 apport-gtk
 libsdl1.2debian-alsa
 libsdl1.2debian
 pulseaudio
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Is there any way to get my panel and my sound back? Any ideas on the Firefox problems?

Thanks again in advance,

Lee

---

### Post by Dougie187 on 2009-02-20
Did you run 
```
sudo dpkg --configure -a
```
before 
```
sudo apt-get -f install
```
?

---

### Post by go7Ul1ai on 2009-02-20
Yes I ran all three commands in order, errors etc. typing gnome-panel in terminal brings up an error too. It still won't let me update.

---

### Post by andrewabc on 2009-02-20
Do you have a similar problem as I do?
See my post and screenshots [here](http://ubuntuforums.org/showpost.php?p=6767878&postcount=20)

No solution yet.
These two problems do seem similar because some apps are not set up, and we are both having panel problems.

---

### Post by go7Ul1ai on 2009-02-20
> **andrewabc said:**
> Do you have a similar problem as I do?
See my post and screenshots [here](http://ubuntuforums.org/showpost.php?p=6767878&postcount=20)

No solution yet.
These two problems do seem similar because some apps are not set up, and we are both having panel problems.

I gave in and just re-installed Jaunty, all is great now :)

---

### Post by andrewabc on 2009-02-20
> **lee.jarratt said:**
> I gave in and just re-installed Jaunty, all is great now :)

Yah, sadly I think that is what I will have to do.
Did you install from Alpha 4? Or did you download daily cd?

I only have alpha 3 downloaded and burned, so I think I'll use that since it will take 6 hours to download 700mb of data. Probably only have 300mb of updates the other way.

---

### Post by go7Ul1ai on 2009-02-20
> **andrewabc said:**
> Yah, sadly I think that is what I will have to do.
Did you install from Alpha 4? Or did you download daily cd?

I only have alpha 3 downloaded and burned, so I think I'll use that since it will take 6 hours to download 700mb of data. Probably only have 300mb of updates the other way.

I downloaded the daily live CD a few hours ago, it hangs just after the partition manager. I had to find one of my older Jaunty Alpha CD (I think it was Alpha 2 or 3. 

Good luck ;)

---

### Post by andrewabc on 2009-02-20
> **lee.jarratt said:**
> I downloaded the daily live CD a few hours ago, it hangs just after the partition manager. I had to find one of my older Jaunty Alpha CD (I think it was Alpha 2 or 3. 

Good luck ;)

Yah, I figure I'll wait 6 days and get alpha 5.
Trying to install alpha 3 now.

EDIT:
Installed fine. 473 updates available totalling 201 mb.
Now the question is do I wait for alpha 5 and format/install again. Or do I attempt the 200mb download/install which could screw stuff up?
I think I'll not do any of the updates and wait for alpha 5. The computer is only used for firefox mainly, so as long as that and the wireless work that will do until alpha 5.

---

