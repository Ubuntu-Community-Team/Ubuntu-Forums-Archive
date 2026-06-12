---
title: "Ubuntu Splash Screen/Throbber"
date: 2009-09-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by go7Ul1ai on 2009-09-04
I'm just wondering when this will be fixed, as the bar is still scrolling up instead of how I think it's supposed to (left to right). 

Anyone have any ideas??

Lee

---

### Post by Vaun on 2009-09-04
```
bzr branch lp:xsplash

```
```
sudo apt-get build-dep xsplash

```
```
cd xsplash
```

```
./configure --prefix=/usr --with-user=gdm
```

```
make
```

```
sudo make install
```

I think you will be pleasantly surprised. :)

---

### Post by woodbj on 2009-09-04
There's a daily PPA as well 
```
https://launchpad.net/~xsplash-team/+archive/ppa
```

---

### Post by woodbj on 2009-09-04
Oh and by the way epically awesome

---

### Post by Vaun on 2009-09-04
Very true.  I just get a slight flicker before transitioning from GDM to desktop, but other than that very impressive.

---

### Post by twright on 2009-09-04
> **lee.jarratt said:**
> I'm just wondering when this will be fixed, as the bar is still scrolling up instead of how I think it's supposed to (left to right). 

Anyone have any ideas??

Lee
Ah,
I thought I was the only one seeing that :-)

---

### Post by skierkyles on 2009-09-04
> **woodbj said:**
> There's a daily PPA as well 
```
https://launchpad.net/~xsplash-team/+archive/ppa
```

Holy cow, just updated to this its looking amazing :shock: I cant wait till the gdm matches!

---

### Post by godhika on 2009-09-04
> **skierkyles said:**
> Holy cow, just updated to this its looking amazing :shock: I cant wait till the gdm matches!

+1
and hopefully with 10.4 also the desktop theme

---

### Post by VMC on 2009-09-04
> **woodbj said:**
> There's a daily PPA as well 
```
https://launchpad.net/~xsplash-team/+archive/ppa
```

Yes, very impressive! --- a different shade of brown :)

---

### Post by setherd on 2009-09-04
SO I have to use autoconf to make the correct configure file?
any pointers?

---

### Post by Vaun on 2009-09-04
```
autoreconf -i
```

---

### Post by setherd on 2009-09-05
thanks! that did it!

---

### Post by alligoodw on 2009-09-05
> **woodbj said:**
> There's a daily PPA as well 
```
https://launchpad.net/~xsplash-team/+archive/ppa
```

I try and copy into Software sources but the add button doesn't highlight, therefore it's not allowing me to add a new resource.

---

### Post by MacUntu on 2009-09-05
Open [https://launchpad.net/~xsplash-team/+archive/ppa](https://launchpad.net/~xsplash-team/+archive/ppa) in a browser. ;)

What you want is:```

deb http://ppa.launchpad.net/xsplash-team/ppa/ubuntu karmic main
```

---

### Post by alligoodw on 2009-09-05
That did it!  Thanks buddy.

---

### Post by Marat89 on 2009-09-06
I made a short clip of the new Design for other :KS

New Design is very impressive :popcorn:

Hope xslash starts after grub and replaces the old bar.

[Youtube Clip]("http://www.youtube.com/watch?v=wBeNMk2W6hw")

---

### Post by cheesypoof on 2009-09-06
Hopefully this color scheme and xsplash screen is actually part of a consistent thought out style, not just one piece of a hodgepodge of very different looking designs.

---

### Post by Marat89 on 2009-09-06
+1

---

### Post by Starks on 2009-09-06
> **MacUntu said:**
> Open [https://launchpad.net/~xsplash-team/+archive/ppa]("https://launchpad.net/%7Exsplash-team/+archive/ppa") in a browser. ;)

What you want is:```

deb [http://ppa.launchpad.net/xsplash-team/ppa/ubuntu](http://ppa.launchpad.net/xsplash-team/ppa/ubuntu) karmic main
```
you can also add it from the "add repo" menu in Software Sources by typing "ppa:xsplash-team" without the quotes.

It'll download the gpg keys and everything.

---

### Post by MacUntu on 2009-09-06
> **Starks said:**
> you can also add it from the "add repo" menu in Software Sources by typing "ppa:xsplash-team" without the quotes.

It'll download the gpg keys and everything.

](*,) Forgot about that (guess you can tell I rarely add PPAs :D).

---

### Post by Darkshade on 2009-09-06
Hmm, I don't see the throbber at all since I added the PPA (I see the background though). Am I the only one?

---

### Post by Starks on 2009-09-06
I think the PPA is older than the bazaar tree and lacks the graphical refresh.

---

### Post by andrek on 2009-09-06
Mine looks just like Iteration 3, is that correct?

---

### Post by Darkshade on 2009-09-06
Just installed it on my laptop too. I can see the throbber there. Still can't see it on my desktop though. The only thing I can think of is that it doesn't like my twinview setup. :confused:

---

### Post by Copernicus1234 on 2009-09-06
Looks good. :)

---

### Post by NCLI on 2009-09-06
> **Darkshade said:**
> Just installed it on my laptop too. I can see the throbber there. Still can't see it on my desktop though. The only thing I can think of is that it doesn't like my twinview setup. :confused:
Three words: Report a bug. ;)

---

### Post by bacardiandwatermelon on 2009-09-06
> **MacUntu said:**
> 
What you want is:```

deb http://ppa.launchpad.net/xsplash-team/ppa/ubuntu karmic main
```

Legend.. Man that looks so much better :-)

---

### Post by bacardiandwatermelon on 2009-09-12
Arr what happened? It has reverted back after an update :-(

---

### Post by cyberkilla on 2009-09-12
I added the PPA, but it didn't show an update because the version appears to be less recent than what I had already.

Hmm...

---

