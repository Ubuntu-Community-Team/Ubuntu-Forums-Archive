---
title: "Problem With X After Installing Driver For nVidia geForce 7950gt Graphics Card"
date: 2007-05-16
forum: Installation &amp; Upgrades
---

### Post by kasperbs on 2007-05-16
Hi Greetings to you all, this is my first (def not last) post here so let me say hello to all of you. 
I have a question regarding my 7950gt geForce Graphics card, it seems like it is hard to get working in any Linux Distro. A couple of month ago I tried to install openSUSE 10.2 but because the driver from nVidia at the time didn't support 7950gt properly I decided to wait and now as far as I understand they have released a new version of their driver.

I then decided to move away from openSUSE mainly because my dad did as well and try out Ubuntu. I had everything installed and it all seemed good until ubuntu asked me, if I wanted to install the driver for my nVidia Graphics card because Ubuntu had noticed that it supported some 3D things and to get the most out of it, it was recommended that I installed the driver. Ok I thought this sounded good because before I messed around with trying to install it manually and it did'nt work out for me, so hopefully Ubuntu could do the job. But when it was installed and I restarted the System i got the following screen:
[[IMG]http://img234.imageshack.us/img234/2235/01startupdo8.th.jpg[/IMG]](http://img234.imageshack.us/my.php?image=01startupdo8.jpg)

When I say no to view the eserver outpu (which I by the way understand nothing of) I get the following screen sying that X has been disabled:
[[IMG]http://img66.imageshack.us/img66/7339/02xdisabledzl0.th.jpg[/IMG]](http://img66.imageshack.us/my.php?image=02xdisabledzl0.jpg)

I now have no idea how to configure it, when I click ok I just get back to a normal command prompt:
[[IMG]http://img218.imageshack.us/img218/4108/03cmdpromptps7.th.jpg[/IMG]](http://img218.imageshack.us/my.php?image=03cmdpromptps7.jpg)

And from my experiences on SUSE I knew that the command startx would try and run the X Server, but when I do so, I get a familiar screen which I remember from my SUSE time and it looks something like this (and yes I have checked all my power cables and everything)
[[IMG]http://img230.imageshack.us/img230/535/04startxrg2.th.jpg[/IMG]](http://img230.imageshack.us/my.php?image=04startxrg2.jpg)

I hope I have provided ebough information to clarify my problem, I have heard and read a lot of good things about you guys on this forum, and I really look forward to spending time on here.

Kasper

---

### Post by chaoswings on 2007-12-02
I have the exact same card as you just bought it yesterday and I am having the exact same problem...I have tried Nvidia-glx-new AND I went so far as to install the drivers from Nvidia themselves nothing seems to work.

is there some setting we need to modify in the xorg.conf maybe? i've tried everything I could think of. I'm using ubuntu 7.10 and the graphics that ubuntu installs by default  are fine without the accerlerated driver. i just can't use compiz

---

### Post by kasperbs on 2007-12-04
I got my problem solved here:
[http://ubuntuforums.org/showthread.php?t=448505]("http://ubuntuforums.org/showthread.php?t=448505")

---

