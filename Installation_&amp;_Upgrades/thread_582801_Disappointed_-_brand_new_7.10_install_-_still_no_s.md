---
title: "Disappointed - brand new 7.10 install - still no sound from utube in Firefox !!"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by ubnewbie2 on 2007-10-20
This was a problem I had in Feisty, and never really solved.  I had hopes that something that would be so commonly used, would be fixed in 7.10.  

But, on a completely clean install of 7.10 - nothing but silence from flash playing in utube under Firefox.:(

---

### Post by Arenlor on 2007-10-20
I do not get this problem, what flash player is installed?

---

### Post by shad0w_walker on 2007-10-20
This looks more like a problem specific to you. I have been quite happily using flash and youtube with sound for the last few releases.

---

### Post by ubnewbie2 on 2007-10-20
> **Arenlor said:**
> I do not get this problem, what flash player is installed?

Whichever one they bundled with restricted apps bundle.

---

### Post by ubnewbie2 on 2007-10-20
> **shad0w_walker said:**
> This looks more like a problem specific to you. I have been quite happily using flash and youtube with sound for the last few releases.

Nope, not specific to me.  When I was fighting it with Feisty, many others were having the same problem.

Anyway, how can it be specific to me? It's nothing to do with hardware, and ALL the software is bog standard as delivered by Ubuntu?

---

### Post by Arenlor on 2007-10-20
Is it the Adobe one then? Try to uninstall it and install the GNU version.

---

### Post by ubnewbie2 on 2007-10-20
> **Arenlor said:**
> Is it the Adobe one then? Try to uninstall it and install the GNU version.

Great suggestion.  I was not even aware of the gnu version, gnash. I uninstalled adobe's, and installed gnash.

It is alpha quality, but at least it does have sound.

---

### Post by Arenlor on 2007-10-20
You could check to see if a newer version of Adobe will have sound maybe (reinstall it and check, if it doesn't you know the solution, if it does then well it works)

---

### Post by floke on 2007-10-20
System/Preferences/Sound/Sounds - uncheck (or check - can't remember which!) Enable software sound mixing. Only problem is that this turns off your system sounds so remember to reverse the procedure when you're done with youtube.

---

### Post by dummy_online on 2007-10-20
```
 mv ~/.asoundrc .asoundrc.old
 mv ~/.asoundrc.asoundconf ~/.asoundrc.asoundconf.old
```

---

### Post by ubnewbie2 on 2007-10-20
> **floke said:**
> System/Preferences/Sound/Sounds - uncheck (or check - can't remember which!) Enable software sound mixing. Only problem is that this turns off your system sounds so remember to reverse the procedure when you're done with youtube.

Actually it doesn't make any difference.  No sound either way from Adobe.

---

### Post by ubnewbie2 on 2007-10-20
> **dummy_online said:**
> ```
 mv ~/.asoundrc .asoundrc.old
 mv ~/.asoundrc.asoundconf ~/.asoundrc.asoundconf.old
```

Neither of these files exist.

---

### Post by mgmiller on 2007-10-20
Do you have the ubuntu-restricted-extras package installed?  This worked for me.

---

### Post by firstcupoffreshpressed on 2007-10-20
I have no sound or picture in video with Gutsy 7.10. I have installed all the codecs. I installed gnash because neither gnash nor flash was installed on my clean install gutsy.

With the Gutsy beta I had picture but no sound

In Feisty I had both picture and sound

For a while I thought the problem was a conflict between pulse audio and alsa.

Now I am going to try going back to the non free flash and see if that works.

---

### Post by firstcupoffreshpressed on 2007-10-20
update:  My problem seems to be solved by uninstalling gnash.  IT then found that the mozilla flash plugin was already installed.

I now have sound and picture in google video.

Another time I will try uninstalling the flash plugin and substituting gnash
                                                                      .:guitar:

---

### Post by neoroses on 2007-10-20
ok hopefully:

for your flash sound problem: 

[http://ubuntuforums.org/showthread.php?t=255422&highlight=sound+in+flash]("http://ubuntuforums.org/showthread.php?t=255422&highlight=sound+in+flash")

and for the no sound atall try:

[http://ubuntuforums.org/showthread.php?t=515578](http://ubuntuforums.org/showthread.php?t=515578)

and use VLC

hope this helps

---

### Post by thompson42 on 2007-10-21
> **dummy_online said:**
> ```
 mv ~/.asoundrc .asoundrc.old
 mv ~/.asoundrc.asoundconf ~/.asoundrc.asoundconf.old
```

Thanks for this, it solved the problem for me.

---

