---
title: "At my wits end with BRL-CAD"
date: 2010-03-23
forum: Installation &amp; Upgrades
---

### Post by amonaaron on 2010-03-23
I've been trying (unsuccessfully) to install BRL-CAD on my 64 bit Ubuntu system, I've looked through the forums and I've seen others that have had issues as well. Maybe it's because my brain is fried from trying to get it to install, but I am officially out of ideas.

 I downloaded the brlcad_7.12.2_x86_64.tar.gz file from Sourceforge into my /home/aaron directory and then used the following code (per the instructions in the Install readme file).

```
gunzip brlcad_7.12.2_x86_64.tar.gz
tar -xvf brlcad_7.12.2_x86_64.tar.gz
sudo mv usr/brlcad /aaron/
```Beyond that I tried to follow the instructions, but quite honestly after I reach that point I cannot seem to figure anything out. I also have tried the installation instructions on [http://brlcad.org/wiki/Building_from_SVN](http://brlcad.org/wiki/Building_from_SVN). This yielded slightly more success, but it would not install.

As far as I can tell I've installed all of the necessary packages to install this, but nothing seems to be working for me. I have looked at [http://ubuntuforums.org/showthread.php?t=1428226&highlight=brlcad](http://ubuntuforums.org/showthread.php?t=1428226&highlight=brlcad) and got very little help from it, as my brain is pretty much fried right now.


Thanks in advance, and I'm sorry if this is repetitive.

---

### Post by bigseb on 2010-04-19
See this link for instructions: [http://openae.org/download-brl-cad](http://openae.org/download-brl-cad)

It has directions for both the 32bit and 64bit. I'm running x64 brl-cad on x64 Karmic. Works a treat!

---

### Post by amonaaron on 2010-07-23
Thanks for the help, unfortunately this still isn't working for me. I follow those instructions and get nowhere. I keep getting the error below, so obviously there is something that needs to be done that I'm not sure how to do.

```
/usr/usr/brlcad/bin/mged: error while loading shared libraries: libtermio.so.19: cannot open shared object file: No such file or directory
```

I haven't looked at trying to install this until today, but I'm about ready to give up on it completely.

---

### Post by pmorton on 2010-08-17
Can't help, but have got the same problem, same error message. Can bigseb say how he got it running?

---

### Post by brlcad on 2010-08-17
> **amonaaron said:**
> Thanks for the help, unfortunately this still isn't working for me. ```
/usr/usr/brlcad/bin/mged: error while loading shared libraries: libtermio.so.19: cannot open shared object file: No such file or directory
```


Hm, that's pretty odd.  Are you using the 7.12 or 7.16 release binary?  I am seeing libtermio.so.19 in the most current 7.16 release binary:

```
prompt$ cd /usr/brlcad/lib && ls -la libterm*
-rw-r--r--   1 morrison  morrison  67696 Aug  5 13:39 libtermio.a
-rwxr-xr-x   1 morrison  morrison    901 Aug  5 13:39 libtermio.la
lrwxr-xr-x   1 morrison  morrison     19 Aug 17 13:30 libtermio.so -> libtermio.so.19.0.1
lrwxr-xr-x   1 morrison  morrison     19 Aug 17 13:30 libtermio.so.19 -> libtermio.so.19.0.1
-rwxr-xr-x   1 morrison  morrison  66027 Aug  5 13:39 libtermio.so.19.0.1
```

What do you get if you run ldd on /usr/brlcad/bin/mged ?

Building BRL-CAD from a source distribution is usually really trivial and might be a trivial work-around.

Cheers!
Sean

---

### Post by heitzmann on 2010-09-06
I had the same problem when I put the brlcad files in **/usr/local**.

Before trying to compile it myself, I moved the brlcad folder back to **/usr** and now it works.

So I'm guessing it's just a installation path issue.

---

