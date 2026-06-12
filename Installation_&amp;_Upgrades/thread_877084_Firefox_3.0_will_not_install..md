---
title: "Firefox 3.0 will not install."
date: 2008-08-01
forum: Installation &amp; Upgrades
---

### Post by kaldor on 2008-08-01
I decided to try out firefox 3 today. I uninstalled firefox 3 Beta 5 first. I download firefox off of the mozilla site, and then extract it to my home folder. I try sudo apt-get install firefox-3.0, and it installs. I then open firefox to find that it is still firefox 3 beta 5. 

I am not too great with the terminal, as I rarely install anything.

---

### Post by tuxxy on 2008-08-01
You should be running FF 3.01 if you have been installing updates

---

### Post by miegiel on 2008-08-01
maybe you can find some inspiration here

[http://ubuntuforums.org/showthread.php?t=876864](http://ubuntuforums.org/showthread.php?t=876864)

---

### Post by Vahids on 2008-08-01
goto terminal and type:
> which firefox
then goto this path and see it, if it's firefox 3 beta 5 replace it with firefox 3 (Full)

---

### Post by oldos2er on 2008-08-01
> **kaldor said:**
> I decided to try out firefox 3 today. I uninstalled firefox 3 Beta 5 first. I download firefox off of the mozilla site, and then extract it to my home folder. I try sudo apt-get install firefox-3.0, and it installs. I then open firefox to find that it is still firefox 3 beta 5. 

I am not too great with the terminal, as I rarely install anything.

 Anytime you use apt-get, aptitude, Add/Remove Programs, or Synaptic Package Manager, they look to the online repositories for programs, not on your local disk(s).

 Go to the Firefox 3.0 folder you extracted, and click on "firefox."

---

### Post by aysiu on 2008-08-01
```
sudo apt-get install firefox
``` will fetch the Ubuntu repositories version of Firefox 3.0, which is beta, apparently.

What you downloaded as a .tar.bz2 is the Mozilla version of Firefox 3.0.

To install that, follow [these instructions](http://www.psychocats.net/ubuntu/firefox#terminal).

---

### Post by MentalOxide on 2008-09-24
OK, I'm stumped. 

I tried the synaptic package manager and searched for firefox 3, but all i see are b4 (beta) versions, no final versions. I've looked around for update library buttons and things but i cant see any. I've tried to install following all the 'super simple' manual install guides on .tar files, with that god forsaken 1980's looking command terminal and I just get unhelpful nerd jargon, with 'command not found' etc, because their command lines obviously assume I should modify some part of it to suit my own system. 

I really like Ubuntu, and I know all that all the IT guys love that 'terminal' thing and how 'powerful and flexible' it is, but it's definately not for 'humans', i.e. average people. It's for people who know and love computer code, and it seems like a step back to the MS DOS days. I thought 'user friendly' was when we got away from typing and moved to icons and GUIs. 

Sorry.. letting off steam, i've been trying to figure this out on my own for weeks now and I haven't got anywhere, and those tarball guides aren't simple enough. 

thanks in advance.

---

