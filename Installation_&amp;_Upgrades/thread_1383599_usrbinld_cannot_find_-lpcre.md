---
title: "/usr/bin/ld: cannot find -lpcre"
date: 2010-01-17
forum: Installation &amp; Upgrades
---

### Post by UltimusRex on 2010-01-17
Hello. I am quite new to Linux and Ubuntu, so I apologize if my lack of knowledge/understanding on the subject frustrates anyone. I'm running Ubuntu 9.10.

Here is the last bit copied from the terminal when trying to install prce-8.00, including the error it returns.

```
libtool: relink: g++ -shared -nostdlib /usr/lib/gcc/i486-linux-gnu/4.4.1/../../../../lib/crti.o /usr/lib/gcc/i486-linux-gnu/4.4.1/crtbeginS.o  .libs/pcrecpp.o .libs/pcre_scanner.o .libs/pcre_stringpiece.o   -L/usr/local/lib -lpcre -L/usr/lib/gcc/i486-linux-gnu/4.4.1 -L/usr/lib/gcc/i486-linux-gnu/4.4.1/../../../../lib -L/lib/../lib -L/usr/lib/../lib -L/usr/lib/gcc/i486-linux-gnu/4.4.1/../../.. -L/usr/lib/i486-linux-gnu -lstdc++ -lm -lc -lgcc_s /usr/lib/gcc/i486-linux-gnu/4.4.1/crtendS.o /usr/lib/gcc/i486-linux-gnu/4.4.1/../../../../lib/crtn.o    -Wl,-soname -Wl,libpcrecpp.so.0 -o .libs/libpcrecpp.so.0.0.0
/usr/bin/ld: cannot find -lpcre
collect2: ld returned 1 exit status
libtool: install: error: relink `libpcrecpp.la' with the above command before installing it
make[1]: *** [install-libLTLIBRARIES] Error 1
make[1]: Leaving directory `/home/ultimusrex/Downloads/pcre-8.00'
make: *** [install-am] Error 2
```This all started when I was trying to install fuppes (0.640) so I can use my Ubuntu system as a media server for the other devices on my network. from reading a couple of the files that came with the package, I figured out how to run the "./configure", "make", and "make install" commands, and I'm hoping that it will eventually work out. But I also saw that it had a dependency on the PCRE package which I downloaded and started trying to install in the same manner. The first time I tried (installing PCRE), I saw a couple errors about "g++" so I checked the Synaptic Package Manager and was pleased to find exactly that in there, after installing g++ the PCRE package gave me no more errors about it, but it did error out where I noted above, copied from the terminal. I have no idea how to "relink 'libpcrecpp.la' with the above command before installing it."

Alternatively, I would love if someone could tell me how to do all of these installs via the GUI, if there's a way to add them to the Synaptic Package Manager and let ***it*** take care of them, or something... but I'm also no stranger to the concept of command line interface... So any help anyone can offer me on this would be greatly appreciated.

---

### Post by Shhnap on 2010-01-18
As one of the developers on fuppes I can tell you that you don't need to build pcre from source in order to compile fuppes. You just need the pcre dev package. If you did want to build pcre from source then I would recommend running debuild in the pcre source directory.

Take a look at the dependencies of the fuppes wiki page: [http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Compiling_on_Ubuntu_Linux]("http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Compiling_on_Ubuntu_Linux")

Install them and a simple:

autoreconf -vfi && ./configure && make should be enough to completely compile fuppes.

P.S. And in a few weeks a package should be released for fuppes. See the main fuppes on karmic thread on these forums. :) ;)

---

