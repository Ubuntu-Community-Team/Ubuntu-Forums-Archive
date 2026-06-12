---
title: "ldconfig"
date: 2010-06-02
forum: Installation &amp; Upgrades
---

### Post by ahso4271 on 2010-06-02
Hi
I try to compile a 32bit app on 64bit 10.04. 
Now that's the error I get:
------------
g++ -Lmedia/openSuse-/usr/lib/ -m32 -shared -o"lin.xpl"  ./main.o    -lSDL -lSDL_mixer -lalut -lSDL_image -lGL -lGLU
/usr/bin/ld: skipping incompatible  /usr/lib/gcc/x86_64-linux-gnu/4.4.3/../../../libSDL.so when searching  for -lSDL
/usr/bin/ld: skipping incompatible  /usr/lib/gcc/x86_64-linux-gnu/4.4.3/../../../libSDL.a when searching for  -lSDL
/usr/bin/ld: skipping incompatible /usr/lib/libSDL.so when searching for  -lSDL
/usr/bin/ld: skipping incompatible /usr/lib/libSDL.a when searching for  -lSDL
/usr/bin/ld: cannot find -lSDL
collect2: ld returned 1 exit status
make: *** [lin.xpl] Fehler 1
------
Can I copy the libs from suse to f.ex. /usr/libsSuse32 and then simply  run ldconfig from that directory? What's the syntax for ldconfig?
Thanks

---

### Post by tommcd on 2010-06-02
> **ahso4271 said:**
> 
I try to compile a 32bit app on 64bit 10.04. 
First, what package are you trying to compile? And why do you need to compile it from source code? Is the package not available in the Ubuntu repos?
> **ahso4271 said:**
> 
Can I copy the libs from suse to f.ex. /usr/libsSuse32 and then simply  run ldconfig from that directory? What's the syntax for ldconfig?

Why would you copy libs from Suse???
Is the package you are trying to compile from the Suse repos or something? Please provide a link to exactly what you are trying to compile.

To install 32 bit apps on 64 bit Ubuntu, install the **ia32-libs** package *from the Ubuntu repos*:
[http://packages.ubuntu.com/lucid/ia32-libs](http://packages.ubuntu.com/lucid/ia32-libs)
[https://help.ubuntu.com/community/32bit_and_64bit#How%20to%20make%2032-bit%20application%20work%20on%20a%2064-bit%20Operating%20System](https://help.ubuntu.com/community/32bit_and_64bit#How%20to%20make%2032-bit%20application%20work%20on%20a%2064-bit%20Operating%20System)
Then install the desired 32 bit app from the Ubuntu repos. 
If the package is not available in the Ubuntu repos, which is unlikely, then install the **build-essential** package:
[http://packages.ubuntu.com/lucid/build-essential](http://packages.ubuntu.com/lucid/build-essential)
and then compile the app from *source code* instead of trying to make a Suse RPM package work on an Ubuntu .deb system.

---

### Post by ahso4271 on 2010-06-03
Hi
i've selected the 32libs at ubuntu install. Now I'm trying to crosscompile with Eclipse for 32bit/Windows/Intel Mac
Any help with my error? Basically I need to let ld know about f.ex. a different SDL lib with same name but different location. For now it only finds the installed 64bit version. 
Many thanks
Michael

---

### Post by tommcd on 2010-06-03
> **ahso4271 said:**
> 
i've selected the 32libs at ubuntu install. Now I'm trying to crosscompile with Eclipse for 32bit/Windows/Intel Mac
Any help with my error? Basically I need to let ld know about f.ex. a different SDL lib with same name but different location. For now it only finds the installed 64bit version. 

I am not familiar with eclipse. However, I found these 2 references for eclipse in the Ubuntu wiki:
[https://help.ubuntu.com/community/EclipseWebTools](https://help.ubuntu.com/community/EclipseWebTools)
[https://help.ubuntu.com/community/EclipseIDE](https://help.ubuntu.com/community/EclipseIDE)
The second link covers installing eclipse from source code as well as some troubleshooting.

---

### Post by ahso4271 on 2010-06-03
ok but Eclipse install is in fact trivial.
Now could I add a directory with libs of the same name as the default 64bit installed alike below? (sdl etc.) As the toolchains are present for Mac & win as well i suppose it should be possible somehow also to add mac & win libs.
-------
Add the path "/usr/lib/firefox" to the file "/etc/ld.so.conf" and  execute "sudo ldconfig" once. 
-------
Thanks

---

