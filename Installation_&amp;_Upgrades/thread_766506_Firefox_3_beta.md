---
title: "Firefox 3 beta ???"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by Sale on 2008-04-25
Hi,

I've just upgraded to Hardy and...everything seems to have worked out well so far, except that I now have Firefox 3 Beta 2 as my default browser, even though Synaptic says there is beta 5 in the repository. I've tried to reinstall from Synaptic but it's still beta 2. 

What is wrong? I'd like to have my Beta 5 back, please :)

BTW, my VLC media player also doesn't work - when I click on it, I only get the skin (not the default one that I only used before) which does nothing.
Synaptic reinstalation also didn't help.

---

### Post by giumbolo on 2008-04-25
Sale, I've just installed Hardy on a new disk. I have Mozilla Firefox 3 beta 5. So it is reported by the Help aBout. Frankly speaking the title of the frame where I'm writing from says "[ubuntu] Firefox 3 beta ??? - Ubuntu Forums - Mozilla Firefox 3 Beta 5".
May be you're misled by the title, but you've the beta 5 ...

---

### Post by Sale on 2008-04-25
No...Sadly, both Help - About and the frame title say the same thing: "Firefox 3 Beta 2". Here is the screenshot:


Even more strange is that I used to run Beta 5 under Gutsy... :(

---

### Post by Sale on 2008-04-25
I have just discovered that I have the /usr/lib/firefox-3.0b5 directory but wheb I click on the firefox executable in it, the "beta 2" shows up.

BTW, my Java isn't working as well

---

### Post by giumbolo on 2008-04-25
In my same folder, the file application.ini reports ...
[App]
Vendor=Mozilla
Name=Firefox
<<<<< Version=3.0b5 >>>>>>>>>
BuildID=2008041514
Copyright=Copyright (c) 1998 - 2008 mozilla.org
ID={ec8030f7-c20a-464f-9b0e-13a3a9e97384}

---

### Post by Sale on 2008-04-25
> **giumbolo said:**
> In my same folder, the file application.ini reports ...
[App]
Vendor=Mozilla
Name=Firefox
<<<<< Version=3.0b5 >>>>>>>>>
BuildID=2008041514
Copyright=Copyright (c) 1998 - 2008 mozilla.org
ID={ec8030f7-c20a-464f-9b0e-13a3a9e97384}

The same here... :confused:

---

### Post by Sale on 2008-04-25
OK...it's solved now...

I uninstalled firefox thru synaptic but the icon was still on the launcher panel. And FF Beta 2 was still starting when I clck on it.

Than I did "which firefox" in terminal, and...

There was a symlink im /usr/bin pointing to /opt/firefox/firefox and that was what was being started all the time. I'm guessing it was a leftower from an earlier installation of FF beta 2. Strangely, Synaptic/apt was completelly unaware of this one. I manually deleted the symlink and /opt/firefox/ folder, Reinstalled Firefox with Synaptic...but the launcher still didn't work. It still ponted to the old FF. After I manually edited the launcher to point to /usr/lib/firefox-3.0b5/firefox, everything seems to be fine now.

---

