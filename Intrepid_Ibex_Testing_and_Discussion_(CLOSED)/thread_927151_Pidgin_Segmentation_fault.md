---
title: "Pidgin Segmentation fault"
date: 2008-09-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by LavianoTS386 on 2008-09-22
Ever since I updated the Kernel Pidgin wont' load.

> pidgin
Segmentation fault (core dumped)


Anyone else?

---

### Post by jaakan on 2008-09-22
Does it do it if you rename .purple to .purple_old
```
mv .purple .purple_old
```

---

### Post by Bodil on 2008-10-02
It crashes for me whenever I try to connect to a network through an HTTP proxy. Bonjour works fine, but GTalk and MSN makes it crash. This happens when I start with a fresh .purple directory too. :(

---

### Post by dacorr on 2008-10-02
if i recall a segmentation fault is a C++ compiler error, my guess its causing issues with how the updated kernal works

---

### Post by syko21 on 2008-10-02
Pidgin segfaults when you set gnome proxy and the rest of the form does not fill in. If you have the "Use the same proxy for all protocols" option checked and the other spaces are blank and gray then pidgin will crash. Try unchecking then rechecking that option in gnome proxy to fill those boxes in and pidgin will stop crashing. I had this issue too but they told me it was fixed, guess not.

---

### Post by davekenny on 2008-10-02
move doesn't run either..
the 'mv' did help

I cannot try the other stuff because it doesn't get that far!
I'm not sure if its a segementation fault or something else.
it just don't work under 8.04

firefox 3.0.3 also doesn't run...

-davekenny

---

### Post by Kow on 2008-10-02
> **dacorr said:**
> if i recall a segmentation fault is a C++ compiler error, my guess its causing issues with how the updated kernal works

No, it is rarely a compiler error and is in all likelihood a program-level issue.

> 
A segmentation fault occurs when a program attempts to access a memory location that it is not allowed to access, or attempts to access a memory location in a way that is not allowed (for example, attempting to write to a read-only location, or to overwrite part of the operating system).


I would recommend backing up all pidgin-related data to a temp folder and then installing it from scratch. After backing up the data you can do a complete removal of pidgin from synaptic. Same should be done for any installed package with pidgin or libpurple in it. Usually this is just pidgin, pidgin-data, libpurple0 and libpurple-bin.

---

### Post by khc on 2008-10-02
> **syko21 said:**
> Pidgin segfaults when you set gnome proxy and the rest of the form does not fill in. If you have the "Use the same proxy for all protocols" option checked and the other spaces are blank and gray then pidgin will crash. Try unchecking then rechecking that option in gnome proxy to fill those boxes in and pidgin will stop crashing. I had this issue too but they told me it was fixed, guess not.

It's fixed in the next release.

---

### Post by Bodil on 2008-10-11
> **syko21 said:**
> Pidgin segfaults when you set gnome proxy and the rest of the form does not fill in. If you have the "Use the same proxy for all protocols" option checked and the other spaces are blank and gray then pidgin will crash. Try unchecking then rechecking that option in gnome proxy to fill those boxes in and pidgin will stop crashing. I had this issue too but they told me it was fixed, guess not.

Worked for me too. Thanks :)

---

### Post by nystire on 2008-10-11
> **davekenny said:**
> move doesn't run either..
the 'mv' did help

I cannot try the other stuff because it doesn't get that far!
I'm not sure if its a segementation fault or something else.
it just don't work under 8.04

firefox 3.0.3 also doesn't run...

-davekenny

Stupid question, perhaps, but have you rebooted since applying the update?

---

### Post by Seine on 2008-10-22
I get the segfault if I use gnome proxy settings and try to set up a XMPP (for gchat).

If I use environment settings instead it works fine (with http_proxy env setting from terminal).

---

### Post by RamR on 2008-10-27
I get this fault and can't get it fixed.  The previous suggestion from syko21 that seems to be working is that settings within Pidgin Preferences that are checked and unchecked?

---

### Post by syko21 on 2008-10-27
Actually the bug I was referring to has been fixed in  Pidgin 2.5.2. It had to do with the gnome proxy preferences not filling in properly when the "use same proxy for all protocols" option was checked.

---

### Post by RamR on 2008-10-27
OK, so that is not the problem for me.  Is there any other ideas out there?

---

