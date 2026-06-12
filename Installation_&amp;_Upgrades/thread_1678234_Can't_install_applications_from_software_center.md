---
title: "Can't install applications from software center"
date: 2011-01-30
forum: Installation &amp; Upgrades
---

### Post by ranjix on 2011-01-30
Need help installing applications from software center. Recently, software center has been showing an error and can't install any applications through it. Here is screen shot of that error.

---

### Post by mörgæs on 2011-01-30
Can you install the same packages through Synaptic?

---

### Post by ranjix on 2011-01-30
yes. can download through synaptic..

---

### Post by JOHNNYG713 on 2011-01-30
Than download via **synaptic** ! **Much MUCH faster** !! U.S.C. **SUCKS** !!! (IMHO!)):P

---

### Post by sikander3786 on 2011-01-30
> **ranjix said:**
> yes. can download through synaptic..
Please post the _complete_ output of following command from Applications > Accessories > Terminal.

```
sudo apt-get update
```

While posting, click the # icon in post menu and paste your text in between the generated [code] tags.

---

### Post by ranjix on 2011-01-31
Complete output of code: "sudo apt-get update "
```

$ sudo apt-get update
Hit http://us.archive.ubuntu.com maverick Release.gpg  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick-updates Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick-security Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick Release
Hit http://us.archive.ubuntu.com maverick-updates Release
Hit http://us.archive.ubuntu.com maverick-security Release
Hit http://us.archive.ubuntu.com maverick/main i386 Packages
Hit http://us.archive.ubuntu.com maverick/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick/universe i386 Packages
Hit http://us.archive.ubuntu.com maverick/multiverse i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/main i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/multiverse i386 Packages
Hit http://us.archive.ubuntu.com maverick-security/main i386 Packages
Hit http://us.archive.ubuntu.com maverick-security/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick-security/universe i386 Packages
Hit http://us.archive.ubuntu.com maverick-security/multiverse i386 Packages
Reading package lists... Done 



```

---

### Post by mörgæs on 2011-01-31
Good. Then if you afterwards run **sudo apt-get upgrade** your system will be updated. 

Together with Synaptic these two commands (and **sudo apt-get clean** for cleaning up) are all that is needed for package management. 


Software Centre is slow and buggy. Best is to forget about this one.

---

### Post by ranjix on 2011-02-01
Software Center is working well again. Is it due to that command??

---

### Post by mörgæs on 2011-02-01
Maybe. It is possible that you have installed a bug fix for Software Centre in the process.

---

### Post by ranjix on 2011-02-05
Oohh!! good then!!

---

