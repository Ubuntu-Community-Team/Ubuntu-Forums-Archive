---
title: "from 8.04 to 10.04 via upgrade-manager"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by etienne.mon on 2010-04-30
Hello,

I am would like to upgrade my 8.04 LTS to 10.04 via the upgrade-manager. But
upgrade-manager just propose to my 9.04 and not 10.04.
Of course I do not want to go by 9.04 then 9.10 then 10.04:)
Is it possible to pass from 8.04 to 10.04 via upgrade-manager ? or shall I burn a CD and install it.


Thank, 

Etienne

PS may be I should wait july to get the 10.04 LTS ?

---

### Post by byStanderone on 2010-04-30
a direct upgrade from hardy to lucid is not possible...use a live cd install instead.

---

### Post by etienne.mon on 2010-04-30
thanks for your reply,

I also found this that help me
[http://ubuntuforums.org/showthread.php?t=1466355](http://ubuntuforums.org/showthread.php?t=1466355)

but it does not solve the problem :(

---

### Post by Arand on 2010-04-30
LTS -> LTS is fully possible
As it has always been

see: [https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades)

- Arand

---

### Post by etienne.mon on 2010-04-30
I suppose it is possible but **upgrade-manage**r does not propose it
I am currently on 8.04 and he proposes 9.04...which is really strange because the next version was 8.10 and the last was 9.10 or now 10.04.

---

### Post by galleon03 on 2010-04-30
It's possible that you have "normal releases" selected for your upgrades. To check, go to:
[INDENT]System -> Administration -> Software Sources -> Updates[/INDENT]

At the bottom, you should see 'Release Upgrade'. To see the upgrade for 10.04, you need to have "Long term support releases only" selected. Once you have that selected, press Alt-F2 and type:

[INDENT]update-manager --devel-release   [/INDENT]

then click "Check" for new updates. Then, if the right one shows up, continue upgrading like they describe [here]("http://www.ubuntu.com/getubuntu/upgrading"). 

I had the same issue earlier and this solved it, so I hope it helps you get going. :)

edit: just noticed the link you posted. If this doesn't work, then perhaps try upgrading through the alternate cd.

---

