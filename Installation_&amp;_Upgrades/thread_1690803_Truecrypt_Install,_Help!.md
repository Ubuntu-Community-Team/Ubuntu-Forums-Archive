---
title: "Truecrypt Install, Help!"
date: 2011-02-19
forum: Installation &amp; Upgrades
---

### Post by SlowDemiseOfWindows on 2011-02-19
Hi all,  I'm trying to install truecrypt's current edition on Ubuntu 10.10. It downloads. I'm then asked which program I want to open it with. I did some reading here that told me that I actually don't want to open it with a program but rather a command line. (I think I got my attempt at this right. Right click and then create launcher?) When I put in the setup command  $ ./truecrypt-7.0a-setup-x64 I got the error message:  Could not display &quot;/home/****/Downloads/truecrypt-7.0a-linux-x64.tar.gz.sig&quot;.  What do I do from here?  Do I want the 32 bit version or 64 bit? I assume I want the standard as opposed to console-only as well. I just need the standard off the shelf version.   Thanks much all!

---

### Post by wilee-nilee on 2011-02-19
The off the shelf version puts a icon for the program in accessories, for the full gui. You don't have to use the command line.

---

### Post by SlowDemiseOfWindows on 2011-02-19
That's just it. My computer isn't able to open the program. How do I get it to do that?  Thanks much!

---

### Post by wilee-nilee on 2011-02-19
Go here, and down load the 32 0r 64 bit version of the standard install. Be sure if you have more problems to be very accurate in your description. Your going to encrypt something in the end, and if you don't follow some guidelines you can lose it.
[http://www.truecrypt.org/](http://www.truecrypt.org/)
[ATTACH]183927[/ATTACH]

---

### Post by deconstrained on 2011-02-19
> **SlowDemiseOfWindows said:**
> Do I want the 32 bit version or 64 bit?
Fire up gnome-terminal and issue the command 'uname -a'. If the kernel spec includes "x86_64", your system is 64-bit and thus you'll want the 64-bit binary. Otherwise, 32 bit is generally safe.

> **SlowDemiseOfWindows said:**
> Hi all,  I'm trying to install truecrypt's current edition on Ubuntu 10.10. It downloads. I'm then asked which program I want to open it with.
Don't "open" it, just download it. Then extract it (you've already done this I suppose). The installer should be executable (if not, change it with 'chmod a+x'). Run it as root with 'sudo' and it will install properly.

---

### Post by SlowDemiseOfWindows on 2011-02-22
What is the extension for an executable file in linux?  Thanks much!

---

### Post by deconstrained on 2011-02-22
A file needs no extension to be executable. 

The executable bit in the file mode just has to be 1 and that's it.

---

