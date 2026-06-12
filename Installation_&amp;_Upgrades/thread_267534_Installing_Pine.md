---
title: "Installing Pine"
date: 2006-09-28
forum: Installation &amp; Upgrades
---

### Post by n3r0 on 2006-09-28
Hello

I have just set up a mail server as per the faq on how to do that. telnetting to the server works great!

So then I went to run mail. Ubuntu doesnt have this command? OK well mail sucks anyways, so i go to install pine. apt-get doesnt know wtf im talking about so I go download the RPM. oops! ubuntu doesnt know what rpms mean. So i download the .deb. Success! dpkg aparently knows what to do with this. However when running it I get a failed dependency... 
```
dpkg: dependency problems prevent configuration of pine:
 pine depends on libssl0.9.7; however:
  Package libssl0.9.7 is not installed.

```
Oh the horror... I hate that word.. dependency.. But i figure ok its just one package so I try to apt-get it. no dice. So i go try and download the package ( [http://packages.debian.org/stable/libs/libssl0.9.7](http://packages.debian.org/stable/libs/libssl0.9.7) ). Ok its source, I can do this easy. ./configure make make install right?

NOPE.. it tells me to run ./config so I do that then it says it cant find make (!!!) which to me means stop, find out how you could be so wrong in understanding how this works and RTFM.

So here I is. I could just forget about installing pine, but what happened to mail? and WhereTF is make??!

---

### Post by Sef on 2006-09-28
To compile, build-essential needs to be installed.  Have you installed it?

If not, then from the terminal:

sudo aptitude update

sudo aptitude install build-essential

---

### Post by n3r0 on 2006-09-28
aptitude eh.. looks like some kind of alternative package management system.. Ill try it thanks.

---

