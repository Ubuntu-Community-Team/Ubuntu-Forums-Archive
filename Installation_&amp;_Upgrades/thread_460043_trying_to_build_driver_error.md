---
title: "trying to build driver error"
date: 2007-05-31
forum: Installation &amp; Upgrades
---

### Post by justifier on 2007-05-31
Hi,

I am trying to build a driver for my touchscreen by following the instrucions on the product website at


[http://solutions.3m.com/3MContentRetrievalAPI/BlobServlet?locale=en_US&univid=1114294724399&fallback=true&assetType=MMM_Image&blobAttribute=ImageFile&placeId=34513&version=current](http://solutions.3m.com/3MContentRetrievalAPI/BlobServlet?locale=en_US&univid=1114294724399&fallback=true&assetType=MMM_Image&blobAttribute=ImageFile&placeId=34513&version=current)

but when trying to build the package, i get the error

make[2]: *** No rule to make target 'modules' . Stop
make[1]: *** [default] Error 2
make: *** [makeit] Error 2 
error: Bad exit status from /var/tmp/rpm-tmp.35780 (%build)


RPM build errors:
          Bad exit status from /var/tmp/rpm-tmp.35780 (%build)


Sorry for lack of complete copy but as that machine doesnt have a mouse (as its a touchscreen going on) i am having to type it all, 

any and all ideas will be welcomed

Justy

---

### Post by renzokuken on 2007-05-31
what command are you running to build the package?

from what i understand you are installing an .rpm file, which is messy at best on ubuntu since ubuntu is debian (.deb) based

may be better to convert rpm to deb using alien

sudo aptitude install alien

then

sudo alien name_of_file.rpm

sudo dpkg -i name_of_file.deb

also make sure you have kernel headers installed, these are in synaptic and you can find out which kernel you have by running ```
uname -r
``` at the terminal

---

### Post by justifier on 2007-05-31
command i am running, following the instructions is 

sudo rpmbuild -ba TWDrv.spec

and kernel headers are installed

the problem is that it isnt actually an rpm yet.

---

### Post by renzokuken on 2007-05-31
ahhh i see......i only skimmed over the instructions....i'll give em a proper read in a mo.....have you installed the "build-essentials" package yet?

---

### Post by justifier on 2007-05-31
yup, made sure of it before i even tried, adn kernel-headers are in aswell, also got make installed, and all packages with a refereance to rpm in the standard repos

---

