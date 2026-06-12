---
title: "Karmic unreportable kernel suspend error"
date: 2009-08-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by meindian523 on 2009-08-01
I'm running Karmic Koala Alpha3 and while I noticed no problem last time I logged in,when I log in today,Apport tells me that there was a suspend problem with the kernel which prevented it from resuming successfully.So,I click report problem,Apport collects the information,and then tells me "This problem cannot be reported: This is not a genuine Ubuntu package" Recollections of WGA nevertheless,I would like to report this bug,but only if I can find where Apport stores it's collected information.Obviously a bug report which says "Apport says kernel bug,but I don't know what it is" won't exactly work. :P

---

### Post by 23meg on 2009-08-02
Did you compile your own kernel, or install a kernel package from an unofficial repository?

---

### Post by scradock on 2009-08-02
> **23meg said:**
> Did you compile your own kernel, or install a kernel package from an unofficial repository?
I have had exactly the same error message, and I never use any kernels except those from the repository (US or Main). 

Since suspend/resume hasn't worked yet in karmic I'm hoping this is something that will get fixed before release......

---

### Post by meindian523 on 2009-08-02
Uh,no.I installed Karmic (and the kernel) from the Alpha3 CD downloaded from releases.ubuntu.com via torrent.

EDIT:That still doesn't answer the question as to where Apport stores it's information.I would like to add my logs to Launchpad bugs which I reported(and subsequently confirmed as being already reported,and marked as Affecting me to)AFAIK,Apport didn't report my logs(the information) to LP after I selected the "Affects me too" option.IMHO,more the variety of hardware logs the devs can get,the better it is for them to isolate the bug.

---

### Post by taavikko on 2009-08-02
The crash files are located in /var/crash/ folder.

---

### Post by nanog on 2009-08-02
I have a possibly related kernel-suspend issue:

[http://ubuntuforums.org/showthread.php?t=1229143](http://ubuntuforums.org/showthread.php?t=1229143)

You should try running the script described here:

[https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend)

---

### Post by meindian523 on 2009-08-04
> **taavikko said:**
> The crash files are located in /var/crash/ folder.
Thanks.

---

