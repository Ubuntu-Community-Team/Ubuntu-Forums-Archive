---
title: "Lyx spellchecker does not work on ubuntu 10.04"
date: 2011-10-29
forum: Installation &amp; Upgrades
---

### Post by xrobbo on 2011-10-29
Hello to all. As many unhappy user of new ubuntu 11.10 but lovers of the old 10.04 I've recently downgraded. Lyx comes in version 1.6 in ubuntu 10.04. I needed to upgrade to the 2.0.1 version, which I did.
Here the problem I have not been able to solve.
The spell checker does not work. Libraries are correctly installed but I cannot access the command spell check and there is not possibility to spell check in any language. I'm quite hopeless because the only way to have the spell check working is downgrading to lyx 1.6. But then I will no more be able to access all the files edited with lyx 2.0.1.
Anybody has an answer for that?
thanks in advance for any suggestion to take me out of this trouble!

---

### Post by linas on 2012-09-09
Per several different discussions, notably here: [http://comments.gmane.org/gmane.editors.lyx.general/70372](http://comments.gmane.org/gmane.editors.lyx.general/70372)
it appears that lyx 2.0 in the more recent ubuntus was compiled without spell-check enabled.   I haven't yet found a launchpad ticket for this.

(I have this problem in precise pangolin)

---

### Post by linas on 2012-09-09
I found teh answer here: Yayyyy!

[http://ubuntuforums.org/showthread.php?t=1929675](http://ubuntuforums.org/showthread.php?t=1929675)

I have now got the answer to this problem from the LinuxFormat Forum.

Check in the Software Centre to see if ENCHANT is installed. If not, install it.  Then start Lyx,select TOOLS, PREFERENCES, LANGUAGE SETTINGS, SPELLCHECKER.  Then at SPELLCHECKER ENGINE, select ENCHANT, press ENTER KEY, and click on SAVE.

You should now have a spell checker!

:KS:KS:KS:KS:KS

---

