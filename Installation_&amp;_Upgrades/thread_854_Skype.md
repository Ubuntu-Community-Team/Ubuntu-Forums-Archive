---
title: "Skype"
date: 2004-10-16
forum: Installation &amp; Upgrades
---

### Post by snowx1000 on 2004-10-16
Does anyone know how to get skype working in ubuntui? Using AMD64 RC, it complains about libs that I have.

---

### Post by -baHam- on 2004-10-16
The stupid chat program for windows?

---

### Post by HungSquirrel on 2004-10-16
Correction: the useful, free, multiplatform VOIP client.

---

### Post by nico1278 on 2004-10-16
I had no problems installing skype by downloading the unstable linux version from the official skype site (the last in the list). Works just fine :)

---

### Post by snowx1000 on 2004-10-16
I geth this output from that version: error while loading shared libraries: libXrender.so.1: cannot open shared object file: No such file or directory.

---

### Post by bronson on 2004-10-17
apt-get install libxrender1

(or, install the libxrender library using synaptic)

---

### Post by ubuntu-geek on 2004-10-17
Try this:

wget [http://www.skype.com/go/getskype-linux-fc2](http://www.skype.com/go/getskype-linux-fc2)

sudo alien -d skype-0.92.0.2-fc2.i386.rpm

sudo dpkg -i skype_0.92.0.2-1_i386.deb

note: I had to install some qt stuff to get it to work

sudo apt-get install libqt3-mt-dev

---

### Post by snowx1000 on 2004-10-18
All those packages are installed and when I try alien it complains that amd64 not found.  I would try some more things, but I cant log in due to ICE having changed permissions for one reason or another, so I will try later.  Thanks

---

### Post by easy_target on 2004-11-26
Thanks for the tip Geek. It worked like a charm. I have looked for it for a long time.

---

### Post by luiska on 2004-11-27
Hi

I was also sceptical about skype but it is a brilliant piece of software. Phoning from Finland to South Africa for a 0.07 cents a minute. None of the phone companies can give you that price. 

Luiska

---

### Post by jiyuu0 on 2004-11-27
install skype:
[http://kitech.com.my/ubuntu/4.10/index.html#skype](http://kitech.com.my/ubuntu/4.10/index.html#skype)

---

### Post by jbh on 2004-12-30
after typing 'ldd skype' I get this:

libXrender.so.1 => not found

So I installed the deb qt modules and still no avail. apt-get libxrender1 sez I have the latest one installed already. any idea how I can 'point' or get a path command to skype can find it?

thanks

---

### Post by amerigo5 on 2005-01-01
[QUOTE=jiyuu0]install skype:
[http://kitech.com.my/ubuntu/4.10/index.html#skype](http://kitech.com.my/ubuntu/4.10/index.html#skype)[/QUOTE]

Update:

[http://ubuntuguide.org/index.html#skype](http://ubuntuguide.org/index.html#skype)

---

### Post by aburda on 2005-04-07
Before I start my request, I'd like to thank all of the uncelebrated hero's that make apt-get function....

But wouldn't skype be a good thing to add to the universe repository?  Is it not there because it is not OpenSource?  

Its an extremely useful program.


Aaron

---

### Post by greatshape on 2005-04-09
[QUOTE=aburda]Before I start my request, I'd like to thank all of the uncelebrated hero's that make apt-get function....

But wouldn't skype be a good thing to add to the universe repository?  Is it not there because it is not OpenSource?  

Its an extremely useful program.


Aaron[/QUOTE]

Yes, i vote for it too. Would be great(and easier for a lot of users!)to have it in the universe repo. :|

---

### Post by RadomE on 2005-04-17
skype: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

Where i can find that lib?

---

### Post by syltty on 2005-04-18
[QUOTE=RadomE]skype: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

Where i can find that lib?[/QUOTE]


Apt-file is your friend:

$ apt-file search libGL.so.1

fglrx-driver: usr/X11R6/lib/libGL.so.1.2
mesag3: usr/lib/libGL.so.1
mesag3: usr/lib/libGL.so.1.4.500
mesag3+ggi: usr/lib/libGL.so.1
mesag3+ggi: usr/lib/libGL.so.1.4.500
mesag3-glide2: usr/lib/libGL.so.1
mesag3-glide2: usr/lib/libGL.so.1.4.500
nvidia-glx: usr/lib/libGL.so.1
nvidia-glx: usr/lib/libGL.so.1.0.6111
xlibmesa-gl: usr/X11R6/lib/libGL.so.1
xlibmesa-gl: usr/X11R6/lib/libGL.so.1.2
xlibmesa-gl: usr/lib/libGL.so.1
xlibmesa-gl: usr/lib/libGL.so.1.2
xlibmesa-gl-dbg: usr/X11R6/lib/debug/libGL.so.1
xlibmesa-gl-dbg: usr/X11R6/lib/debug/libGL.so.1.2
xlibmesa-gl-dbg: usr/lib/debug/libGL.so.1
xlibmesa-gl-dbg: usr/lib/debug/libGL.so.1.2


I have xlibmesa-gl installed.

---

### Post by RadomE on 2005-04-21
[QUOTE=syltty]Apt-file is your friend:
...
I have xlibmesa-gl installed.[/QUOTE]

 :roll: 

Ehm i've some prob with that pakage...maybe a conflict with ATi Drivers...well apt can't install it.

---

