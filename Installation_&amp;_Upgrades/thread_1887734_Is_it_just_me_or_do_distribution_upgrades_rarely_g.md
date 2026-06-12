---
title: "Is it just me or do distribution upgrades rarely go flawlessly anymore?"
date: 2011-11-27
forum: Installation &amp; Upgrades
---

### Post by Amurko on 2011-11-27
I've been running Ubuntu on a particular system since 6.10 and have upgraded all the way to 11.10 without reinstalling although the 11.10 upgrade has seriously gotten me to consider reinstalling.

The first few updates in the 6's, 7's, and even 8's went rather flawlessly with all essential components working without any need to go into the terminal to tweak.  In other words, I did not need to ask any questions on the forums or even open a terminal window to solve any minor problems that came up and had Internet, sound, graphics, etc. all working smoothly before and after the update.

After about the 9's and 10's, it seems like a regular occurrence that some critical feature of my system would stop working after each distribution upgrade.  Either the GUI would fail..  or the sound (this time)..  or the Internet..  or some essential program (i.e. Skype, Wine, etc.)

Has Ubuntu been in decline recently?  Or is my experience not typical due to the fact that I'm probably way overdue for a reinstall (this computer started running Ubuntu in 2006 and has not seen a single reinstall yet.)

I'm SERIOUSLY considering reinstalling my system but I need some serious advice about how to save as much of my current setting as possible and not have to spend hours figuring out how to reconfigure everything to the way they are right now.  The idea of having to recreate 5 years of custom settings after reinstalling is enough to give me a panic attack!!! Can someone guide me through the reinstall process as to preserve as many of my current custom settings as possible?  (I've reinstalled another machine before.. even though I preserved the /home directory, the new installation had trouble recognizing the old users' files there and I had gone through many commands in the terminal to get it to recognize those files again.  Can anyone refresh me on that too?)

---

### Post by fantab on 2011-11-27
> **Amurko said:**
> I'm SERIOUSLY considering reinstalling my system but I need some serious advice about how to save as much of my current setting as possible and not have to spend hours figuring out how to reconfigure everything to the way they are right now.  The idea of having to recreate 5 years of custom settings after reinstalling is enough to give me a panic attack!!! Can someone guide me through the reinstall process as to preserve as many of my current custom settings as possible?  (I've reinstalled another machine before.. even though I preserved the /home directory, the new installation had trouble recognizing the old users' files there and I had gone through many commands in the terminal to get it to recognize those files again.  Can anyone refresh me on that too?)

Personally, I never Upgrade. I don't like the idea. I always Clean Install whenever I think and feel I need a newer version. 
I don't use ' /home ' partition at all instead I use just a Linux formatted, ext4 partition which can either be mounted automatically or Manually at each system restart. This way I only have to format only the ' / ' partition without worrying about losing my Data.

Also Ubuntu 11.10 has made a big leap with gtk3 engine. So I think this will cause upgrade issues though I don't know this first hand.

Fresh install is a good idea.

---

### Post by bluexrider on 2011-11-27
> **fantab said:**
>  

Fresh install is a good idea.

ALWAYS! 

I did one upgrade and was a disaster some years ago and vowed to never do that again. PERIOD!

---

### Post by CryptAck on 2011-11-27
I've "upgraded" but never flawlessly either. Every upgrade I do now is a clean install. 

I too set my partitions up so that I don't need to worry about /home data, but only /.

---

### Post by vasa1 on 2011-11-28
The thing I don't like about the upgrade is that there's duplication of bandwidth usage.

First, we (mostly) download the LiveCD to make sure it will play well with our hardware. Then, unfortunately, the upgrade doesn't take input from the LiveCD but from the internet which can be a long process for some of us.

Anyway, just for the record, I did upgrade from 11.04 to 11.10 with no problem but it took me a long, long time since I don't have a fast connection.

---

### Post by Mark Phelps on 2011-11-29
I've not had an update go flawlessly since the 8.04 to 8.10 days ...

So, like the others who replied here, I always now do a clean install.

---

### Post by lisati on 2011-11-29
Join the club!
I'm looking to do a fresh install for my server after a recent update from 9.10 to 10.04 - I'm discovering minor breakages here and there, nothing serious in themselves but sufficiently troublesome to warrant the effort of backing up and starting with a clean install.

---

