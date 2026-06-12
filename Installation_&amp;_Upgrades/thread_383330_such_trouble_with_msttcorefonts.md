---
title: "such trouble with msttcorefonts"
date: 2007-03-13
forum: Installation &amp; Upgrades
---

### Post by fleshberkowski on 2007-03-13
hello,

i've tried installing microsoft truefonts a million different ways. i've done it through synaptic with all the repositories selected and i've tried it through the terminal and i get nothing but errors. the latest error was from synaptic and stated:

E: msttcorefonts: subprocess post-installation script returned error exit status 1

and before, in the terminal i got this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
msttcorefonts is already the newest version.
The following packages were automatically installed and are no longer required:
  libxine-main1 libboost-python1.33.1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up msttcorefonts (1.2ubuntu3) ...
warning: /usr/share/fonts/X11/truetype does not exist or is not a directory
warning: /usr/lib/X11/fonts/truetype does not exist or is not a directory
These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)
 
******

any info on what i can do would be greatly appreciated. this has been driving me crazy and i've read endless forums and i can't tell what i'm doing wrong

best,

doug

---

### Post by zvacet on 2007-03-13
[http://sft.if.usp.br/msttcorefonts/]("http://sft.if.usp.br/msttcorefonts/")

---

### Post by linear on 2007-03-13
For future reference, you appear to have a proxy (without an address) set for wget. If you aren't behind a proxy server, you need to disable this. Search the forums for "proxy" and "wgetrc", and you should find instructions.

---

### Post by fleshberkowski on 2007-03-14
what could i do with the fonts on  that page? andale32.exe? i tried just dropping them into the font folder but that of course didn't know and i don't know what i can do w/ an exe file in linux. 

also since i tried and failed to install msttcorefonts, everytime i do an apt-get install in  the terminal (or in synaptic) it tells me how the mscorefonts failed. is there anyway to get rid of that? 

oh and one more thing, what exactly am i looking for w/ proxy and wgetrc?

---

### Post by linear on 2007-03-15
> **fleshberkowski said:**
> oh and one more thing, what exactly am i looking for w/ proxy and wgetrc?

You are looking to disable the attempted use of a proxy server, for example as described in [this post]("http://ubuntuforums.org/showpost.php?p=1273283&postcount=15").

---

### Post by fleshberkowski on 2007-03-16
nope, that did not  do it.

---

### Post by mysurface on 2007-12-14
Try the solution from here, [http://geek00l.blogspot.com/2007/11/ubuntu-msttcorefonts-problem-fixed.html](http://geek00l.blogspot.com/2007/11/ubuntu-msttcorefonts-problem-fixed.html)

---

