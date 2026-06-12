---
title: "Chrome Installation error: Wrong architechture"
date: 2011-05-07
forum: Installation &amp; Upgrades
---

### Post by anohs on 2011-05-07
I just installed ubuntu 11.04 and when trying to install google chrome on it, I am been told by Ubuntu software center that "Wrong architecture 'i386'"

I downloaded 32 bit setup from google website.

please help

---

### Post by Paddy Landau on 2011-05-07
You don't want Google Chrome; you want Chromium, which is the Linux version. Also, you don't want to download it. Ubuntu Software Centre handles this for you (amongst other useful and important actions).


[LIST=1]
[*]Go to your Ubuntu Software Centre.
[*]Search for Chrome (search bar in the top right).
[*]Look for Chromium Web Browser in the list.
[*]Press the Install button.
[/LIST]

It's that easy.

---

### Post by Frogs Hair on 2011-05-07
The correct package for your architechture should be detected when installing from the software center . Try as Paddy suggested and report back.

---

### Post by oldos2er on 2011-05-07
> **anohs said:**
> I just installed ubuntu 11.04 and when trying to install google chrome on it, I am been told by Ubuntu software center that "Wrong architecture 'i386'"

I downloaded 32 bit setup from google website.

please help

Go here [http://www.google.com/chrome/eula.html?platform=linux](http://www.google.com/chrome/eula.html?platform=linux) and choose 64-bit

---

### Post by yugnip on 2012-01-01
Chromium is a good option, and available for easy install using Software Center. If you however want Chrome, it's pretty easy to install.

Download the .deb for your architecture, 32 or 64 bit, to your Downloads folder. Then, assuming you have no other .debs in your download folder:

```
cd Downloads
sudo dpkg -i *.deb
```

If you are storing or have other .debs in Downloads, you will need to change the *.deb to the name of the actual Chrome .deb.

Hope this helps.

---

### Post by rockaday on 2012-02-20
> **yugnip said:**
> Chromium is a good option, and available for easy install using Software Center. If you however want Chrome, it's pretty easy to install.

Download the .deb for your architecture, 32 or 64 bit, to your Downloads folder. Then, assuming you have no other .debs in your download folder:

```
cd Downloads
sudo dpkg -i *.deb
```

If you are storing or have other .debs in Downloads, you will need to change the *.deb to the name of the actual Chrome .deb.

Hope this helps.

Thanks for this - just helped me out with installing the latest version of Chrome.  I had a problem with Chromium a while back, but everything works in Chrome so I'm using that for now.  I'll pick up the latest Chromium and try it again at some point.

---

