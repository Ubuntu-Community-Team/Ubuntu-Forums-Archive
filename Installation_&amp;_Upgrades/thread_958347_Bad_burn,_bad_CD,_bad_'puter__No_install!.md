---
title: "Bad burn, bad CD, bad 'puter?  No install!"
date: 2008-10-25
forum: Installation &amp; Upgrades
---

### Post by pterandon on 2008-10-25
Hello.

While trying to install kubuntu 8.04.1 on a computer, the install process conked out with this message:
```
[225.54890  Buffer I/O error on device fd0 logical block 0]
[263.55293  Buffer I/O error on device fd0 logical block 0]
```

I got this with two different downloads of the iso across three different attempts.  I guessing it's not a bug in ubuntu :)

The question is whether I have a bad CD burner or a bad "computer" or bad physical media?  The computer currently has kubuntu 7.04 running happily on it now, but is about 5 years old.

---

### Post by oldos2er on 2008-10-25
Are you running the 'Check CD for defects' app before installing? Or checking the CD with md5sum?

---

### Post by pterandon on 2008-10-26
Thanks for the idea. You at least had the right piece of hardware in mind.

What actually turned out to be the problem is that I had previously installed a brand new DVD drive and had two of them in the 'puter both as Master.  I switched things around, made the new one master and old one slave, and now the installation is well under way.   It's just funny, probably not a design flaw, that 'buntu choked on this setup without telling me why.

thanks.

---

