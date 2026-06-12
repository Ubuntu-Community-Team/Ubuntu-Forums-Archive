---
title: "download for offline update"
date: 2005-08-25
forum: Installation &amp; Upgrades
---

### Post by rquint on 2005-08-25
I have two ubuntu machines (one i386, one ppc) whose only connection to the internet is a dialup connection.  I can use a Windows PC elsewhere with a broadband connection.  Where can I find updates which I can download by FTP and transfer by sneaker net (ZIP disks, CDs) for these machines-e.g., kernel source updates? These are close to 40MB and my ISP is unstable after an hour or two online.

---

### Post by weekend warrior on 2005-08-29
You could use the Unofficial Ubuntu 5.04 Add-On CD to update from a snapshot made 2005-08-01

Get it [here](http://ubuntuforums.org/showpost.php?p=150088&postcount=1)

---

### Post by rquint on 2005-08-29
[QUOTE=weekend warrior]You could use the Unofficial Ubuntu 5.04 Add-On CD to update from a snapshot made 2005-08-01

Get it [here](http://ubuntuforums.org/showpost.php?p=150088&postcount=1)[/QUOTE]
 Thanks for the info about the CD.  What about downloading a single file?  For example, if I download an update on one machine, I can copy the deb from file from the cache to another machine and update from that.  When I look at the repositories using a browser on an XP machine I can't locate the deb files I could use to update Ubuntu boxes.

---

### Post by navneet on 2005-08-29
Did you look at the /var/cache/apt/archives directory ? All the downloaded debs seem to be there on my machine

---

### Post by rquint on 2005-08-30
[QUOTE=navneet]Did you look at the /var/cache/apt/archives directory ? All the downloaded debs seem to be there on my machine[/QUOTE]
 That's the location on my machine where downloads go.  What I need is the url for the deb file so I can download it to an XP box connected to the internet at another location.

---

### Post by GozzoMan on 2005-08-31
Hi,
 I was trying to do the same thing, and after a bit of surfing, the location to download single deb files seems to be:

[http://archive.ubuntu.com/ubuntu/pool/](http://archive.ubuntu.com/ubuntu/pool/)

Actually I'm assuming (and hoping) that these are the most updated stable debs for Hoary, and in fact I like someone to confirm it, since it doesn't seem to be specified anywere.

Note that in the [http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/) directory there do are subdirectory named by release, but they seem to contain all packages compressed in one whole gz or bz2 file, while we'd like to download single debs instead.

So, anyone from the staff to confirm it? 
(I volunteer to write a brief wiki entry once found out.)

I also think I read somewhere that a more proper web interface for this purpose is planned, do I remember correctly?

Thanks all.

---

### Post by rquint on 2005-09-02
Thanks, exactly what I was looking for.

---

### Post by GozzoMan on 2005-11-21
[QUOTE=GozzoMan]
I also think I read somewhere that a more proper web interface for this purpose is planned, do I remember correctly?
[/QUOTE]

Hi all,
   maybe it's obvious, but I just found out. 

Here it is:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

There are also firefox search plugins for it:
[http://mycroft.mozdev.org/download.html?name=ubuntu&submitform=Find+search+plugins](http://mycroft.mozdev.org/download.html?name=ubuntu&submitform=Find+search+plugins)


Bye,

---

