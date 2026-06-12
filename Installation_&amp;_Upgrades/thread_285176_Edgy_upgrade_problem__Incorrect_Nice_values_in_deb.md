---
title: "Edgy upgrade problem:  Incorrect Nice values in debconf"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by Paradoxdruid on 2006-10-26
I'm trying to upgrade a Kubuntu 6.04 system to Kubuntu Edgy 6.10, and it continually errors out--

It displays the error dialog Debconf "Incorrect Nice value Please enter an integar between -20 and 19", but the only buttons are Next and Cancel.  Next does nothing, cancel ends it...  but also ends the dist-upgrade.

In the terminal, I see ```
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN1> line 4.
```  (if I hit "Next" in the debconf dialog, the final line reference continually advances.

This is preventing x11-common from installing, which is stopping everything else...  Help?

Side-note:  Every solution aptitude offers says not to install upstart, but I think that's an important part of Edgy.  Could these issues have the same root cause?

Thank you for any help!

---

### Post by Paradoxdruid on 2006-10-26
So, no one else has seen this problem?  Maybe I'll end up downloading the CD and reformatting...  Ugh.

---

### Post by pielgrzym on 2006-10-26
I have this problem too ](*,) ](*,) ](*,) this drives me mad :(

---

### Post by pielgrzym on 2006-10-26
Anyone? Please?

---

### Post by Paradoxdruid on 2006-10-27
Just an update-  I thought maybe a package was corrupted, so I cleared my apt-cache and re-downloaded all 600 MB of files.  Nope, still giving the same Niceness error, says it's part of the x11-common installation script.  I think I have a corrupted perl, maybe.  But how to fix that?  If I try to install a new package, it asks me to resolve this mess first.

---

### Post by Paradoxdruid on 2006-10-28
This problem has now occured on 3 systems--  2 Kubuntu dapper and one Ubuntu dapper with Kubuntu also installed.

Here's output from the latest one (which I caught and Ctrl-C'ed before it destroyed the system).
```
Do you want to continue? [Y/n/?]
Writing extended state information... Done
Extracting templates from packages: 100%
DESTROY created new reference to dead object ' Qt::VBoxLayout', <> line 988 during global destruction.
Preconfiguring packages ...
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN47> line 2.
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN52> line 3.
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN52> line 6.
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN62> line 13.
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN67> line 4.
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN67> line 9.
DESTROY created new reference to dead object ' Qt::VBoxLayout' during global destruction.

Received signal.  Aborting x11-common package config script.
```

It also displayed the Incorrect Debconf Nice value dialog, again with "Next" and "Cancel" buttons.

Three machines, 3 failures due to a perl or debconf bug.  Yuck.  I'll try Edgy again in a month or 3.

---

### Post by fraenhawk on 2006-10-30
Same problem here as well, stuck with the next/cancel window. I even tried doing the next to see if it would ever get past it... after about 50 clicks I finally gave up. So I'm stuck mid install and afraid to reboot this machine since everything seems to be working for now in the condition I'm in.

update: found a workaround for debconf here: [http://ubuntuforums.org/showthread.php?t=285853](http://ubuntuforums.org/showthread.php?t=285853). Now successfully running edgy

---

### Post by barrel on 2006-11-06
Same problems here and workaround for me didn;t work since debconf segfaulted.

After a reboot (was able to backup using the running system ;-)
ubuntu hang when trying to startup X (I guess).

What a mess, back to reinstall the previous version and I definitely won't do a dist-upgrade anymore!!!

---

### Post by ramaz on 2006-11-23
I had the same problem. Running sudo dpkg-reconfigure debconf and choosing "dialog" as frontend solved the issue. Thank you very much.

---

### Post by yargevad on 2006-12-07
the dpkg-reconfigure solution worked for me too. just a +1, thanks!

---

### Post by aaronwh98 on 2007-03-19
I had the same problem with Feisty Faun (herd 5).  The problem seemed to be with the x11-common update.  I kept that from updating and everything else updated successfully.

---

