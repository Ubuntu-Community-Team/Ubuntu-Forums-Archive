---
title: "Installation GUI problem"
date: 2007-03-28
forum: Installation &amp; Upgrades
---

### Post by chenks on 2007-03-28
I have a Acer Travelmate 8204 laptop
Intel Centrino Duo T2500
2 GB RAM
Radeon X1600 mobility (256mb)
15'' widescreen (1680x1050 native resolution)

My problem is that whenever I try to install Ubuntu (6.10 image download) whether in normal or safe graphical mode, I get a distorted desktop (see attachment).

The only screen i can actually see properly is the initial boot options menu.

I tried CTRL-ALT-BACKSPACE to see if that would take me to a console, but all that gives me is a black screen (no flashing cursor and nothing i type appears on screen).

Also, just after i get the initial 'loading kernel' pop-up it then very briefly shows some errors, they disappear so fast that i couldn't see the whole message, but it was something like

'unable to allocate........ blah blah blah....... region(?)...'

Anyone able to help me resolve this ?

---

### Post by chenks on 2007-03-28
ok well i managed to finally get to a working console by pressing CTRL-ALT-F1.
i ran the following command

```
sudo dpkg-reconfigure xserver-xorg
```

played about with the settings, set what i thought were the correct settings for the gpu and monitor sizes.
unfortunately still didn't resolve the problem.

while on the console i did notice quite a few similar errors at the top (see attached)

please help !

---

### Post by pradeepadapa on 2007-03-28
dont bother much abt those errors, they donot mean any harm ,just why dont u see trying the command $startx  at the terminal so that u can set the monitor attributes...

---

### Post by chenks on 2007-03-28
because whenever x starts, i get the corrupt GUI as per the first post.

---

