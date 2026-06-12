---
title: "msttcorefonts fails and keeps trying when installing somehting else"
date: 2006-11-13
forum: Installation &amp; Upgrades
---

### Post by l2ich84 on 2006-11-13
I'm pretty new to ubuntu or linux in general. 

I tried install the msttcorefonts, and it always fails. I get this in terminal: 

Preconfiguring packages ...
Selecting previously deselected package msttcorefonts.
(Reading database ... 173692 files and directories currently installed.)
Unpacking msttcorefonts (from .../msttcorefonts_1.2ubuntu1_all.deb) ...
Setting up msttcorefonts (1.2ubuntu1) ...
Regenerating /etc/vfontcap... done
Regenerating /etc/vflib3/vflibcap... Regenerating
/etc/vflib3/vflibcap-tex... done
warning: /usr/lib/X11/fonts/truetype does not exist or is not a directory
These fonts were provided by Microsoft "in the interest of cross-
platform compatibility". This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.
--18:10:15--
[http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
=> `./andale32.exe'
Resolving belnet.dl.sourceforge.net... 193.190.198.97<http://193.190.198.97>
Connecting to belnet.dl.sourceforge.net[193.190.198.97<http://193.190.198.97>]:80...
failed: Connection timed out.
Giving up.

--18:10:20--
[http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
=> `./andale32.exe'
Resolving easynews.dl.sourceforge.net... 69.16.168.245<http://69.16.168.245>
Connecting to easynews.dl.sourceforge.net[69.16.168.245<http://69.16.168.245>]:80...
failed: Connection timed out.
Giving up.

--18:10:26--
[http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
=> `./andale32.exe'
Resolving twtelecom.dl.sourceforge.net... 207.250.4.12 <http://207.250.4.12>
Connecting to twtelecom.dl.sourceforge.net[207.250.4.12<http://207.250.4.12>]:80...
failed: Connection timed out.
Giving up.

--18:10:31--
[http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
=> `./andale32.exe'
Resolving aleron.dl.sourceforge.net... 204.157.3.229 <http://204.157.3.229>
Connecting to aleron.dl.sourceforge.net[204.157.3.229
<http://204.157.3.229>]:80...
failed: Connection timed out.
Giving up.

--18:10:37--
[http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
=> `./andale32.exe'
Resolving cesnet.dl.sourceforge.net... 195.113.161.88<http://195.113.161.88>
Connecting to cesnet.dl.sourceforge.net[195.113.161.88<http://195.113.161.88>]:80...
failed: Connection timed out.
Giving up.

--18:10:43--
[http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
=> `./andale32.exe'
Resolving switch.dl.sourceforge.net... 130.59.138.20 <http://130.59.138.20>
Connecting to switch.dl.sourceforge.net[130.59.138.20
<http://130.59.138.20>]:80...
failed: Connection timed out.
Giving up.

andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
msttcorefonts

And now everytime I try to install anything else it keeps trying to install this. How do I just stop it and tell it to stop trying?

---

### Post by dcstar on 2006-11-14
> **l2ich84 said:**
> I'm pretty new to ubuntu or linux in general. 

I tried install the msttcorefonts, and it always fails. I get this in terminal: 
.......
And now everytime I try to install anything else it keeps trying to install this. How do I just stop it and tell it to stop trying?

Start Synaptic, select that package and remove it.

If that doesn't work, try the "Fix broken packages" option.

---

### Post by Fabiano Shark on 2006-11-17
After installing the *m$ttfonts* manually [SIZE="1"](you can find many ways in the web)[/SIZE], for stopping showing this message you can remove or move it's files... like this:

```

$ sudo mkdir /var/lib/dpkg/info/msttcorefonts_bkp
$ sudo mv /var/lib/dpkg/info/msttcorefonts.* /var/lib/dpkg/info/msttcorefonts_bkp
$ sudo mv /var/cache/apt/archives/msttcorefonts_1.2ubuntu3_all.deb /var/cache/apt/archives/msttcorefonts_1.2ubuntu3_all.deb.bkp

```

Just it! ;)

---

