---
title: "help! Package caused havoc need to remove..."
date: 2007-01-26
forum: Installation &amp; Upgrades
---

### Post by gaillard on 2007-01-26
Hi everyone I need desperate help.

I accidently installed the gcc-4.1-base_4.1.1-21 I think it was called and it messed a lot up.  Thats all though.  Now I have the correct one on my desktop, I just need to replace the one thats there but how???!

Keep in mind this has to be done offline.

Thanks for the help and I really need this pc working for work tonight.

Thanks again

---

### Post by taurus on 2007-01-26
How did you install gcc-4.1-base_4.1.1-21?  Did you download and install it as .deb?

```
sudo dpkg -r gcc
```

---

### Post by gaillard on 2007-01-26
yes i did, wont this remove a ton of other packages as well?

---

### Post by gaillard on 2007-01-26
:( and shouldn't I specify the rest of the name or no?

---

### Post by taurus on 2007-01-26
What's the output of this command from a terminal?

```
gcc -v
```

---

### Post by gaillard on 2007-01-26
gaillard@gaillard-desktop:~$ gcc -v
Using built-in specs.
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release x86_64-linux-gnu
Thread model: posix
gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)

---

### Post by taurus on 2007-01-26
I guess that is the version that you want to remove.  You can try to include the version number in there if you want but right now, it seems like you only have one version of gcc on your machine.

```
sudo dpkg -r gcc-4.1
```

---

### Post by gaillard on 2007-01-26
I installed the deb called this. gcc-4.1-base_4.1.1-21_amd64.deb    it was a debian file.  The one I want on the system is this gcc-4.1-base_4.1.1-13ubuntu5_amd64.deb. 

the base file has a 21 ending and the other 13, I need to replace that 21 how do I do that without removing everything?

---

### Post by taurus on 2007-01-26
You have both of them on your machine currently!  Why not remove everything, gcc, and reinstall the right version that you want to use.  That way, you don't have any conflict later when you try to use gcc compiler.

---

### Post by gaillard on 2007-01-26
Sorry to be so much trouble, the thing is in order for me to use the internet here at my university, I must have java installed for a browser.  I have 64 bit ubuntu and no java at the moment.  All I was trying to do was install the java and 32 bit browser manually by transfering files with my thumb and I accidently downloaded a debian deb of the wrong version.

The guide I was going to follow was located here.
[https://help.ubuntu.com/community/Firefox2AMD64Flash9Java?highlight=%28java%29%7C%2864%29](https://help.ubuntu.com/community/Firefox2AMD64Flash9Java?highlight=%28java%29%7C%2864%29)

I have to have java on a browser to login to their cisco security stuff.

What exactly should I do?  This is a fresh install so I could just install it again...?

Thanks so much for the help I am rather new..

---

### Post by taurus on 2007-01-26
Why not install the x86 (i386) version.  Then, you don't have to worry about java or flash plugins for your browser.  Personally, I would go that way, x86 instead of x86_64.

---

### Post by gaillard on 2007-01-26
I have an amd64, would that not fit better with the processor?  I want to learn, and if performance would be better or lower latency since I plan on setting up some audio routing and processing with jack then I'd rather stick with 64.  Would I not see *some* advantage with 64 bit?

---

### Post by gaillard on 2007-01-26
Also if anyone would mind telling me what I need to look out for when installing firefox and java based on this guide while not connected to a network (moving files with a thumb drive) that would be great.

[https://help.ubuntu.com/community/Firefox2AMD64Flash9Java?highlight=%28java%29%7C%2864%29](https://help.ubuntu.com/community/Firefox2AMD64Flash9Java?highlight=%28java%29%7C%2864%29)

As far as I understand I just install the listed dependencies one by one starting from the bottom most (or one that doesn't have any) and going up the ladder correct?  

Also, is this guide better or the one Killz wrote found here?
[http://www.ubuntuforums.org/showthread.php?t=202537](http://www.ubuntuforums.org/showthread.php?t=202537)

Thanks soooorrry for all the trouble...
Guess I'll just reinstall

---

### Post by gaillard on 2007-01-26
Woohoo, ok now this pc is online and I can work, however the howto located here,
[https://help.ubuntu.com/community/Firefox2AMD64Flash9Java?highlight=%28java%29](https://help.ubuntu.com/community/Firefox2AMD64Flash9Java?highlight=%28java%29)

worked wonderfully for java but the flash download it gives seems to not be around anymore.

Thanks for all the help!

---

### Post by taurus on 2007-01-26
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

Or

[https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)

---

