---
title: "Step by Step guide to resolve Firefox crash in 7.1 (Gutsy)"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by BeanBoy on 2007-10-29
Hi,

I like ubuntu enough to have upgraded my initial dapper drake version to ubuntu gutsy 7.1 (By upgrade I mean a complete hard disk reformat and install).

I was disappointed to find I cannot now run Youtube videos in Firefox. It just crashes the whole pc and I can't get out of it without the power going off and on again. (anyone tell me how to do a force quit in this new version I'm grateful)

I have searched the forums but as yet have no luck in finding a satisfactory solution. I think its to do with flash. I've tried a few things. None have worked. 

For the avoidance of doubt please assume I have an absolutely plain vanilla install. What I want is a step by step process of what to do to get you tube videos running.

Many thanks in advance for all your kind help

---

### Post by It_Was_Luck on 2007-10-29
If you go to watch a youtube video doesn't it appear and say "You need to update to the newest version" Then it gives you a link?

If I remember correctly it did for me, then once you install the Java update youtube videos will work again. Also just clicking on the "exit" button should bring up the "force quit" option.

---

### Post by BeanBoy on 2007-10-29
Hi,

I'm sorry but it does not ask me to update the version. Also, it is not possible to move the mouse to click over the x to close button and hence force a quit. It is a true crash (every time).

Thanks...

---

### Post by virilc on 2007-11-01
To avoid restarting, kill the firefox processes.
First, get the PID of firefox (number on the left-most part of the list):

```
ps ax | grep firefox
```

Then kill the one with /usr/lib/firefox/firefox-bin:

 6952 ?        Ss     0:00 /bin/sh /usr/bin/firefox
 6964 ?        S      0:00 /bin/sh /usr/lib/firefox/run-mozilla.sh /usr/lib/firefox/firefox-bin
 6968 ?        Sl     0:30 /usr/lib/firefox/firefox-bin
 7034 pts/0    R+     0:00 grep firefox

```

kill 6968
```

Then you can use firefox again! :)

---

### Post by bashologist on 2007-11-01
When an animal becomes unresponsive and is freezing, you must put it down. Euthanize Firefox.

---

### Post by DonL on 2007-11-16
I got rid of the Microsoft Core Fonts from the "add/remove programs" and so far I can't make it crash. This was after  considering going to something like Mint with everything pre-configured. Time will tell if this was really the cause.
If it fails, I'll let you know.

---

### Post by DonL on 2007-11-18
So far so good.
I've tried to make Firefox crash just by doing all the normal things I used to do, but it seems to be fixed.
Looks like getting rid of the mscorefonts did it.
As an added bonus, the fonts I have now look better, even on my laptop.
Go figure.

---

### Post by santana on 2007-11-20
Hi, I had firefox crashes after an upgrade to gutsy, for me the fix was to reinstall flash. Didn't find anyone with the same exact problem so posting it here, so it will be somewhere.

---

### Post by arjanito on 2008-03-31
Hi there.completely remove Gnash and Flash Player.Then install Flash Player again .Works fine for me.

---

