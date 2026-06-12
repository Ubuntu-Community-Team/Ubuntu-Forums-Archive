---
title: "wrong library version (32 v/s 64 bit)?"
date: 2012-04-02
forum: Installation &amp; Upgrades
---

### Post by dieter-erich on 2012-04-02
Hi,
  changing from 10.04LTS 32 bit to 10.11 64 bit I encounter the following compilation problem:

/usr/bin/ld: i386:x86-64 architecture of input file `external/inria/extrema.os' is incompatible with i386 output
/usr/bin/ld: i386:x86-64 architecture of input file `external/inria/convert.os' is incompatible with i386 output
......

I suppose that it has to do with a wrong inria library. How to find the correct one? Apparently, ubuntu 10.04 has chosen /installed the correct one automatically but ubuntu 10.11 does not. Or do I have to install the 32 bit version?

Thanks, D-E

---

### Post by wojox on 2012-04-02
Did you try installing the 32 bit libs?

```
sudo apt-get update; sudo apt-get install ia32-libs
```

---

### Post by dieter-erich on 2012-04-02
Thanks a lot! 

I shall try that asap and post the results! I did not know how to find these libraries!

 - BTW - : 

I have a previous version of the program running that (apparently) installed/needed/used the correct libraries automatically Suppose I now install the ones you proposed, could this screw up the old installation? 

It is no clear to me how the older version of the program (on the same machine/with the same 32 bit ubuntu 10.04) would have used a 64 bit inria library and now the newer version would need a 32 bit library?

Is there a way to find out what version I have currently installed and whether it is different from the one you propose?

---

### Post by wojox on 2012-04-02
That package will let you run 32 bit apps under a 64 bit enviorment.

---

