---
title: "INstall Gparted"
date: 2010-08-01
forum: Installation &amp; Upgrades
---

### Post by dsub42 on 2010-08-01
Hi im using ubuntu 10.04LTS

Im really new to linux , so this might be a silly question...

once i have downloaded the software and extracted it ... how the hell to I install it? :)

Any help would be appriciated

---

### Post by snowpine on 2010-08-01
Not a silly question at all. :)

```
sudo apt-get install gparted
gksu gparted
```

You can also install Gparted from the Ubuntu Software Center if you prefer a GUI.

Gparted is also on the Ubuntu Live CD. Personally I prefer to partition from the Live CD rather than running from my hard drive install.

Good luck, ask if you have more questions! :)

---

### Post by dsub42 on 2010-08-01
If I use the commands specified, will this not invoke a GUI installer?

---

### Post by snowpine on 2010-08-01
> **dsub42 said:**
> If I use the commands specified, will this not invoke a GUI installer?

I like the terminal, but you can also use Ubuntu Software Center or Synaptic Package Manager if you prefer a GUI.

---

### Post by atomizer on 2010-08-01
Most of the time you don't need to download and extract.

Synaptic is the GUI to install programs (or ubuntu software centre, but you will not find everything there)

All the programs will be downloaded and installed from a trusted reposetory with one click of the button.

---

### Post by howefield on 2010-08-01
dsub42, for your purposes you will need to use GParted from a Live CD, as you won't be able to resize your Ubuntu partition whilst it is in use.

As snowpine said, it is a preferable method.

---

### Post by dsub42 on 2010-08-01
So i need to download the live cd software .. burn to a cd and then run off the cd?

---

### Post by howefield on 2010-08-01
Do you have your Ubuntu CD, it has GParted already on it ?

---

### Post by snowpine on 2010-08-01
> **dsub42 said:**
> So i need to download the live cd software .. burn to a cd and then run off the cd?

Maybe you have a Live CD already? How did you install Ubuntu?

Can you back up a couple of steps and tell us what is your final goal here?

---

### Post by dsub42 on 2010-08-01
i installed by downloading a file and running it from windows.

my final goal is to extend the partition ubuntu is on as I have run out of space, i need an extra 40gb and my plan is to extend the partition ubuntu is on by extending it into another unused partition

---

### Post by snowpine on 2010-08-01
> **dsub42 said:**
> i installed by downloading a file and running it from windows.

It sounds like you installed Ubuntu using WUBI, is that accurate?

[http://wubi-installer.org/](http://wubi-installer.org/)

If that is the case, unfortunately I have never used WUBI before and won't be able to assist you. But there are lots of other knowledgeable people here on the forums. :)

---

