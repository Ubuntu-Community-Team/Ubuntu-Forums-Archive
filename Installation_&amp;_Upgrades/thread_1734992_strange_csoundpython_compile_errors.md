---
title: "strange csound/python compile errors"
date: 2011-04-20
forum: Installation &amp; Upgrades
---

### Post by david.medine on 2011-04-20
Hello,
I am running Ubuntu 10.10 on an AMD quadcore and I am trying to install Csound plus its fancy python jazz.  I am attempting to use python2.7 (although it doesn't make a difference if I specify another version). Anyway, the build command I run is something like this:
code:
scons buildInterfaces=1 buildPythonWrapper=1 etc.

and the error that I get is this:
/usr/bin/ld: /usr/local/lib/libpython2.7.a(abstract.o): relocation R_X86_64_32 against `.rodata.str1.8' can not be used when making a shared object; recompile with -fPIC
/usr/local/lib/libpython2.7.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
scons: *** [_csnd.so] Error 1
scons: building terminated because of errors.

Csound builds just fine when I exclude the python wrapper flag. 

Now, when I build python, I notice that there are all kinds of -fPIC flags flying when it is putting the libraries into /usr/local/lib. Just in case I have tried reinstalling with the -fPIC on after hitting make. Still nothing. I have been at it for days with no success.

What is truly odd is that I have done this successfully (with no problems at all!!) on my little lenovo netbook (also running Ubuntu 10.10).

No one else on the web (as far as I can see) is encountering this error.   I have requested a login to the csound forum, but they insist on  granting each one via email and I am still awaiting a reply.

I presume that this must have something to do with 64 vs 32 bit architecture (the problematic desktop is 64), but I have no idea where to begin rectifying this situation.

Any ideas?

---

### Post by mantaraya36 on 2011-04-22
This is a weird problem... Can you try the Csound-devel mailing list?

[https://lists.sourceforge.net/lists/listinfo/csound-devel](https://lists.sourceforge.net/lists/listinfo/csound-devel)

---

### Post by david.medine on 2011-04-22
Thanks,
I will do that. I am still waiting approval to post in the Csound forums. . .

---

