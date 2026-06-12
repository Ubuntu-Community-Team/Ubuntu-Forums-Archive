---
title: "Failed instalation"
date: 2013-04-30
forum: Installation &amp; Upgrades
---

### Post by DrongoBG on 2013-04-30
Hey guys. Here's the situation. I have an old PC (CPU ~800MHz, 256mb ram) and I am trying to instal lubuntu from the alternate CD (13.04), but it fails mainly at Select and install software. The % at which it fails varies across the instalations, and if it, let's say fails at 85% it also fails to install bootloader if I choose to skip this step. THis happens both if I choose to make the HHD in one partition(ext4) or if I make 2 partitions (again ext4). I have internet while the instalation is running (though I don't see how this is relevant). I tried detaching the HDD and plugging it in my other PC (dual core, 2gb ram, etc) and the instalation there (from the same CD) goes perfectly, and on returning the HDD on the old PC i can boot the os, but things like LAN card, printers and maybe sound (I actually forgot to test that) don't work.

I am asking, what could be the problem?

---

### Post by ibjsb4 on 2013-04-30
This could be a hardware problem, but with those specs your really pushing the minimum limit.  

I would suggest even a more basic install of Lubuntu.  Theres a big difference in packages between 12.04 and 13.04, I would go with 12.04 install without the recommended packages.  You can do that with the alternate CD and do a terminal only install.  After that you would add Lubuntu minimal with the terminal command:

```
sudo apt-get install --no-install-recommends lubuntu-desktop
```

[http://packages.ubuntu.com/precise/lubuntu-desktop](http://packages.ubuntu.com/precise/lubuntu-desktop)

[http://packages.ubuntu.com/quantal/lubuntu-desktop](http://packages.ubuntu.com/quantal/lubuntu-desktop)

---

### Post by DrongoBG on 2013-04-30
This is a "noobish" question, but how do I load up the terminal from the alternate CD (there is no OS on the HDD)?

---

### Post by ibjsb4 on 2013-04-30
At the beginning of the install its in one of the "F" keys at the bottom.  I think it was F4.  Take a look, post back if Im wrong.  Are you doing 12.04?

---

### Post by DrongoBG on 2013-04-30
Well this is strange, the instalation just succeeded :/. I did nothing different than the things in the first post.

---

### Post by ibjsb4 on 2013-04-30
Stuff happens :)

Curious, on those specs, does it run ok or is there lag?

---

### Post by DrongoBG on 2013-04-30
That is another strange thing. It runs ok, but from time to time form what I can tell on a random basis gets very laggy (idle, just moving cursor, browsing a webpage, using gnumerator). And also, it is on a constant 100% cpu usage. This really makes me think there might be a hardware problem.

---

### Post by ibjsb4 on 2013-04-30
When it lags, swap could be kicking in.  Take a look at whats using your resources.

In terminal:

```
top
```

---

### Post by DrongoBG on 2013-04-30
It's not the swap, but I'm begging to see a patern. After boot if I don't launch anything - it's smooth. If I launch an app or two - still it's not bad. Bud when I start opening and closing apps it just goes down from there. Now, if I open a few apps, the close them, after about 10 mins it gets ok again. And sometimes I get "out of memory" by the browser, when clearly there are 60-70mbs free. I think the RAM is too old (SDR) and can't cope with quick deallocation.

---

### Post by ibjsb4 on 2013-04-30
Maybe a light weight browser would help.

[https://help.ubuntu.com/community/WebBrowsers](https://help.ubuntu.com/community/WebBrowsers)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=lightweight+browsers&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=lightweight+browsers&sa=Search&cof=FORID:9)

---

