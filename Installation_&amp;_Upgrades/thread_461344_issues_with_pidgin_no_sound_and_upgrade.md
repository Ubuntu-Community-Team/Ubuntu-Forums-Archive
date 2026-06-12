---
title: "issues with pidgin no sound and upgrade"
date: 2007-06-01
forum: Installation &amp; Upgrades
---

### Post by asnd16 on 2007-06-01
Go a few issues, Pidgin I cannot get the sound to work I have even downloaded the sound files and put them in a dir and still no sound.   Second how am I to install the new version without the .deb?   I have the old version how do I upgrade the current version?

Also I have the error i get while trying to install deluge.  . when doing ./config I receive the following error and when I type make it cannot find the make file. 
The msgfmt command is required to build libpurple.  If it is installed
on your system, ensure that it is in your path.  If it is not, install
GNU gettext to continue.

---

### Post by sinzmanual on 2007-06-15
yeah.
i having this problem too..

---

### Post by NeoLithium on 2007-06-15
Have you tried going into Preferences -> Sound and then select: METHOD - Command and enter this in the sound command line: play %s

---

### Post by fernando_lopes_jr on 2007-07-19
Great NeoLithium's worked like a charm :D

---

### Post by letubenaiah on 2007-08-09
I'm also having trouble getting sound in pidgin.  I installed vs 2.1 from source and I used 
```

sudo apt-get build-dep gaim

```
to install all the dependencies.  I've also tried using the commands play, aplay, and bplay to get sound to work, but so far no luck.  What else could I do to fix this problem?

Thanks!
Benaiah

---

### Post by victorbrca on 2007-09-24
This resolved for me on Edgy

```
play %s
```

Vic.

---

### Post by Reculpine on 2008-04-16
The command one with play %s didn't work for me.I had issue getting music to play when I installed Gutsy Gibbon 7.10 64-bit. I ended up resolving it, but I remembered that in my research I saw a lot of mention about ALSA. Well, seeing that Pidgin messed up when I fixed my VLC sound, I thought they had to be connected, and I was right!

For me, the simple fix was to use the **ALSA** setting in Preferences>Sound instead of the command one.  I hope this may help some of you.

---

### Post by psychofish25 on 2008-05-08
> **Reculpine said:**
> The command one with play %s didn't work for me.I had issue getting music to play when I installed Gutsy Gibbon 7.10 64-bit. I ended up resolving it, but I remembered that in my research I saw a lot of mention about ALSA. Well, seeing that Pidgin messed up when I fixed my VLC sound, I thought they had to be connected, and I was right!

For me, the simple fix was to use the **ALSA** setting in Preferences>Sound instead of the command one.  I hope this may help some of you.

And how do I do that? I don't see that option.

---

### Post by victorbrca on 2008-05-08
> **psychofish25 said:**
> And how do I do that? I don't see that option.

Under the Method drop down menu

---

### Post by psychofish25 on 2008-05-08
> **victorbrca said:**
> Under the Method drop down menu

my only optinos are Command, No Sounds, and System Beep. I am running v 2.4.1.

---

### Post by victorbrca on 2008-05-08
> **psychofish25 said:**
> my only optinos are Command, No Sounds, and System Beep. I am running v 2.4.1.

Which Ubuntu version are you using?

---

### Post by psychofish25 on 2008-05-09
8.04 Lts

EDIT: I did a reinstall and now I have the extra options, i tried selecting ALSA and Automatic but still no sound. What is going on here?

---

### Post by victorbrca on 2008-05-13
> **psychofish25 said:**
> 8.04 Lts

EDIT: I did a reinstall and now I have the extra options, i tried selecting ALSA and Automatic but still no sound. What is going on here?


Sorry taking so long to reply. Can you take screenshots of your pidgin sound options and gnome sound preferences (System=>Preferences=>Sound)?


Vic.

---

### Post by letubenaiah on 2008-05-13
You've probably already checked this but one mistake I made for a while was not realizing that pidgin sounds were muted...Tools >> Mute Sounds

> **psychofish25 said:**
> 8.04 Lts

EDIT: I did a reinstall and now I have the extra options, i tried selecting ALSA and Automatic but still no sound. What is going on here?

---

### Post by Valacosa on 2008-05-18
> **letubenaiah said:**
> You've probably already checked this but one mistake I made for a while was not realizing that pidgin sounds were muted...Tools >> Mute Sounds
Thanks. That did it for me. 

Why are there TWO places to disable sounds? Argh.

---

### Post by kahram.yoon on 2008-05-23
I typed in sudo apt-get build-dep gaim in console and it replied saying:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

i typed in dpkg --configure -a
and got this in return:
dpkg: requested operation requires superuser privilege

I restarted my computer while installing the new upgrade(practically at the end) because it froze.

---

### Post by letubenaiah on 2008-05-24
> **kahram.yoon said:**
> I typed in sudo apt-get build-dep gaim in console and it replied saying:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

i typed in dpkg --configure -a
and got this in return:
dpkg: requested operation requires superuser privilege

I restarted my computer while installing the new upgrade(practically at the end) because it froze.

Run it using sudo:
```

sudo dpkg --configure -a
```

---

