---
title: "Other distro installation from live cd"
date: 2012-05-02
forum: Installation &amp; Upgrades
---

### Post by Butchas on 2012-05-02
Hello, at the moment i have only a xubuntu 10.xx live cd in my hands, and i want to install absolutely other distribution to the hard drive, is it possible? even "command-line system" would bee good for me... Anyone could help me? Btw, it's an old system, so it doesnt support booting from usb stick. :popcorn:

---

### Post by kc1di on 2012-05-02
Not sure what your asking exactly?? 

Which O.S. are you trying or want to install, what is on the system at the moment?  and What are the specs on the machine your desire to install to?

All these would be important to knowing what to recommend for you.

Is this going to be a dual boot machine?

If you could answer some of those questions it would be much easier to give you advice on what you might want to try.

---

### Post by Butchas on 2012-05-02
sy

---

### Post by Butchas on 2012-05-02
> **kc1di said:**
> Not sure what your asking exactly?? 

Which O.S. are you trying or want to install, what is on the system at the moment?  and What are the specs on the machine your desire to install to?

All these would be important to knowing what to recommend for you.

Is this going to be a dual boot machine?

If you could answer some of those questions it would be much easier to give you advice on what you might want to try.

System is pretty old, it's a laptop with a 1,6ghz intel centrino processor, 368MB RAM, etc... now hard drive is just formated and empty, i want to install lubuntu, or empty ubuntu called "command-line system" . It will not be dual boot. 

What i want is to install for example lubuntu, by using xubuntu live cd and internet. Hope now i told everything clear enough. :lolflag:

---

### Post by mips on 2012-05-02
> **Butchas said:**
> System is pretty old, it's a laptop with a 1,6ghz intel centrino processor, 368MB RAM, etc... now hard drive is just formated and empty, i want to install lubuntu, or empty ubuntu called "command-line system" . It will not be dual boot. 

What i want is to install for example lubuntu, by using xubuntu live cd and internet.

Not possible I think and if it is it would be quite a hassle.

Why don't you just download the lubuntu iso?

Another option is to download the small 30MB Mini iso and install whatever you want from there.

---

### Post by kc1di on 2012-05-02
> **mips said:**
> Not possible I think and if it is it would be quite a hassle.

Why don't you just download the lubuntu iso?

Another option is to download the small 30MB Mini iso and install whatever you want from there.
Believe what mips says is true.. you need to download the lubuntu iso.  not sure how well it will work on that machine. but give the live cd a try and see if it does try the install. if not try a light weight distor like puppy.

---

### Post by Butchas on 2012-05-02
The problem is that i'm in the woods camp house about 40kilos from nearest shop, and have no empty cd... Got any suggestions, how to install something to that machine? Anything like wubi for win?

---

### Post by kc1di on 2012-05-02
> **Butchas said:**
> The problem is that i'm in the woods camp house about 40kilos from nearest shop, and have no empty cd... Got any suggestions, how to install something to that machine? Anything like wubi for win?

have you tried the xubuntu cd ? 
it may work but would likely be slow. 

If it does you can use the terminal from it. 
to install - lubuntu by this command

```
sudo update
sudo apt-get install lubuntu-desktop
```

---

### Post by Butchas on 2012-05-02
> **kc1di said:**
> have you tried the xubuntu cd ? 
it may work but would likely be slow. 

If it does you can use the terminal from it. 
to install - lubuntu by this command

```
sudo update
sudo apt-get install lubuntu-desktop
```

Lubuntu software list is quite small, and that what i liked, so after installing xubuntu, using sudo, will i have exact lubuntu instalation, without applications from xubuntu left?

somebody should make something like wubi for linux :)

---

### Post by sisco311 on 2012-05-02
You can use debootstrap to install a minimal system, then chroot into it and install the rest:  [https://help.ubuntu.com/community/Installation/FromLinux#Without_CD](https://help.ubuntu.com/community/Installation/FromLinux#Without_CD)

---

