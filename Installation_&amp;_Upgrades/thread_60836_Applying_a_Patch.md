---
title: "Applying a Patch"
date: 2005-08-29
forum: Installation &amp; Upgrades
---

### Post by amcavoy on 2005-08-29
I have downloaded the VLC media player, and have to apply a patch (from an outside site - Google).  I downloaded the patch to my desktop.  All that came up was "vlc-diff.txt" with no instructions.  Can anyone tell me how I actually patch the program (VLC)?

Thanks for your help.

---

### Post by pmjdebruijn on 2005-08-29
Hi,

Please note, Google could have easily answered your question, but here goes:

Take your application source code tarball and untar it:
```
tar zxvf ~/myapp.tar.gz
cd myapp
**patch -p1 < ~/myapp_weird_new_feature.diff**
./configure
make 
make install
```
And shazam, you're done.

Regards,
Pascal de Bruijn

**NOTE:** This should work for almost all applications, though there may be exceptions, when things differ from the instructions given here, they are generally listed at the top of the patch file itself. Also if the patch doesn't apply properly, you can try another -p level, so try -p0 for example, or increase fuzz level with (fox eaxmple) --fuzz=4.

---

### Post by amcavoy on 2005-08-29
I actually did use Google and found instructions similar to that.  The reason I posted is because it seemed like those instructions were for patching a program before it was installed (hence the tar.gz).  I was wondering if there is a way to do it to an already-installed program.  I'll try what you suggested though.

Thanks for your help, I appreciate it.

---

### Post by pmjdebruijn on 2005-09-02
No, you can't patch an already installed program.

Regards,
Pascal de Bruijn

---

