---
title: "Skype"
date: 2008-04-20
forum: Installation &amp; Upgrades
---

### Post by Dyffo on 2008-04-20
Have just installed the latest version of Skype - no problems works very well except still no SMS !!.
Question is - when I was installing this it said it was installing in "download". This file cannot be found , also when I visit Add/ Remove programmes it is not there. so WHERE IS IT , can't find it anywhere on my system. If I go to " Applications" Internet sure there it is for me to open. But what if I want TO REMOVE IT. Nothing drastic here just annoying.:confused:

---

### Post by TheWizzard on 2008-04-20
> **Dyffo said:**
> Have just installed the latest version of Skype - no problems works very well except still no SMS !!.
Question is - when I was installing this it said it was installing in "download". This file cannot be found , also when I visit Add/ Remove programmes it is not there. so WHERE IS IT , can't find it anywhere on my system. If I go to " Applications" Internet sure there it is for me to open. But what if I want TO REMOVE IT. Nothing drastic here just annoying.:confused:

what is the result of:
```
aptitude search skype
```

---

### Post by TheWizzard on 2008-04-20
> **Dyffo said:**
> Have just installed the latest version of Skype - no problems works very well except still no SMS !!.
Question is - when I was installing this it said it was installing in "download". This file cannot be found , also when I visit Add/ Remove programmes it is not there. so WHERE IS IT , can't find it anywhere on my system. If I go to " Applications" Internet sure there it is for me to open. But what if I want TO REMOVE IT. Nothing drastic here just annoying.:confused:

wait. how did you install skype in the first place???

---

### Post by Dyffo on 2008-04-20
Installed Skype direct from their website. In firefox opened Skype for Linux - downloaded latest version. Hope this helps

---

### Post by Fedz on 2008-04-20
> **TheWizzard said:**
> wait. how did you install skype in the first place???

You'd be surprised how Ubuntu gets around ;)

[http://www.skype.com/intl/en-gb/download/skype/linux/choose/](http://www.skype.com/intl/en-gb/download/skype/linux/choose/)

---

### Post by Sim777 on 2008-04-20
> **Fedz said:**
> You'd be surprised how Ubuntu gets around ;)

[http://www.skype.com/intl/en-gb/download/skype/linux/choose/](http://www.skype.com/intl/en-gb/download/skype/linux/choose/)

What about poor soobs who can't do 386? Is there a way around it?

---

### Post by mikewhatever on 2008-04-20
You should be able to remove skype with <sudo dpkg -r skype>, and if you have to know, most of it is in /usr/share.

---

### Post by TheWizzard on 2008-04-21
> **Dyffo said:**
> Installed Skype direct from their website. In firefox opened Skype for Linux - downloaded latest version. Hope this helps

next time install packages from the repo's using aptitude! 
this allows you to remove packages easy. including the dependencies you installed.

---

### Post by TheWizzard on 2008-04-21
> **Fedz said:**
> You'd be surprised how Ubuntu gets around ;)


mmm, i'm afraid you didn't get my question. at least i don't understand your answer.

---

