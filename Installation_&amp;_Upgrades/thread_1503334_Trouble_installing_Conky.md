---
title: "Trouble installing Conky"
date: 2010-06-06
forum: Installation &amp; Upgrades
---

### Post by feathre on 2010-06-06
I installed conky, lm-sensors, hddtemp, & python-parsers.
I have my conkyrc file all filled out the way I want it.  I have the corresponding script in its scripts folder.  I hit alt+f2 and type Conky and hit run.  There are no error messages or anything.  Just nothing happens at all.  Conky won't come up.

I have restarted my computer several times and have set Conky to be a startup program.  What am I doing wrong?  Shouldn't it at least attempt to start...?  There are only so many times that one can hit alt+f2.

I should also note that I am using Linux Mint 9 i386.  It is based heavily on Ubuntu, which is why I came here for help.  Oh and I am also using gnome, not KDE.  Please help me!  Thank you.

---

### Post by ajgreeny on 2010-06-06
You should have a hidden file called .conkyrc in your home folder in which all the configuration is placed.  I have attached mine so you can see what that does and then perhaps edit it to your needs.

It can be quite complicated to get the output you want and in the right colour etc etc, but use this as a template and you should be able to sort something to your liking.  Don't forget to rename the file and don't forget the . at the front of the name to make it hidden, or it won't work.

---

### Post by feathre on 2010-06-06
> **feathre said:**
> I have my conkyrc file all filled out the way I want it.

I have my conkyrc file done.  The problem is getting Conky to even start at all.  I go to run and type in conky and it does nothing.  Do I have to write a bash script or something?  Something I need to do to "activate" the config file?  I am confused.

---

### Post by feathre on 2010-06-06
Problem solved.  I had to type
```
conky -c ~/.conkyrc
```
in the terminal.

---

