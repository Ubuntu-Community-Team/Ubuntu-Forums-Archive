---
title: "downgrade ubuntu"
date: 2011-05-29
forum: Installation &amp; Upgrades
---

### Post by xoron on 2011-05-29
I installed latest ubuntu 11.04 64 but the flash on it is awful...it keeps crashing and sometimes flash content doesn't fully appear. I cant find a fix for this :( ...

so I was wondering is there a way to downgrade ubuntu to 32 bit?

thanks in advanced :D

---

### Post by Markmental on 2011-05-29
get a new live cd and install over the partition where 11.04 is located

---

### Post by scradock on 2011-05-29
Short answer - No. You would have to re-install using a 32-bit version.

The Flash saga is infuriating - every time something changes it works for some people, not for others. 

Good luck!

---

### Post by xoron on 2011-05-29
> **Markmental said:**
> get a new live cd and install over the partition where 11.04 is located

i want to keep all my files an programs... files are easy to copy to external HD but the programs are going to be a pain i cant even remember them all (not to mention things like conky settings, startup programs, etc)

---

### Post by Markmental on 2011-05-29
make a text file with the commands to install the programs and back that up

---

### Post by xoron on 2011-05-29
> **Markmental said:**
> make a text file with the commands to install the programs and back that up

is it possible to copy filesystem from 64bit to external HD, install 32bit, replace 32bit filesystem with the copy of filesystem from 64 bit?

---

### Post by elliotbeken on 2011-05-29
This thread might help with the flash issue

---

### Post by xoron on 2011-05-29
> **elliotbeken said:**
> This thread might help with the flash issue

can you post the thread again please.

---

### Post by elliotbeken on 2011-05-29
sorry how stupid of me lol 

[http://ubuntuforums.org/showthread.php?t=1767492&highlight=elliotbeken](http://ubuntuforums.org/showthread.php?t=1767492&highlight=elliotbeken)

---

### Post by Bobhuber on 2011-05-29
> **xoron said:**
> I installed latest ubuntu 11.04 64 but the flash on it is awful...it keeps crashing and sometimes flash content doesn't fully appear. I cant find a fix for this :( ...

so I was wondering is there a way to downgrade ubuntu to 32 bit?

thanks in advanced :D
If you can find the adobe flash player revision 10.0r45 it works fine in Maverick and Natty. You will have to uninstall the flash-plugin installer thru the package manager before installing the older flash version.

---

### Post by cogier on 2011-05-29
Regarding your comment "...but the programs are going to be a pain i cant even remember them all..."

If you open Synaptic Package Manager then **File>Save markings as..**, check the **Save full state...** checkbox. Give the file a name and save it, this file will contain a list of all your programs. You can then use Synaptic to install them all with **File>Read markings** once you have your new installation.

---

