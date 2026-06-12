---
title: "Installation: cannot open /dev/sda"
date: 2007-06-22
forum: Installation &amp; Upgrades
---

### Post by Kleenux on 2007-06-22
Hello,

when starting the installation of Ubuntu 7.04 / Desktop, about 30 seconds after it started, I get this in a console:

```
/bin/sh: can't access tty; job control turned off
```

The 1st line of casper.log  shows

```
/init: /init: 1: cannot open /dev/sda: No such file
```


I tried multiple things in the BIOS, like changing from SATA to ATA, disabling cards...  but it doesn't help.

Prior to installing Desktop I installed **successfully** Ubuntu 7.04 Server - with no problem!

[ I'm new to Ubuntu, coming from red hat and suse. Initially I thought Server may have more stuff than Desktop, this is why I installed Server first ]

Hardware: Dell notebook Latitude D630 - brand new.

Please help, I'm stuck with this problem.

---

### Post by Ultra Magnus on 2007-06-22
Hi - I've found a blog post that might help you...

[http://blog.shevin.info/2007/04/how-did-i-fix-cant-acess-tty-in-feisty.html](http://blog.shevin.info/2007/04/how-did-i-fix-cant-acess-tty-in-feisty.html)

---

### Post by Kleenux on 2007-06-22
Thanks, interesting link - but on my Dell Latitude D630 there is only one DVD, one HD.
Anyway I tried to disable again whatever possible in the BIOS but the problem remains.

The weird thing is that the Server version installs Ok, only the Desktop fails.

Could it be due to the previous install of Ubuntu Server? (while I even tried to reformat the Linux partition before installing Desktop...) 

Any other idea is very welcome.

---

### Post by Kleenux on 2007-06-23
Ok now it doesn't give this error anymore!

**SOLUTION**

The solution on my Dell Latitude D630 was

1. to make a 2nd copy of the install CD of Ubuntu 7.04 Desktop
2. to connect a 2nd DVD drive (USB) - yes! - loaded with the 2nd CD

At this point I have 1 CD in the main drive and 1 CD in the USB drive

And **it works!**  The installation starts from the main drive, then after a while (about 45") switches to the USB drive...

[ --- note for the Ubuntu developers: there is this exact same scenario with SuSE 9.3 ; so the problem is likely to come from the Kernel. And, remember, no problem with the Server version --- ]


Ok, now it cannot start the Xserver because it doesn't know the card (GM965 / Intel Crestline Graphics / GMA X3100). And  I don't know where to find this driver.

It take so much time - to be honest, I'm not far from giving up ;)

---

### Post by strangedata on 2007-06-27
Hi,

I'm having a similar problem on my Sony Vaio laptop. First I get:
 /bin/sh: can't access tty; job control turned off

And the casper.log file says (repeatedly):
cannot mount /dev/sda1 on /cdrom: no such file
cannot mount /dev/sda2 on /cdrom: no such file
...
...
could not find any media with live CD data (or something similar)

What's up?

Thanks!

---

### Post by strangedata on 2007-06-27
FYI: The solution posted [_here_]("http://ubuntuforums.org/showthread.php?t=421588&highlight=%2Fbin%2Fsh%3A+can%27t+access+tty%3B+job+control+turned+off") solves the problem for me.

I still have to figure out how to make it recognize my wireless card and support 1024x768 resolution though.

---

