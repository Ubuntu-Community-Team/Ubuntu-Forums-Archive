---
title: "Extreme instabillity after last upgrade"
date: 2007-02-10
forum: Installation &amp; Upgrades
---

### Post by pecanov on 2007-02-10
After this morning's upgrades (kernel, and gnome stuff), there is much instability on my desktop. Eclipse is a very fine example of it. It crashes constantly.

I tried going back to the previous kernel, but things were just much worst ... even simple gtk widgets were looking very very odd.

Does anyone know what package exactly is "to be blamed"? Will this be fixed soon?

---

### Post by matt_risi on 2007-02-10
My wireless is gone and my sound is sporadic now. What a pain in the ***.

---

### Post by lojic on 2007-02-10
Lost my wifi too. I started a thread specific to the wifi problem here:

[http://ubuntuforums.org/showthread.php?t=358004](http://ubuntuforums.org/showthread.php?t=358004)

but it hasn't resulted in too much explanation as of yet. Maybe you could post your specifics there regarding your wireless hardware, and hopefully some Ubuntu guru(s) will have some answers eventually.

---

### Post by Tanker Bob on 2007-02-10
After doing OK through the initial update recovery yesterday (NVidia card and all), this morning more updates appeared for install.  After installing them, I could not reboot into Kubuntu--even to the recovery mode.  

After numerous attempts to either get into the -10 kernel or recovery mode going, I finally got access to the text shell in kernel -11 recovery mode.  I then installed and ran the Envy script.  That seemed to work, but then the X-Server wouldn't start.  I think that I was in some kind of lala land the first time through, so I did it all over again.  (I just went to the Envy home page and saw the Alt-F1 recovery, which is how I got Envy to finish the second time.)  The second time, everything seemed to work and I'm back up again as far as I can tell.  I thought that things were fixed last night, but apparently not.  This update episode wasn't for the faint of heart.

On the good side, we need to give Alberto Milone, Envy's author, a big raise.  His script has saved more people than I can count in the old thread.  And now me, too!

---

### Post by Tanker Bob on 2007-02-10
Well, I spoke too soon.  I've had two major lockups since my last message.  I've reinstalled the NVidia driver with Envy twice now.  It seems to work each time until I reboot.  Then I have to start over.

There seems to be something really not good about this latest kernel update.  As best I can tell, the lockups themselves are related to (wired) networking and possibly Firestarter.  It looks like the wifi issue may not be so isolated to wifi but may be part of a larger networking issue.

---

### Post by lojic on 2007-02-10
Interesting. I do use Firestarter on the laptop that has wifi issues with the -11 kernel. There's no way I'm going to run my laptop without a firewall, so even if disabling Firestarter helps, it's not an option for me.

I'm still confused by the fact that the update states "ABI bump to -10", so does the update install the "real" -11 kernel, or was it just a version number change because they made an ABI change to the -10 kernel?

I'm a little concerned that the "official" folks seem to think everything is ok now i.e. just recompile some modules and you're good to go. It doesn't seem like that's the case for many people.

---

### Post by Tanker Bob on 2007-02-10
Yeah, I can't say for sure it's Firestarter.  It may be just something in the networking layer that Firestarter trips to failure.  Or it may just be a coincidence that Firestarter was the last app to run before the lockups.  The network was busy during both incidents.  Video was working fine at the time.  That's why I don't think the NVidia drivers are the core issue with the lockups, although they seem to be the reason for the lack of clean reboots.

FWIW, I've recompiled everything that I know of that can be recompiled.  I've changed some program settings to minimize their interface to networking.  Time will tell if any of this makes a difference.

---

