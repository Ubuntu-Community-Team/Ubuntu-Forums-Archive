---
title: "GDM could not write to your authorization file."
date: 2007-02-18
forum: Installation &amp; Upgrades
---

### Post by ebcovert3 on 2007-02-18
Ok, I have searched threw a multitude of forums and have found nothing so far to help.  So now I am registered and am posting my request.  I installed one of the "you need to upgrade you linux kernel" updates via update-notifier (done it a hundred times with no issues).  When I went to log on after doing it I was presented with my normal graphical login screen.  However, I get a message about:
```
GDM could not write to your authorization file. 
```
Not enough disk space or permissions are incorrect.  Checked the perms - they are fine. I ran DF and here is what I get:```

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/mapper/Ubuntu-root
                      75924576  74634108         0 100% /
varrun                  127464       176    127288   1% /var/run
varlock                 127464         4    127460   1% /var/lock
udev                    127464       116    127348   1% /dev
devshm                  127464         0    127464   0% /dev/shm
lrm                     127464     18856    108608  15% /lib/modules/2.6.15-28-386/volatile
/dev/hda1               233335     55763    165124  26% /boot
```
100%??!  Any ideas?  I am completely stumped.  This is the only time I have ever had a problem with Ubuntu that I could not fix  I am completely stumped.  TIA!

---

### Post by taurus on 2007-02-18
Boot into recovery mode from the GRUB menu and at the prompt, type

```
aptitude clean
rm ~/.Trash/*
rm /home/**username**/.Trash/*
(Replace **username** with the actual name of your login name.)
df -h
```

---

### Post by ebcovert3 on 2007-02-18
Thanks.  I will give it a try later tonight.  Is this a common issue or did I most likely just hose something up?

---

### Post by ebcovert3 on 2007-02-18
Ok, I ran the commands in the order you listed them (in recovery mode for the last linux image I have on the machine).  Then I ran df -h again got what appears to be the same result.  My "/" directory is still pegged at 100%.

---

### Post by taurus on 2007-02-18
What's the output of this command while you are still in the recovery mode?

```
du -h /var
```

---

### Post by ebcovert3 on 2007-02-20
Attached is the results of the du -h /var command.  thanks!

PS - Sorry about the delay.  I was OBE at work.

---

### Post by ebcovert3 on 2007-02-20
Ok, after looking more closely at the /var/backup directories in the du.txt file I posted, I noticed some anomalies.  Several of my automated backup files were HUGE.  On a whim, I started clearning out that directory and re-ran:
<code>df -h</code>
Low and behold, my disk space was back where it should be.  Finally, I was able to log in as I expected.  Thank you very much for pointing me in this direction.

---

