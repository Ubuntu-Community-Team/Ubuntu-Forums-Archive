---
title: "VERY slow apt network connection"
date: 2010-03-10
forum: Installation &amp; Upgrades
---

### Post by sublimation on 2010-03-10
It may have something to do with my recent installation and removal of tor, but I can't narrow down when exactly it began. I'm getting no better than about 5000B/s download rates for apt. This means just a download of the package list takes a good 5 minutes. 

Other networking seems to run fine, but synaptic and apt are crawling.

Any suggestions on where to begin troubleshooting?

---

### Post by MelDJ on 2010-03-10
go to system-admin-software sources and change your software server

---

### Post by sublimation on 2010-03-10
First thing I tried. I've used about a dozen different servers, and none give better results. 
Currently I'm using a server that's housed at a local college. I've got quick ping times to the server, too.

When running the "select best server" it decided that a server half way across the planet was best. I gave it a shot, found it as slow as the others, and reverted to the more geographically close server.

---

### Post by sublimation on 2010-03-12
Just noticed that DropBox client also seems to have rather slow connections. It would seem that all low-level traffic is really choked. Any way to track how things like apt connect to the internet versus a browser?

I just had the bright idea to see if wget would run quick or slow, and I got the following:

```
xxx@yyy:~$ wget http://ubuntuforums.org
Error parsing proxy URL http://localhost:4001 : Bad port number.
xxx@yyy:~$ 
```

So.... how do I find out what's running the proxy?

---

### Post by 2hot6ft2 on 2010-03-12
You could also use apt-p2p to get files from other users like other p2p apps to make downloads faster.
```
sudo apt-get install apt-p2p
```
then edit the sources.list file
```
gksu gedit /etc/apt/sources.list
```
use find and replace to replace
> http://
with
> [http://localhost:9977/](http://localhost:9977/)
choose replace all
It should look like this now for each:
> deb [http://localhost:9977/astromirror.uchicago.edu/ubuntu/](http://localhost:9977/astromirror.uchicago.edu/ubuntu/) karmic-updates main restricted
deb-src [http://localhost:9977/astromirror.uchicago.edu/ubuntu/](http://localhost:9977/astromirror.uchicago.edu/ubuntu/) karmic-updates main restricted
then save and close.

Then run
```
sudo apt-get update
```
the first time it will take a while but after that you should get faster downloads. If a package can't be found on the p2p network it will fall back to the repositories to get it.

---

### Post by sublimation on 2010-03-13
I like the idea of using the Ubuntu community to leverage faster downloading. I think I'll give that a shot. If I were to use apt-p2p, would I be able to keep 2 sources.list, one with the localhost redirection and one without, and have both function if I switch them out? I'd be able to fall back on the original if needed.


While that would solve the main symptom I noticed, I think the fact that wget errors looking for localhost redirection means that I've got some leftovers from my Tor and anon-proxy installs. I'll have to hunt those down to return everything to working condition.

Thanks for the suggestion!

---

