---
title: "Can't open ati control panel."
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by Kirky_D on 2005-10-14
ok so i managed to get my ati drivers working. And now i install the fglrx-control package in synaptic which installs fine. but i cant find it in the applications list and also i cant figure out what command will open it up from the terminal. 

Can anybody help?

cheers

---

### Post by matthew on 2005-10-16
I want to bump this as I am also looking.

---

### Post by matthew on 2005-10-16
I'm gonna answer my own bump here. The command to start the ati control panel from a terminal is
```
fireglcontrolpanel
```

---

### Post by Kirky_D on 2005-10-16
[QUOTE=matthew]I'm gonna answer my own bump here. The command to start the ati control panel from a terminal is
```
fireglcontrolpanel
```[/QUOTE]

lol. Ok cheers for the info

---

### Post by toujours on 2005-10-16
Thanks ! I learned something new by reading this post !

It's a surprising command isn't it ...

---

### Post by matthew on 2005-10-16
You're welcome. It is such a nice thing to have that I made a menu entry for it in Applications->System Tools. I travel and use a projector from time to time so the dualscreen menu is quite handy.

---

### Post by JuanC on 2005-10-16
Ati Control doesn't work in my case too.

I get this error :
> /usr/X11R6/bin/fireglcontrolpanel: error while loading shared libraries: libexpat.so.0: cannot open shared object file: No such file or directory

My system is an AMD64 Laptop.

---

### Post by ThaRabbit on 2005-10-28
[QUOTE=JuanC]Ati Control doesn't work in my case too.

I get this error :


My system is an AMD64 Laptop.[/QUOTE]

i have the same problem... fglrx drivers are working well with the older x lib but the control panel still isn't.

64 bit ubuntu

---

### Post by xaque on 2005-11-13
Same here, AMD64 laptop. I ran 
```
locate libexpat.so.0
```
which returned
```
/usr/lib/libexpat.so.0
/usr/lib32/libexpat.so.0

```
So it's there, but it's not being linked. I tried running ldconfig on fireglcontrolpanel (I don't know if that would do anything, but it's worth a try.) Still nothing. Maybe it's not 64-bit compatible?

---

### Post by Robocoastie on 2005-11-25
ditto: (64bit also)

```

rob@talviak05:~$ which fireglcontrolpanel
/usr/bin/fireglcontrolpanel
rob@talviak05:~$ fireglcontrolpanel
fireglcontrolpanel: error while loading shared libraries: libexpat.so.0: cannot open shared object file: No such file or directory
rob@talviak05:~$ locate libexpat.so.0
/usr/lib/libexpat.so.0
/usr/lib32/libexpat.so.0
rob@talviak05:~$
```

It works on my 32bit Ubuntu partition though. The list of 64 bit incompatibilities is getting pretty long. I had wanted to try a 64 bit OS to see if it boosts video conversion any faster (recorded tv shows to various formats) but that project is becoming a complicated procedure getting all the codecs to work. Heck I'd pay for a multimedia linux that takes care of all these multimedia problems with legal and easy to install and use codecs even. Oh wait! There is one -- Mac OSX LOL. heh its the planned obscelence in retail software that makes me appreciate open source.

---

### Post by Takeshi Miya on 2006-01-13
Same problems here with AMD64.

Could recompiling expat in 64bits soulve the problem?

---

### Post by zakusage on 2006-01-17
I had the very same problem, again on an AMD64 system. Really seems like this build of Ubuntu lacks the polish of the 32-bit versions.

Anyway, simply add the following to your /etc/ld.so.conf file, which should take care of this and any more annoying false missing library file warnings:

/lib
/usr/lib
/usr/local/lib

The second is the only one that really matters in this case, as that is where Ubuntu places the file by default, but again the others will help later. After you edit, reboot.

Cheerio!

---

### Post by meydey on 2006-02-03
In my case I didn't have libexpat.so.0 but a newer libexpat.so.1...  Do an "ldd fireglcontrolpanel" to see which lib it's actually looking for.  In that case you can install an older expat lib alongside or use a cheap hack that might work, like linking libexpat.so.0 to your existing libexpat.so.1.  Cheers!

---

### Post by nico23 on 2006-03-30
i have this problem to on my ubuntu 64 bit

and i think my lib is already linked

```

$ fireglcontrolpanel
fireglcontrolpanel: error while loading shared libraries: libexpat.so.0: cannot open shared object file: No such file or directory

```

