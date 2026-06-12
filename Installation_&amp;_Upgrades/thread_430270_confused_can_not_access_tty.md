---
title: ":confused: can not access tty"
date: 2007-05-02
forum: Installation &amp; Upgrades
---

### Post by gerrydeng on 2007-05-02
:confused: I downloaded the iso file of 7.04,named ubuntu-7.04-desktop-i386.iso,and the md5 is right.I burned it ,but I got a error mesage when I install it.

can't access tty; job control turned off

I searched the forums,but I did not get any answer.Some body said  they get the same error message when they upgrade from 6.10 to 7.04,but I maked the new install.

Who can tell me why,waiting......

---

### Post by theGasman on 2007-05-02
I and many others are having the same problem as you.
Nobody seems to have a solution I'm afraid!

Martin

---

### Post by gerrydeng on 2007-05-02
Is this depend on the hardware?Maybe it is a bug of revison 7.04.
Who can give a answer?

thx!

---

### Post by Topsiho on 2007-05-02
It is a problem that occurs on some computers and not on others. You can check the bug reports on Launchpad and see there whether there are solutions, there is one particular for this bug: #78380.

Maybe you could use the Alternate CD, this CD installed feisty on my computer without any problem.

Topsiho

---

### Post by hmann on 2007-05-02
I had the exact same problem..

all i did to get it to work was this:

when you get to the menu press F6

edit the line at the bottom:
xxxxxxxxxxxxxxxxxxxxxxxxxx splash --

and make it:
xxxxxxxxxxxxxxxxxxxxxxxxxx splash irqpoll --

hope this helps?


regards,
hmann

---

### Post by jerrylamos on 2007-05-02
There are a couple of fixes to this problem in my post "Workarounds" in "Installation and Upgrades".  

In trying to speed up boot, Ubuntu (and Debian) development are trying to do operations in parallel.  My interpretation, In some cases triggered by time dependencies some function will try to operate before a dependency is active, and crash.

I haven't tried the "irqpoll" fix; that might be interesting.  What I need is an F6 option to boot serially like Edgy and Dapper do.

Cheers, Jerry

---

### Post by Topsiho on 2007-05-03
"In trying to speed up boot, Ubuntu (and Debian) development are trying to do operations in parallel. My interpretation, In some cases triggered by time dependencies some function will try to operate before a dependency is active, and crash."

Great, (in the sense: good to know something)

I knew something must have been changed in the installer. This change seems to backfire on some computers. Better a (little) slow boot than a boot that does not work.
Trouble for the developers is that on most computers this parallel processing seems to work flawlessly.

The installer in the alternate CD seems not to be affected.

Topsiho

---

