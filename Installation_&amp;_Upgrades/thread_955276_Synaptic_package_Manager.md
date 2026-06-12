---
title: "Synaptic package Manager"
date: 2008-10-22
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2008-10-22
When I use Synaptic package manager to install a program where does it install it ?
for example I have just used it to install Maven2 it works but I don't know where is the installation directory of the installed maven2 ?.

---

### Post by steviefordi on 2008-10-22
I'm a bit of a newb to Linux myself, but I'll try to answer your question...

The binary executables (.exe's if you like) will normally go into a subdirectory of /usr/bin or /usr/bin/local/ that is probably called maven2 or something similar.

I'm guessing you come from a MS Windows background as I do, and probably expect everything for one application to be installed into the same directory (which you can normally specify on installation). Linux - and Unix systems in general - have a strongly defined directory structure. Everything has a place and everything in it's place. I'm sure you can change or configure where Linux looks for  executables but why do that?

Similarly, any libraries (DLL's if you like) will be in /usr/lib/ or /usr/local/lib/. I'm sure there's a directory for documentation and help files, but I don't know where that is.

Not controlling where things install may seem strange to you, as it did to me, but when you get used to it, it just seems to make a lot more sense than throwing anything anywhere on your system.

---

### Post by tommcd on 2008-10-22
> **hoboy said:**
> When I use Synaptic package manager to install a program where does it install it ?
for example I have just used it to install Maven2 it works but I don't know where is the installation directory of the installed maven2 ?.

Just out of curiosity, why do you need to know this? Is there some problem you are having? As StevieFordi said, most apps go to /usr, or /usr/lib, /usr/share, or /usr/local. There is usually a symlink to /usr/bin for the executable. If you really need to know where all the bits of Maven2 went, run this command:
```
sudo locate Maven2 | less
```
You can scroll up and down with the arrow keys, or the page_up and page_down keys to see where everything is located. Just hit the "q" key to close out of the less command.
 If you need to uninstall Maven2, just open synaptic, search for Maven2, right-click on it and select 'mark for complete removal', click 'apply' and it will be gone. Don't try to remove stuff manually unless you have a good reason for doing so.

---

### Post by sethvath on 2008-10-22
Do not run sudo unless its absolutely required. 

locate maven2 
will do just fine

---

### Post by cboese on 2010-04-29
I need the installation directory for integration into m2eclipse plugin for the eclipse IDE.
It must be given in the plugins preferences when adding an external installation and /usr/bin/mvn does not work and gives an error.
For all wondering, if I use
/usr/share/maven2/
it works.

---

