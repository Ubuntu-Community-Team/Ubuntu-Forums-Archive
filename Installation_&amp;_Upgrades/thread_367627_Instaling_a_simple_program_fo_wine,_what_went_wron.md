---
title: "Instaling a simple program fo wine, what went wrong?"
date: 2007-02-22
forum: Installation &amp; Upgrades
---

### Post by Liger_XT5 on 2007-02-22
I have been having a problem installing wine wich seems to be a simple program for many to install. I have installed it through the Konsole, but I can't seem to get it working, it downloads as far as I know.

Does anyone know of any good guides that I can look at that might help out?
I'd give links to where I've looked, but I'm not on my pc at the moment.

---

### Post by eradicator on 2007-02-23
I used this straight forward guide right from the source:
[http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

Worked like a charm first try.

You can also get a good amount of information here:
[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

Good luck!

---

### Post by Liger_XT5 on 2007-02-25
Thanks for helping, but in the other link, it mentions "Open the terminal, and cd into the directory where the .EXE is located."

I opened the terminal, but I don't understand the cd into the directory where the .exe.
if "cd" is short for something, that might be what is confusing me.
so, lets say I put ding.exe on the desktop, what would the command look like?

---

### Post by NotPhil on 2007-02-25
> **Liger_XT5 said:**
> Thanks for helping, but in the other link, it mentions "Open the terminal, and cd into the directory where the .EXE is located."

I opened the terminal, but I don't understand the cd into the directory where the .exe.
if "cd" is short for something, that might be what is confusing me.
Yes, like most UNIX/Linux command-line programs, its name is a cryptic abbreviation. In this case "cd" is short for "change directory."
> **Liger_XT5 said:**
> so, lets say I put ding.exe on the desktop, what would the command look like?
When you open your terminal it will be located in your home folder (~/) to change directories to your desktop, type "cd Desktop".

---

### Post by Liger_XT5 on 2007-02-25
oh, thanks man, that made a lot more since. (One of my linux friends in town said it was for the cd drive xD, knew it wasn't that...)

edit:
I'm getting this error:
wine: creating configuration directory '/home/name/.wine'...
Bus error
wine: wineprefixcreate failed while creating '/home/name/.wine'.

---

### Post by NotPhil on 2007-02-27
> **Liger_XT5 said:**
> I'm getting this error:
wine: creating configuration directory '/home/name/.wine'...
Bus error
wine: wineprefixcreate failed while creating '/home/name/.wine'.Did you get that when you typed winecfg in the terminal?

---

### Post by Liger_XT5 on 2007-02-27
No, I got that when I typed cd Desktop, then wine (name of program).exe
I'd give the specific name, but I'm on my windows xp computer atm.

---

### Post by NotPhil on 2007-02-27
> **Liger_XT5 said:**
> No, I got that when I typed cd Desktop, then wine (name of program).exe I'd give the specific name, but I'm on my windows xp computer atm.Try installing the Windows program to your ~/.wine/drive_c directory. If you don't have that folder yet, type winecfg in the terminal; it should create that directory along with some other files that WINE needs to emulate Windows. Then, you should be able to run the program with ...
```
wine /home/(your user-name)/.wine/drive_c/(program).exe
```

---

### Post by Liger_XT5 on 2007-02-28
wine: creating configuration directory '/home/liger/.wine'...
Bus error
wine: wineprefixcreate failed while creating '/home/liger/.wine'.

samething still, what does it mean by "bus?"

---

### Post by NotPhil on 2007-02-28
> **Liger_XT5 said:**
> wine: creating configuration directory '/home/liger/.wine'...
Bus error
wine: wineprefixcreate failed while creating '/home/liger/.wine'.

samething still, what does it mean by "bus?"A data bus is a little piece of hardware that moves data around from one part of your computer to another.

Are you using the 64-bit version of Ubuntu?

---

