---
title: "skype installation"
date: 2013-11-28
forum: Installation &amp; Upgrades
---

### Post by DaSkinna on 2013-11-28
I have a notebook running Ubuntu 12.04 can anyone tell me if you can install Skype and how to do so, I'm quite new to Ubuntu 12 so can you please explain in noob speak :p

---

### Post by ansus on 2013-11-28
Hi DaSkinna,
I am new to Ubuntu also. I have 13.10 dual boot windows 8.1 on the desktop and 12.04 LTS on a very old lap top. Both have Skype in Ubuntu now. I just went to the Skype web page when using the Ubuntu operating system and it had a selection for Ubuntu distribution and I downloaded that. It installed under the Software Centre. Below is the Link to Skype, you then select your distribution. Hope this helps.
[http://www.skype.com/en/download-skype/skype-for-linux/](http://www.skype.com/en/download-skype/skype-for-linux/)

---

### Post by fantab on 2013-11-28
> **DaSkinna said:**
> I have a notebook running Ubuntu 12.04 can anyone tell me if you can install Skype and how to do so, I'm quite new to Ubuntu 12 so can you please explain in noob speak :p

Open 'Software Center' ->Edit -> Software sources -> Other Software -> select/check 'Canonical Partners' and 'Independent'. Close Software Center. Open Terminal [ctrl+alt+t] and run the following commands:

```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install skype
```

Always install software from Ubuntu repositories in Software Center, if available. The applications in 'Software Center' are TESTED on Ubuntu version you are using. Installing software from other sources CAN cause problems.

---

