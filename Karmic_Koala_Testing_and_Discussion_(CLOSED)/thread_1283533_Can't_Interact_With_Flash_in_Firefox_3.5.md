---
title: "Can't Interact With Flash in Firefox 3.5"
date: 2009-10-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jdorenbush on 2009-10-05
*I am using Firefox (Shiretoko) 3.5.4 with Ubuntu 9.10, 64-bit.*

I no longer have the ability to interact with YouTube player controls. It seems other people were having problems with Flash in Firefox 3.5; opening a video in fullscreen mode. Obviously I can't test to see if I have this problem because I can't click the fullscreen button.

I just tested Flash on another website and I can't interact with Flash there either. 

Seems the problems doesn't lie within just YouTube. I can view Flash video without problems, but not interact/control it. It's a Flash/Firefox problem. Maybe something to do with Ubuntu 9.10 too? I am not sure. It does seem as though the problem started to occur when I updated to 9.10 yesterday, but there was also Firefox 3.5 packages that were updated as well.

**UPDATE:** Flickr uploader no longer works either and that finally just started working for me a few months ago. 

It was like all the functions of Internet browsing that were flawed or broken to me using Ubuntu, 64-bit and Firefox finally started to resolve themselves. Then I upgraded to Ubuntu 9.10 and Firefox 3.5 and it all came crashing down again.

---

### Post by jdorenbush on 2009-10-07
Anyone? :\

---

### Post by daas88 on 2009-10-07
I have the same problem, with karmic beta 64, but i hadn't paid much attention to it because i could still pause with spacebar and go to fullscreen pressing F. I just found this, check it out:

[http://www.khattam.info/2009/08/18/solved-flashplugin-controls-not-working-in-ubuntu-9-10-karmic-koala-alpha-4/](http://www.khattam.info/2009/08/18/solved-flashplugin-controls-not-working-in-ubuntu-9-10-karmic-koala-alpha-4/)

I think i'll try downloading the 64-bit flash alpha prerelease from adobe.

**Edit: i downloaded the 64-bit flash alpha and put it into /usr/lib/mozilla/plugins and it's working fine now.**

---

### Post by jdorenbush on 2009-10-08
Thanks daas88! Problem solved. Below are the steps I took to fix the problem:

1. Downloaded: [Flash Player 10 for 64-bit Linux]("http://labs.adobe.com/downloads/flashplayer10.html")

2. Removed the flashplugin via Synaptic Package Manager

3. Extract file (libflashplayer.so) from libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz into /usr/lib/mozilla/plugins/ via Alt+F2, "gksu nautilus"

4. Rebooted (*Not sure if this is necessary, but I tried launching Firefox after I installed new Flash plugin and I was having problems. Reboot seemed to have solved that problem.*) Everything is working fine now.

---

### Post by slymi2005 on 2009-10-09
This would cause firefox to crash when I would try to watch something on hulu. Has this been fixed?

---

### Post by dcstar on 2009-10-09
> **slymi2005 said:**
> This would cause firefox to crash when I would try to watch something on hulu. Has this been fixed?

Why not report it as a bug - as **specifically requested for this BETA** software.

---

### Post by neekz on 2009-10-22
Worked a treat for me.

---

### Post by Isthan on 2009-10-24
> **jdorenbush said:**
> Thanks daas88! Problem solved. Below are the steps I took to fix the problem:

1. Downloaded: [Flash Player 10 for 64-bit Linux]("http://labs.adobe.com/downloads/flashplayer10.html")

2. Removed the flashplugin via Synaptic Package Manager

3. Extract file (libflashplayer.so) from libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz into /usr/lib/mozilla/plugins/ via Alt+F2, "gksu nautilus"

4. Rebooted (*Not sure if this is necessary, but I tried launching Firefox after I installed new Flash plugin and I was having problems. Reboot seemed to have solved that problem.*) Everything is working fine now.

THANKS jdorenbush and daas88!  This solved my issues of not being able to interact with youtube video windows and pandora's interface buttons.  I'm using Karmic 9.10 updated as of 10/24/09 with the alternate AMD build.

Just a note, I did not understand how to use step 3 using nautilus.  I'm very new to Ubuntu, so this is not a big shock.  I do; however, know how to use UNIX.  I was able to complete step 3 in the following manner:

Downloaded the libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz from the website given by jdorenbush.  I extracted to my Documents folder.  To make this universal for anyone else, begin by navigating to the extracted folder in a terminal window.  Then execute:

```
sudo mv libflashplayer.so /usr/lib/mozilla/plugins/
```

This was necessary because simply trying to drag/drop inside (nautilus?) will present a permissions error.

Sorry for my limited knowledge, but if anyone else reading this has my same level of competency, this may help!

---

### Post by daas88 on 2009-10-25
Of course! i did it that way too. Terminal is faster ;-)

But in order to move it via nautilus you have to open nautilus with root permissions typing "sudo nautilus" in terminal or "gksudo nautilus" in alt+f2 (run command).

I guess you are one of the few guys that found CLI easier than an UI :-D

---

### Post by Metal_Reign on 2009-10-26
Worked perfectly. Many thanks!:smile:

---

### Post by Luke has no name on 2009-10-26
Why hasn't the Flash 10 64-bit plugin been dropped in the repositories? 

"It's beta" isn't an excuse. Ubuntu is beta quality more than half the time, and the Flash 10 x64 plugin has not once crashed on me since using it in the past 4 months.

"It's non-free" is unreasonable, since we already have several nonfree packages, including 32bit Flash.

---

### Post by zika on 2009-10-26
> **Isthan said:**
> THANKS jdorenbush and daas88!  This solved my issues of not being able to interact with youtube video windows and pandora's interface buttons.  I'm using Karmic 9.10 updated as of 10/24/09 with the alternate AMD build.

Just a note, I did not understand how to use step 3 using nautilus.  I'm very new to Ubuntu, so this is not a big shock.  I do; however, know how to use UNIX.  I was able to complete step 3 in the following manner:

Downloaded the libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz from the website given by jdorenbush.  I extracted to my Documents folder.  To make this universal for anyone else, begin by navigating to the extracted folder in a terminal window.  Then execute:

```
sudo mv libflashplayer.so /usr/lib/mozilla/plugins/
```This was necessary because simply trying to drag/drop inside (nautilus?) will present a permissions error.

Sorry for my limited knowledge, but if anyone else reading this has my same level of competency, this may help!I think that it is better and safer to put libflshplayer.so in ~/.mozilla/plugins (without sudo). That way it could make less damage ... Just my .05$.
(Keep as much of stuff as possible in Your local folder without root privileges ....)

---

### Post by philinux on 2009-10-26
> **Luke has no name said:**
> Why hasn't the Flash 10 64-bit plugin been dropped in the repositories? 

"It's beta" isn't an excuse. Ubuntu is beta quality more than half the time, and the Flash 10 x64 plugin has not once crashed on me since using it in the past 4 months.

"It's non-free" is unreasonable, since we already have several nonfree packages, including 32bit Flash.

It's not even beta it's still an alpha refresh. Download from adobe extract and copy the file to ~/.mozilla/plugins simple. Works really well. Better than ia32libs and the 32 bit flash.

---

### Post by tonybeccar on 2009-10-26
Thanks man! It works like a charm!

---

