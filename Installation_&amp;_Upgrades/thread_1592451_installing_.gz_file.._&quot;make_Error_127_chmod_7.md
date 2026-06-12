---
title: "installing .gz file..: &quot;make: Error 127 chmod 755 &quot;"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by UbuNoob001 on 2010-10-10
So I am new to linux and computing in general: 


I am installing curphoo ( a yahoo chat client). The README file contains the following text ```
You need a Python 2.4 series interpretter starting with Curphoo 0.4.0.
Starting with 0.4.0, Curphoo uses a purely Python implementation of
the YMSG authentication protocol.  It also uses new functions found
only Python 2.4's curses module.

Curphoo 0.3.12 continues to work with Python 2.1, 2.2 an 2.3 however,
but you will need a GNU development toolchain and also the headers for
your curses implementation installed.

* Installation 

    1. Unpack the source tarball
    2. cd to the newly made directory
    3. Type make (or gmake on bsd)
    4. Type ./curphoo
    5. Enjoy!

```When I get to step 3, I get the following: ```
~/Desktop/curphoo/curphoo-0.4.3-3$ make
/bin/sh: c: not found
make: [curphoo] Error 127 (ignored)
chmod 755 curphoo

```I have python version 2.6.5 and the contents of the unpacked curphoo directory are: ```
AUTHORS       cmdparser.py  encodep.py         Makefile       shexec.py
babelizer.py  color         Entry.py           md5crypt.py    yahoodef.py
boot.py       commands      floo2phoo          output.py      yahoo_fn.py
BUGS          COPYING       ignoremsg.donkey   pickle2txt.py  YahooMD5.py
ChangeLog     cpformat.py   ignoremsg.iggygun  pysha.py       Yahoo.py
clopt.py      curphoo.1     __init__.py        README
cmdhelp.py    driver.py     m9dec.py           Session.py
```any suggestions?

---

### Post by JackNocturne on 2010-10-10
hi,

go to 
~/Desktop/curphoo/curphoo-0.4.3-3

instead of make type ```
**./make**
```

---

### Post by UbuNoob001 on 2010-10-10
> **JackNocturne said:**
> hi,

go to 
~/Desktop/curphoo/curphoo-0.4.3-3

instead of make type ```
**./make**
```

Jack, unfortunately ```
./make
bash: ./make: No such file or directory

```

---

### Post by JackNocturne on 2010-10-11
Ok,

Do you have all the **dependencies** installed?

according to the read me 
1)You need Gnu toolchain (**gcc **package installed)
2. Headers for your curses implementation installed.(I dont know what this is)

---

### Post by JackNocturne on 2010-10-11
I did some more digging, the curses implementation & gcc  can be found in **Synaptic Package Manager**. 
When you enter just search for them under Quick search, install them,you should be good to go.

---

### Post by UbuNoob001 on 2010-10-11
> **JackNocturne said:**
> I did some more digging, the curses implementation & gcc  can be found in **Synaptic Package Manager**. 
When you enter just search for them under Quick search, install them,you should be good to go.

I have the GCC, GCC base package and GCC support library. That README isnt very specific as to which development toolchain and curses implementation they want me to have. Any suggestions. 

thanks for all the help JackN :)

---

### Post by UbuNoob001 on 2010-10-11
> **JackNocturne said:**
> I did some more digging, the curses implementation & gcc  can be found in **Synaptic Package Manager**. 
When you enter just search for them under Quick search, install them,you should be good to go.

I have the GCC, GCC base package and GCC support library. That README isnt very specific as to which development toolchain and curses implementation they want me to have. Any suggestions?

thanks for all the help JackN :)

---

### Post by JackNocturne on 2010-10-11
Interesting, i also downloaded the package and tried it, finding same **error** as you:P
more info here > [http://curphoo-kc.sourceforge.net/docs/cpfaq.html](http://curphoo-kc.sourceforge.net/docs/cpfaq.html)  <  I think solution could be in that link


By the way it looks like you want a yahoo chat client? Have u tried **GYachE **Improved??
Its really good,contains more features than even official yahoot chat client.

---

### Post by UbuNoob001 on 2010-10-12
> **JackNocturne said:**
> Interesting, i also downloaded the package and tried it, finding same **error** as you:P
more info here > [http://curphoo-kc.sourceforge.net/docs/cpfaq.html](http://curphoo-kc.sourceforge.net/docs/cpfaq.html)  <  I think solution could be in that link


By the way it looks like you want a yahoo chat client? Have u tried **GYachE **Improved??
Its really good,contains more features than even official yahoot chat client.

Jack,
   Yeah unfortunately I have been unable to get it to work. While setting the path to python2.6 allowed the first step to work, there were issues with deprecation and md5 import requirements etc.   However I checked out GYachE and this seems basically what I was looking for. More fully featured than GAIM and very lean. Thanks for the help :)

---

