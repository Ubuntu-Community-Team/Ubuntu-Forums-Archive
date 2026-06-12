---
title: "Linux Chromium now with Flash"
date: 2009-07-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ktp on 2009-07-12
[http://h3g3m0n.wordpress.com/2009/07/12/linux-chrome-flash-ext/](http://h3g3m0n.wordpress.com/2009/07/12/linux-chrome-flash-ext/)

---

### Post by Revolutionary101 on 2009-07-12
I am glad they finally put flash into Chromium.

---

### Post by wayne_cat on 2009-07-12
Great ... works with youtube ... but it still has problems with the videos from liveleak

---

### Post by ktp on 2009-07-12
Ya still has some work to do but good to see flash working.  

FYI, if you are using 64-bit then remember to use 32-bit flash lib.

---

### Post by darco on 2009-07-12
Would this be the latest version?  3.0.192.0

thxs
darco

---

### Post by ktp on 2009-07-12
daily builds are 3.0.194.0

---

### Post by vinutux on 2009-07-12
its evolving very fast.................

hope final version available soon.........

---

### Post by darco on 2009-07-12
I am getting a "permission denied" error when updating the source list

sudo echo "deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main #chromium-browser" > /etc/apt/sources.list.d/chromium.list
bash: /etc/apt/sources.list.d/chromium.list: Permission denied

any ideas?

thxs

darco

---

### Post by Joe_Bishop on 2009-07-12
output redirection is done to the current user, something like
sudo ( echo "..." > /etc/...) should works

---

### Post by paul_in_london on 2009-07-12
Not sure, but instead of creating an entry in **/etc/apt/sources.list.d** are you able to add these lines to** /etc/apt/sources.list**?

```
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main
```

That's what I have in mine anyway...

---

### Post by mattduckman on 2009-07-12
> **darco said:**
> I am getting a "permission denied" error when updating the source list

sudo echo "deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main #chromium-browser" > /etc/apt/sources.list.d/chromium.list
bash: /etc/apt/sources.list.d/chromium.list: Permission denied

any ideas?

thxs

darco

```
echo "deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main #chromium-browser" | sudo tee /etc/apt/sources.list.d/chromium.list
```

---

### Post by ktp on 2009-07-12
> **darco said:**
> I am getting a "permission denied" error when updating the source list

sudo echo "deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main #chromium-browser" > /etc/apt/sources.list.d/chromium.list
bash: /etc/apt/sources.list.d/chromium.list: Permission denied

any ideas?

thxs

darco

You can just open up the file as root and add the line to it.

---

### Post by psyke83 on 2009-07-12
> **darco said:**
> I am getting a "permission denied" error when updating the source list

sudo echo "deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main #chromium-browser" > /etc/apt/sources.list.d/chromium.list
bash: /etc/apt/sources.list.d/chromium.list: Permission denied

any ideas?

thxs

darco

Using pipes or redirects with sudo don't work as intended. There's probably a way to make it work if you modify the syntax, but I don't know off-hand. Temporarily becoming the superuser (sudo -s) before invoking those commands is another way.

---

### Post by BwackNinja on 2009-07-12
sudo bash -c 'echo "deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main #chromium-browser" > /etc/apt/sources.list.d/chromium.list'

---

### Post by crjackson on 2009-07-12
I got it working.  Was hoping for better performance, but it'still the same old flash plugin after all...:rolleyes:

---

### Post by aamukahvi on 2009-07-13
> **psyke83 said:**
> Temporarily becoming the superuser (sudo -s) before invoking those commands is another way.

I think that's "sudo -i" for interactive mode.

---

### Post by darco on 2009-07-13
Since I have x64 flash installed and I dont want to remove it, what I did was copy an x32bit flashplayer.so into the chromium plugin folder and now I have flash! My original FF is untouched.
Chromium is blazing fast and now w/flash and AdSweep, its my default browser!

darco

---

### Post by Tom Mann on 2009-07-13
> **darco said:**
> I am getting a "permission denied" error when updating the source list

sudo echo "deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main #chromium-browser" > /etc/apt/sources.list.d/chromium.list
bash: /etc/apt/sources.list.d/chromium.list: Permission denied

any ideas?

thxs

darco

Hey there, your command will not work as the redirect will be under your usual user. Try the following:

```
sudo su -c 'echo deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main #chromium-browser > /etc/apt/sources.list.d/chromium.list'
```

Probably not the best method but it works for me :)

---

