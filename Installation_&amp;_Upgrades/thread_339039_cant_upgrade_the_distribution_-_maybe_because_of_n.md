---
title: "cant upgrade the distribution - maybe because of nvidia-glx"
date: 2007-01-15
forum: Installation &amp; Upgrades
---

### Post by amitm02 on 2007-01-15
Hello,

while trying to update my packages through the update manager, i was asked to upgrade the distribution.
but then i received the following message:

A unresolvable problem occurred while calculating the upgrade.
Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.

the log file shows:
"""
Starting 2
Investigating nvidia-glx
Package nvidia-glx has broken dep on nvidia-kernel-1.0.9629
  Considering linux-restricted-modules-2.6.17-10-386 0 as a solution to nvidia-glx 0
  Removing nvidia-glx rather than change nvidia-kernel-1.0.9629
Done
MarkUpgrade() called on a non-upgrable pkg: 'ubuntu-desktop'
ERROR:root:Dist-upgrade failed: 'A essential package would have to be removed'
Installing libberyldecoration0 as dep of beryl
Starting
Starting 2
Investigating nvidia-glx
Package nvidia-glx has broken dep on nvidia-kernel-1.0.9629
  Considering linux-restricted-modules-2.6.17-10-386 0 as a solution to nvidia-glx 0
  Removing nvidia-glx rather than change nvidia-kernel-1.0.9629
Done
MarkUpgrade() called on a non-upgrable pkg: 'ubuntu-desktop'
ERROR:root:Dist-upgrade failed: 'A essential package would have to be removed'
Installing libntlm0 as dep of xchat
Installing libberyldecoration0 as dep of beryl
Starting
Starting 2
Investigating nvidia-glx
Package nvidia-glx has broken dep on nvidia-kernel-1.0.9629
  Considering linux-restricted-modules-2.6.17-10-386 0 as a solution to nvidia-glx 0
  Removing nvidia-glx rather than change nvidia-kernel-1.0.9629
Done
MarkUpgrade() called on a non-upgrable pkg: 'ubuntu-desktop'
ERROR:root:Dist-upgrade failed: 'A essential package would have to be removed'
Installing python-all as dep of beryl-settings-bindings
Installing libntlm0 as dep of xchat
Installing libberyldecoration0 as dep of beryl
Starting
Starting 2
Investigating nvidia-glx
Package nvidia-glx has broken dep on nvidia-kernel-1.0.9629
  Considering linux-restricted-modules-2.6.17-10-386 0 as a solution to nvidia-glx 0
  Removing nvidia-glx rather than change nvidia-kernel-1.0.9629
Done
MarkUpgrade() called on a non-upgrable pkg: 'ubuntu-desktop'
"""

if i understand this correctly i have a non compatible nvidia-glx.
is that really the case?
i've got ver 1.0.9629+2.6.17.6-2~amaranth(edgy)
i can force the package nvidia-glx ver 1.0.8776+2.6.17.7-10.1(edgy-security)
but 
1) will it solve the problem?
2) will that version will be able to support my beryl under xorg 7?

any suggestions?
thanks in advance
amit man

---

### Post by bkeithly on 2007-01-16
amit, 

Your not alone, myself and a few others are having the same issue.

You and I seem to be having the exact same issue (although I am currently not running beryl).

Just trying to get a fire going so we can get this issue fixed(I posted about it several times and got no responses).  Anyway if you get an answer please let me know!

---

### Post by amitm02 on 2007-01-16
Hi after talking with some people at #ubuntu-glx i solved it.

add the repos:
(you need only one but i don't remember which)

deb [http://SeerOfSouls.com/](http://SeerOfSouls.com/) edgy e17
deb-src [http://SeerOfSouls.com/](http://SeerOfSouls.com/) edgy e17
deb [http://SeerOfSouls.com/](http://SeerOfSouls.com/) edgy contrib
deb-src [http://SeerOfSouls.com/](http://SeerOfSouls.com/) edgy contrib
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main


the update and upgrade. the nvidia-glx will be upgrade and problem solved (at least for me)

best luck
amit

---

### Post by Seine on 2007-01-20
The following worked for me. (You may not get the same kilometreage). 

[http://www.ubuntuforums.org/showthread.php?p=2041710#post2041710](http://www.ubuntuforums.org/showthread.php?p=2041710#post2041710)

---

### Post by bkeithly on 2007-01-20
Using envy fixed the issue for me.    


At least so far.

---

