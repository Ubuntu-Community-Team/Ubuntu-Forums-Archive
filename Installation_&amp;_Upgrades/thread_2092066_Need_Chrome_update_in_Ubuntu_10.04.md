---
title: "Need Chrome update in Ubuntu 10.04"
date: 2012-12-06
forum: Installation &amp; Upgrades
---

### Post by jtheb on 2012-12-06
Chrome is not updating in Ubuntu 10.4 
My  version is 18.0.1025.168 (Developer Build 134367 Linux) Ubuntu 10.04

My Ubuntu version in12.04 is 20.+
My Mac version is 22.+

Anyone know the reason for this?

---

### Post by kostkon on 2012-12-06
Is it chrome or chromium? If it's chrome, how did you install it?

I'm asking this because when you download and install chrome from google it automatically adds its repository (to your software sources list) and you get frequent updates. Actually, the stable chrome in linux is in version 23
```
~:$apt-cache policy google-chrome-stable 
google-chrome-stable:
  Installed: (none)
  Candidate: 23.0.1271.95-r169798
  Version table:
     23.0.1271.95-r169798 0
        500 http://dl.google.com/linux/chrome/deb/ stable/main Packages
```
I have chrome beta in my 10.04 and I get an update every 2-3 days
```
~:$apt-cache policy google-chrome-beta 
google-chrome-beta:
  Installed: 24.0.1312.32-r170871
  Candidate: 24.0.1312.32-r170871
  Version table:
 *** 24.0.1312.32-r170871 0
        500 http://dl.google.com/linux/chrome/deb/ stable/main Packages
        100 /var/lib/dpkg/status
```

---

### Post by jtheb on 2012-12-06
Thanks
Don't know the difference between Chrome and Chromium
But I do have Chrome
Thought I installed from Synaptic
Was going to do a PPA but then thought since 10.04 is coming to the end maybe they didn't want to mess with it

---

### Post by kostkon on 2012-12-06
Hmm, try this:
in the terminal, type google-chrome and then press the tab key twice to see all the available options and then do a apt-cache policy on them and paste the output(s) here if you want.

---

### Post by jtheb on 2012-12-06
Sorry 
no output with that command
used tab key twice
not familiar with that one

---

### Post by kostkon on 2012-12-06
Actually, I think you have chromium, so if you do a
```
apt-cache policy chromium-browser
```
you should see an output.

---

### Post by jtheb on 2012-12-06
john@Kahuna:~$ apt-cache policy chromium-browser
chromium-browser:
  Installed: 18.0.1025.168~r134367-0ubuntu0.10.04.1
  Candidate: 18.0.1025.168~r134367-0ubuntu0.10.04.1
  Version table:
 *** 18.0.1025.168~r134367-0ubuntu0.10.04.1 0
        500 [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) lucid-updates/universe Packages
        100 /var/lib/dpkg/status
     18.0.1025.151~r130497-0ubuntu0.10.04.1 0
        500 [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) lucid-security/universe Packages
     5.0.342.9~r43360-0ubuntu2 0
        500 [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) lucid/universe Packages

---

### Post by kostkon on 2012-12-06
So, you could stay with chromium or [download chrome]("http://www.google.com/chrome"). Just be warned that flash might not work in chrome (only happens in 10.04, but lucid will become EOL pretty soon anyway).

Hope that helps.

---

### Post by jtheb on 2012-12-07
Thanks
From Iowa USA

---

