---
title: "How to set Firefox to open PDF on browser"
date: 2006-10-19
forum: Installation &amp; Upgrades
---

### Post by textguru on 2006-10-19
I have Firefox 1.5.0.7 installed on xubuntu machine. How do I set firefox to automatically open PDF files with evince?

---

### Post by pay on 2006-10-19
To install acrobat with a plugin for firefox would be ```
sudo apt-get install acroread mozilla-acroread acroread-plugins
```

---

### Post by textguru on 2006-10-19
I already have the .deb files:

acroread_7.0.1-0.0.ubuntu1_i386.deb
acroread-plugins_7.0.1-0.0.ubuntu1_i386.deb

if I do the apt-get install, it will get the update from the internet. How do I install acrobat reader without going to the internet?

---

### Post by pay on 2006-10-19
If the deb files are in your home folder then```
sudo dpkg -i acroread_7.0.1-0.0.ubuntu1_i386.deb
sudo dpkg -i acroread-plugins_7.0.1-0.0.ubuntu1_i386.deb
```

---

### Post by textguru on 2006-10-19
Is it only acrobat reader can automatically open pdf files? can Evince cannot do this?

---

### Post by crumja on 2006-10-19
Evince currently doesn't play very nicely with firefox.

[http://ubuntuforums.org/archive/index.php/t-25685.html](http://ubuntuforums.org/archive/index.php/t-25685.html) is about as good as you'll get (maybe [http://handlet.blogspot.com/2006/07/wsop-first-screen-shot-of-evince_20.html)](http://handlet.blogspot.com/2006/07/wsop-first-screen-shot-of-evince_20.html)).

It's a pity b/c acroread is a terrible package.

---

### Post by textguru on 2006-10-20
> **crumja said:**
> Evince currently doesn't play very nicely with firefox.

[http://ubuntuforums.org/archive/index.php/t-25685.html](http://ubuntuforums.org/archive/index.php/t-25685.html) is about as good as you'll get (maybe [http://handlet.blogspot.com/2006/07/wsop-first-screen-shot-of-evince_20.html)](http://handlet.blogspot.com/2006/07/wsop-first-screen-shot-of-evince_20.html)).

It's a pity b/c acroread is a terrible package.

I have tried installing mozplugger and modify the file that  is stated on the thread but pdf doesn't open. I've tried to restart the machine but still it doesn't work. I only see blank display.

---

### Post by textguru on 2006-10-23
Any solution on this? :confused:

---

### Post by textguru on 2006-10-31
Hey guys!

I really need solution on this problem. Hoping for your response.

---

### Post by SebMKd on 2007-04-28
I have the same problem.
I've downloaded all acroread Deb files (and a newer mozplugin; it seems that I needed a version > 1.7.2) and installed them successfully. 
But still not possible to open PDF in Firefox 2.0!

Anybody has an answer?

---