```

user@system:/usr/bin$ ldd fireglcontrolpanel
        linux-gate.so.1 =>  (0xffffe000)
        libGL.so.1 => /usr/lib32/libGL.so.1 (0x5557a000)
        libXmu.so.6 => /usr/lib32/libXmu.so.6 (0x55619000)
        libXt.so.6 => /usr/lib32/libXt.so.6 (0x5562e000)
        libICE.so.6 => /usr/lib32/libICE.so.6 (0x5567c000)
        libSM.so.6 => /usr/lib32/libSM.so.6 (0x55695000)
        libdl.so.2 => /lib32/tls/libdl.so.2 (0x5569c000)
        libXext.so.6 => /usr/lib32/libXext.so.6 (0x5569f000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0x556ad000)
        libfontconfig.so.1 => /usr/lib32/libfontconfig.so.1 (0x5576d000)
        libexpat.so.0 => not found
        libXinerama.so.1 => /usr/lib32/libXinerama.so.1 (0x5579b000)
        libXrender.so.1 => /usr/lib32/libXrender.so.1 (0x5579e000)
        libXrandr.so.2 => /usr/lib32/libXrandr.so.2 (0x557a6000)
        libfreetype.so.6 => /usr/lib32/libfreetype.so.6 (0x557aa000)
        libXxf86vm.so.1 => not found
        libXft.so.2 => /usr/lib32/libXft.so.2 (0x55814000)
        libXcursor.so.1 => /usr/lib32/libXcursor.so.1 (0x55826000)
        libstdc++.so.5 => /usr/lib32/libstdc++.so.5 (0x5582f000)
        libm.so.6 => /lib32/tls/libm.so.6 (0x558e9000)
        libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0x5590c000)
        libc.so.6 => /lib32/tls/libc.so.6 (0x55917000)
        libpthread.so.0 => /lib32/tls/libpthread.so.0 (0x55a45000)
        /lib/ld-linux.so.2 (0x55555000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0x55a56000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0x55a59000)
        libz.so.1 => /usr/lib32/libz.so.1 (0x55a5e000)
        libexpat.so.1 => /usr/lib32/libexpat.so.1 (0x55a72000)
        libXfixes.so.3 => /usr/lib32/libXfixes.so.3 (0x55a91000)

```

```

user@system:/usr/lib32$ ls -l
.
.
lrwxrwxrwx  1 root root       13 2006-03-24 17:07 libexpat.so.0 -> libexpat.so.1
lrwxrwxrwx  1 root root       17 2006-03-24 17:07 libexpat.so.1 -> libexpat.so.1.0.0
-rw-r--r--  1 root root   125168 2005-04-22 18:05 libexpat.so.1.0.0
.
.

```
i think that shows that the file is already linked. am i right ?

the driver is runnig very well i think i can play ut2004 very fast

but i want to configure my dual screen :(

---

### Post by aldous on 2006-04-01
I tried this, but to no avail.

[I]...simply add the following to your /etc/ld.so.conf file, which should take care of this and any more annoying false missing library file warnings:

/lib
/usr/lib
/usr/local/lib[/I]

Any new suggestions?  I'm stuck here also.

---

### Post by mckeja on 2006-04-10
I have the same problem.  

fireglcontrolpanel: error while loading shared libraries: libexpat.so.0: cannot open shared object file: No such file or directory

However, libexpat.so.0 exists.  I tried the earlier suggestion, adding:
     /lib
     /usr/lib
     /usr/local/lib
to /etc/ld.so.conf. This did not solve the problem. I rebooted and tried it again. It still gives the same error. Any other suggestions?

---

### Post by StalfoS on 2006-04-15
I tried making a script to launch fireglcontrolpanel as such:

#!/bin/sh
LD_LIBRARY_PATH="/usr/lib/:/usr/lib32/"
export LD_LIBRARY_PATH
exec /usr/bin/fireglcontrolpanel

except now i get the new error:

/usr/bin/fireglcontrolpanel: error while loading shared libraries: libXxf86vm.so.1: cannot open shared object file: No such file or directory


ideas????

---

### Post by ruiorey on 2006-04-25
Your script definitely works, just doing this before executing it:

1) Download libxxf86vm1_7.0.0-2_i386.deb: packages.ubuntu.com/breezy/libs/libxxf86vm1
2) ar -x libxxf86vm1_7.0.0-2_i386.deb
3) tar -zxf data.tar.gz
4)sudo cp -p usr/lib/* /usr/lib32
5) Create symlink: sudo ln -s /usr/lib32/libXxf86vm.so.1.0.0 /usr/lib32/libXxf86vm.so.1

I think that probably it's a problem related to the libxxf86vm1_7.0.0-2_amd64.deb package. Strangely it works using the i386 one.
Just a note: this procedure let you start the app, but i don't think it will make it work. The only thing we have to do is just to hope ATi to wake up on linux support, especially on 64bit platforms. 
Bye my dears...

---

### Post by Khaotik on 2006-06-18
I also have a problem with this ATi control panel. I installed ATi drivers through synaptic. Also the Control panel. I ran this command (fireglcontrolpanel). It brought up the panel but gave me an error (dont remember exact words). In the control panel there is only 1 tab. And under Vendor it says that i am currently still using the Mesa drivers. What is the command to switch?

(Dapper Drake)

---

### Post by Tristan9669 on 2006-07-14
thanks

---

