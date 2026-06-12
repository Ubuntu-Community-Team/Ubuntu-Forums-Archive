---
title: "OpenOffice only loads Splash Screen and then Crashes"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by TedBuckland on 2007-04-26
Hi Folks!

I have searched everywhere for a solution, but couldn't find any:

Everytime when I try to open OpenOffice, only the Splash Screen comes up, the Bar loads up to 40% and then the Splash Screen Vanishes.
There is only this message in the Terminal:
WARNING **: Unknown error forking main binary / abnormal early exit ...

I am using Ubuntu Feisty Fawn and didn't have any problems with OO in Edgy. I have already installed, erased, reinstalled ... everything that has a relation to OO, but nothing works. I don't have any clue how to do it.

Anybody have an idea? I miss my OpenOffice!

Thanks!

/edit:
I already had single .deb files installed and also went from .rpm to .deb, but still there is no effect. OO crahes after three seconds and now there isn't even a crash message in the terminal.

Any ideas? You would make my day!

---

### Post by John Jason Jordan on 2007-04-26
> **TedBuckland said:**
> Everytime when I try to open OpenOffice, only the Splash Screen comes up, the Bar loads up to 40% and then the Splash Screen Vanishes.
There is only this message in the Terminal:
WARNING **: Unknown error forking main binary / abnormal early exit ...

I am using Ubuntu Feisty Fawn and didn't have any problems with OO in Edgy. I have already installed, erased, reinstalled ... everything that has a relation to OO, but nothing works. I don't have any clue how to do it.
/edit:
I already had single .deb files installed and also went from .rpm to .deb, but still there is no effect. OO crahes after three seconds and now there isn't even a crash message in the terminal.
This is probably unrelated, but I had a problem with OpenOffice that was solved by reinstaling dictionary-common. The problem was that the hyphenation module depends on dictionary-common, but gets confused and thinks dictionary-common is not installed.

This may not be related to your problem, so no guarantees. I just offer it because it's worth a shot.

---

### Post by schmidty on 2007-04-27
I just installed Feisty and noticed that I can't run OO from the Applications menu. It shows the splash screen and then crashes! I tried running it under Root and it ran fine. It has somthing to do with Java runtime environment, I think? Here is the error message;

[Java framework] Error in function createUserSettingsDocument (elements.cxx).javaldx failed! 
[Java framework] Error in function createUserSettingsDocument (elements.cxx).
** (process:1396): WARNING **: Unknown error forking main binary / abnormal early exit ...


I think this might be an easy fix but am not sure? It could also be my system as I am running a P3 (850mhz) with an old Intel board and memory. But then again maybe not... :|

Schmidty

---

### Post by schmidty on 2007-04-27
Well - I just fixed my problem!  

I must have ran OO under root because the .openoffice2 folder under my account directory had root:root ownership of the file directory. I simply did a **sudo chown schmidty:schmidty .openoffice2** and that fixed the problem - I hope.

Anyways, I love Ubuntu Linux!!!  :) 

Schmidty

---

### Post by TedBuckland on 2007-04-27
Thanks for your tips, but these don't change anything at my machine.

Further ideas?

---

### Post by dphan on 2007-05-01
that happens exactly same to me, 
** (process:6804): WARNING **: Unknown error forking main binary / abnormal early exit ...

I have run Edgy 6.10 kernel 2.6.17

Notice: the error happens together with acroread at the same time and it looks like I changed sth in boot&shutdown process!!! using sysv-rc-conf

please help me!
D.Phan

---

### Post by aldeby on 2007-05-28
If you installed SCIM imput for non latin languages this fix done the job for me: 
> [http://ubuntuforums.org/showpost.php?p=2568329](http://ubuntuforums.org/showpost.php?p=2568329)
Hope it helps. It has been a very annoying bug.

---

