---
title: "upgrade from hardy to lucid"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by jabrilm on 2010-05-10
Hi,

I have hardy heron installed on my desktop and would like to upgrade to the most recent LTS, lucid lynx. When I run update manager, the upgrade that is offered is 8.10, intrepid ibex. I went into System --> Administration --> Software Sources and in the Updates tab clicked "long term support releases only" but then in the update manager no upgrade option is listed (not lucid lynx and not intrepid ibex). How can I get the update manager to offer me lucid lynx? I have installed all the other various software updates that are offered.

Thanks for any help.
Cheers

---

### Post by proggy on 2010-05-10
You have to choose normal releases in update manager.

---

### Post by jabrilm on 2010-05-10
But then it only offers me an upgrade to 8.10. I want the newest LTS, lucid lynx.

---

### Post by proggy on 2010-05-10
Have you tried this method just scroll down to 8.04 to 10.04 
[https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades)

---

### Post by jabrilm on 2010-05-11
Thanks, Proggy. That worked for me. I had actually gone through those steps once before with no success, but it worked the second time.

---

### Post by proggy on 2010-05-11
Great! i hope your upgrade goes flawless.

---

### Post by jabrilm on 2010-05-11
It went well for the most part, except that I have no sound now. Trying to sort that out...

---

### Post by Soul-Sing on 2010-05-12
via  the update manager you get an "update to 10.4" only after the 10.4.1 release in July this year.....

---

### Post by proggy on 2010-05-12
all sound was muted after i did upgrade

---

### Post by jabrilm on 2010-05-12
Nothing seems to be muted when I run 'alsamixer.' Not sure what's going on.

---

### Post by proggy on 2010-05-12
> **jabrilm said:**
> Nothing seems to be muted when I run 'alsamixer.' Not sure what's going on.
so you`re not getting system sounds as well? 
someone possibly has the solution here [http://ubuntuforums.org/showthread.php?t=1466891](http://ubuntuforums.org/showthread.php?t=1466891)

---

### Post by jabrilm on 2010-05-12
No sounds at all. Thanks for the link - I tried 'amixer set Speaker 100%' but still no luck.

---

### Post by proggy on 2010-05-13
Can you try a 10.04 live cd and see if you have sound.
I don't know where i`m going with this but  something went  wrong in the upgrade at least it would show if a clean install might solve the problem.

---

### Post by proggy on 2010-05-13
You could also try going to Preferences>Startup Applications , see if Pulseaudio Sound System is checked also Gnome login sound.

---

