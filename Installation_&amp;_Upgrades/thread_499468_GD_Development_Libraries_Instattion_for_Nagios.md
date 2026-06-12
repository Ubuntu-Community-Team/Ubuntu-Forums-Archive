---
title: "GD Development Libraries Instattion for Nagios"
date: 2007-07-12
forum: Installation &amp; Upgrades
---

### Post by djung01 on 2007-07-12
Hi, I just got my UBUNTU 7 up and running, and am trying to install GD Development Libraries for the Nagios reprequisit, by running the command, "sudo apt-get install libgd2-dev"
after running it, it says "You should explicitly select one to install."  E: Package libgd2-deev has no installation candidate.

What must I do?  I am new to the UBUNTU, and UNIX world, please help me.  Thank you all.

---

### Post by drum_lord_jr on 2007-11-09
i'm stuck in the same boat. I read in another fourm post that doing

*[CENTER][I]apt-get install libgd2-xpm*[/CENTER][/I]

would work instead of -dev. I tried this, it installed some things but i'm still thinking it didnt fix the issue.  

I did see on nagios.org that its very important to have these development libraries running or else you wont get statusmap, trends, and histogram CGI's working. What i've run into is trying to figure out how to get all the libraries installed that are needed. I just dont know how to do it. 

libgd
libgd-devel
libpng
libpng-devel
libjpeg
libjpeg-devel
zlib
zlib-devel

When I looked in the library directory I noticed that there where simular files in there however instead of it saying zlib it said libz. dunno if its one in the same but I do know that i'm still having issues with the CGI's which is related to these dev libraries.

[http://www.nagios.org/faqs/viewfaq.php?faq_id=55](http://www.nagios.org/faqs/viewfaq.php?faq_id=55)

---

### Post by Mari on 2007-11-11
I have the same problem. I've tried "sudo apt-get install libgd2-dev" for NAGIOS and it's not working. NAGIOS is running, but status information for localhost server is "Return code of 127 is out of bounds - plugin may be missing"

Mari

---

### Post by compiledkernel on 2007-11-20
Mari thats a plugin issue, not related to libgd2-dev. 

The plugin that your calling for a check doesnt exist on the server, or is malformed. Are you using or did you install nagios-plugins properly?

---

### Post by drum_lord_jr on 2007-11-20
Obvisouly I've missed something. I thought I did it all correct durring the install. After all, thats the only thing that didn't work to start. 

I did find this article that seemed to explain my issue, and leads me to believe its related to the GD Library.

[http://www.nagios.org/faqs/viewfaq.php?faq_id=55&expand=false&showdesc=false](http://www.nagios.org/faqs/viewfaq.php?faq_id=55&expand=false&showdesc=false) 

The only problem is that i've run out of ways I know of to install these lib files. I cant even find them listed for Ubuntu, so chances are what Lib files i've been attempting to install and recompile with are no good. 

Is there a command I can run that will show if the correct lib files are installed? I tried 'make devclean'  as described in the link, but it scrolls by so fast even Chuck Norris would have a tough time reading it.

Any help on this is greatly appreciated.

---

### Post by compiledkernel on 2007-11-20
Our DSF howto is pretty self expalantory, did you install it similar to this manner? 

[http://doc.gwos.org/doku.php/doc:network:nagios](http://doc.gwos.org/doku.php/doc:network:nagios)

---

### Post by drum_lord_jr on 2007-12-04
yes, however the command
"sudo apt get install libgd2-dev" without quotes comes back with an error stating that it cant find libgd2-dev.  I ended up downloading gd-22.0.35.tar.gz and was able to install and compile it. However the libjpeg library that I assume is in the libgd2-dev isn't showing as being compiled. its in the lib dir but dosn't show up as "yes" when compiling or making gd-2.0.35.  I installed jpeg-6b and did the compile and make, on it but it still show's as "no". Status Map on nagios along with a few other CGI's depend on the jpeg lib. any suggestions?

---

### Post by drum_lord_jr on 2007-12-06
**UREKA!!! thanks to this site:**
[http://www.boutell.com/gd/faq.html](http://www.boutell.com/gd/faq.html)

**I read the following and found:**
"gd keeps saying it can't find png or jpeg support. I did install libpng and libjpeg. What am I missing?
Be sure to do "make install-headers" for libpng and "make install-lib" for libjpeg, in addition to "make install." You may also need to use a command line like this one when configuring gd: ./configure '--with-jpeg=/usr/local' '--with-png=/usr/local' 
'--with-zlib-dir=/usr/local' Often, users have installed these things in /usr/local/include and /usr/local/lib, but do not actually have those directories in their default include and library paths when configuring gd. Thanks to Santanu Misra and Alastair Battrick. "

**the key to getting jpeg support in the GD is to install jpeg-6b by first unzipping it, then doing a "make", "make install-headers", "make install-lib", and "make install". Then go to the GD install folder, do a "make clean", then do the ./config --with-jpeg=/usr/local, then the make, and make install.**

The only bummer to all this is that I thought it would fix the issue in Nagios where you get a 404 error on the Status Map, Trends, and Alert Histogram pages- It didn't. Seems I may have one more crucial part to making it work, but not everything yet. however this is how I got GD to recognize and support JPEG... or at least say that it did.

---

