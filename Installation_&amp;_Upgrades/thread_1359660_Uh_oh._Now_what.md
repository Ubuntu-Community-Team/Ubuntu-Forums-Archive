---
title: "Uh oh. Now what?"
date: 2009-12-19
forum: Installation &amp; Upgrades
---

### Post by joecichocki on 2009-12-19
I recently installed Ubuntu 9.10 on an older Dell. It is wonderful. I then got in my head the idea to do the same with my iMac PPC with 600MHz processor and 512MHz Ram. After fiddling around for a couple of weeks, I finally got Ubuntu 8.04.01  to install. Now, instead of getting the lovely desktop and everything else I got on the Dell, I have text only asking for commands, which I know nothing about. I realize I screwed up, but how can I get myself the graphics and all else like on the Dell. I know my installation is older on the iMac and cannot expect exactly what is on the Dell, but I was surprised to find only test. What am I missing?

Thank you for your help.
As you can see, I am totally new to this....

Joecichocki

Please excuse my total lack of knowledge about what I have been trying to do.

---

### Post by jerrrys on 2009-12-19
did you do it like this

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by joecichocki on 2009-12-19
I held down the C key as I booted the iMac, and then I followed the prompts that Ubuntu 8.04.01 put on the screen. It was not at all like the Ubuntu 9.10 install I did on the Dell, which had been running Windows Xp.

---

### Post by jerrrys on 2009-12-19
this isnt the server edition is it?

---

### Post by joecichocki on 2009-12-20
I believe it was.......

---

### Post by XubuRoxMySox on 2009-12-20
It sounds like you have Karmic for the desktop on the Dell, and a server version of Hardy on the Mac. The server version is not meant for ordinary desktop use. But you can install a super lightweight desktop environment if you want. [LXDE]("http://lxde.org") works well on Hardy. Just be sure your 'puter is fully updated, then

```
sudo apt-get install LXDE
```

It'll give you a pretty, ultralight desktop reminiscent of Win98 to work with. Or for a more custom "Hardy Lite," check out [U-Lite]("http://u-lite.org") (Hardy with LXDE).

-Robin

---

### Post by jerrrys on 2009-12-20
if thats the case you will not have a desktop (GUI), server edition is text only.  you can add the desktop to it with this command

sudo apt-get install ubuntu-desktop

and before you do that its a good idea to update

sudo apt-get update

---

### Post by Gtklocker on 2009-12-20
Do so:

apt-get update
apt-get install xorg-*
apt-get install kubuntu-desktop

---

### Post by jerrrys on 2009-12-20
my bad

need to install xorg too.  i do not use server edition so people that do can tell you of the other packages that are not installed and there are more...really better off just reinstalling a desktop edition in my opinion.  and for your information kubuntu (once again in my opinion) is ubuntu with eye candy...

---

### Post by joecichocki on 2009-12-20
I have ubuntu installed, but I forgot the x.org. Everything is incredibly slow. Stupid question: can I install x.org now, or do I have to go through the whole installation process of everything again? It took me ten minutes just to get through the password screen and hear the ubuntu fanfare.

---

### Post by jerrrys on 2009-12-20
get to a terminal and install it

---

### Post by joecichocki on 2009-12-20
mouse and usb ports unresponsive

---

### Post by jerrrys on 2009-12-20
boot into recovery mode and try the fix broken packages option just to see if anything else is going on.  you can also open a terminal and install xorg.

[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

---

