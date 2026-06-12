---
title: "Ubuntu several upgrade (ad naseum)"
date: 2015-05-11
forum: Installation &amp; Upgrades
---

### Post by david-oldcolo on 2015-05-11
Flame on at me for asking but figure to just point blank it...

A friend (yes, this is true) has a Ubuntu 13.04 install.  Can I just install over it with a 15.04 install DVD?  Or, can someone point me to an upgrade path.  

I have researched and can muck my way thru it but figure why not just ask directly, get flamed, and hopefully get a direct answer.

Flame on (me), but anyone have a pointer on this several version upgrade HowTo.

tx

---

### Post by ubfan1 on 2015-05-11
You might be better off with Ubuntu 14.04 (a long term support version), since 15.04 only has 9 months of support.  That upgrade would be 13.04 -> 13.10    then 13.10 ->14.04.  As detailed in [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)
Backup your files in any case, things can go badly wrong.
The alternative would be to install the 15.04, then restore your files from the backup you took.  Upgrade to 15.10, then 16.04, the next long term support release.
I like to do a fresh install at least every other upgrade -- old stuff does tend to accumulate.

---

### Post by Geoffrey_Arndt on 2015-05-11
Chances of a successful update are minimal.    13.04 is "relatively" an ancient release now.    Best to do full reinstall - - let the installer put the new version over 13.04.   Much faster & safer (using a new iso on DVD or USB-Flash Stick).

---

### Post by sudodus on 2015-05-12
I would recommend to backup everything important from the current system (with 13.04), and after that make a ***fresh install of 14.04 LTS*** (with long time support). Depending on the computer hardware and the preferences of your friend, the end user, you might select a different flavour of Ubuntu. It is worthwhile to consider not only standard Ubuntu, so
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]

---

### Post by Bucky Ball on 2015-05-12
No reason going 13.04> 13.10> 14.04 LTS wouldn't work if your friend hasn't added lots of PPAs and customised his install radically, but it would be a long and tedious process fraught with pitfalls ...

Clean install of 14.04 LTS for mine, after a backup of all important data in case things go pear-shaped, that is. Good luck. ;)

---

### Post by Elfy on 2015-05-12
> **sudodus said:**
> I would recommend to backup everything important from the current system (with 13.04), and after that make a ***fresh install of 14.04 LTS*** (with long time support). Depending on the computer hardware and the preferences of your friend, the end user, you might select a different flavour of Ubuntu. It is worthwhile to consider not only standard Ubuntu, so
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]

Agreed

> **Bucky Ball said:**
> No reason going 13.04> 13.10> 14.04 LTS wouldn't work if your friend hasn't added lots of PPAs and customised his install radically, but it would be a long and tedious process fraught with pitfalls ...

Other than they're going to have to hope old-releases works:)

It might be wise to tell your friend not to leave it so late next time - there are reasons that EOL is announced.

---

### Post by Bucky Ball on 2015-05-12
> **Elfy said:**
> 


Other than they're going to have to hope old-releases works:)



Yea, good point. Could be problematic as 13.04 and 13.10 are both EOL. I think I'm awake now! :)

---

### Post by grahammechanical on 2015-05-12
This is the wiki page for end of life upgrades. Note that you will have to do this twice since 13.10 is also end of life. You need to get that machine on 14.04.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

It can be done. I have done it as an experiment but a fresh install is to be preferred in my opinion.

Regards.

---

### Post by david-oldcolo on 2015-05-13
Thank you all!  I was hoping for ya'll's with experience to present  avenues, and brief explanations as to why.  Everyone has been most, most  helpful and for that I am grateful.  I know these repeated questions are a drag, but hopefully this will benefit others too.  It has me.  

I  followed the advice towards backing up the home dir, flattening and  reinstalling to Ubuntu current.  And then restoring.  Worked a peach.   And in the end shorter than crawling thru sequential upgrades.  

So, much appreciated the responses and while I deserved to get flamed, ya'lls didn't... but ya still can, heh.  

tx, david

---

### Post by sudodus on 2015-05-13
Congratulations :KS

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by david-oldcolo on 2015-05-13
Thank you for the gracious response.  I am grateful for this thread and everyone's pitching in ideas.   It helps to cut to the chase... tho do know I research and rarely ask.  But on this, voices of experience...... help.


> **sudodus said:**
> Congratulations :KS

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by Bucky Ball on 2015-05-13
Well done. You got there! I think second link in my signature is what you might be looking for. Good luck with the OS. ;)

---

