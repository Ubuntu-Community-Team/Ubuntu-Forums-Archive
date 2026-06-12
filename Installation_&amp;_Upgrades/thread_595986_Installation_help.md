---
title: "Installation help"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by sagarin on 2007-10-29
i have installed Ubuntu Fiesty Fawn on my Laptop. It has Windows XP too.

 I am behind a proxy server that does not allow downloading packages. I can't download and install Wine. I have the wine setup package acquired from a friend. I also have Opera browser setup package. Can you help me in installing these two applications? 

Also can you give me some guidelines on how to install any application from such a package in Ubuntu, without connecting to the internet?

---

### Post by kingpoiuy on 2007-10-29
Your best bet is to get apt working for you behind your proxy.  I had this same problem a while back and can help you with it.  

Go to your terminal and type in:
```
sudo gedit /etc/apt/apt.conf
```

Then in that file you will want to type this in:
```
acquire::http::proxy "http://username:password@proxyname.com:port";
```

That will be the only thing in that file.  Save it and close it.  Then go back to terminal and type:
```
sudo apt-get update
```

Now you may use your "add and remove programs" or any other package installer.  

You can install wine with:
```
sudo apt-get install wine
```

Let me know if you have troubles

---

