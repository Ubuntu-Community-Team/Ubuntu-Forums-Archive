---
title: "How do you use Intrepid?"
date: 2008-07-02
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by BackwardsDown on 2008-07-02
This is the first time I'm using an alpha version of Ubuntu, a few months ago I did test the Beta's of hardy.

Now this Alpha seems so stable to me, except for a few missing features like sound I can live with. I'm running Intrepid the last few days full time to spot as many bugs as I can. I know it can be dangerous to use it as a primary os but having my files in a separate partition, a weekly backup, hardy as a rescue-OS and a live-cd nearby I feel pretty safe. 

Now I was wondering if more people do that. Do you use Intrepid as your primary OS? Or do you just boot it up once in a while to check for bugs?

---

### Post by Seventh Reign on 2008-07-02
I have my II installed on a backup system that I dont care if I lose anything on it.  I try to go through the motions on it as if I was actually using it like I would the system I'm on now.  I figure its better for testing if you actually USE it.  

So far the only bugs I've found are;
1. The no sound.  
2. The same bug is still there when you change your login graphic.  It doesnt save and you have to do it twice.

McDonald's might sue me ... but I'm Lovin` It.

---

### Post by JACooks on 2008-07-02
Similarly, I install it on my laptop.  We always have laptop bugs to test with releases, and I just use the laptop when I'm in front of the TV.  Games, email, web browsing and the like.  I've got Hardy on the desktop for important stuff.

---

### Post by autocrosser on 2008-07-02
I use it as my main OS--I have a backup Intrepid install that I update one a week & a Hardy just in case. I keep separate /home(s) for each & sync them every couple of weeks.

---

### Post by Gina on 2008-07-02
I have Intrepid installed on mt new AMD64 desktop and my laptop.  The other desktop - a P4 multimedia machine is the only one with MS Windows (XP) installed (which I need occasionally) and I don't run development software on that at least until the Beta phase when I'm pretty sure there will be no disasters.

My AMD64 machine has a problem with the partition table on the HD (only the one at present) which TestDisk on the SystemRestoreCD seems unable to fix.  I'm currently backing up everything ready to either try to fix it or wipe clean and start anew.  I don't actually have anything I can't regenerate but keeping a backup will save time.  It would seem either Intrepid or something messed up the partition table - some partitions are usable but I can't format new ones.

---

### Post by Nullack on 2008-07-02
IMHO the best way to test it is not in a VM, and to install it direct on a machine you can recover from if the worst happens. I use it as my daily and I think that has helped my testing process.

For example the bug I reported on the gnome file roller where it segfaults in certain conditions would not have most likely not been found otherwise.

I find alot of information is kept in the logs too, /var/log, and this can be handy to trawl through.

---

### Post by almostlinux on 2008-07-02
Had an installation of hardy but got rid of it.  If there are issues, I'll be forced to find a way out... but so far I've had no problems at all!

---

### Post by spamzilla on 2008-07-02
I had it installed on virtualbox, but I never used it. I upgraded hardy to intrepid, so I am now using it all the time :D

Problems?
> No sound
> Login screen sometimes doesn't appear but login sounds still go off.

---

### Post by pluckypigeon on 2008-07-02
I have hardly any problems with it.

I did have a problem with the sound coming through the pc speaker but I just changed the settings in pulseaudio.

Also the bootsplash loading graphic was broken and spread around the screen.

---

### Post by philinux on 2008-07-02
> **spamzilla said:**
> I had it installed on virtualbox, but I never used it. I upgraded hardy to intrepid, so I am now using it all the time :D

Problems?
> No sound
> Login screen sometimes doesn't appear but login sounds still go off.

It's been said on here, just change to alsa mixer in sound prefs until PA fixed.

I'm running it in VBox for now, Might install on second hard drive and wipe mint which I'm not keen on. Might do that with alpha 2.

---

### Post by MaX on 2008-07-02
Not at all at the moment, My vacation is soon here and I have no time to patch nvidia drivers etc... I'll probably use it 30% of the time after I come back again.
I watch alot of film/tv through the computer and right now the video out only works in Vista...

---

### Post by ronacc on 2008-07-02
I run any dev version on its own drive on a test box and have a seperate stable box to fall back on .I use the dev install as my "main" system unless the function I need is broken . any data I want to survive an oops is saved to a seperate data drive and backed up regularly .

---

### Post by Nullack on 2008-07-02
Haha ronacc your sig is GOLD! Haha

FWIW I just tried Kubuntu daily alternate and the install failed. Back to gnome for me. KDE4 looks not to be robust from OpenSuse user feedback.

---

### Post by spamzilla on 2008-07-02
> **philinux said:**
> It's been said on here, just change to alsa mixer in sound prefs until PA fixed.

Oh yes, thanks :KS

---

### Post by mitchellcipriano on 2008-07-03
I have it installed in VMs on each of my machines. I can then use it as my primary OS, but I can always drop back to a stable environment with a couple key clicks if needed.

---

### Post by marine63 on 2008-07-03
> **Seventh Reign said:**
> I have my II installed on a backup 
So far the only bugs I've found are;
1. The no sound.  
2. The same bug is still there when you change your login graphic.  It doesnt save and you have to do it twice.


3. the brown colored theme...

---

