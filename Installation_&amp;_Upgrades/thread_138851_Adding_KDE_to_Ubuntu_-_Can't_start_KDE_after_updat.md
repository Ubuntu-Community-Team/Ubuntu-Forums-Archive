---
title: "Adding KDE to Ubuntu - Can't start KDE after update"
date: 2006-03-02
forum: Installation &amp; Upgrades
---

### Post by preside on 2006-03-02
I have  added the KDE desktop files to my installation as per these commands, found on 

[COLOR="DeepSkyBlue"]http://blog.mypapit.net/2005/12/installing-kde-35-on-ubuntu-breezy-510.html[/COLOR]

**Login as root and run the following commands from the console**

wget [http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg](http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg)
apt-key add kubuntu-packages-jriddell-key.gpg

**Add the following lines to /etc/apt/sources.list**

# Ubuntu 5.10 KDE 3.5 Repository
deb [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) breezy main

**Run the following commands**

apt-get update
apt-get dist-upgrade

After I did this, I logged out and expected to be able to select my session at the login page. Nope. What did I do wrong?

---

### Post by aysiu on 2006-03-02
[QUOTE=preside]
After I did this, I logged out and expected to be able to select my session at the login page. Nope. What did I do wrong?[/QUOTE] Did you already have KDE installed? It seems those instructions just upgrade an existing KDE to version 3.5.

Try ```
sudo apt-get install kubuntu-desktop
```

---

### Post by Rouge8 on 2006-03-02
Also, I'd recommend changing the line in your sources.list to either:

```
deb http://kubuntu.org/packages/kde351 breezy main
```

That'll get you KDE 3.5.1 and this: 

```
deb http://kubuntu.org/packages/kde-latest breezy main
```

Will grab the latest version of KDE.

Of course, you'll still need to ```
sudo apt-get install kubuntu-desktop
```

The [Kubuntu website](http://kubuntu.org) provides new versions of KOffice, amaroK and KDE when they come out and have instructions explaining how to get them.

---

### Post by preside on 2006-03-02
I got back from a family skate on the Rideau Canal Skateway (google it) and found this advice. I followed it and, Voila! I had the option of choosing whichever desktop i wanted. Thanks Aysiu and Rouge8.

Paul

---

### Post by rzapeople on 2006-03-25
okay, I also wanna know something. I managed to install kubuntu and kde, but how do I update my sources.list so as to get updates for kubuntu and not for ubuntu? Or am I asking a dumb question?

---

