---
title: "XMMS - no acceptable C compiler?"
date: 2005-08-06
forum: Installation &amp; Upgrades
---

### Post by Grey Breaker on 2005-08-06
Yeah, I'm new, and I couldn't find anything like this in the search. Sorry if this has already been answered, but...

When trying to install Xmms, I go to the root prompt and CD to the directory I decompressed it into, and run the configure command, but I get this:

checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for prefix by checking for xmms... no
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

Erm... this is my first install on Ubuntu... can someone please translate?

---

### Post by Grey Breaker on 2005-08-06
Answered my own question. heh.

[http://www.linuxforums.org/forum/topic-50692.html](http://www.linuxforums.org/forum/topic-50692.html)

For those of you also wondering...

---

### Post by Grey Breaker on 2005-08-06
Alright, in the spirit of talking to myself... Sorry for the triple post...

Now I recieve this error after considerable more time is spent configuring stuff...

configure: error: *** GLIB >= 1.2.2 not installed - please install first ***

Any thoughts?

---

### Post by garydevitt on 2005-08-07
[QUOTE=Grey Breaker]Alright, in the spirit of talking to myself... Sorry for the triple post...

Now I recieve this error after considerable more time is spent configuring stuff...

configure: error: *** GLIB >= 1.2.2 not installed - please install first ***

Any thoughts?[/QUOTE]
 Yeh i got the same GLIB error message...any help here folks?

---

### Post by Grey Breaker on 2005-08-16
Alright, learned about apt-get. No, it's not the final answer, but atleast it solved the problem and now I'm happy with Ubuntu.

For those who don't know about it, go to [http://ubuntuguide.org/](http://ubuntuguide.org/)
 and follow the instructions. life is so much easier now. :-D

---

