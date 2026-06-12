---
title: "Installing Kubuntu-desktop (KDE)"
date: 2008-03-12
forum: Installation &amp; Upgrades
---

### Post by CONCORAN on 2008-03-12
Hello,
I installed Ubuntu using the download CD (Live CD). But it doesn't have KDE. 

So, I downloaded Ubuntu DVD.. It was quite a fun to find Ubuntu DVD image, since Ubuntu website doesn't take me to DVD download (at least I couldn't figure that out). So, only a google search 'Ubuntu  DVD' took me to the website where I finally downloaded Ubuntu DVD.

Now that I have DVD,  kubuntu-desktop doesn't appear in 'add/remove' programs. Is it possible to install KDE without haaving to install fresh Ubuntu?

---

### Post by zxscooby on 2008-03-12
Yes,

You can install it with the package manager 

or
sudo apt-get install kubuntu-desktop

check out the documentation first.

[https://help.ubuntu.com/community/InstallingKDE?highlight=%28kde%29%7C%28install%29](https://help.ubuntu.com/community/InstallingKDE?highlight=%28kde%29%7C%28install%29)

---

### Post by angry_johnnie on 2008-03-12
just make sure all your repositories have been enabled, and then do what zxscooby suggested.

---

### Post by _xray7224 on 2008-03-12
To install more desktop environments on Ubuntu you need to make sure you have told it ware to look so make sure all the repositories are enabled check this by going to the source.list fine in 

```
/etc/apt/source.list
```

then go to terminal and type:

```
sudo -i
[password]
apt-get install kubuntu-desktop
```

then just let it install

---

