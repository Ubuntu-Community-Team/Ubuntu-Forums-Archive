---
title: "easy sound problem (I think)"
date: 2009-04-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Awareness on 2009-04-10
I had sound working in 8.10 since 8.04 (not perfect, for example it didnt work in wine and some other native games) but vlc and flash worked (even at the same time witch was an issue hard to work out for me)

I had to reinstall 8.10 because a video problem i couldnt work out... after that only vlc works fine... flash and games does not

I tried all kind of stuff... the last thing i tried was to upgrade to 9.04 expecting everything to work out again somehow :S

Well it didn't... but i noticed if I created a new user, the sound works fine... so the question is... what do i have to delete from my user to get default values again?

Thanks :)

---

### Post by Awareness on 2009-04-11
bump ):P

---

### Post by pbpersson on 2009-04-11
If you used your current user to create a new user, can't you use the new user to delete your current user and then create a new current user?

---

### Post by pbpersson on 2009-04-11
> **Awareness said:**
>  so the question is... what do i have to delete from my user to get default values again?


In theory it would be in a hidden folder or file in your home directory.  In my home directory there is a hidden file called .asoundrc.asoundconf and it says it is for ALSA configuration

I don't know if that helps

---

### Post by taavikko on 2009-04-11
> **pbpersson said:**
> If you used your current user to create a new user, can't you use the new user to delete your current user and then create a new current user?

Dude, you got me so confused :)

For OP, I suggest to read this [http://ubuntuforums.org/showthread.php?t=1084919](http://ubuntuforums.org/showthread.php?t=1084919)

Many of problems are solved by updates on kernel and pulseaudio, but few may remain due to broken configs (.asound* .pulse)

---

### Post by crimsun on 2009-04-11
> **Awareness said:**
> I tried all kind of stuff... the last thing i tried was to upgrade to 9.04 expecting everything to work out again somehow :S

Well it didn't... but i noticed if I created a new user, the sound works fine... so the question is... what do i have to delete from my user to get default values again?

You should at least rm -f ~/.asoundrc ~/.pulse*

---

### Post by Awareness on 2009-04-12
> **crimsun said:**
> You should at least rm -f ~/.asoundrc ~/.pulse*

That worked allright! thanks :)

---

