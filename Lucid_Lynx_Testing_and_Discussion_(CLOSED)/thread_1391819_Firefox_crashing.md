---
title: "Firefox crashing"
date: 2010-01-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by henwyn on 2010-01-27
FF will not keep running for me under Lucid; just crashes and disappears which means I can't get online, can't install Opera and can't send in a bug report. I'm hoping that an upgrade will solve this or I may go for a re-install in case I screwed something up trying to improve graphics and video. Just wondered if anyone else has seen this. Running 64 bit Lucid Alpha 2.

---

### Post by phenest on 2010-01-27
Have you tried starting ff from a terminal to see if there's any errors?

---

### Post by jerrylamos on 2010-01-27
> **henwyn said:**
> FF will not keep running for me under Lucid; just crashes and disappears which means I can't get online, can't install Opera and can't send in a bug report. I'm hoping that an upgrade will solve this or I may go for a re-install in case I screwed something up trying to improve graphics and video. Just wondered if anyone else has seen this. Running 64 bit Lucid Alpha 2.

What video graphics do you have?  It matters.

Jerry

---

### Post by tawmas on 2010-01-27
I*have the same: Firefox does not start, or it crashes right after starting before displaying its window.

If invoked from the console, no error message is displayed. Nothing is logged to xsession-errors, either.

Something I*noticed while installing an unrelated package is that package firefox-3.5 and its dependencies are marked as "no longer required":

```
The following packages were automatically installed and are no longer required:
  libxklavier15 xulrunner-1.9.1-gnome-support libboost-iostreams1.38.0 python-nose
  libboost-thread1.38.0 firefox-3.5 firefox-3.5-branding firefox-3.5-gnome-support libfaad0
Use 'apt-get autoremove' to remove them.
```

This appears erroneous in light of the following apt-cache output:

```
tawmas@tylke:~$ apt-cache policy firefox
firefox:
  Installed: 3.6+nobinonly-0ubuntu1
  Candidate: 3.6+nobinonly-0ubuntu1
  Version table:
 *** 3.6+nobinonly-0ubuntu1 0
        500 http://archive.ubuntu.com lucid/main Packages
        100 /var/lib/dpkg/status
tawmas@tylke:~$ apt-cache policy firefox-3.5
firefox-3.5:
  Installed: 3.6+nobinonly-0ubuntu1
  Candidate: 3.6+nobinonly-0ubuntu1
  Version table:
 *** 3.6+nobinonly-0ubuntu1 0
        500 http://archive.ubuntu.com lucid/main Packages
        100 /var/lib/dpkg/status
tawmas@tylke:~$ apt-cache policy firefox-3.6
firefox-3.6:
  Installed: (none)
  Candidate: (none)
  Version table:
```

If I can read this, Firefox 3.6 is provided by package firefox-3.5 and uninstalling it will remove Firefox altogether.

---

### Post by tawmas on 2010-01-27
> **jerrylamos said:**
> What video graphics do you have?  It matters.

```
tawmas@tylke:~$ sudo lspci -v | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9400 GT] (rev a1)
```

Using 190.53 nVidia driver from the Lucid repositories (package nvidia-current version 190.53-0ubuntu9).

---

### Post by dino99 on 2010-01-27
few days ago, i was having troubles with sound, wine and memory crashs. I was suspected alsa/pulseaudio but purging them and reinstalling did not help.

So, i ran "bleachbit" with admin rights (apps --> system --> bleachbit as root), then my system was very stable and fast.

Be aware about bleachbit, it known how to clean your system but it's so powerfull that it can wipe definitively your data, so you must understand what you ask him to do before pulling down "enter" ( you can preview before applying)

---

### Post by coral66 on 2010-01-27
Not sure of the syntax, but have you looked into using curl or wget to download another browser.

I found this, it might be worth a go, not using Ubuntu at the moment, so I can't try it myself!

From a terminal window ...

