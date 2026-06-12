---
title: "Karmic locks constantly"
date: 2009-10-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by bitchballs on 2009-10-07
Is anyone else noticing this? The problem certainly seems consistent, it happens about every 1-5 minutes regardless of what I'm doing at the time, including nothing. Does anyone know where I could look in the logs to find usefull information about this? I'd like to make a bug report if one hasn't been made already.
 
Oh BTW I'm using a Sager NP5793.

---

### Post by nhasian on 2009-10-07
wow that was an expensive laptop wasnt it?  I've been running karmic on four different makes/models of laptops since alpha4, and i dont think i've had a single lockup.  Can you tell us if your doing the same thing each time the pc locks up?  or is it different every time?  does it crash on firefox, flash pages, does it crash if you just leave the desktop sitting there with no programs running?  Can you disable your wifi adaptor in the bios or hardware switch and see if the lockups stop?  are you using the restricted graphics drivers from the repos or did you install some new drivers youself?

---

### Post by bitchballs on 2009-10-07
Well, it happens pretty much irrespective of what I am doing. It even happens if i boot to recovery mode and just let it sit for a few minutes in the command line. This is a fresh install with no changes made and no additional drivers, though I have made several unsuccessful attempts to download upgrades. None have succeeded because the downloads are always interrupted by lockups and I haven't applied anny of the few packages that were downloaded. I have the wifi turned off witht he hardware switch.
 
Also, the song in your sig gives me the lolz.

---

### Post by nhasian on 2009-10-07
Hmm that is strange.  just for testing purposes have you tried a Hardy 8.04 or Jaunty 9.04 liveCD?  Does it lockup on those as well?  If so you may be looking at a hardware problem like your laptop overheating, or possibly bad memory or hard disk, etc.

---

### Post by kansasnoob on 2009-10-07
I was having that problem and got some helpful info about logs here:

[http://ubuntuforums.org/showthread.php?t=1276146](http://ubuntuforums.org/showthread.php?t=1276146)

I was lucky and updates seem to have "healed" mine.

---

### Post by bitchballs on 2009-10-07
> **nhasian said:**
> Hmm that is strange. just for testing purposes have you tried a Hardy 8.04 or Jaunty 9.04 liveCD? Does it lockup on those as well? If so you may be looking at a hardware problem like your laptop overheating, or possibly bad memory or hard disk, etc.
 
 
I have been running Intrepid since about 4 days ago with no issues.  I updated to Jaunty and the networking all went to ****.  I did some reading and discovered that the Realtek drivers for the network adapter had issues with the kernel in use in Jaunty, but had been fixed as of 2.6.30, I decided to hop on over to Karmic, what with the release coming soon anyway.  Karmic was running fine on the livecd other than being horrendously slow, though I didn't really spend much time on it; I may have missed it if it was a problem there.

---

### Post by nhasian on 2009-10-07
in a terminal type:

```
sudo lshw -C disk
```

this will tell you the make and model of your hard disk.  then go to the manufacturer's website and download the diagnostics tool for your hard disk.  it should be an ISO image that you burn to a CD.  you can boot off the HD diagnostic tool to test your hard disk.

also on the liveCD i believe one of the boot options is to test your computer's memory.

---

### Post by bitchballs on 2009-10-07
Running Windows fine now, and other than the networking issue Jaunty, and before that Intrepid.  I suppose I could check the disk and do a memtest, but I don't see what it has to do with anything.  I'll post later about it tho I got other stuf to do right now.

---

### Post by VMC on 2009-10-07
> **bitchballs said:**
> Running Windows fine now, ...I didn't notice any previous reference to Windows. Was it also effected?

While in Windows you can run eventvwr and look at any reports there that might shed some light. If it appears on eventvwr then it would be hardware related, if not then assume its just linux driver somewhere.

---

