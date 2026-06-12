---
title: "Manual parititoning to install Edgy"
date: 2007-01-10
forum: Installation &amp; Upgrades
---

### Post by chettyk on 2007-01-10
I have two hard drives on my computer, sda and hda. The following is the structure of the two drives:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+  83  Linux
/dev/sda2            2433        2675     1951897+  82  Linux swap / Solaris
/dev/sda3            2676        7539    39070080   83  Linux
/dev/sda4            7540        9729    17591175   83  Linux

/dev/hda1               1        7296    58605088+  83  Linux
/dev/hda2            7297        7540     1959930   82  Linux swap / Solaris
/dev/hda3   *        7541        9733    17615272+  83  Linux

```

I have been trying to install Edgy Eft on hda3 with hda2 set as swap using manual partitioning.

But the manual partitioning box during installation insists on setting hda1 as the root partition. When I try to set hda3 as the root partition, I get an error message: "No root file system". I am attaching a screenshot.

Is this a bug or am I doing something wrong? 

Thanks all.

---

### Post by taurus on 2007-01-10
Perhaps you should try to use the alternate CD to install it on your machine since you have more control over where to install Ubuntu.

---

### Post by chettyk on 2007-01-10
Thanks, Taurus. The thought crossed my mind. What sort of desktop does the alternate CD install? The other option is, I suppose, to use a server install and then use apt-get to install a desktop.

By the way, is the problem I had during manual installation due to a bug or is the installation software designed to mount root only on the first partition of a disk?

---

### Post by taurus on 2007-01-10
The alternate CD comes with exactly the same stuff as the LiveCD (Gnome) so you are not missing anything important if you use the alternate CD.  The only major difference is the LiveCD will boot into Live session first while the alternate CD allows you to install, text mode, right away.  Even in text mode, it's not that hard to follow.

---

### Post by chettyk on 2007-01-10
Great. Thanks very much for your help. Taurus.

---

### Post by hollerith on 2007-01-12
Seems to be a pretty fundamental flaw in the LiveCD.  Wouldn't take too much testing to discover that one - unless its intentional :-k (dons tinfoil hat).  

@Taurus: any particular reason you didn't you answer the question you were asked twice?  

](*,)  

In a world of Linux some people might want to keep their Windows partition so they can consult the ubuntuforums.  

Guess I'll just go fetch that alternate CD then...

---

