---
title: "Wont boot"
date: 2009-09-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by b3n87 on 2009-09-23
Hello,

I have a Dell XPS M1330. Ive just downloaded the latest daily live build of Karmic, and burn the disc, just checked the MD5sum and its fine, but it wont boot.

It "loads" Ubuntu, then a blank screen appears, and nothing else, if you press escape I get to see the bash command line, and its asking me to log in.

Althought I dont know the LiveCD login name or password so I could execute "startx". Even though Im not meant to be doing that.

Any ideas to help test, and report the bug?

---

### Post by qwerty800 on 2009-09-23
I believe that the LiveCD login is ubuntu (On jaunty, at least).

It don't have any password.

---

### Post by Eclipse. on 2009-09-23
The installer could have got corrupt when burning, I just installed the latest daily today without any problem.

---

### Post by zoobuntoo on 2009-09-25
I have this issue on my karmic install (upgraded from intrepid) and also the LiveCD.
The login screen does not load after bootup and on moving the mouse or pressing a key the command line appears.
System is 
AMD Phenom 2 X4 940
BIOSTAR mobo TA790GX
Sapphire ATI Radeon HD4850 540
4 gb ocx (of which only 3.2 is available of course)
22" viewsonic VA2226W

I'm really stuck here, any suggestions are welcome....
Also if I'm forced to install and choose 64bit OS this time will my home partition settings be affected?

---

### Post by Aries K on 2009-09-25
I believe you caught the live cd during the "boot bug". I lucked out and got the yesterday's daily build and just caught it before this happened. I notice when I ran updates I had this problem too. So after a reinstall I read through the forums and found these threads:

[http://ubuntuforums.org/showthread.php?t=1274795&page=2](http://ubuntuforums.org/showthread.php?t=1274795&page=2)

[http://ubuntuforums.org/showthread.php?t=1275079](http://ubuntuforums.org/showthread.php?t=1275079)

Good luck.:)

---

### Post by ranch hand on 2009-09-26
> **zoobuntoo said:**
> I have this issue on my karmic install (upgraded from intrepid) and also the LiveCD.
The login screen does not load after bootup and on moving the mouse or pressing a key the command line appears.
System is 
AMD Phenom 2 X4 940
BIOSTAR mobo TA790GX
Sapphire ATI Radeon HD4850 540
4 gb ocx (of which only 3.2 is available of course)
22" viewsonic VA2226W

I'm really stuck here, any suggestions are welcome....
Also if I'm forced to install and choose 64bit OS this time will my home partition settings be affected?
There has been a problem with the ATI cards in the past.  I am too whipped to find the threads but they are there.  I think that it has been fixed.

Basically you had to edit the xorg.conf file to read, in the device section'
```

driver           "vesa"
DRI              "0"

```
I think that the newest kernals do not need this.

I would try updating if you can get to recovery or xterm or a text login.

---

### Post by taavikko on 2009-09-26
> **ranch hand said:**
> There has been a problem with the ATI cards in the past.  I am too whipped to find the threads but they are there.  I think that it has been fixed.

Basically you had to edit the xorg.conf file to read, in the device section'
```

driver           "vesa"
DRI              "0"

```
I think that the newest kernals do not need this.

I would try updating if you can get to recovery or xterm or a text login.

It's been fixed by the latest mesa+xorg-driver-ati
r600dri.so was removed from default setup which was the culprit.

---

