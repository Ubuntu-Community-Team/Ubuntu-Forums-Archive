---
title: "[SOLVED] Asking &amp;quot;Insert Disc&amp;quot; for installing new programs"
date: 2008-01-06
forum: Installation &amp; Upgrades
---

### Post by hnprashanth on 2008-01-06
I have installed Ubuntu 7.10 through a DVD came with indian Magazine Digit. Everything working fine. But when I tried installing some new programs, it asks for 
> Please insert the disk labeled:
Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)
in drive /cdrom/

If I insert that DVD it repeatedly asking same thing.

I even tried of writing separate DVD including directories related only to Ubuntu (since DVD provided magazine has some other files/windows applications on it).

Pleaase help!!!

---

### Post by PmDematagoda on 2008-01-06
Open Software Sources in System>Administration>Software Sources and then uncheck the check box for the Ubuntu installation CD, that should fix the problem.

---

### Post by LaRoza on 2008-01-06
If you have high speed internet, you can disable the disk asking in System->Administration->Synaptic Package Manager

In there: Settings->Repositories and then uncheck the disk entry.

---

### Post by stalker145 on 2008-01-06
> **hnprashanth said:**
> I have installed Ubuntu 7.10 through a DVD came with indian Magazine Digit. Everything working fine. But when I tried installing some new programs, it asks for 


If I insert that DVD it repeatedly asking same thing.

I even tried of writing separate DVD including directories related only to Ubuntu (since DVD provided magazine has some other files/windows applications on it).

Pleaase help!!!

Try ```
sudo nano /etc/apt/sources.list
``` in the terminal, comment out the line that calls for the DVD/CD```
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

```(should be at the very top), save and exit, ```
sudo aptitude update
```and install the program of your choice.

@LaRoza OK, that's twice in the last few minutes. Go back to the Community area ;) 

Please don't kill me, I'm kidding.

---

### Post by hnprashanth on 2008-01-06
Thank you all,
In either way my problem got resolved.
Thanks again!! :guitar:

---

