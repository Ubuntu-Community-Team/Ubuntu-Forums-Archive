---
title: "Acrobat Reader installation gives trouble on 12.04"
date: 2012-11-13
forum: Installation &amp; Upgrades
---

### Post by Gan_HOPE326 on 2012-11-13
Hello,

I just installed Ubuntu 12.04 64bit on my new laptop (on my previous one I used 11.10). One of the first programs I installed was Adobe Reader, and I did so by downloading the .deb package from the Adobe website. The program works fine; however, the first installation gave an error message. By reading the details, the last lines were:

```
Error in function: 
Setting up adobereader-ita:i386 (8.1.7) ...
dpkg: error processing adobereader-ita:i386 (--configure):
 subprocess installed post-installation script returned error exit status 1
``` 

Now I get the same problem whenever I install anything from the Software Center. The programs are installed just fine, but there always is a final error message and these lines pop up in the details (copypasted from the installation of Geany):

```
Setting up adobereader-ita:i386 (8.1.7) ...
dpkg: error processing adobereader-ita:i386 (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up geany-common (0.21.dfsg-1ubuntu4) ...
Setting up geany (0.21.dfsg-1ubuntu4) ...
Errors were encountered while processing:
 adobereader-ita:i386
Error in function: 
Setting up adobereader-ita:i386 (8.1.7) ...
dpkg: error processing adobereader-ita:i386 (--configure):
 subprocess installed post-installation script returned error exit status 1
```

It seems to me that the USC tries to run an installation for the 32 bit version of Acroread, as if queued...? But I don't really get what's going on. It's just an annoyance, actually, since it doesn't cause any functional problem, but I still would like to eliminate it. Could you suggest anything? What should I clean up/delete to make the Software Center stop trying to install this stuff?

---

