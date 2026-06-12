---
title: "Installing Tribler"
date: 2010-01-28
forum: Installation &amp; Upgrades
---

### Post by Bananasdoom on 2010-01-28
I have found this cool torrent client but it only has support for hardy, intrepid, jaunty is it possible like in windows I can use a program from an older version, and if so how??


Download ----->> [http://www.tribler.org/Download](http://www.tribler.org/Download)

~Thanks

---

### Post by mikewhatever on 2010-01-28
That particular program might actually work. Try adding the repository for Jaunty and then installing. That said, it looks like it's been unmaintained since July 2009.

---

### Post by tommcd on 2010-01-28
First, just out of curiosity, what is so special about Tribler? There are a crap load of torrent programs in the Ubuntu repos. I just use Transmission, which is part of a default Ubuntu install. It is a lightweight app (unlike a lot of stuff that Ubuntu includes) and works very well.

Second, if you really have your heart set on Tribler, just add the Tribler Jaunty repo to your /etc/apt/sources.list:
```
deb http://ubuntu.tribler.org/ jaunty main
``` 
The details of doing that are linked to on the Tribler page in your post:
[http://www.tribler.org/trac/wiki/faq#DoyousupportLinux](http://www.tribler.org/trac/wiki/faq#DoyousupportLinux)
Looking at the packages that it will install, as far as I know it won't overwrite or conflict with anything present on Ubuntu:
[http://ubuntu.tribler.org/dists/jaunty/main/binary-i386/](http://ubuntu.tribler.org/dists/jaunty/main/binary-i386/)
The one question is that python-vlc. I don't find a package by that name in the Ubuntu Karmic repos. I don't know if it would cause dependency issues with other python libraries in Ubuntu though. So install Tribler at your own risk, if you must.

---

### Post by mikewhatever on 2010-01-28
Python-vlc in in Tribler's repository, and the neat feature is video preview. Hope the OP posts some updates on how it went.

---

### Post by James Haigh on 2010-09-25
Hi,
I had the same problem: I wanted to install Tribler on Lucid Lynx.

I added:

```
deb http://ubuntu.tribler.org/ jaunty main
```

to my sources and then installed Tribler, but when I ran Tribler I got this:

```
[james@james-laptop ~]$ tribler
Unfortunatly we were not able to find a unicode package for wxPython 2.8 (python version 2.4, 2.5, or 2.6).
Cannot run Tribler, sorry
```

wxPython 2.8 is installed but I found that it has been moved to a different directory since Jaunty.

Tribler is writen in Python, so it's files are text rather than binary. In fact /usr/bin/tribler is a bash script that tells Python where everything is, gives errors if it can't find something and then tells Python to run Tribler.

So edit this file with a text editor (vim or nano etc.):

```
$ sudo vim /usr/bin/tribler
```

find the bit of code that looks for wxPython (line 20):

```
...
	# look for the python-wx library
	WXPYTHONVER=`ls -1d /usr/lib/$1/site-packages/wx-2.8* 2>/dev/null | grep -v ansi | sed -e 's/.*wx-//g' -e 's/-.*//g' | sort -nr | head -1`
	if [ "$WXPYTHONVER" != "" ]; then
		_WXPYTHONPATH=`ls -1d /usr/lib/$1/site-packages/wx-$WXPYTHONVER* | grep -v ansi | head -1`
	fi
...
```

and change 'site-packages' to 'dist-packages' as it is now called:

```
...
	# look for the python-wx library
	WXPYTHONVER=`ls -1d /usr/lib/$1/dist-packages/wx-2.8* 2>/dev/null | grep -v ansi | sed -e 's/.*wx-//g' -e 's/-.*//g' | sort -nr | head -1`
	if [ "$WXPYTHONVER" != "" ]; then
		_WXPYTHONPATH=`ls -1d /usr/lib/$1/dist-packages/wx-$WXPYTHONVER* | grep -v ansi | head -1`
	fi
...
```

Save and exit. Now Tribler should run.

James.

---

### Post by narcisgarcia on 2010-10-19
Easier arrangement for any 9.04+ version, and to allow updates:
```
if [ -d /usr/lib/python2.6 ] ; then sudo ln -s /usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode /usr/lib/python2.6/site-packages/wx-2.8-gtk2-unicode ; fi
if [ -d /usr/lib/python2.8 ] ; then sudo ln -s /usr/lib/python2.8/dist-packages/wx-2.8-gtk2-unicode /usr/lib/python2.8/site-packages/wx-2.8-gtk2-unicode ; fi
```

---

### Post by watchpocket on 2010-12-09
> First, just out of curiosity, what is so special about Tribler?

[http://bit.ly/egXfVa](http://bit.ly/egXfVa)

---

### Post by urulooke on 2010-12-11
It's a descentralized torrent downloader, you don't need a server to find seeds.... that's why it has an embedded search.

Ah, and also the video preview ;)

Anyway, I use deluge and are just testing it!!!

---

### Post by Tanath on 2010-12-11
Looks like OP read this:
[http://torrentfreak.com/truly-decentralized-bittorrent-downloading-has-finally-arrived-101208/](http://torrentfreak.com/truly-decentralized-bittorrent-downloading-has-finally-arrived-101208/)

This thread should be marked [solved].

---

### Post by synctext on 2011-01-27
Lot of thanks from the Tribler development team.
The simple add-on above was very helpful.

Currently we're working on Ubuntu 10.10 compatibility.
Problem is that VLC significantly altered their Python bindings.

We got some help and should be solved in next update release: [Tribler Dev Forum Post]("http://forum.tribler.org/viewtopic.php?f=2&t=1470&p=2304#p2304")
  - Tribler coordinator

---

