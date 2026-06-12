---
title: "winbind - dist-upgrade fails due to missing ;;"
date: 2008-08-01
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by eeclark on 2008-08-01
If anyone else has the problem where a dist-upgrade fails due to a missing ;; in winbind, here is what I did to fix it.
I use vi, but you can use gedit if you want.
```

sudo vi /etc/init.d/winbind

```
scroll to the bottom and insert
```

;;

```
just above
```

*)

```
then enter the escape key and exit with x.
Re run you dist-upgrade and you should be fine.

---

### Post by Nullack on 2008-08-01
People should not use dist-upgrade, weve had extensive talks about why in previous threads.

---

### Post by eeclark on 2008-08-01
Ok...
That is what I use.
I do not know if update throws the same error or not...so YMMV.
Thought I'd share.

---

### Post by knarf on 2008-08-01
Using dist-upgrade you at least get to see why a package croaks. When you use update-manager you only get a failure message and a chance to report a bug. As to what went wrong update-manager leaves you in the dark. So, by all means use them both... if you are able to fix a problem when it shows up. If something goes wrong try apt-get -f install and see what the problem is, try to solve it if you can, report the bug and submit a patch. That way everyone can contribute to Ubuntu according to their capabilities...

---

### Post by Nullack on 2008-08-01
Brocken packages are reported automatically

Whats wrong with sudo apt-get update? Theres plenty wrong with dist-upgrade during an alpha

---

### Post by BackwardsDown on 2008-08-01
a fix already has been released

---

### Post by Eclipse. on 2008-08-01
dist-upgrade isnt the problem, its just a bug.I have the same problem with just the usual apt-get upgrade.A fix has been released.

---

### Post by Nullack on 2008-08-01
dist-upgrade is a problem because it ignores package dependencies which is especially problematic during an alpha

---

### Post by aamukahvi on 2008-08-02
I have this problem and no dist-upgrades. Just update-manager.

---

### Post by nystire on 2008-08-02
I was always under the impression that update simply updates the current packages to the newer versions. Dist-upgrade also allows packages to be replaced with completely different packages.

---

### Post by knarf on 2008-08-02
There's no need to be dogmatic about using or not using dist-upgrade versus update-manager, both have their places. Using dist-upgrade is faster and somtimes gives more insight in why things don't work. With update-manager the process takes longer, needs a running X session and error messages are hidden but the chance of ending up with a non-functional system is smaller. Alpha or not, update-manager sometimes hides to much useful information. Use what you feel comfortable with but realise the responsibility which comes with the power of the command line. In other words, if you break it... you get to keep all pieces.

---

### Post by eeclark on 2008-08-02
Well said.
I always use dist-upgrade. I also monitor to see what it wants to do. For example, if it says "I want to remove xorg.", I say "No" and stop the process. Then in a few days I try the dist-upgrade again to see if the dependencies are fixed.

Like I said, YMMV.

---

### Post by meborc on 2008-08-02
> **Nullack said:**
> Whats wrong with sudo apt-get update? Theres plenty wrong with dist-upgrade during an alpha

emm... you must be meaning **sudo apt-get upgrade** since update just updates the repository info, it does not upgrade the programs

and without dist-upgrade, a change in ubuntu development where one pack is removed or substituted with something else will never reach your computer as upgrade does not remove packages

in short words - dist-upgrade will probably break your computer, upgrade will leave you with not so up-to-date system with a LOT of packages unable-to-upgrade

---

### Post by plun on 2008-08-02
> **meborc said:**
> 

in short words - dist-upgrade will probably break your computer, upgrade will leave you with not so up-to-date system with a LOT of packages unable-to-upgrade


No a dist-upgrade doesn't normally break a computer  :)

In some cases it can break a computer but its clearly showed
in the terminal output before a user confirms that its OK to do this.

Aptitude can also be used for different solutions.

Just standard Debian apt commands. Nothing to be afraid of...IMHO

---

### Post by meborc on 2008-08-02
> **plun said:**
> No a dist-upgrade doesn't normally break a computer  :)

In some cases it can break a computer but its clearly showed
in the terminal output before a user confirms that its OK to do this.

Aptitude can also be used for different solutions.

Just standard Debian apt commands. Nothing to be afraid of...IMHO

thats what i meant :) 

i was just worried about the *dist-upgrade is bad, use update* thing ;)

i use dist-upgrade to keep me on the edge and reading before confirming has become my habit

---

### Post by Nullack on 2008-08-02
So we dont reinvent the wheel, people interested in the problems with doing a dist-upgrade during an alpha should search this sections thread history for some informed comments :)

---

### Post by plun on 2008-08-03
> **Nullack said:**
> So we dont reinvent the wheel, people interested in the problems with doing a dist-upgrade during an alpha should search this sections thread history for some informed comments :)

Well... there are maybe more difficult challenges then a dist-upgrade for
a development version.

Late in Hardys development
[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2008-March/000401.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2008-March/000401.html)

A user without backups should NOT run a development version. IMHO....

Maybe it&#347; also a good idea to learn about CLI commands when running
a dev version.


A starter/entrance to MOTU perhaps....:)

---

### Post by Benjamin_Lebsanft on 2008-08-06
Winbind still fails to install, where did you find the updated version?

---

### Post by ricktick on 2008-08-12
> **eeclark said:**
> If anyone else has the problem where a dist-upgrade fails due to a missing ;; in winbind, here is what I did to fix it.
I use vi, but you can use gedit if you want.
```

sudo vi /etc/init.d/winbind

```
scroll to the bottom and insert
```

;;

```
just above
```

*)

```
then enter the escape key and exit with x.
Re run you dist-upgrade and you should be fine.

re did this  and the tiny vi version included with 8.10 did not 
exit with x but started erasing the last part of the code in windbind so did a hard shutdown  
now have a few problems have no internet connection in 8.10 
so wonder if winbind is the problem 
and can't get into 8.10 either as it stopped the connection when the splash screen had the login problem any suggestions ??
Thanks for the attention

---

