---
title: "Firefox won't open with the latest updates...?!"
date: 2010-03-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Nickedynick on 2010-03-23
I've just updated my Lucid install, had to restart for the new kernel, and when I got back Firefox refused to open. Has anyone else experienced this?! The lock file doesn't seem to be in my /home/nick/.mozilla/firefox/ folder, and trying to run it via the terminal yields no output at all. :S

---

### Post by philinux on 2010-03-23
> **Nickedynick said:**
> I've just updated my Lucid install, had to restart for the new kernel, and when I got back Firefox refused to open. Has anyone else experienced this?! The lock file doesn't seem to be in my /home/nick/.mozilla/firefox/ folder, and trying to run it via the terminal yields no output at all. :S

Odd indeed. No problems here at all. Try another reboot.

---

### Post by Nickedynick on 2010-03-23
Just gave that a try, to no avail. I'm glad I installed Chromium on here now, as much as I'm not a huge fan!

Strangely, it's not even showing up then vanishing from system monitor - it's just not there at all.

*EDIT: Just gave "firefox --profilemanager" a go - seems my profile has screwed up somehow.*

---

### Post by EzraReeves on 2010-03-23
I am getting this as well. When I use --profilemanager it will only open if I create a new profile, then if I close Firefox and try to use that profile again I get the same problem as before. I have to create a new profile every time I open Firefox.

---

### Post by Nickedynick on 2010-03-23
Removed the solved tag, I'm getting the same problem as you now. I thought it was just a problem with one of my extensions, but it's obviously not the case now.

---

### Post by _h_ on 2010-03-23
Have you tried a complete removal of Firefox (including all profile information), and installing a fresh new copy of FF?

---

### Post by Nickedynick on 2010-03-23
Not yet, I'll give that a go and report back...

---

### Post by hexion on 2010-03-23
This might help:
[http://ubuntuforums.org/showthread.php?t=1407753](http://ubuntuforums.org/showthread.php?t=1407753)

Delete file compatibility.ini and start again.

---

### Post by xebian on 2010-03-23
Is this the new FF 3.6.2 released today?

---

### Post by Nickedynick on 2010-03-23
Running "firefox -safe-mode", closing then trying again normally seemed to do the trick for me.

---

### Post by lovinglinux on 2010-03-24
If you have Prism installed, remove it. It is causing exactly that problem with Firefox 3.6. Firefox doesn't start and doesn't output any errors in the terminal.

---

### Post by Nickedynick on 2010-03-24
Good work, sir! There is a [Prism add-on]("https://addons.mozilla.org/en-US/firefox/addon/6665") for Firefox now, which seems to avoid this problem.

---

### Post by BavarianPH on 2010-03-24
Namoroka (Firefox) version 3.6.3pre, from  

[http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu)

works fine.

And just now discovered a new Firefox update,

but I cannot try it because I am writing to this forum right now.

BavarianPH,
Ubuntu forever!

---

### Post by rockyjones on 2010-03-25
I have the problem of Firefox not starting if I try to run it with a symlink to the .mozilla directory.  I keep all my data on a separate partition and use symlinks in the home directory pointing to Thunderbird, Pictures, Downloads, etc.  When Firefox 3.6 came out, it would no longer start when I used a symlink like previous versions would.  I had to move my .mozilla file from my separate partition into my home directory for it to work.  Don't know why that is though.

Joe

---

### Post by mdurham on 2010-03-25
post #10 from [here]("http://ubuntuforums.org/showthread.php?t=1407753") fixed it for me.

---

