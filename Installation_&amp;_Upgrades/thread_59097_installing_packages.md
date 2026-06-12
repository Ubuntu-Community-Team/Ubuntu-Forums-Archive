---
title: "installing packages"
date: 2005-08-22
forum: Installation &amp; Upgrades
---

### Post by Becu on 2005-08-22
Hi, 

I have installed Ubuntu on my laptop because I need to install and use an open source "tagger" for linguistic analysis, which is Linux-based (I am working on my MA thesis on discourse analysis). So, I'm a newbie and this is my first experience with Linux...

The tagger installing process (in the "terminal") is asking me for some "packages" (db-lcfg-pcre-something) I had to download from the web. I cannot install them from the graphic "manager" supposed to be used for easily installing these things...¿is there any way for installing these "external" packages, other than using the terminal... I'm not familiar with its commands and I'm afraid I should be, because apparently the tagger has no graphic interface ...  and I'm not sure I'm clear enough in explaining this problem :S 

Help! 


Thank you in advance!

Becu

---

### Post by Swab on 2005-08-22
[QUOTE=Becu]Hi, 

I have installed Ubuntu on my laptop because I need to install and use an open source "tagger" for linguistic analysis, which is Linux-based (I am working on my MA thesis on discourse analysis). So, I'm a newbie and this is my first experience with Linux...

The tagger installing process (in the "terminal") is asking me for some "packages" (db-lcfg-pcre-something) I had to download from the web. I cannot install them from the graphic "manager" supposed to be used for easily installing these things...¿is there any way for installing these "external" packages, other than using the terminal... I'm not familiar with its commands and I'm afraid I should be, because apparently the tagger has no graphic interface ...  and I'm not sure I'm clear enough in explaining this problem :S 

Help! 


Thank you in advance!

Becu[/QUOTE]

Can you tell us the exact filenames of the packages?

---

### Post by Becu on 2005-08-23
This are the packages required and these I have installed:

libpcre 6.1

Berkeley DB 4.3

libcfg+0.6.1

It seems that I've managed to install these following the instructions given by the tagger manual. But... Here´s a new problem: I have installed these packages in this path: ./configure --prefix=/usr/local/mylibs, then "make" and "make install".

Now, when I come to install the tagger with the following instruction:
cd FreeLing-1.2 (this is the name of the tagging program)

./configure CPPFLAGS='-I/usr/local/mylibs/include' LDFLAGS='-L/usr/local/mylibs/lib'

That's ok. But when I type "make": everything goes fine for a while until I get the message asking for "libdb_cxx" (???)

Does this have anything to do with Berkeley DB package? Why do I get this message when I have installed that packaged correctly?


Thank you!!

---