wget [http://www.opera.com/download/index.dml?platform=linux](http://www.opera.com/download/index.dml?platform=linux)

Just found this ([http://my.opera.com/desktopteam/blog/happy-new-year](http://my.opera.com/desktopteam/blog/happy-new-year))

curl [http://snapshot.opera.com/unix/labs-6177/opera-10.50-6177.linux.i386.tar.bz2](http://snapshot.opera.com/unix/labs-6177/opera-10.50-6177.linux.i386.tar.bz2) | tar xjf -

cd opera-10.50-6177.linux.i386/

./opera &

---

### Post by musaul on 2010-01-28
I did a full update on lucid on the 27th. Firefox 3.6 doesn't normally start.

What I have to do is run the Mozilla 3.7 nightly build I downloaded last week, exit it, and then run 3.6.

If I exit 3.6 and try to run it again, it doesn't work. I have to do the whole process again.

Anybody found out what prevents 3.6 from just running? I had a look a the logs and whatnot, but couldn't find anything.

---

### Post by ranch hand on 2010-01-28
If you go to synaptic and search for "browser" you will get several choices.

I didn't look paste epiphany bout also saw abrowser (stripped FF) and chromium-browser.

---

### Post by tawmas on 2010-01-28
> **ranch hand said:**
> If you go to synaptic and search for "browser" you will get several choices.

I didn't look paste epiphany bout also saw abrowser (stripped FF) and chromium-browser.

hum... I do want Firefox, though! I'm going to try a little bit harder and the file a bug.

---

### Post by emarkay on 2010-01-28
Might this be the same issue?

I was working with a developer up to about a month ago, but there were problems with "Apport" that prevented them getting any data.

[http://ubuntuforums.org/showthread.php?t=1305002](http://ubuntuforums.org/showthread.php?t=1305002)

---

### Post by tawmas on 2010-01-28
OK, I'm onto something here. I used

```
firefox -ProfileManager
```

to create a new profile, and Firefox starts correctly, but, when closed, it doesn't restart, neither with the old profile nor with the new one.

So, it occurred to me that my true .mozilla directory is inside my encrypted private folder, and my ~/.mozilla is just a symlink to that. I deleted the symlink and copied the mozilla folder back to my home, and now Firefox can start with the new profile.

I hope this helps some of you, and at least I have more data for a sensible bug report. I'll keep you posted.

---

### Post by henwyn on 2010-01-29
Sorry I started this and then didn't get back. I got snowed at work, which happens. Anyway, Firefox is working for me again under Lucid after updating everything this evening. That was what I hoped would happen. Tawmas, I really appreciated your posts and your thinking about ways to get around the problem. Thanks. And thanks to everyone who responded for your input. This really seemed like something indirectly affecting Firefox being broken in the upgrade process and hopefully now it's fixed.

---

### Post by caryb on 2010-01-29
Strange my 3.6 is fine but 3.7 is pooched on my system.





Cary

---

### Post by zika on 2010-01-29
> **caryb said:**
> Strange my 3.6 is fine but 3.7 is pooched on my system.
Cary[I've just posted a question about 3.7...](http://ubuntuforums.org/showpost.php?p=8742064&postcount=378)

---

### Post by tghe-retford on 2010-01-29
I've noticed in the last day that 3.7 will crash if any Flash animation or video takes place on that page (using Flash 64-bit pre-release) which since yesterday will cause 3.7 to keel over. 3.6 is fine.

---

### Post by mdurham on 2010-01-29
> **tawmas said:**
> OK, I'm onto something here. I used

```
firefox -ProfileManager
```

to create a new profile, and Firefox starts correctly, but, when closed, it doesn't restart, neither with the old profile nor with the new one.

So, it occurred to me that my true .mozilla directory is inside my encrypted private folder, and my ~/.mozilla is just a symlink to that. I deleted the symlink and copied the mozilla folder back to my home, and now Firefox can start with the new profile.

I hope this helps some of you, and at least I have more data for a sensible bug report. I'll keep you posted.

That's interesting. I have the same problem of it only working once, but my home directory is on another partition accessed via a link. Maybe it's  because of the link?

---

### Post by jerrylamos on 2010-01-29
> **tghe-retford said:**
> I've noticed in the last day that 3.7 will crash if any Flash animation or video takes place on that page (using Flash 64-bit pre-release) which since yesterday will cause 3.7 to keel over. 3.6 is fine.

2.6.32-12 and Firefox 3.6 plays video to the end of the segment then hangs altogether.  Force quit time. 

This is 32 bit VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]

I don't think that happened with 2.6.32-11 maybe I'll check.

Jerry

---

### Post by mdurham on 2010-01-29
FF 3.6 doesn't start if I access my home through /home/link-to-mike. If I access my home in /home/mike it works okay.
What does it all mean?

---

### Post by Hallavej on 2010-01-31
I think add-ons may be the problem. I deleted .mozilla and removed all plugins and extensions. Then firefox worked again.

---

### Post by mdurham on 2010-01-31
> **Hallavej said:**
> I think add-ons may be the problem. I deleted .mozilla and removed all plugins and extensions. Then firefox worked again.

But does it keep working if you log out and log in again? It doesn't for me.

---

### Post by Hallavej on 2010-01-31
> **mdurham said:**
> But does it keep working if you log out and log in again? It doesn't for me.

It keeps working here.

---

