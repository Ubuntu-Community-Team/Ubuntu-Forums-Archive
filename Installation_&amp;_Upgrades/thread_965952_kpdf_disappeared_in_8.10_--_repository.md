---
title: "kpdf disappeared in 8.10 -- repository?"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by diagonallemma on 2008-10-31
Since upgrading to intrepid, kpdf, kdvi and kghostview have disappeared from my system, and I can't install them via apt-get. I guess I have to add the kubuntu repositories to my sources.list? Could anyone help me with the syntax for that?

Thanks.

---

### Post by joker77 on 2008-11-01
Same problem here too. Konsole stays and is working. evince document viewer disappeared from the Applications menu, but works.

---

### Post by neil.bacon on 2008-11-02
In KDE4 kpdf has been replaced by okular, which comes as part of the kdegraphics package. Cheers,

---

### Post by joker77 on 2008-11-05
Thanks. Am enjoying okular. Had no idea.

---

### Post by Stargazer989 on 2008-12-08
[bug output]("http://paste.stirk.org/45204")

i keep getting this every time i start okular in gnome, any ideas ?

---

### Post by mailforbiz on 2009-01-26
> **Stargazer989 said:**
> [bug output]("http://paste.stirk.org/45204")

i keep getting this every time i start okular in gnome, any ideas ?
Somewhat different problem here...okular works from gnome or command line but if I try to right-click on document and "open with okular", I get the above error. Ideas?

---

### Post by mailforbiz on 2009-01-26
> **mailforbiz said:**
> Somewhat different problem here...okular works from gnome or command line but if I try to right-click on document and "open with okular", I get the above error. Ideas?

Hmmm...interesting. I played around a bit and set the icon for Okular in the Gnome panel and now it works w/o error.

---

### Post by jARLAXL on 2009-02-18
Ok here is a mini how-to install kpdf in intrepid:

