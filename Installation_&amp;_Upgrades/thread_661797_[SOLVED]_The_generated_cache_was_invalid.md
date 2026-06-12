---
title: "[SOLVED] The generated cache was invalid"
date: 2008-01-08
forum: Installation &amp; Upgrades
---

### Post by rocky_raccoon on 2008-01-08
When I try to install or remove some packages I get the message "the generated cache was invalid". It appears, though, that the process (of installing or removing) is completed "correctly" because I can use the program. I hope anyone can help, I was not getting this message in the past.

For example:

```
sudo apt-get install kpdf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  khelpcenter
Recommended packages:
  kghostview
The following NEW packages will be installed
  kpdf
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/344kB of archives.
After unpacking 1073kB of additional disk space will be used.
Selecting previously deselected package kpdf.
(Reading database ... 112208 files and directories currently installed.)
Unpacking kpdf (from .../kpdf_4%3a3.5.8-0ubuntu1_i386.deb) ...
Setting up kpdf (4:3.5.8-0ubuntu1) ...
The generated cache was invalid.

```

---

### Post by angry_johnnie on 2008-01-12
have you installed amsn... or anything else that requires autopackage?
i started having that same problem, just yesterday, after installing amsn.
i came across this:

[http://tuxvermelho.blogspot.com/2007/09/gimp-data-generated-cache-was-invalid.html](http://tuxvermelho.blogspot.com/2007/09/gimp-data-generated-cache-was-invalid.html)

now, my portuguese is lousy, but it looks like it's got something to do with the icon cache.

so, you could  go to /usr/share/icons/highcolor,  /usr/share/icons/locolor,  and so on, and just delete autopackage-installer.png.

---

### Post by rocky_raccoon on 2008-01-12
I do have amsn installed via autopackage.  Did you try the solution, did it work for you?

---

### Post by angry_johnnie on 2008-01-13
haha, sorry... i should've stated this first, but yes.  i did try it, and it worked allright.  it's just something about the icon cache that's not being done correctly.  so go ahead and delete it (the icon: autopackage-installer.png), or move it somewhere else.  that should do it.

---

### Post by rocky_raccoon on 2008-01-15
Thank you, It worked, I don't get the message anymore

---

### Post by gsiliceo on 2008-01-16
worked for me too, thx

---

### Post by psavva on 2008-02-26
Thanks dude, worked here as well

---

