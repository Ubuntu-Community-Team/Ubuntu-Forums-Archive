---
title: "Real VNC"
date: 2006-10-12
forum: Installation &amp; Upgrades
---

### Post by lloydlloyd on 2006-10-12
Hi, I am pretty new to Linux/Ubuntu, but have been using it over XP for a couple weeks now.
One thing I am having a hard time with is installing programs that I've downloaded from the net. Specifically, I need to get Real VNC up and running for work. I have downloaded a "GZipped Tarfile", but from there, I'm stuck.
The website for the program is [http://www.realvnc.com/](http://www.realvnc.com/)
If anyone could help, it would be much appreciated.
Thanks
Elliot...

---

### Post by encompass on 2006-10-12
I linux many things are able to be installed with a package manager so you don't have to worry about that file at all. Go into System... Administration... Synaptic Package Manager... you will see thousand of searchable programs that you can use.
[http://www.ubuntuforums.org/search.php?searchid=8789146](http://www.ubuntuforums.org/search.php?searchid=8789146)
This is a great start.  I searched for 'howto vnc' and got those.
Remember vnc is rather insecure and not really the best way to do everything on your computer.  I recommend learning ssh if your using this stuff over the internet.
Which brings me to my question for you...
What do you WANT to do? Be detailed.

---

### Post by lloydlloyd on 2006-10-12
Well I need to be able to connect from home to our city office to access a specific program on one of the computers there.
I can do it on my XP box, but have found that I've been using Ubuntu more and more at home to the stage where it's pretty much all I'm using.
Real VNC is just what I've used in the past, and I'm open to using another (more secure, better, faster, stronger) program.
And anyway, can I connect to my office computer if it's XP and I'm running Linux??
If not then I guess this is a bit redundant.
But thanks for your help anyway.

---

### Post by encompass on 2006-10-13
I think by default you have vncveiwer installed... just run it fron the terminal... remember though, that vnc is very prone to hacking, everything is sent in plain text.
Layout is like so..
```
vncviewer ip.ad.dre.ss:screen#
```
Tehre are fancier programs that do the same thing... just look up vnc in synaptic package maneger.

---