0. Reasons why to install:
 a: Because evince cannot select properly two rowed documents which are most usual for scientific documents etc.(this bug hasn't been fixed for years due to its low priority)
 b: Evince and okular cannot properly copy paste tables from documents (eg. tables are pasted without rows in gedit)

1. download dependency libpoppler2:
```
wget http://security.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler2_0.6-0ubuntu2.3_i386.deb
```

2. Double click the downloaded libpoppler2_0.6-0ubuntu2.3_i386.deb file and press install

3. Once install of libpoppler has finished you can close the windows of gdebi installer and download kpdf from mirror near your country: [http://packages.ubuntu.com/hardy/i386/kpdf/download]("http://packages.ubuntu.com/hardy/i386/kpdf/download") 

4. follow the same procedure as in 2, for the kpdf_3.5.9-0ubuntu1_i386.deb file

5. last but not least, find a pdf document right click->properties->"open with" tab->kpdf

and voila! kpdf opens now the kpdf documents!

---

### Post by calsaverini on 2009-04-04
This sucks...

I liked kpdf cause it was more complete than evince and much lighter than okular or acrobat reader for linux. 

I'm not confortable with okular. Particularly, it sucks having to wait the program load when I want to check on my pdflatex output... (what I do every second when I'm writing something...)

---

### Post by Ian Sinclair on 2009-04-20
My moan about Okular is that there is no provision for printing a range of pdf pages on both sides (printing odd-number pages then reloading into the printer to print even-number pages. Evince used to do this until a recent CUPS upgrade stopped Evince working. Adobe Reader printed four pdf pages on each A4 side. Might have to hook up the printer to the old Windows machine:(

---

### Post by Ian Sinclair on 2009-04-22
Tried your suggestion jARLXL, to install kpdf. It fell at teh first step with the terminal display:

~$ wget [http://security.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler2_0.6-0ubuntu2.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler2_0.6-0ubuntu2.3_i386.deb)
--2009-04-22 13:56:57--  [http://security.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler2_0.6-0ubuntu2.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler2_0.6-0ubuntu2.3_i386.deb)
Resolving security.ubuntu.com... 91.189.88.37
Connecting to security.ubuntu.com|91.189.88.37|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2009-04-22 13:56:58 ERROR 404: Not Found.

How do I get out of this one?

---

### Post by ThomasTC on 2009-05-21
Here are alternative instructions, that should keep working regardless of package versions or platform.

Go to each of these two:
[http://packages.ubuntu.com/hardy/libpoppler2](http://packages.ubuntu.com/hardy/libpoppler2)
[http://packages.ubuntu.com/hardy/kpdf](http://packages.ubuntu.com/hardy/kpdf)

Click the appropriate Download link at the bottom (amd64 or x86, depending on your platform). Save the files anywhere you like.

Double-click the libpoppler2 package and install it. Then do the same with the kpdf package.

---

### Post by agustinalarconmuller on 2009-05-31
Thanks to you all, I was missing Kpdf too for the reasons above (no double-side printing in okular)

---

### Post by oygle on 2009-06-16
Kpdf is not in Jaunty either.   :(

---

### Post by jARLAXL on 2009-07-25
Ok looks like the ubuntu staff did a good job to eliminate the kpdf application for jaunty/intrepid/etc for whatever reason (get more bug reports to fix okular perhaps?)

However, the reasons to install (as i posted in a previous post in this thread) still remain. Unfortuantely okular cannot cover my needs (as compared to kpdf)
so here is a way to install kpdf in jaunty:
1. download libpoppler2:
[http://packages.ubuntu.com/hardy/i386/libpoppler2/download](http://packages.ubuntu.com/hardy/i386/libpoppler2/download)
run/install the deb package (eg. double click)
2. download the kpdf package:
[http://packages.ubuntu.com/hardy/kpdf](http://packages.ubuntu.com/hardy/kpdf)
run/install as baove
3. enjoy!

I predict that kpdf will be removed when hardy support is over.
too bad
so hurry up and download and save the packages before that disaster.
hope at least that okular will have caught up by that time.

and a small request to ubuntu staff:
please let kpdf survive in the next versions of ubuntu.

---

### Post by abitemple on 2009-10-27
I also needed to be able to print even/odd pages, and after quite a bit of searching, I found that jaunty's repositories include a program called epdfview which is based on poppler libs. After installing it, I looked in the printing options, and low and behold, it supports even/odd pages as well as a specified range. :D

---

### Post by frisket on 2010-08-15
For the benefit of those who have upgraded to 10.4 and are still missing kpdf and kdvi, the news from the okular-devel mailing list is not good.

There have been several posts about the most glaring problem: the missing "Print Current Page" feature, and this is only listed as "wishlist".

Someone at KDE took there eye off the ball, and allowed Kpdf and Kdvi to be replaced prematurely with the much-degraded Okular, and this was a bad error of judgment.

You can still install Kpdf and Kdvi from Lenny, however. Download
[http://security.debian.org/debian-security/pool/updates/main/k/kdegraphics/kviewshell_3.5.9-3+lenny3_i386.deb](http://security.debian.org/debian-security/pool/updates/main/k/kdegraphics/kviewshell_3.5.9-3+lenny3_i386.deb)
[http://security.debian.org/debian-security/pool/updates/main/k/kdegraphics/kdvi_3.5.9-3+lenny3_i386.deb](http://security.debian.org/debian-security/pool/updates/main/k/kdegraphics/kdvi_3.5.9-3+lenny3_i386.deb)
[http://security.debian.org/debian-security/pool/updates/main/k/kdegraphics/kpdf_3.5.9-3+lenny3_i386.deb](http://security.debian.org/debian-security/pool/updates/main/k/kdegraphics/kpdf_3.5.9-3+lenny3_i386.deb)
and install them with aptitude or your favourite GUI package installer.

Don't expect the Okular problems to be fixed: the team are fine programmers, but they are not graphics developers, typographers, or document engineers, and they appear to have no understanding at all of the blunder that has been made.

Worse, the Ubuntu team appear to be blissfully unaware of the problem.

---

### Post by frisket on 2010-12-13
Just to update what jARLAXL said about installing kpdf in intrepid:

> Reasons why to install: Lots, Okular is broken.

> Download dependency libpoppler2: This doesn't seem to be available as given: instead, download the following (as at 2010-12-13)

[LIST=1]
[*]From [http://security.ubuntu.com/ubuntu/pool/main/p/poppler/](http://security.ubuntu.com/ubuntu/pool/main/p/poppler/) get libpoppler2_0.6.4-1ubuntu1_i386.deb and install it.

[*]From [http://packages.ubuntu.com/hardy/i386/kpdf/download](http://packages.ubuntu.com/hardy/i386/kpdf/download) get kpdf_3.5.10-0ubuntu1~hardy1.1_i386.deb and install it. It will probably prompt for some other missing KDE dependencies; let it install them too.

[*]From [http://packages.ubuntu.com/hardy/kviewshell](http://packages.ubuntu.com/hardy/kviewshell) get kviewshell_3.5.10-0ubuntu1~hardy1.1_i386.deb and install it.

[*]From [http://packages.ubuntu.com/hardy/i386/kdvi/download](http://packages.ubuntu.com/hardy/i386/kdvi/download) get kdvi_3.5.10-0ubuntu1~hardy1.1_i386.deb and install it.
[/LIST]
You should now be able to view PDFs and DVIs and have all the missing facilities back.

///Peter

---

