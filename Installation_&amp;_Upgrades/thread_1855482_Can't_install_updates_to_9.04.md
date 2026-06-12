---
title: "Can't install updates to 9.04"
date: 2011-10-06
forum: Installation &amp; Upgrades
---

### Post by Scott216 on 2011-10-06
I installed Ubuntu 9.04 from CD to an old computer I had lying around.  I tried installing versions 10 and 11, but the computer ran very very slow, while with 9.04 it's pretty good.  I have an Compaq EVO Pentium 4, 2.4GHz CPU, 1.5 GB RAM.  The only thing I want to do is use it as an FTP server that my security cameras can write too.  When I try to install ftp using: 
sudo apt-get install vsftpd 
it fails.  Trying to do sudo apt-get udpate fails on everything because it can't find the files online.  I read that version 9.04 is not supported and even these old files are not available anymore. What should I do? The newer Ubuntu versions don't work well on my hardware. How can I get FTP server running?

---

### Post by gordintoronto on 2011-10-06
Install a current version of Xubuntu or Lubuntu. Either one should run very nicely on that configuration.

---

### Post by Frogs Hair on 2011-10-06
You can get old packages but only for LTS versions , which excludes 9.04 . As stated above your hardware looks fine for Lubuntu or Xubuntu . Why Ubuntu runs slow is unclear with your current hardware .

---

### Post by viperdvman on 2011-10-06
I too don't see any reason why 10.04 would run slow on your computer with that setup. But if all else fails, I'd just run either Xubuntu or Lubuntu 10.04 if you're wanting an older version of said OS's that have Long-Term Support.

---

### Post by Scott216 on 2011-10-06
I tried Ubuntu 10.10, not 10.04.  I read some forum posts where a lot of people had performance problems when they upgraded to 10.10 from 10.04.

Anyway, I installed Lubuntu 11.04 and it seems fair.  Not as good as Ubuntu 9.04, but I'll give it a try.

---

### Post by Scott216 on 2012-04-17
I'm working on this FTP Server project again.  Lubuntu 11.04 actually turns out to be pretty slow.  So does Xubuntu 10.04.  The only installs that run well are Ubuntu 9.04 and Xubuntu 9.04. Something is odd with this computer and Ubuntu after 9.04. 

I'm want to get FTP Sever running, but I'm bumping up against a lot of problems.  For example I tried to RPM on Ubuntu, but is said RPS wasn't installed and I should run 
sudo apt-get install rpm

But I get an error when I try: Package rpm is not available 

I'd appreciate any help on getting an FTP server setup on this PC.

---

### Post by jadtech on 2012-04-17
if all your using it for is a server you dont need all the fancy bells and whistle for video and such ...

---

### Post by Scott216 on 2012-04-17
> **jadtech said:**
> if all your using it for is a server you dont need all the fancy bells and whistle for video and such ...

That's right, all I need is the for the security camera to have access to the FTP directory to write files.

---

### Post by oldos2er on 2012-04-17
Support ended for 9.04 ended in Oct. 2010, so I suggest you install a supported version. 

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by Scott216 on 2012-04-17
> **oldos2er said:**
> Support ended for 9.04 ended in Oct. 2010, so I suggest you install a supported version. 

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

I tried more recent versions and the PC runs so slow it's unusable.  9.04 is the only one that works.  It has a decent processor and RAM, I don't know why the performance is so bad, but it is.

PC has Pentium 4, 2.4GHz and 1.5GB RAM (Compaq Evo D31M)

---

### Post by mörgæs on 2012-04-17
Then Lubuntu 11.10 would be worth trying.

When you have it installed, please post which application is slowing it down.

---

### Post by iponeverything on 2012-04-17
For reference -- one can install packages for old unsupported versions ubuntu -- just modify the /etc/apt/source-list file -- it quite easy to google the specifics. The only caveat being that the package had to exist for version before it stopped being supported. 

For systems that are being used for purposes as described by this op I see no reason to go for current release over old release -- basic functions of an ftp server hasn't changed in 20 years.. 

If the system is connected to a public network, use a supported version or take extra care in securing the system.

---

### Post by Scott216 on 2012-04-17
> **iponeverything said:**
> For reference -- one can install packages for old unsupported versions ubuntu -- just modify the /etc/apt/source-list file -- it quite easy to google the specifics. The only caveat being that the package had to exist for version before it stopped being supported. 


What specifically should I change in /etc/apt/source-list

---

### Post by iponeverything on 2012-04-18
modify the archive addresses to be:

old-releases.archive.ubuntu.com

---

### Post by Scott216 on 2012-04-18
> **mörgæs said:**
> Then Lubuntu 11.10 would be worth trying.

When you have it installed, please post which application is slowing it down.

I tried that version, same problem.  When it runs slow, it's any application I open.  It's just very slow overall.

---

### Post by mörgæs on 2012-04-18
Does **top** indicate what's going on?

---

### Post by tmaranets on 2012-04-18
Try installing other distributions like Xubuntu or Lubuntu, maybe try Kubuntu.

---

### Post by Scott216 on 2012-04-18
> **iponeverything said:**
> modify the archive addresses to be:

old-releases.archive.ubuntu.com

That didn't work, I get errors like:
-releases.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages  404 Not Found [IP: 91.189.92.182 80]

If I go to [http://old-releases.archive.ubuntu.com/ubuntu/ubuntu/dists/](http://old-releases.archive.ubuntu.com/ubuntu/ubuntu/dists/) with my browser, there is nothing for /jaunty/, just hardy, lucid and others.  Do you know where jaunty files are?

---

### Post by dino99 on 2012-04-18
> **Scott216 said:**
> That didn't work, I get errors like:
-releases.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages  404 Not Found [IP: 91.189.92.182 80]

If I go to [http://old-releases.archive.ubuntu.com/ubuntu/ubuntu/dists/](http://old-releases.archive.ubuntu.com/ubuntu/ubuntu/dists/) with my browser, there is nothing for /jaunty/, just hardy, lucid and others.  Do you know where jaunty files are?

its life have stopped now :(
why do you want to install/use a so old release ?

myself run Oneiric smootly with the same config as yours (Pentium 4, 2.4GHz CPU, 1 GB RAM )

---

### Post by iponeverything on 2012-04-18
> **Scott216 said:**
> That didn't work, I get errors like:
-releases.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages  404 Not Found [IP: 91.189.92.182 80]

If I go to [http://old-releases.archive.ubuntu.com/ubuntu/ubuntu/dists/](http://old-releases.archive.ubuntu.com/ubuntu/ubuntu/dists/) with my browser, there is nothing for /jaunty/, just hardy, lucid and others.  Do you know where jaunty files are?

my fault:

[http://old-releases.ubuntu.com/ubuntu/dists/](http://old-releases.ubuntu.com/ubuntu/dists/)

---

### Post by Scott216 on 2012-04-19
> **iponeverything said:**
> my fault:

[http://old-releases.ubuntu.com/ubuntu/dists/](http://old-releases.ubuntu.com/ubuntu/dists/)

That worked.  Thanks!!

---

### Post by mörgæs on 2012-04-19
Please mark the thread 'solved'.

---

