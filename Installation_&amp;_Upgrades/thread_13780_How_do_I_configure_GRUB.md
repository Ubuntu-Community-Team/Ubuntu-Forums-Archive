---
title: "How do I configure GRUB?"
date: 2005-02-02
forum: Installation &amp; Upgrades
---

### Post by mandruku on 2005-02-02
I've just installed, and because it's the family computer, I want Windows to be the defualt choice for the GRUB menu. It's on the list, but not the default, other people in the family are retarded so they can't remember to change it. Don't worry when I get the internet running 100% on Ubuntu I'll change them all, but right now I need to know. Couldn't find any info in the FAQ

If I knew where the config file was maybe I could change it but I don't

---

### Post by AlBundy on 2005-02-02
[Ubuntu starter Guide](http://ubuntuguide.org/#changedefaultosgrub)

---

### Post by El Guapo on 2005-02-02
I tried that but the default was still Ubuntu and not WinXP.  The users guide says to put X_sequence instead of 0 on the default space.  Is this correct?

---

### Post by rudi on 2005-02-02
x stands for the number of os, so change it to three if your options are: 
  
  ubuntu kernel bla
  ubuntu kernel bla safemode
  Windoze
  
 (or you could not change that number and put the windows bit in front of the ubuntu parts, then windows is automatically numero uno (watch out after a kernel upgrade, check you menu.lst then! :D)

---

### Post by El Guapo on 2005-02-02
I knew that I was missing something simple.  Thanks for that.  I will try not to be so dense next time. 8-[

---

