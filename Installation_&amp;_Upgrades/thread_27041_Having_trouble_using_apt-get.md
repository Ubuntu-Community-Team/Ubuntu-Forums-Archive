---
title: "Having trouble using apt-get"
date: 2005-04-14
forum: Installation &amp; Upgrades
---

### Post by VTHokie on 2005-04-14
Hey all,
I'm not sure if this is the correct sub-forum to use for my question but I guess I'll ask here anyways.  Ok, so I've just started using Ubuntu and I am really liking some of the stuff I'm seeing here as I'm fairly new to linux, but I'm having trouble really using this apt-get system as most of the time I can't seem to do anything with it.  

For example, I'm trying to add multimedia codecs to Ubuntu such as xvid and others so I read in the beginners guide that I need to add w32codecs to get these so I: 

sudo apt-get install gstreamer0.8-plugins first which goes over well with no problems, but then when I try to:

sudo apt-get install w32codecs I run into a all too familiar problem I see now:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package <package name> or in this case w32codecs

This is my first time using a debian based system and I'm completely unfamiliar with what to do.  

I next tried to add extra repositories that were mentioned in the beginners guide but that didn't change anything either.  I'm not sure what I'm doing wrong... could someone please tell me what I'm doing wrong and if there is some site that might have a crash course in how to use debian based systems correctly please.  :wink: 

Thanks in advance,

VTHokie

---

### Post by p!=f on 2005-04-14
Hi,

Did you read [http://ubuntuguide.org?](http://ubuntuguide.org?) ;)
Add Hoary backports to your /etc/apt/sources.list
```

deb http://backports.ubuntuforums.org/backports hoary-backports main universe multiverse restricted
deb http://backports.ubuntuforums.org/backports hoary-extras main universe multiverse restricted

```
Run sudo apt-get update and install the package.

---

### Post by VTHokie on 2005-04-14
Thanks p!=f  :grin: 
I actually screwed up because when I looked back over what you said, I did do that... unfortunately I only uncommented the needed lines but forgot to add:

deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

to the end of the list, after which the thing worked like a champ.  Next time I need to fully read all the instructions I guess.  ](*,) 

VTHokie

---

