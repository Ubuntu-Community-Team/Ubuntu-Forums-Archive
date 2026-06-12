---
title: "installing openoffice 3"
date: 2008-10-17
forum: Installation &amp; Upgrades
---

### Post by eric489 on 2008-10-17
Hi all. :)

I just installed kubuntu 8.04 and realised it still had openoffice 2.4

I tought i'd give the third release a try, so I uninstalled the 2.4 and downloaded the latest version. 

The only problem is that once i got the archive uncompressed, i find myself with a folder filled with different .debs :confused:

When clicking on some debs i get an Error message stating : Error Dependency not satifiable.

So what do I do to get openoffice installed  ?

Kinda frustrating when linux is supposed to be so easy.
And I'll say it even if it may shock some of you : Installing progs is way easier on windows...

---

### Post by alresave on 2008-10-17
Hi. Open a terminal, cd to the DEB folder and type
```
sudo dpkg -i *.deb
```
When its finished cd to the desktop-integration folder an repeat the dpkg command above.

---

### Post by eric489 on 2008-10-17
> **alresave said:**
> Hi. Open a terminal, cd to the DEB folder and type
```
sudo dpkg -i *.deb
```
When its finished cd to the desktop-integration folder an repeat the dpkg command above.

what's "cd" ? how do i do it ?

---

### Post by howefield on 2008-10-17
cd means change directory

in other words, navigate to your folder containing the debs.

---

### Post by eric489 on 2008-10-17
> **howefield said:**
> cd means change directory

in other words, navigate to your folder containing the debs.

I got an error message for some debs


:(

---

### Post by 0x29a on 2008-10-17
Did you notcie if the error messages mentioned java? Something to the effect of java environment not installed? I'm not at home to look at my notes so I can't quote exactly what the message says, but if you're seeing what I think you're seeing, the debs you're seeing the errors with are openoffice.org3-dict-en, openoffice.org3-dict-es, and openoffice.org3-dict-fr.

Sound about right?

---

### Post by vratnica on 2008-10-18
I succeeded in installing openoffice  but I cannot start it. when I try to open some OO document or to directly open OO, I just see as it is trying to open it, but it never finishes

---

### Post by 0x29a on 2008-10-18
Interesting. Please try reinstalling using the method you used from above and using your mouse to highlight it, copy and paste all of the output here. That way we can see more of what may be occurring.

I know it seems like a pain in the neck, but things really can be super-simple after a little experience getting used to new tools. Remember the first time you used a computer? Trying to figure out how to list the content of a directory let alone change to it was at first mind-boggling. Linux is just a different paradigm. Here's a link that, while tending to not being terribly empathetic, talks about some of the things that many of us who migrated from a strictly Microsoft diet encountered. It gave me a lot to think about when I started suggesting Linux as an alternative to my friends.

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Thanks!

---

### Post by steveneddy on 2008-10-18
[Try this.]("http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/") This is for 32 bit open office.

For 64 bit open office try this link:

[http://queleimporta.com/en/](http://queleimporta.com/en/)

---

### Post by dbcalo on 2008-10-18
Worked for me.

---

