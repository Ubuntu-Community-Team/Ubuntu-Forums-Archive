---
title: "Where does all software downloaded with synaptic goes?"
date: 2008-06-30
forum: Installation &amp; Upgrades
---

### Post by clayder on 2008-06-30
Hello:

I just would like to know, where(path) ubuntu install software, downloaded through typing 'apt-get install ...'?

Most of times, I use synaptic package manager; however, I don't where all files of the downloaded software goes.

Thanks for your time.

---

### Post by iaculallad on 2008-06-30
> **clayder said:**
> Hello:

I just would like to know, where(path) ubuntu install software, downloaded through typing 'apt-get install ...'?

Most of times, I use synaptic package manager; however, I don't where all files of the downloaded software goes.

Thanks for your time.

Browse to this directory:

> /var/cache/apt/archives

This is where your packages are downloaded.

---

### Post by oldos2er on 2008-06-30
> **clayder said:**
> Hello:

I just would like to know, where(path) ubuntu install software, downloaded through typing 'apt-get install ...'?

Most of times, I use synaptic package manager; however, I don't where all files of the downloaded software goes.

Thanks for your time.

 In Synaptic, right-click on an installed package, choose Properties, Installed Files. This will tell you the installation path of each file in the package.

---

### Post by philk949 on 2008-07-07
Hi,
I was having the same problem locating packages installed by the Synaptic Manager, but now have located them. Thank you. The problem now is how to extract and access them for use.

philk949

---

### Post by muteXe on 2008-07-07
Synaptic does this automatically doesn't it?

---

### Post by BlueSkyNIS on 2008-07-07
> **iaculallad said:**
> Browse to this directory:

```
/var/cache/apt/archives
```

This is where your packages are downloaded.

I went there and found over 150Mb of *.deb files. Can I delete those *.deb files?

---

### Post by muteXe on 2008-07-07
And if you mean you've dl'd and installed stuff with Synaptic, but nothing new is added to the menus, you might want to read this post:

[http://ubuntuforums.org/showthread.php?t=2985&highlight=add%2Fremove](http://ubuntuforums.org/showthread.php?t=2985&highlight=add%2Fremove)

---

