---
title: "Installing printer"
date: 2006-09-01
forum: Installation &amp; Upgrades
---

### Post by Jos_Havinga on 2006-09-01
I've just updated my Ubuntu to 6.06
Now I'm trying to install my Epson Stylus DX3850. But when I try to add a new printer the database with all the different printers is totally empty. I can't select a manufacturer nor a printer.
Can somebody help me?

---

### Post by ahaslam on 2006-09-01
Have you got 'cupsys' installed & enabled at boot? Have you also got these:
[IMG]http://img68.imageshack.us/img68/9475/untitledne8.jpg[/IMG]

Tony.

---

### Post by Jos_Havinga on 2006-09-02
yes, i've got them installed (marked green in my synaptic like the screenshot you showed). is this the same as 'enabled at boot'?
it's still not working..

---

### Post by ahaslam on 2006-09-02
Download BUM - boot up manager & check that 'cupsys' is enabled.
Failing that, I'm stumped.

Tony.

---

### Post by timothyM on 2006-09-02
I had the same problem as this. After much faffing around I solved with the command:

```

sudo apt-get install gnome-cups-manager
```

I had gnome-cups-manager installed, but it installed libgnomecupsui1.0-1c2a replacing libgnomecupsui1.0-1 and that seemed to fix the problem. See if this works for you.

---

### Post by Jos_Havinga on 2006-09-02
Timothy, it worked! Thank you very much!
And also thanks to you Tony for your help!

---

