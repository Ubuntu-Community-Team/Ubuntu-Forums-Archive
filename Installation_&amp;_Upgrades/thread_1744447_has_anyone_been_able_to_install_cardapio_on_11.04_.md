---
title: "has anyone been able to install cardapio on 11.04 64 bit?"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by rvchari on 2011-04-30
hi,
i am a happy user of maverick 32 bit. i wish to upgrade to 64 bit natty for which i am presently trying it out by testing on the usb live stick. i am searching for cardapio (gnomenu like applet) for my awn which i am using in maverick. any idea how and where can i find the ppa or how to install ?

---

### Post by lechien73 on 2011-04-30
I've read of people who are using (or at least testing) cardapio with 11.04, so can you just install it using:

```
sudo add-apt-repository ppa:cardapio-team/unstable
sudo apt-get update
sudo apt-get install cardapio
```

---

### Post by garwol on 2011-05-21
its not working for me, when i try to add it to panel i got message that there was a problem with loading "OAFIID:GNOME_Cardapio" :|

---

### Post by tienhoait on 2011-06-08
```

sudo add-apt-repository ppa:cardapio-team/unstable
sudo apt-get update
sudo apt-get install cardapio

```

After using the command to install. you download file from [the link]("http://webupd8.googlecode.com/files/cardapio.tar.gz") here to extract and copy to folder.
```
~/.local/share/applications/
```

p/s: I'm not good at English so that you understand

source: [http://blog.laptrinh3c.com/s%E1%BB%AD-d%E1%BB%A5ng-classic-menu-trong-ubuntu-unity/](http://blog.laptrinh3c.com/s%E1%BB%AD-d%E1%BB%A5ng-classic-menu-trong-ubuntu-unity/)

---

