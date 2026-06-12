---
title: "LibreOffice very slow on Ubuntu 16.04"
date: 2016-06-03
forum: Installation &amp; Upgrades
---

### Post by jdhamric on 2016-06-03
Upgraded to Ubuntu 16.04 a while back & LibreOffice was obviously upgraded at the same time. Since then, LibreOffice has been very slow/unresponsive, greying out for extended periods at times. This is despite the size of the file (so it's not specifically related to another post here). I uninstalled/re-installed, purged/reinstalled & purged/installed the recent RC version all with the same result. It worked fine with Ubuntu 15.10 & the previous LO version. I have configured LO according to most suggestions (checking/unchecking graphics settings, etc.) with no change. I have noticed that without libreoffice-gtk it seemed much faster, but looked like something out of 1992.

I have a Toshiba C55t laptop with integrated Intel graphics.

Does anyone have any suggestions?

---

### Post by vasa1 on 2016-06-03
> **jdhamric said:**
> ... I uninstalled/re-installed, purged/reinstalled & purged/installed the recent RC version all with the same result. ...
Uninstalling/reinstalling may not achieve much if the debs are stored in /var/cache/apt/archives. They'll just be reused.

Also, purging doesn't affect your profile which just possibly may the source of the problem. Have you tried a [new profile]("https://wiki.documentfoundation.org/UserProfile")?

Are these files created *ab initio* in LibreOffice?

---

### Post by jdhamric on 2016-06-04
vasa1--

I renamed the .libroffice folder entirely with no change in behavior. I restored the old .libreoffice folder, renamed "user" & opened up a file with no improvement. A
ll files I have used have been created under previous versions of LO to date.

---

### Post by vasa1 on 2016-06-04
Did you mean "~/.config/libreoffice/4/user"? BTW, I too have integrated graphics *without any GPU*. I prefer to start LibreOffice using gtk2 instead of gtk3. gtk2 seems less taxing in some respects:```
SAL_USE_VCLPLUGIN=gtk libreoffice --calc
```

---

### Post by jdhamric on 2016-06-04
> **vasa1 said:**
> Did you mean "~/.config/libreoffice/4/user"? BTW, I too have integrated graphics *without any GPU*. I prefer to start LibreOffice using gtk2 instead of gtk3. gtk2 seems less taxing in some respects:```
SAL_USE_VCLPLUGIN=gtk libreoffice --calc
```

Yep, tried that. No difference.

---

### Post by dkeats on 2016-06-11
I am having the same thing since a few days ago. Have tried everything short of going back to 15.10. Downgraded LO to previous version, upgraded to unstable, uninstalled and installed OpenOffice. They all do the same thing, which makes me think it is a bug somewhere else, not in Libreoffice itself.

---

### Post by dkeats on 2016-06-11
I don't know if this is helpful, but in my case, I found that something during an update had set the graphics driver back to Nouveau. I re-installed the latest proprietary Nvidia driver, and that seems to have fixed the problem, I hope!

---

### Post by lliseil on 2016-06-11
If LO keeps being #!¤@ slow upon (temporarily) removing its existing profile, or better on a "test user" session then we'll know for sure it's system related, and not to LO settings.

For the record LO loads a heavilly formatted and annotated 350 pages document in 20 seconds on my six years old Atom netbook (which has no nVIdia Titan hi hi hi but the extremely pitiful Intel 945 integrated GPU).

---

### Post by vasa1 on 2016-06-11
> **lliseil said:**
> ...
For the record LO loads a heavilly formatted and annotated 350 pages document in 20 seconds on my six years old Atom netbook (which has no nVIdia Titan hi hi hi but the extremely pitiful Intel 945 integrated GPU).
Hi,
could you please share the output from
```
lsb_release -a
```
and
```
apt-cache policy libreoffice
```

---

### Post by lliseil on 2016-06-12
Arch GNU/Linux rolling
_

Small correction: document used for test is 250 pages only and 550k characters and I set it to use gtk. LO-fresh 5.1 (re)loads in 18 (14) sec on the netbook. ABout the same with LO-still.  

@jdhamric can you please confirm you tried starting LO:
- on a *newly created* user session (to get rid of possibly annoying older user's session/Unity settings)
- with Java (jre) unactivated.

---

### Post by jdhamric on 2016-06-18
> **lliseil said:**
> Arch GNU/Linux rolling
_

Small correction: document used for test is 250 pages only and 550k characters and I set it to use gtk. LO-fresh 5.1 (re)loads in 18 (14) sec on the netbook. ABout the same with LO-still.  

@jdhamric can you please confirm you tried starting LO:
- on a *newly created* user session (to get rid of possibly annoying older user's session/Unity settings)
- with Java (jre) unactivated.

1. De-activating Java makes no difference in current user session.
2. LO is snappy in a newly created user session!

---

### Post by jdhamric on 2016-06-30
So another interesting point--

I created a new (simple) spreadsheet & everything worked quickly; no lags/unresponsiveness in data entry, moving to another cell, etc. Saved the file & closed it. Reopened it & the problem is back!

Another thing--checkboxes in the options are all in white & hard to see. I'm using a RAVE-X theme and switching to a Radiance-based theme makes the LO icons hard to see (Sifr). To me this points to a GTK problem.

Anybody got ANY ideas?

---

### Post by k-rob2 on 2016-07-04
> **jdhamric said:**
> So another interesting point--

I created a new (simple) spreadsheet & everything worked quickly; no lags/unresponsiveness in data entry, moving to another cell, etc. Saved the file & closed it. Reopened it & the problem is back!

Another thing--checkboxes in the options are all in white & hard to see. I'm using a RAVE-X theme and switching to a Radiance-based theme makes the LO icons hard to see (Sifr). To me this points to a GTK problem.

Anybody got ANY ideas?


I'm experiencing the same problem. Ubuntu 16.04, 16gb ram, fast drive with lots of space... Kernel 4.6.2.

---

### Post by peter-rozenbottels on 2016-09-08
I am experiencing the same problem since I upgraded my laptop to 16.04 leaving it pretty useless to me. I need to make a lot of presentations and simply can't: just adding a slide or saving the document takes forever. 

This is a real problem becaue I want to upgrade the other PC's in my office. The problem seems to be with GTK, there is a workaround here [http://askubuntu.com/questions/785417/why-is-libreoffice-so-slow-when-used-in-ubuntu-16-04](http://askubuntu.com/questions/785417/why-is-libreoffice-so-slow-when-used-in-ubuntu-16-04) but I don't want a win'95 like look. 

Can this issue be solved?

---

### Post by mörgæs on 2016-09-09
Which Buntu are you using? If you are using Lubuntu please click the old hardware link in my signature and search in the guide for *flicker*.

May work for other Buntus too. 

It's not my invention. I just stumbled upon the idea and tested it with good results.

---

### Post by pablosquared on 2016-09-09
I had the same problem in the last couple of weeks - very laggy when scrolling spreadsheets etc. I upgraded yesterday to v5.2.1.2, the "Fresh" version, following Joey's instructions on omgubuntu:

[http://www.omgubuntu.co.uk/2016/08/install-libreoffice-5-2-on-ubuntu-ppa](http://www.omgubuntu.co.uk/2016/08/install-libreoffice-5-2-on-ubuntu-ppa)

Problem solved for me - back to speedy scrolling, menu opening etc. 

HTH
PP

---

### Post by jdhamric on 2016-10-02
I installed the latest version of LO today along with libreoffice-gtk2 & libreoffice-gnome. Without libreoffice-gnome LO is slow & "grays-out" periodically. With libreoffice-gnome LO is a little quicker but my best results are still without any libreoffice-gtk version installed.

---

