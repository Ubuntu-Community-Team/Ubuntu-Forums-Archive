---
title: "Lenovo T500 won't suspend afte upgrade"
date: 2010-08-11
forum: Installation &amp; Upgrades
---

### Post by onthenarrowpath on 2010-08-11
I'm experiencing an annoying issue since I upgraded from 9.10 to 10.4: when I try to put my Laptop to sleep, the control sign for suspension starts blinking and that's it: the system hangs and I've got to kill it with pressing the power button. Resuming doesn't work either, same symptoms.

Does anybody have an idea why this happens? It seems that noone else has this problem with a Lenovo T500...

Any help greatly appreciated!

---

### Post by sijodk on 2010-10-05
I'm having a very similar problem. I installed 10.4 and everything was  fine for a week or so, then suspend stopped working with the same  symptoms you describe. I haven't yet found a solution to the problem,  though.

---

### Post by onthenarrowpath on 2010-10-11
I've done some more researching about our problem, it seems that other users experience similar, though not identical problems. I've found some suggestions to solve it, but it involves messing with kernel configurations and stuff. Maybe we should just try out 10.10 (which should released now) and hope that the problem thus dissolves as easily as it has evolved. I will probably install 10.10 tomorrow and post my experiences with regard to suspending a T500.
Greetings,
Reto

Update: I haven't been proposed to upgrade so far, which is strange regarding the fact that 10.10 should be out since 10.10. I'll inform you as soon as I've updated

---

### Post by onthenarrowpath on 2010-10-23
So, I finally got this Meercat installed, and this really solves the problem. I can suspend as much as I want now. And I didn't have any issues except the one described [here]("http://ubuntuforums.org/showthread.php?t=1592487") (with a quick and efficient solution by yazid1).

Hope it helps!

PS: I am unsure whether I should mark this thread solved (after all, upgrading to a new version is not really the typical solution to such an issue). Maybe some visiting admin can tell me whether this is appropriate?

---

### Post by Russel_Winder on 2010-10-24
I am having the opposite problem Lucid used to suspend fine on my T500 now I have upgraded to Meerkat, the machine will not suspend.  I have to use Debian Squeeze to have a suspendable machine.

The symptoms of the failed suspend are as everyone knows, closing the lid or selecting the suspend menu option causes the "suspend" light to start flashing but it never stops.

---

### Post by bofphile on 2010-10-25
Same problem here on my T500 (2082-7SG). Suspend worked fine on previous version of Ubuntu but not anymore on 10.10.
I found this bug report [https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/644223]("https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/644223")
I hope this will be solved quickly.

---

### Post by onthenarrowpath on 2010-10-26
Thanks for the link, bofphile. They suggest there that the problem could be solved with kernel versions 2.6.36 upwards (currently, I have installed 2.6.35.22).
And, yeah, the hybernate problem still persists, even on my machine. But strangely I can suspend as much as I want without any problems (I do it a lot every day).
So, I won't mark this thread solved, definitely not.

---

### Post by ghsfr33d0m on 2010-10-27
Same issue as everyone else, on a Lenovo SL410. Attempt to suspend, screen blanks as if suspending, 'suspend light' starts flashing, and it hangs. This laptop had the same issue for 10.04, and it persists to 10.10.

---

### Post by b49P23TIvg on 2010-12-09
This,  from bofphile's  post, fixed  the  problem in  ubuntu 10.10  on
Lenovo T500 and  impedes nothing I do?  However,  the "restart" option
doesn't  (or still  doesn't)  quite work.   When  rebooting there's  a
timeout dropping into a shell at which point I exit.

# /etc/modprobe.d/blacklist.conf
# suggested blacklist to fix lenovo suspend failure.  lambertdw
blacklist parport
blacklist parport_pc
blacklist ppdev
blacklist lp
blacklist tpm_tis

---

### Post by kiracofe8 on 2011-02-09
Contrary to what everyone says, it seems that "blacklist" does not completely prevent modules from loading.  I did exactly as b49P23TIvg did but 'parport' and 'lp' were still being loaded, and still preventing a clean suspend.  I also had to remove 'lp' manually from /etc/modules  (ubuntu 10.10, T500).

Daniel

---

