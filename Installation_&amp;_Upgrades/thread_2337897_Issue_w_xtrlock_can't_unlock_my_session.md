---
title: "Issue w/ xtrlock: can't unlock my session"
date: 2016-09-22
forum: Installation &amp; Upgrades
---

### Post by alexlesexe on 2016-09-22
Hi everyone!
I installed xtrlock on my Ubuntu 14.04 LTS with
```
sudo apt-get install xtrlock
```
but every time I launch xtrlock I can't go back to my session! The blue lock is appearing on my mouse pointer as it should but when I type my pwd and then hit enter nothing happens...
When I run it in sudo, I get the following error: password entry has no pwd
I tried alock as an alternative but couldn't manage to make it work :]
Can anyone help me with this?
Thanks a lot!

---

### Post by CantankRus on 2016-09-22
Before entering your password check capslock is not on and then hit Escape to clear 
any password characters that may have already been entered.

What is alock... can't find that one?

---

### Post by alexlesexe on 2016-09-26
alock is another minimal screenlocker for X, originally based on xtrlock [https://github.com/Arkq/alock](https://github.com/Arkq/alock)
I checked for capslock and tried to clear with Esc, still not working.
I used ```
xtrlock & sleep 20 && pkill xtrlock
``` to test so after 20 seconds I can go back to my session.
Do you think keyboard mapping could have something to do with this issue? I use an AZERTY keyboard.
Tank you for your answer btw!

---

### Post by CantankRus on 2016-09-26
I played around with xtrlock a few years ago and worked fine.
Testing here on 16.04 also unlocks no problem.
Are you just running a normal Ubuntu session?

Don't know how azerty keyboard woud cause errors.
Could test typing your password with xdotool.
```
sudo apt install xdotool
```

Then running ...
```
xtrlock & sleep 5 && xdotool key --delay 50 [COLOR="#FF0000"]P A S S W O R D[/COLOR] Return; sleep 10 && pkill xtrlock
```
where [COLOR="#FF0000"]P A S S W O R D[/COLOR] is your password with each character separated by a space.
Test the xdotool command first in terminal to see if it types your password then hits the Return key.

---

### Post by alexlesexe on 2016-09-27
Hey!
I think I found why it wasn't working... My password contained a 'é' character. I changed it and now xtrlock is working as it should :)
Thank you very much for your help!!

---

### Post by CantankRus on 2016-09-27
No problem.
Don't know why your using xtrlock, but this thread may be of interest...
[URL="https://ubuntuforums.org/showthread.php?t=2125918"][B][U][COLOR="#B22222"]How do I retrieve a stored password from the gnome keyring?
[/COLOR][/U][/B][/URL]

---

