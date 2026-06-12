---
title: "Installation Help"
date: 2007-07-08
forum: Installation &amp; Upgrades
---

### Post by sands on 2007-07-08
Hi,
I am not new to Ubuntu. I used previous versions of ubuntu in my Desktop. I was very happy with that.
Now I bought a new laptop. I am trying to install Ubuntu, but it fails to install.
I am using Ubuntu 7.04 CD. It boots into ubuntu, then I hit the live option. It goes well for some time in CLI, I can see some output on the screen. Then all of sudden at a certain point it hangs. I tried using -nopci (noacpi I guess). Using this nopci, some times it goes into the gnome desktop & hangs after some time. Sometimes it even doesnt work that way. I am really sick of this damn windows. Some one help me out of this.

By the way my laptop is Compaq Presario V6101. Here you can see my laptop config [http://h10025.www1.hp.com/ewfrf/wc/genericDocument?docname=c00775173&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN](http://h10025.www1.hp.com/ewfrf/wc/genericDocument?docname=c00775173&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN)

I will be glad, if someone could help me out of this..


Regards,
Sands..

---

### Post by mikewhatever on 2007-07-08
Does it boot into Ubutnu, so that you get to see the desktop and all, or do you only see the black screen with boot choices and then it hangs?
How did you download the iso, over http/ftp or bittorrent?
Have you tried [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM?highlight=%28md5sum%29") checking?

---

### Post by sands on 2007-07-08
I see the following lines
Starting GNOME Display manager...
Starting Unix printing........
Then Blank Screen

I downloaded it through bittorrent. I checked md5sum. It is fine..

---

### Post by Gremlinzzz on 2007-07-08
Try burning with a brand new cd.When i bought a new pc it wouldn't read my old rewrite cds.bought new cds everythings fine.

---

### Post by sands on 2007-07-08
I burnt the iso in a new writable CD & the md5sum is also fine.

---

### Post by sands on 2007-07-09
Finally I got it.. Thanks for your help buddies..
I added noapic irqpoll noirqdebug as the parameters. 
Finally everything is up & running..

---

