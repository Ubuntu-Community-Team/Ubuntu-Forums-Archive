---
title: "LTSP GUI screen for setting up"
date: 2007-09-03
forum: Installation &amp; Upgrades
---

### Post by keiffee30 on 2007-09-03
I have used Edbuntu 7.04 and that has been running LTSP without any problems. all i needed was a small pc to log in with a GUI interface that can run firefox and office. 
In Edbuntu there was a small app in the System/Apps, there you can see what is going on on the  remote PCs. 

I have now gone over to Ubuntu 7.04. I have installed the LTSP by using 

**sudo apt-get install ltsp-server-standalone openssh-server**

and it has installed ok 

then i did the client install by 
[B]
sudo ltsp-build-client[/B]

This is all fine.... but is there a GUI interface where you can configure the LTSP server and how it works. so instead of editing files (and making some misstakes along the way) have something like the app called Envy that sorts out ATI and Nvidia driver problems.

---

### Post by Kalif on 2007-09-07
as to my knowledge, there is no gui planned for the near future,
and there is not any gui available now either.

observe: no offence intended with the following:

A netbooting environment is very complex, and there are many
varibles and as far as I know (and I have been netbooting for
more than 15 years, not with ltsp all the time obviously) it is
very hard to make a "one size fits all configuration". As I am
not actively working on the ltsp project, I can not do other
than speculate upon the likelyhood of any gui comming soon.

There are basically 3 variables besides the actual client machines
to be booted and the low level networking infrastructure like
VLAN configuration, routing and general network topology:

1. DHCP sometimes you can not run a DHCP server on your
LTSP server machine, in most cases you can.

2. DNS setup may not allways be easy to configure depending
on the needs of the LTSP envirionment.

3. TFTP and NFS issues may also come up if you are using these
protocols for more things than running your LTSP farm.

On top of this things will soon get interesting when you start
mixing PC:s with old Mac:s and a few born again windows CE
based thin client machines; then you will have to provide different
boot images for each and every machine. On top of this issue
there are an ongoing effort in making ordinary PC:s multi-user
by installing several graphics adapters, keyboards and mouses,
integrating this in a LTSP envirionment also takes some thinking 8-)

Hence I think the present solution with a few scripts to automate
the most important basic tasks, and then a good tutorial upon
how to set things up is the most reasonable solution. If you are
running a small (home?!) office or school everything should be
easy running from the same machine.

That's my view, do not bet on it, but as far as I can see, there
are more deserving areas for automation in the ubuntu world
dominance effort ;-)

Best,
K.A. Lif.

---

### Post by keiffee30 on 2007-10-19
yes that is very true. and point taken. I have found a kind of GUI for LTSP. and its a web base admin tool

its called Webmin and you can find it at this address.....

[http://www.webmin.com/index.html](http://www.webmin.com/index.html)

this is also access to other admin systems as well. so i will press on with this 

Many thanks for your input into this post

---

### Post by coolaj86 on 2008-07-04
Easy-LTSP is a Google SoC project with SuSE that has been making progress.

[http://developer.novell.com/wiki/index.php/Easy-LTSP](http://developer.novell.com/wiki/index.php/Easy-LTSP)

---

