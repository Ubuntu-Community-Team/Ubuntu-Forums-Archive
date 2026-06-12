---
title: "Still no sound after restart from Ubuntu 9.10 to Windows XP (CA0106)"
date: 2009-10-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by PiotrekS on 2009-10-27
I have no sound in Windows XP after restart computer with my SB Audigy (CA0106). I hadn't this problem before... In 9.04 it was working good... but now... 
Somebody have similar problem ?

---

### Post by fancypiper on 2009-10-27
I could never get my SB Audigy to work in Windows (tried in 3 different boxen), but I don't have any problems with it in Linux.

---

### Post by PiotrekS on 2009-10-27
> **fancypiper said:**
> I could never get my SB Audigy to work in Windows (tried in 3 different boxen), but I don't have any problems with it in Linux.

I haven't any problem with SB Audigy in Windows. In previous version of Ubuntu though. I have no idea what's going on...

---

### Post by whirlwind on 2009-10-28
Same here.  No sound in Windows Vista Home Premium after installing Karmic RC.  I have an Audigy 2ZS, latest drivers.  When I tried to reinstall the Audigy drivers from Creative it said I don't have a device that can be used with these drivers.  All was good before, I installed over a partition I had previously been using with Fedora.  No changes made to the Windows partition.  Sound works fine in Ubuntu.

And Karmic is great, BTW.  Very well done.

whirlwind

---

### Post by PiotrekS on 2009-10-28
> **whirlwind said:**
> Same here.  No sound in Windows Vista Home Premium after installing Karmic RC.  I have an Audigy 2ZS, latest drivers.  When I tried to reinstall the Audigy drivers from Creative it said I don't have a device that can be used with these drivers.  All was good before, I installed over a partition I had previously been using with Fedora.  No changes made to the Windows partition.  Sound works fine in Ubuntu.

And Karmic is great, BTW.  Very well done.

whirlwind

I think that solution would be installing latest version of ALSA but I'm not sure that it would works.

Unfortunately there is no latest version of ALSA in repository (Maybe I'm wrong).

---

### Post by whirlwind on 2009-10-28
> **PiotrekS said:**
> I think that solution would be installing latest version of ALSA but I'm not sure that it would works.

Unfortunately there is no latest version of ALSA in repository (Maybe I'm wrong).
Thanks for the suggestion, but why would installing ALSA in Ubuntu affect my Windows Vista partition?

whirlwind

---

### Post by PiotrekS on 2009-10-28
> **whirlwind said:**
> Thanks for the suggestion, but why would installing ALSA in Ubuntu affect my Windows Vista partition?

whirlwind

Resources of sound card after restart from Ubuntu is not properly released I think. There is a problem with sound card kernel module... So when you boot Windows sound card cannot be founded.

---

### Post by PiotrekS on 2009-10-28
I have installed latest version of ALSA (1.0.21). Unfortunately it's not working :(

---

### Post by whirlwind on 2009-10-28
I've tried disabling the audio device within Karmic and rebooting into WinVista, still no luck.  Can anyone think of any other workaround?  I don't mind if I don't have sound in Karmic as I only really use it for coding for school.  My games in Windows just aren't as much fun without sound.  :(

---

### Post by jbslaw on 2009-10-28
I think Piotreks is correct.  The workaround is instead of restarting, power off (shut down) from Karmic.  When you power back up you should be starting with a clean slate.  If this doesn't work, you have a broken sound card.

---

### Post by ranch hand on 2009-10-28
> **jbslaw said:**
> I think Piotreks is correct.  The workaround is instead of restarting, power off (shut down) from Karmic.  When you power back up you should be starting with a clean slate.  If this doesn't work, you have a broken sound card.
I think that this is the way to go.

I do not go along with the broken card theory at all.  I believe that your problem is the ram on sound card is still full of Ubuntu.

I had this problem with my dialup modem when I still had Win JerryLewus Pro on here.

I had to hit whatever it was that detected new hardware, even after a complete cold start.  You might try that, it always brought the modem right back up and ready to run.  SB cards should not be too hard a fix.

---

### Post by PiotrekS on 2009-10-29
> **jbslaw said:**
> I think Piotreks is correct.  The workaround is instead of restarting, power off (shut down) from Karmic.  When you power back up you should be starting with a clean slate.  If this doesn't work, you have a broken sound card.

Yes, it works. After shut down everything is OK. 
I tried install latest version of ALSA but it doesn't works so it's not problem with ALSA but with something else... Maybe new HAL architecture on Ubuntu ? Maybe some changes in Linux kernel ? 

Maybe somebody known other workaround ? Shutting down every time is not so comfortable.

---

